# 辨别 DNS 是否被污染

图中可以看到我们的 ISP 的 DNS 服务器在图中叫做 DNS Recurser，在解析一个域名的时候，总共经过了以下的步骤，图是以 www.wikipedia.org 作为示范的：

  1. 向 root 服务器获取该 gTLD 的管辖服务器，图中为 org 结尾的域名
  2. root 服务器返回 org 的管辖服务器
  3. 向 org 的管辖服务器查询，谁来负责解析 wikipedia.org 这个域名的
  4. org 的管辖服务器返回解析 wikipedia.org 的服务器 IP 地址
  5. 向 wikipedia.org 的解析服务器发出查询，解析 www.wikipedia.org 的 IP 地址
  6. 拿到最终要的 IP 地址

共6个步骤。那么如果在最后一次查询的时候，有人假冒了 wikipedia.org 的解析服务器，则可以在中间进行欺骗攻击，致使用户最后得到的 IP 地址不是真实的地址。如图所示，

![](https://botu.me/wp-content/uploads/2011/08/563px-An_example_of_theoretical_DNS_recursion.svg_1.png)

解析请求被劫持

更详细的关于 DNS 的内容，可以自行参考 rfc1035（[http://tools.ietf.org/html/rfc1035](http://tools.ietf.org/html/rfc1035)）。

### 手工模拟

以上是大致的解析原理，我们手工一步一步来模拟解析的每个步骤吧。这里我用的环境是北京联通 ADSL + Mac OS X 10.7 『Lion』 + 某国家 VPN 一条。工具用到了 dig 和 tcpdump 来完成，Windows 下默认木有俩工具似乎，大家自行寻找吧，或者找一个 GNU/Linux 发行版装上，个人推荐 Ubuntu，有 red hat 情节的，就 Fedora 好了。首先用联通的 ADSL 来试验下

`$ dig //直接获取根服务器的地址`

`

; <<>> DiG 9.7.3 <<>>  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 12586  
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:  
;. IN NS

;; ANSWER SECTION:  
. 473766 IN NS e.root-servers.net.  
. 473766 IN NS c.root-servers.net.  
. 473766 IN NS j.root-servers.net.  
. 473766 IN NS h.root-servers.net.  
. 473766 IN NS m.root-servers.net.  
. 473766 IN NS f.root-servers.net.  
. 473766 IN NS g.root-servers.net.  
. 473766 IN NS l.root-servers.net.  
. 473766 IN NS b.root-servers.net.  
. 473766 IN NS k.root-servers.net.  
. 473766 IN NS d.root-servers.net.  
. 473766 IN NS i.root-servers.net.  
. 473766 IN NS a.root-servers.net.

`

`;; Query time: 30 msec ;; SERVER: 202.106.46.151#53(202.106.46.151) ;; WHEN: Sat Aug 13 22:18:56 2011 ;; MSG SIZE rcvd: 228`

这里我们可以看到，全球的域名根服务器共有从 a 到 m，共 13 组服务器。继续去 dig 出来这些服务器的地址吧，随便找一个好了

`$ dig e.root-servers.net`

`

; <<>> DiG 9.7.3 <<>> e.root-servers.net  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2043  
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:  
;e.root-servers.net. IN A

;; ANSWER SECTION:  
e.root-servers.net. 560668 IN A 192.203.230.10

`

`;; Query time: 29 msec ;; SERVER: 202.106.46.151#53(202.106.46.151) ;; WHEN: Sat Aug 13 22:21:10 2011 ;; MSG SIZE rcvd: 52`

这里我们抓到了其中一组的 DNS 根服务器 e.root-servers.net 的地址为 192.203.230.10，继续

`$ dig -t ns @192.203.230.10 com.`

`

; <<>> DiG 9.7.3 <<>> -t ns @192.203.230.10 com.  
; (1 server found)  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11080  
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 13, ADDITIONAL: 15  
;; WARNING: recursion requested but not available

;; QUESTION SECTION:  
;com. IN NS

;; AUTHORITY SECTION:  
com. 172800 IN NS m.gtld-servers.net.  
com. 172800 IN NS d.gtld-servers.net.  
com. 172800 IN NS g.gtld-servers.net.  
com. 172800 IN NS c.gtld-servers.net.  
com. 172800 IN NS e.gtld-servers.net.  
com. 172800 IN NS k.gtld-servers.net.  
com. 172800 IN NS h.gtld-servers.net.  
com. 172800 IN NS j.gtld-servers.net.  
com. 172800 IN NS a.gtld-servers.net.  
com. 172800 IN NS f.gtld-servers.net.  
com. 172800 IN NS i.gtld-servers.net.  
com. 172800 IN NS b.gtld-servers.net.  
com. 172800 IN NS l.gtld-servers.net.

;; ADDITIONAL SECTION:  
a.gtld-servers.net. 172800 IN A 192.5.6.30  
a.gtld-servers.net. 172800 IN AAAA 2001:503:a83e::2:30  
b.gtld-servers.net. 172800 IN A 192.33.14.30  
b.gtld-servers.net. 172800 IN AAAA 2001:503:231d::2:30  
c.gtld-servers.net. 172800 IN A 192.26.92.30  
d.gtld-servers.net. 172800 IN A 192.31.80.30  
e.gtld-servers.net. 172800 IN A 192.12.94.30  
f.gtld-servers.net. 172800 IN A 192.35.51.30  
g.gtld-servers.net. 172800 IN A 192.42.93.30  
h.gtld-servers.net. 172800 IN A 192.54.112.30  
i.gtld-servers.net. 172800 IN A 192.43.172.30  
j.gtld-servers.net. 172800 IN A 192.48.79.30  
k.gtld-servers.net. 172800 IN A 192.52.178.30  
l.gtld-servers.net. 172800 IN A 192.41.162.30  
m.gtld-servers.net. 172800 IN A 192.55.83.30

`

`;; Query time: 497 msec ;; SERVER: 192.203.230.10#53(192.203.230.10) ;; WHEN: Sat Aug 13 22:32:29 2011 ;; MSG SIZE rcvd: 509`

上面共有从 a 到 m，一样是 13 组服务器在所有的 com. 的 gTLD 的记录保存。

``

`

$ dig -t ns @192.5.6.30 twitter.com

; <<>> DiG 9.7.3 <<>> @192.203.230.10 twitter.com  
; (1 server found)  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 4691  
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:  
;twitter.com. IN A

;; ANSWER SECTION:  
twitter.com. 33917 IN A 203.98.7.65

`

`;; Query time: 111 msec ;; SERVER: 192.203.230.10#53(192.203.230.10) ;; WHEN: Sat Aug 13 22:21:59 2011 ;; MSG SIZE rcvd: 45`

这里看到问题了么？本来应该返回 twitter.com 的具体的解析服务器，为什么直接返回了一个 A 记录？而且还是这么诡异的一个地址？查询以下这个 IP 的归属地，是『新西兰 奥克兰Telstraclear公司』，应该是胡乱编出来的地址了。至此再测试下去意义也就不大了，具体原因等会儿分析。换上 VPN 看看结果如何

``

`

$ dig

; <<>> DiG 9.7.3 <<>>  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63584  
;; flags: qr rd ra; QUERY: 1, ANSWER: 13, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:  
;. IN NS

;; ANSWER SECTION:  
. 82346 IN NS a.root-servers.net.  
. 82346 IN NS b.root-servers.net.  
. 82346 IN NS e.root-servers.net.  
. 82346 IN NS g.root-servers.net.  
. 82346 IN NS i.root-servers.net.  
. 82346 IN NS h.root-servers.net.  
. 82346 IN NS m.root-servers.net.  
. 82346 IN NS c.root-servers.net.  
. 82346 IN NS d.root-servers.net.  
. 82346 IN NS k.root-servers.net.  
. 82346 IN NS j.root-servers.net.  
. 82346 IN NS f.root-servers.net.  
. 82346 IN NS l.root-servers.net.

`

`;; Query time: 138 msec ;; SERVER: 8.8.8.8#53(8.8.8.8) ;; WHEN: Sat Aug 13 22:25:08 2011 ;; MSG SIZE rcvd: 228`

这里的结果完全一样，我们继续选择 e 的那组

``

`

$ dig e.root-servers.net

; <<>> DiG 9.7.3 <<>> e.root-servers.net  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10099  
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:  
;e.root-servers.net. IN A

;; ANSWER SECTION:  
e.root-servers.net. 47915 IN A 192.203.230.10

`

`;; Query time: 191 msec ;; SERVER: 8.8.8.8#53(8.8.8.8) ;; WHEN: Sat Aug 13 22:25:42 2011 ;; MSG SIZE rcvd: 52`

嗯，这里也一样，继续

``

`

$ dig -t ns @192.203.230.10 com.

; <<>> DiG 9.7.3 <<>> -t ns @192.203.230.10 com.  
; (1 server found)  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 56227  
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 13, ADDITIONAL: 15  
;; WARNING: recursion requested but not available

;; QUESTION SECTION:  
;com. IN NS

;; AUTHORITY SECTION:  
com. 172800 IN NS c.gtld-servers.net.  
com. 172800 IN NS a.gtld-servers.net.  
com. 172800 IN NS g.gtld-servers.net.  
com. 172800 IN NS h.gtld-servers.net.  
com. 172800 IN NS b.gtld-servers.net.  
com. 172800 IN NS l.gtld-servers.net.  
com. 172800 IN NS d.gtld-servers.net.  
com. 172800 IN NS j.gtld-servers.net.  
com. 172800 IN NS k.gtld-servers.net.  
com. 172800 IN NS f.gtld-servers.net.  
com. 172800 IN NS m.gtld-servers.net.  
com. 172800 IN NS e.gtld-servers.net.  
com. 172800 IN NS i.gtld-servers.net.

;; ADDITIONAL SECTION:  
a.gtld-servers.net. 172800 IN A 192.5.6.30  
a.gtld-servers.net. 172800 IN AAAA 2001:503:a83e::2:30  
b.gtld-servers.net. 172800 IN A 192.33.14.30  
b.gtld-servers.net. 172800 IN AAAA 2001:503:231d::2:30  
c.gtld-servers.net. 172800 IN A 192.26.92.30  
d.gtld-servers.net. 172800 IN A 192.31.80.30  
e.gtld-servers.net. 172800 IN A 192.12.94.30  
f.gtld-servers.net. 172800 IN A 192.35.51.30  
g.gtld-servers.net. 172800 IN A 192.42.93.30  
h.gtld-servers.net. 172800 IN A 192.54.112.30  
i.gtld-servers.net. 172800 IN A 192.43.172.30  
j.gtld-servers.net. 172800 IN A 192.48.79.30  
k.gtld-servers.net. 172800 IN A 192.52.178.30  
l.gtld-servers.net. 172800 IN A 192.41.162.30  
m.gtld-servers.net. 172800 IN A 192.55.83.30

`

`;; Query time: 337 msec ;; SERVER: 192.203.230.10#53(192.203.230.10) ;; WHEN: Sat Aug 13 22:31:39 2011 ;; MSG SIZE rcvd: 509`

没有什么新奇的，继续…

``

`

$ dig -t ns @192.5.6.30 twitter.com

; <<>> DiG 9.7.3 <<>> -t ns @192.5.6.30 twitter.com  
; (1 server found)  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 26303  
;; flags: qr rd; QUERY: 1, ANSWER: 0, AUTHORITY: 4, ADDITIONAL: 4  
;; WARNING: recursion requested but not available

;; QUESTION SECTION:  
;twitter.com. IN NS

;; AUTHORITY SECTION:  
twitter.com. 172800 IN NS ns1.p34.dynect.net.  
twitter.com. 172800 IN NS ns2.p34.dynect.net.  
twitter.com. 172800 IN NS ns3.p34.dynect.net.  
twitter.com. 172800 IN NS ns4.p34.dynect.net.

;; ADDITIONAL SECTION:  
ns1.p34.dynect.net. 172800 IN A 208.78.70.34  
ns2.p34.dynect.net. 172800 IN A 204.13.250.34  
ns3.p34.dynect.net. 172800 IN A 208.78.71.34  
ns4.p34.dynect.net. 172800 IN A 204.13.251.34

`

`;; Query time: 448 msec ;; SERVER: 192.5.6.30#53(192.5.6.30) ;; WHEN: Sat Aug 13 22:34:05 2011 ;; MSG SIZE rcvd: 179`

到这里的结果就和刚才不一样了，可以看到，192.5.6.30 这个服务器正常返回了应该负责解析 twitter.com 的真实 ns 的服务器，既然都做到这里了，就继续下去吧，继续从里面随便抓一个出来

``

`

$ dig @208.78.71.34 twitter.com any  
;; Truncated, retrying in TCP mode.

; <<>> DiG 9.7.3 <<>> @208.78.71.34 twitter.com any  
; (1 server found)  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 36456  
;; flags: qr aa rd; QUERY: 1, ANSWER: 19, AUTHORITY: 0, ADDITIONAL: 0  
;; WARNING: recursion requested but not available

;; QUESTION SECTION:  
;twitter.com. IN ANY

;; ANSWER SECTION:  
twitter.com. 30 IN SOA ns1.p26.dynect.net. zone-admin.dyndns.com. 2007110572 3600 600 604800 60  
twitter.com. 86400 IN NS ns1.p34.dynect.net.  
twitter.com. 86400 IN NS ns2.p34.dynect.net.  
twitter.com. 86400 IN NS ns4.p34.dynect.net.  
twitter.com. 86400 IN NS ns3.p34.dynect.net.  
twitter.com. 30 IN A 199.59.149.203  
twitter.com. 30 IN A 199.59.149.230  
twitter.com. 30 IN A 199.59.149.235  
twitter.com. 30 IN A 199.59.148.10  
twitter.com. 30 IN A 199.59.148.14  
twitter.com. 30 IN A 199.59.148.81  
twitter.com. 30 IN A 199.59.148.82  
twitter.com. 30 IN A 199.59.149.198  
twitter.com. 600 IN MX 10 aspmx.l.google.com.  
twitter.com. 600 IN MX 20 alt1.aspmx.l.google.com.  
twitter.com. 600 IN MX 20 alt2.aspmx.l.google.com.  
twitter.com. 600 IN MX 30 ASPMX2.GOOGLEMAIL.com.  
twitter.com. 600 IN MX 30 ASPMX3.GOOGLEMAIL.com.  
twitter.com. 600 IN TXT "v=spf1 ip4:199.16.156.0/22 ip4:199.59.148.0/22 ip4:128.121.145.168 ip4:128.121.146.128/27 mx ptr a:postmaster.twitter.com a:ham-cannon.twitter.com mx:one.textdrive.com include:cmail1.com include:aspmx.googlemail.com include:support.zendesk.com -all"

`

`;; Query time: 148 msec ;; SERVER: 208.78.71.34#53(208.78.71.34) ;; WHEN: Sat Aug 13 22:35:46 2011 ;; MSG SIZE rcvd: 696`

我们可以发现挂上 VPN 之后的解析流程才是正确无误的过程，但是为什么不挂上就不能正确解析？自然是 DNS 服务器被污染了。并且拦截的方式**似乎**也很弱智，发现 UDP 53 口的包带有 twitter.com 字样，直接返回一个随即、胡编出来的 IP 地址，也不管人家到底是不是直接要去查 twitter.com 的 A 记录。为了证明这种猜想，继续做一些试验吧。不如发一个错误的 DNS 包出去，看看返回什么结果。

`$ dig @202.204.49.251 twitter.com -t ns --->> 查询的服务器是 202.204.48.251`

`

; <<>> DiG 9.7.3 <<>> @202.204.49.251 twitter.com -t ns  
; (1 server found)  
;; global options: +cmd  
;; Got answer:  
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 19538  
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:  
;twitter.com. IN NS

;; ANSWER SECTION:  
twitter.com. 32460 IN A 159.24.3.173

`

`;; Query time: 213 msec ;; SERVER: 202.204.49.251#53(202.204.49.251) ;; WHEN: Sat Aug 13 22:43:45 2011 ;; MSG SIZE rcvd: 45`

这里的服务器是 iBeiKe 在教育网内的服务器，对于外网没有开除了 80 的任何口，而且也没有 53 的 UDP 开着，果然，够弱智！

### tcpdump 抓包

tcpdump 这个东西虽然叫做 tcpdump，但是 UDP 抓起来也没有问题，随便抓抓 DNS 的解析包，不需要什么重型武器，这种轻量级别就很好用了。环境和上面一样，我用的无线网络，所以在 Mac OS X 的接口就是 en1 了。不上 VPN 看看结果如何吧

`$ sudo tcpdump -i en1 -vvv udp tcpdump: listening on en1, link-type EN10MB (Ethernet), capture size 65535 bytes 22:11:41.687602 IP (tos 0x0, ttl 64, id 37209, offset 0, flags [none], proto UDP (17), length 57) localhost.57689 > ns1.p34.dynect.net.domain: [udp sum ok] 2927+ A? twitter.com. (29) 22:11:41.717641 IP (tos 0x0, ttl 216, id 14349, offset 0, flags [none], proto UDP (17), length 73) ns1.p34.dynect.net.domain > localhost.57689: [udp sum ok] 2927 q: A? twitter.com. 1/0/0 twitter.com. [4h50m45s] A 159.24.3.173 (45) 22:11:41.718373 IP (tos 0x0, ttl 117, id 43381, offset 0, flags [none], proto UDP (17), length 73) ns1.p34.dynect.net.domain > localhost.57689: [bad udp cksum 2700!] 2927 q: A? twitter.com. 1/0/0 twitter.com. [5m] A 37.61.54.158 (45) 22:11:42.306659 IP (tos 0x0, ttl 48, id 61847, offset 0, flags [none], proto UDP (17), length 191) ns1.p34.dynect.net.domain > localhost.57689: [udp sum ok] 2927*- q: A? twitter.com. 3/4/0 twitter.com. [30s] A 199.59.148.82, twitter.com. [30s] A 199.59.149.230, twitter.com. [30s] A 199.59.149.198 ns: twitter.com. [1d] NS ns4.p34.dynect.net., twitter.com. [1d] NS ns2.p34.dynect.net., twitter.com. [1d] NS ns1.p34.dynect.net., twitter.com. [1d] NS ns3.p34.dynect.net. (163)`

唔，有人抢在正确的包之前跑来了。你为什么这么积极呢？为什么呢…
