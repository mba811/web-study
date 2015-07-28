# 有关HTTPS的一些介绍

HTTPS(Hypertext Transfer Protocol Secure)，即超文本传输安全协议，是HTTP与[SSL/TLS](http://zh.wikipedia.org/wiki/%E4%BC%A0%E8%BE%93%E5%B1%82%E5%AE%89%E5%85%A8)的组合，用以提供加密通讯及对网络服务器身份的鉴定。

由于http是明文传输的，所以在互联风上传输隐私信息非常不安全，目前国外大多数网站都已经全面支持https, 但国内情况很差，不仅很少有大型网站全站支持https，甚至有些网站使用https不规范，安全协议过时，留下了一些安全隐患。

### https的原理介绍

https在不安全的网络上创建了一个安全信道，通过使用加密套件和服务器证书可被验证且可被信任，从而防止信息被截获或中间人攻击，实现保证TCP协议之上的传输层安全。

目前浏览器中都会内置一些根证书（常见的如Microsoft、VeriSign等），基于这些根证书以及这些根证书下签署的证书是可被信任的，通常证书是由这些根证书颁发机构来颁发。

用户访问https协议的网址时，客户端浏览器与服务器握手时，会验证服务器的证书有效性，即是否由一个被信任的证书颁发机构签发；如果不是，浏览器会对用户进行警告。然后浏览器会根据握手时约定好的加密信息加密和解密与服务器之间传输的数据，从而保障数据在传输层的安全。

详细的握手过程下面介绍。

### https加密协议版本

主要有TLS和SSL两种协议。

##### TLS/SSL介绍

SSL(Secure Sockets Layer)由网景(Netscape)公司设计，用于对http协议传输的数据进行加密，由此诞生了https. SSL最新的版本是3.0, 之后IETF对SSL 3.0进行了升级，设计了TLS(Transport Layer Security) 1.0, 目前最新版本是1.2, 但还未被广泛支持。

有关SSL/TLS协议的运行机制，可以看阮老师的文章：[SSL/TLS协议运行机制的概述](http://www.ruanyifeng.com/blog/2014/02/ssl_tls.html)

##### 加密方式

https协议使用了三种加密方式：对称加密、非对称加密和HASH算法：

  * 非对称加密算法：RSA，DSA/DSS   
用于在握手时加密生成的密码
  * 对称加密算法：AES，RC4，3DES   
用于对传输的数据进行加密
  * HASH算法：MD5，SHA1，SHA256   
用于验证数据的完整性、有无被篡改

非对称加密算法时生成公钥只能用于加密数据，是公开的；而网站的私钥用于服务器端对数据进行解密，所以需要特别保管，不能泄漏。

### 终端的支持情况

据统计，目前大部分网站使用的`TLS 1.0`协议，其次是`TLS 1.1` 和`TLS 1.2`，SSL协议已经支持的很少了，而且被认为是不安全和低效率的。（数据来自Wikipedia）

目前决大部分浏览器都已经对https支持很好了，国外Google、Twitter、Facebook都已经全站支持了，因此可以放心使用。除一些旧的浏览器如IE6等，如使用最广泛的`TLS 1.0`协议

  * 在IE6及以下版本中是默认Disabled或根本不支持的；

  * 在Opera 4以下版本不支持

除此之外，最新版本的浏览器支持情况还是不错的。

### https解决的安全问题

  * 保护隐私数据，由于数据传输是加密的，因此黑客很难截获和破解信息；因此很多网站至少登陆页面使用的是https。

  * 保障数据完整性，确保数据在传输过程中不会被修改，跟邮件的签名是一样的，比如可以防止运营商劫持、篡改网页内容。

  * 防止钓鱼网站，可以通过在浏览器上查看证书确定所访问的网站是否是钓鱼网站

### https的缺点

  * 费用问题   
https证书颁发是需要一些费用的，一般一年几十美元至上百美元，单域名证书便宜一些，而泛域名证书会很贵。不过也有一些免费证书。

  * 响应问题   
由于增加了握手时的密钥生成和检查过程，因此建立连接时间相比http协议会更长一些，约200ms, 不过有优化的空间，（见下文）

  * 缓存问题   
虽然https协议的数据是可以被缓存的，只要设置好`max-age`等http缓存头，但是仍有部分浏览器或者网络结点服务器不能够很好地处理https缓存。

  * 性能问题   
由于增加了服务器的加密、解密过程，因此会消耗额外的cpu资源。

  * 收录问题   
截止目前，百度对https的网站的抓取仍然不支持。

### https的握手过程

  1. 浏览器将自己支持的一套加密规则发送给网站。

  2. 网站从中选出一组加密算法与HASH算法，并将自己的身份信息以证书的形式发回给浏览器。证书里面包含了网站地址，加密公钥，以及证书的颁发机构等信息。

  3. 获得网站证书之后浏览器要做以下工作：   
a) 验证证书的合法性（颁发证书的机构是否合法，证书中包含的网站地址是否与正在访问的地址一致等），如果证书受信任，则浏览器栏里面会显示一个小锁头，否则会给出证书不受信的提示。   
b) 如果证书受信任，或者是用户接受了不受信的证书，浏览器会生成一串随机数的密码，并用证书中提供的公钥加密。   
c) 使用约定好的HASH计算握手消息，并使用生成的随机数对消息进行加密，最后将之前生成的所有信息发送给网站。

  4. 网站接收浏览器发来的数据之后要做以下的操作：   
a) 使用自己的私钥将信息解密取出密码，使用密码解密浏览器发来的握手消息，并验证HASH是否与浏览器发来的一致。   
b) 使用密码加密一段握手消息，发送给浏览器。

  5. 浏览器解密并计算握手消息的HASH，如果与服务端发来的HASH一致，此时握手过程结束，之后所有的通信数据将由之前浏览器生成的随机密码并利用对称加密算法进行加密。

### 获取证书

  * 免费渠道[startssl](https://www.startssl.com/)和[wosign](https://www.wosign.com/)   
不需要多域名支持，个人使用，一般免费的就够用了，通用性不错，一般浏览器都支持。ijser.cn使用的就是wosign的免费证书。

  * 收费渠道   
收费的就很多了，如godaddy什么的。

  * 自己签署   
如果是app自用，可以选择自建CA，自己给自己签署证书。好处是方便，不必花钱；坏处是需要自己维护CA，保障安全。

证书通常有三种, 购买的时候可根据需要选择：

  1. 单域名证书，只签署一个域名，通常会包括如(ijser.cn, www.ijser.cn)
  2. 多域名证书，可以签署多个静态子域名, 如(blog.ijser.cn, cdn.ijser.cn), 每个域名需要单独配置。
  3. 泛域名证书，可以签署多个动态子域名，如(*.ijser.cn)

### 配置服务器

  * nginx 一般我们会用nginx作为服务器http服务的最外层代理，处理或转发http请求，相应的配置方法如下：
    
    server {  
      ...
      ssl on;
      ssl_certificate /yours.crt;
      ssl_certificate_key /yours.key;
    }
    

以上是最基本的配置，但还可以再优化些， 在server段中添加:
    
    keepalive_timeout 70;  
    ssl_session_cache shared:SSL:10m;  
    ssl_session_timeout 10m;  
    

以上配置是对https进行优化，让https链接保持，并且设置各进程间的session缓存。

#### 强制使用https

我的做法是将http请求全部301重定向到相应的https url上。https使用的是443端口，而http用的是80端口。下面是主要nginx配置：
    
    server {  
      listen 80;
      server_name ijser.cn www.ijser.cn;
      return 301 https://www.ijser.cn$request_uri;
    }
    

以上配置会将所有来自ijser.cn, www.ijser.cn 的http请求重定向到 [https://www.ijser.cn](https://www.ijser.cn/) 。

#### Mixed Content问题

当浏览器地址栏上的https认证图标是黄色三角号警告时，表示当前https页面中含有http协议的资源（未加密内容），如'css,js,image'等外链资源。潜在的安全隐患是：

  1. 这些内容可能会被中间人篡改
  2. 通过http请求发送的cookies可能会被截获

解决的办法也是有的，如Github允许用户在发布的Markdown内容中插入站外图片，如果站外图片的url地址是http的，直接在页面上显示是会导致黄色警告的，Github的解决方案是通过服务器抓取这些图片到自己的服务器上，然后用https访问它们。

> 至于图片木马问题，可以通过在http response中添加header `X-Content-Type-Options: nosniff`解决。

### https的一些最佳实践

  1. 将所有http请求301重定向为https
  2. 设置保持链接keepalive, 并调整合适的timeout值
  3. 保证页面中的其它资源链接都来自https
  4. 将静态资源放到单独的域名下，隔离cookies

### https了就确定安全吗？No.

因为https是基于默认信任根证书的，所以如果CA被黑掉，则其下签发的证书都有安全问题，如最近的CNNIC证书问题。

另外，SSL/TLS加密算法的实现也可能有Bug，如去年的心脏出血。

最后，https只是保证了传输过程中不被中间人攻击和服务端是否伪造，其它安全问题仍是无法保证的，如XSS、XSRF、DDos等等。

### 结尾

可能我们开发网站的大多数都是无证程序员，但最好还是让我们的网站有证上岗，至少可以保障部分安全，于我们的服务器、于我们的用户信息。

### 参考网站

  * [http://en.wikipedia.org/wiki/HTTPS](http://zh.wikipedia.org/zh/%E8%B6%85%E6%96%87%E6%9C%AC%E4%BC%A0%E8%BE%93%E5%AE%89%E5%85%A8%E5%8D%8F%E8%AE%AE)

  * [http://en.wikipedia.org/wiki/Transport_Layer_Security](http://en.wikipedia.org/wiki/Transport_Layer_Security)

  * [http://hengstart.iteye.com/blog/840561](http://hengstart.iteye.com/blog/840561)

  * [http://blog.csdn.net/luocn99/article/details/39777707](http://blog.csdn.net/luocn99/article/details/39777707)

  * [http://www.guokr.com/post/114121/](http://www.guokr.com/post/114121/)

  * [http://en.wikipedia.org/wiki/Template:TLS/SSL_support_history_of_web_browsers](http://en.wikipedia.org/wiki/Template:TLS/SSL_support_history_of_web_browsers)

  * [https://info.ssl.com/pros-and-cons-of-ssl-https-tls/](https://info.ssl.com/pros-and-cons-of-ssl-https-tls/)

  * [http://www.sslzhengshu.com/news/34-cn.html](http://www.sslzhengshu.com/news/34-cn.html)
