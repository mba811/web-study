# VPN

**虚拟专用网**（[英语](https://zh.wikipedia.org/wiki/%E8%8B%B1%E8%AF%AD)：**Virtual Private Network**，简称**VPN**），是一种常用于连接中、大型企业或团体与团体间的私人网络的通讯方法。虚拟私人网络的讯息透过公用的网络架构（例如：[互联网](https://zh.wikipedia.org/wiki/%E4%BA%92%E8%81%94%E7%BD%91)）来传送内联网的网络讯息。它利用已加密的[通道协议](https://zh.wikipedia.org/wiki/%E9%80%9A%E9%81%93%E5%8D%94%E8%AD%B0)（Tunneling Protocol）来达到保密、发送端认证、消息准确性等私人消息安全效果。这种技术可以用不安全的网络（例如：互联网）来发送可靠、安全的消息。需要注意的是，加密消息与否是可以控制的。没有加密的虚拟专用网消息依然有被窃取的危险。

以日常生活的例子来比喻，虚拟专用网就像：甲公司某部门的A想寄信去乙公司某部门的B。A已知B的地址及部门，但公司与公司之间的信不能注明部门名称。于是，A请自己的秘书把指定B所属部门的信（A可以选择是否以密码与B通信）放在寄去乙公司地址的大[信封](https://zh.wikipedia.org/wiki/%E4%BF%A1%E5%B0%81)中。当乙公司的秘书收到从甲公司寄到乙公司的邮件后，该秘书便会把放在该大信封内的指定部门邮件以公司内部邮件方式寄给B。同样地，B会以同样的方式回信给A。

在以上例子中，A及B是身处不同公司（内部网路）的计算机（或相关机器），通过一般邮寄方式（公用网络）寄信给对方，再由对方的秘书（例如：支持虚拟专用网的路由器或防火墙）以公司内部邮件（内部网络）的方式寄至对方本人。请注意，在虚拟专用网中，因应网络架构，秘书及收信人可以是同一人。许多现在的[操作系统](https://zh.wikipedia.org/wiki/%E4%BD%9C%E6%A5%AD%E7%B3%BB%E7%B5%B1)，例如[Windows](https://zh.wikipedia.org/wiki/Windows)及[Linux](https://zh.wikipedia.org/wiki/Linux)等因其所用传输协议，已有能力不用通过其它网络设备便能达到虚拟专用网连接。

## 历史

20世纪90年代，计算机网络上的计算机通过非常昂贵的专线和/或拨号连线互连。视站点间的距离，花费可达数千美元（56kbps连线）或上万美元（T1）。

由于为了避免租用多条各自连接互联网的专线，因为虚拟私人网络可减少网络开支，用户可以安全地交换私密数据，虚拟私人网络变得普及，使昂贵的专线变得多余

## 安全性

安全的虚拟私人网络使用[加密](https://zh.wikipedia.org/wiki/%E5%8A%A0%E5%AF%86)[穿隧协议](https://zh.wikipedia.org/wiki/%E7%A9%BF%E9%9A%A7%E5%8D%94%E8%AD%B0)，通过阻止截听与[嗅探](https://zh.wikipedia.org/wiki/%E5%97%85%E6%8E%A2)来提供[机密性](https://zh.wikipedia.org/wiki/%E6%9C%BA%E5%AF%86%E6%80%A7)，还允许发送者身份验证，以阻止身份伪造，同时通过防止信息被修改提供消息[完整性](https://zh.wikipedia.org/wiki/%E5%AE%8C%E6%95%B4%E6%80%A7)。

某些虚拟私人网络不使用加密保护数据。虽然虚拟私人网络通常都会提供安全性，但**未加密**的虚拟私人网络严格来说是不“[安全](https://zh.wikipedia.org/wiki/%E4%BF%A1%E6%81%AF%E5%AE%89%E5%85%A8)”或“[可信](https://zh.wikipedia.org/wiki/%E5%8F%AF%E4%BF%A1%E8%AE%A1%E7%AE%97)”的。例如，一条通过[GRE](https://zh.wikipedia.org/wiki/%E9%80%9A%E7%94%A8%E8%B7%AF%E7%94%B1%E5%B0%81%E8%A3%85)协议在两台主机间创建的隧道属于虚拟私人网络，但既不安全也不可信。 除以上的GRE协议例子外，本地的明文穿隧协议包括[L2TP](https://zh.wikipedia.org/wiki/L2TP)（不带IPsec时）和PPTP（不使用微软点对点加密(MPPE)时）。

## 协议

常用的虚拟专用网协议有：

  * [L2F](https://zh.wikipedia.org/wiki/L2F)
  * [L2TP](https://zh.wikipedia.org/wiki/%E7%AC%AC%E4%BA%8C%E5%B1%82%E9%9A%A7%E9%81%93%E5%8D%8F%E8%AE%AE)
  * [PPTP](https://zh.wikipedia.org/wiki/%E9%BB%9E%E5%B0%8D%E9%BB%9E%E9%9A%A7%E9%81%93%E5%8D%94%E8%AD%B0)
  * [IPsec](https://zh.wikipedia.org/wiki/IPsec)
  * [SSL VPN](https://zh.wikipedia.org/w/index.php?title=SSL_VPN&action=edit&redlink=1)
  * [Cisco VPN](https://zh.wikipedia.org/w/index.php?title=Cisco_VPN&action=edit&redlink=1)
  * [OpenVPN](https://zh.wikipedia.org/wiki/OpenVPN)
  * Freegate

## 特殊使用

由于[中国大陆境内对于海外网络的限制及封锁](https://zh.wikipedia.org/wiki/%E4%B8%AD%E8%8F%AF%E4%BA%BA%E6%B0%91%E5%85%B1%E5%92%8C%E5%9C%8B%E7%B6%B2%E7%B5%A1%E5%AF%A9%E6%9F%A5)，所以中国大陆兴盛起以采用免费或付费的虚拟专用网（VPN）进行海外网络连接服务的方法进行[翻墙](https://zh.wikipedia.org/wiki/%E7%AA%81%E7%A0%B4%E7%BD%91%E7%BB%9C%E5%AE%A1%E6%9F%A5)，或许多外商公司欲连接回海外网站也多自行架设VPN或采用付费的VPN服务。2015年1月起，中国开始加强对外国VPN服务的封锁。VPN供应商Astrill通知用户，因防火长城升级，使用IPSec、L2TP/IPSec和PPTP协议的设备无法访问它的服务，受影响的主要是iOS设备。[[2]](https://zh.wikipedia.org/wiki/%E8%99%9B%E6%93%AC%E7%A7%81%E4%BA%BA%E7%B6%B2%E8%B7%AF#cite_note-2)[中国工信部](https://zh.wikipedia.org/wiki/%E4%B8%AD%E5%8D%8E%E4%BA%BA%E6%B0%91%E5%85%B1%E5%92%8C%E5%9B%BD%E5%B7%A5%E4%B8%9A%E5%92%8C%E4%BF%A1%E6%81%AF%E5%8C%96%E9%83%A8)曾规定，在中国提供VPN服务的公司必须登记注册，否则将“不受中国法律的保护”。

## 外部链接

  * [OpenVPN](http://www.openvpn.net/)（英文） [OpenVPN](https://zh.wikipedia.org/wiki/OpenVPN)，一个开源的VPN实现
  * [Openswan](http://www.openswan.org/)（英文）

## 参考文献

  1. **[^](https://zh.wikipedia.org/wiki/%E8%99%9B%E6%93%AC%E7%A7%81%E4%BA%BA%E7%B6%B2%E8%B7%AF#cite_ref-1)** Feilner, Markus. "Chapter 1 - VPN—Virtual Private Network". OpenVPN: Building and Integrating Virtual Private Networks: Learn How to Build Secure VPNs Using this Powerful Open Source Application. Packt Publishing.
  2. **[^](https://zh.wikipedia.org/wiki/%E8%99%9B%E6%93%AC%E7%A7%81%E4%BA%BA%E7%B6%B2%E8%B7%AF#cite_ref-2)** [Foreign VPN service unavailable in China](http://en.people.cn/n/2015/0123/c90882-8840092.html)

## 参见

  * [MVPN](https://zh.wikipedia.org/wiki/MVPN)
  * [SoftEther](https://zh.wikipedia.org/w/index.php?title=SoftEther&action=edit&redlink=1)
  * [代理服务器](https://zh.wikipedia.org/wiki/%E4%BB%A3%E7%90%86%E4%BC%BA%E6%9C%8D%E5%99%A8)
