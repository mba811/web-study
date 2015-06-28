# DNS

**域名系统**（[英文](https://zh.wikipedia.org/wiki/%E8%8B%B1%E6%96%87)：**D**omain **N**ame **S**ystem，[缩写](https://zh.wikipedia.org/wiki/%E7%B8%AE%E5%AF%AB)：**DNS**）是[因特网](https://zh.wikipedia.org/wiki/%E5%9B%A0%E7%89%B9%E7%BD%91)的一项服务。它作为将[域名](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D)和[IP地址](https://zh.wikipedia.org/wiki/IP%E5%9C%B0%E5%9D%80)相互[映射](https://zh.wikipedia.org/wiki/%E6%98%A0%E5%B0%84)的一个[分布式数据库](https://zh.wikipedia.org/wiki/%E5%88%86%E5%B8%83%E5%BC%8F%E6%95%B0%E6%8D%AE%E5%BA%93)，能够使人更方便的访问[互联网](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91)。DNS 使用[TCP](https://zh.wikipedia.org/wiki/%E4%BC%A0%E8%BE%93%E6%8E%A7%E5%88%B6%E5%8D%8F%E8%AE%AE)和[UDP](https://zh.wikipedia.org/wiki/%E7%94%A8%E6%88%B7%E6%95%B0%E6%8D%AE%E6%8A%A5%E5%8D%8F%E8%AE%AE)[端口](https://zh.wikipedia.org/wiki/%E7%AB%AF%E5%8F%A3)53。当前，对于每一级域名长度的限制是63个字符，域名总长度则不能超过253个字符。

开始时，域名的字符仅限于[ASCII](https://zh.wikipedia.org/wiki/ASCII)字符的一个子集。2008年，ICANN通过一项决议，允许使用其它语言作为互联网顶级域名的字符。使用基于[Punycode](https://zh.wikipedia.org/wiki/Punycode)码的[IDNA](https://zh.wikipedia.org/wiki/IDNA)系统，可以将[Unicode](https://zh.wikipedia.org/wiki/Unicode)字符串映射为有效的DNS字符集。因此，诸如“x.台湾”这样的域名可以在地址栏直接输入，而不需要安装插件。但是，由于英语的广泛使用，使用其他语言字符作为域名会产生多种问题，例如难以输入，难以在国际推广等。

## 历史

DNS最早于1983年由[保罗·莫卡派乔斯](https://zh.wikipedia.org/wiki/%E4%BF%9D%E7%BD%97%C2%B7%E8%8E%AB%E5%8D%A1%E6%B4%BE%E4%B9%94%E6%96%AF)（Paul Mockapetris）发明；原始的技术规范在882号[因特网标准](https://zh.wikipedia.org/w/index.php?title=%E5%9B%A0%E7%89%B9%E7%BD%91%E6%A0%87%E5%87%86&action=edit&redlink=1)草案（[RFC 882](https://tools.ietf.org/html/rfc882)）中发布。1987年发布的第1034和1035号草案修正了DNS技术规范，并废除了之前的第882和883号草案。在此之后对因特网标准草案的修改基本上没有涉及到DNS技术规范部分的改动。

早期的域名必须以英文句号“.”结尾,当用户访问 www.wikipedia.org 的HTTP服务时必须在址栏中输入：http://www.wikipedia.org.，这样DNS才能够进行域名解析。如今DNS服务器已经可以自动补上结尾的句号。

## 记录类型

主条目：[域名服务器记录类型列表](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E6%9C%8D%E5%8B%99%E5%99%A8%E8%A8%98%E9%8C%84%E9%A1%9E%E5%9E%8B%E5%88%97%E8%A1%A8)

DNS系统中，常见的资源记录类型有：

  * 主机记录(A记录)：RFC 1035定义，A记录是用于名称解析的重要记录，它将特定的主机名映射到对应主机的IP地址上。
  * 别名记录(CNAME记录): RFC 1035定义，CNAME记录用于将某个别名指向到某个A记录上，这样就不需要再为某个新名字另外创建一条新的A记录。
  * IPv6主机记录(AAAA记录): RFC 3596定义，与A记录对应，用于将特定的主机名映射到一个主机的[IPv6](https://zh.wikipedia.org/wiki/IPv6)地址。
  * 服务位置记录(SRV记录): RFC 2782定义，用于定义提供特定服务的服务器的位置，如主机(hostname)，端口(port number)等。
  * NAPTR记录: RFC 3403定义，它提供了[正则表达式](https://zh.wikipedia.org/wiki/%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F)方式去映射一个域名。NAPTR记录非常著名的一个应用是用于[ENUM](https://zh.wikipedia.org/w/index.php?title=ENUM&action=edit&redlink=1)查询。

## 技术实现

### 概述

DNS 通过允许一个名称服务器把他的一部分名称服务（众所周知的zone）“委托”给子服务器而实现了一种层次结构的名称空间。此外，DNS还提供了一些额外的信息，例如系统别名、联系信息以及哪一个主机正在充当系统组或域的邮件枢纽。

任何一个使用[IP](https://zh.wikipedia.org/wiki/%E7%BD%91%E9%99%85%E5%8D%8F%E8%AE%AE)的计算机网络可以使用DNS来实现他自己的私有名称系统。尽管如此，当提到在公共的[Internet](https://zh.wikipedia.org/wiki/Internet) DNS 系统上实现的域名时，术语“域名”是最常使用的。

这是基于504个全球范围的“[根域名服务器](https://zh.wikipedia.org/wiki/%E6%A0%B9%E5%9F%9F%E5%90%8D%E4%BC%BA%E6%9C%8D%E5%99%A8)”（分成13组，分别编号为A至M）[[1]](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F#cite_note-1)。从这504个根服务器开始，余下的Internet DNS 命名空间被委托给其他的DNS服务器，这些服务器提供DNS名称空间中的特定部分。

### 软件

DNS系统是由各式各样的DNS软件所驱动的，包括：

  * [BIND](https://zh.wikipedia.org/wiki/BIND) (Berkeley Internet Name Domain), 使用最广的DNS软件
  * [DJBDNS](https://zh.wikipedia.org/w/index.php?title=DJBDNS&action=edit&redlink=1) (Dan J Bernstein's DNS implementation)
  * [MaraDNS](https://zh.wikipedia.org/w/index.php?title=MaraDNS&action=edit&redlink=1)
  * [Name Server Daemon](https://zh.wikipedia.org/w/index.php?title=Name_Server_Daemon&action=edit&redlink=1) (Name Server Daemon)
  * [PowerDNS](https://zh.wikipedia.org/w/index.php?title=PowerDNS&action=edit&redlink=1)

### 国际化域名

主条目：[Punycode](https://zh.wikipedia.org/wiki/Punycode)

**Punycode**是一个根据RFC 3492标准而制定的编码系统，主要用于把[域名](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D)从地方语言所采用的[Unicode](https://zh.wikipedia.org/wiki/Unicode)编码转换成为可用于[DNS](https://zh.wikipedia.org/wiki/DNS)系统的编码。而该编码是根据[域名相异字表](http://www.iana.org/domains/idn-tables/)(由[IANA](https://zh.wikipedia.org/wiki/IANA)制定)，Punycode可以防止所谓的[IDN欺骗](https://zh.wikipedia.org/wiki/IDN%E6%AC%BA%E9%A8%99)。

### 域名解析

举一个例子，_zh.wikipedia.org_作为一个域名就和IP地址_208.80.154.225_相对应。DNS就像是一个自动的电话号码簿，我们可以直接拨打wikipedia的名字来代替电话号码（IP地址）。DNS在我们直接调用[网站](https://zh.wikipedia.org/wiki/%E7%BD%91%E7%AB%99)的名字以后就会将像_zh.wikipedia.org_一样便于人类使用的名字转化成像_208.80.154.225_一样便于机器识别的IP地址。

DNS查询有两种方式：**递归**和**迭代**。DNS客户端设置使用的DNS服务器一般都是递归服务器，它负责全权处理客户端的DNS查询请求，直到返回最终结果。而DNS服务器之间一般采用迭代查询方式。

以查询 zh.wikipedia.org 为例：

  * 客户端发送查询报文"query zh.wikipedia.org"至DNS服务器，DNS服务器首先检查自身缓存，如果存在记录则直接返回结果。
  * 如果记录老化或不存在，则
  1. DNS服务器向[根域名服务器](https://zh.wikipedia.org/wiki/%E6%A0%B9%E5%9F%9F%E5%90%8D%E4%BC%BA%E6%9C%8D%E5%99%A8)发送查询报文"query zh.wikipedia.org"，根域名服务器返回 .org 域的权威域名服务器地址，这一级首先会返回的是[顶级域名](https://zh.wikipedia.org/wiki/%E9%A1%B6%E7%BA%A7%E5%9F%9F%E5%90%8D)的权威域名服务器。
  2. DNS服务器向 .org 域的权威域名服务器发送查询报文"query zh.wikipedia.org"，得到 .wikipedia.org 域的权威域名服务器地址。
  3. DNS服务器向 .wikipedia.org 域的权威域名服务器发送查询报文"query zh.wikipedia.org"，得到主机 zh 的A记录，存入自身缓存并返回给客户端。

### WHOIS

一个域名的**所有者**可以通过查询WHOIS数据库[[2]](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F#cite_note-2)而被找到；对于大多数[根域名服务器](https://zh.wikipedia.org/wiki/%E6%A0%B9%E5%9F%9F%E5%90%8D%E6%9C%8D%E5%8B%99%E5%99%A8%E5%88%97%E8%A1%A8)， 基本的WHOIS由[ICANN](https://zh.wikipedia.org/wiki/ICANN)维护，而WHOIS的细节则由控制那个域的域注册机构维护。

对于240多个国家代码顶级域名(ccTLDs)，通常由该域名权威注册机构负责维护WHOIS。例如[中国互联网络信息中心](https://zh.wikipedia.org/wiki/%E4%B8%AD%E5%9B%BD%E4%BA%92%E8%81%94%E7%BD%91%E7%BB%9C%E4%BF%A1%E6%81%AF%E4%B8%AD%E5%BF%83)(China Internet Network Information Center)负责 .CN 域名的WHOIS维护，[香港互联网注册管理有限公司](https://zh.wikipedia.org/wiki/%E9%A6%99%E6%B8%AF%E4%BA%92%E8%81%AF%E7%B6%B2%E8%A8%BB%E5%86%8A%E7%AE%A1%E7%90%86%E6%9C%89%E9%99%90%E5%85%AC%E5%8F%B8)(Hong Kong Internet Registration Corporation Limited) 负责 .HK 域名的WHOIS维护，[台湾网络信息中心](https://zh.wikipedia.org/w/index.php?title=%E5%8F%B0%E7%81%A3%E7%B6%B2%E7%B5%A1%E8%B3%87%E8%A8%8A%E4%B8%AD%E5%BF%83&action=edit&redlink=1) (Taiwan Network Information Center) 负责 .TW 域名的WHOIS维护。

## 其他

此外，一些黑客通过伪造DNS服务器将用户引向错误网站，以达到窃取用户隐私信息的目的。这种DNS服务器大约有68000台[[3]](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F#cite_note-3)。

## 相关条目

  * [IP地址](https://zh.wikipedia.org/wiki/IP%E4%BD%8D%E5%9D%80)
  * [域名](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D)
  * [中文域名](https://zh.wikipedia.org/wiki/%E4%B8%AD%E6%96%87%E5%9F%9F%E5%90%8D)
  * [域名抢注](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E6%90%B6%E6%B3%A8)
  * [动态DNS](https://zh.wikipedia.org/wiki/%E5%8B%95%E6%85%8BDNS)
  * [ICANN](https://zh.wikipedia.org/wiki/ICANN)
  * [DNSSEC](https://zh.wikipedia.org/wiki/DNSSEC)
  * [Google Public DNS](https://zh.wikipedia.org/wiki/Google_Public_DNS)
  * [OpenDNS](https://zh.wikipedia.org/wiki/OpenDNS)
  * [域名劫持](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E5%8A%AB%E6%8C%81) - [域名服务器缓存污染](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%BC%93%E5%AD%98%E6%B1%A1%E6%9F%93)
  * [域名服务器记录类型列表](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E6%9C%8D%E5%8B%99%E5%99%A8%E8%A8%98%E9%8C%84%E9%A1%9E%E5%9E%8B%E5%88%97%E8%A1%A8)
  * [根域名服务器](https://zh.wikipedia.org/wiki/%E6%A0%B9%E5%9F%9F%E5%90%8D%E4%BC%BA%E6%9C%8D%E5%99%A8)

## 参考文献

  1. **[^](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F#cite_ref-1)** （英文）[Root Server Technical Operations Assn](http://root-servers.org/). [2014年1月28日].
  2. **[^](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F#cite_ref-2)** [http://whois.net/](http://whois.net/)
  3. **[^](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E7%B3%BB%E7%BB%9F#cite_ref-3)** JORDAN ROBERTSON. [Use of Rogue DNS Servers on Rise](http://ap.google.com/article/ALeqM5ifrgeDBfUGAvXtLH_vgVrKcm0s_wD8UPLR8O1). The Associated Press. [2008-02-18].
  * [RFC 882](https://tools.ietf.org/html/rfc882)
  * [RFC 883](https://tools.ietf.org/html/rfc883)
  * [RFC 1034](https://tools.ietf.org/html/rfc1034)
  * [RFC 1035](https://tools.ietf.org/html/rfc1035)
  * [RFC 1180](https://tools.ietf.org/html/rfc1180) - TCP/IP tutorial

## 外部链接

  * [DNS协议详细资料](http://www.cnpaf.net/class/dns)
  * [DNS & BIND Resources](http://www.bind9.net/)
  * [DNS Security Extensions (DNSS)](http://www.dnssec.net/)
  * [Root Server(EC)](http://www.root-servers.org/)
  * [台湾区电信运营商DNS列表](http://tw.myblog.yahoo.com/ky-lab/article?mid=258)
  * [可以查询域名的MX,CName,A等DNS记录](http://www.dirs.cn/)
  * [名称服务器间谍](http://www.chinawebtools.com/nameserver)