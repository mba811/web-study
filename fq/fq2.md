# Shadowsocks 使用方法及资料汇总

感谢万能的互联网，使我们这一代，如果你想，那么你就可以知晓世界上任何的事情！搜索引擎的出现使得搜索知识比以往要容易的多，你只要知道一个概念就能找出相应的所有的知识；社交网络的出现使得你跟你喜欢的明星的交谈就在一个留言上，不像以前那样，平凡的人是根本没有渠道去做这些事情的；从以前网络的虚假到现在慢慢的越来越真实，一个 ID 在网络上就代表着真实世界中的一个人，你可以与你真实世界中的想法一样当然也可以完全不一样，但这都不能阻碍你成为`个性、有着独立思想、见解的人`，可是生活在天朝，由于种种原因，好多国外世界的资源你是无法看到的，你不能享受你应该得到的这些（xirong 认为每一个个体都有相同的权利去享受互联网带给生活中的改变），这是很令人愤恨的 ！！ 如果不能去看到更多的风景，去尝试生命更多的可能，拥有年轻心态的你怎么会甘心？

> Across the Great Firewall, you can reach every corner in the world.

## 什么是shadowsocks？

> A secure socks5 proxy , designed to protect your Internet traffic.  
Shadowsocks 轻量级科学上网姿势，改变您的生活体验！

做完一个码农，经常需要搜索技术文章，如果不能够使用 google ，那么你的生活是很痛苦的，很多资料根本搜索不到的，所以你应该知道**代理**，通过代理可以绕过gwf（[见识下强大的GFW](http://zh.wikipedia.org/wiki/%E9%98%B2%E7%81%AB%E9%95%BF%E5%9F%8E)），从而去享受不被控制的生活，[科学上网](http://cokebar.info/archives/236)的方式很多，我们最常见的就是vpn，一把屠龙宝刀，像很多的老牌vpn厂商（[green vpn](http://www.greenjsq.info/)、[云梯](http://ytvpn.com/)，更多查看靠谱[vpn推荐网](http://vpntuijian.com/))，而shadowsocks就是一把瑞士军刀，锋利小巧快速简单，适应各种场景，适应各种客户端平台，window、mac、linux、ios、android使用简单。

### shadowsocks 原理

简单理解的话，Shadowsocks是将以前通过 SSH 创建的 Socks5 协议拆开成 Server 端和 client 端，下面这个原理图能简单介绍其翻墙原理，基本上和利用SSH tunnel大致类似：

[![shadowsocks原理图](http://static.ixirong.com/pic/ss/what-is-shadowsocks.png)](http://static.ixirong.com/pic/ss/what-is-shadowsocks.png)

1、PC客户端（即你的电脑）发出请求基于 Socks5 协议跟 SS-Local 端进行通讯，由于这个 SS-Local 一般是本机或路由器等局域网的其他机器，不经过 GFW，所以解决 GFW 通过特征分析进行干扰的问题。  
2、SS-Local 和 SS-Server 两端通过多种可选的加密方法进行通讯，经过GFW的时候因为是常规的 TCP 包，没有明显特征码 GFW 也无法对通讯数据进行解密，因此通讯放行。  
3、SS-Server 将收到的加密数据进行解密，还原初始请求，再发送到用户需要访问的服务网站，获取响应原路再返回 SS-04，返回途中依然使用了加密，使得流量是普通 TCP 包，并成功穿过 GFW 防火墙。

详细理解请参考文章[写给非专业人士看的 Shadowsocks 简介](http://vc2tea.com/whats-shadowsocks/)，不知道GFW？请参考[强大的GFW长城防火墙](http://zh.wikipedia.org/wiki/%E9%98%B2%E7%81%AB%E9%95%BF%E5%9F%8E)

## 为什么要用shadowsocks？

  * 配置简单：只需一次输入服务器ip地址、端口号、加密方式，随时即可轻松代理

  * 跨平台：window、mac、Linux、ios、android安装客户端，一样轻松

  * 与vpn差异

vpnshadowsocks

简单，一键翻墙 简单，一键翻墙

全局，代理浏览器、各种app、所有走网络的都经过vpn服务器 只有浏览器（可以手动设置代理其他app）

免费、收费服务商很多 免费、收费服务商很多

速度可以 速度很快，香港、新加坡几十毫秒

平台性稍差，有些做的也不错了，总体跨平台性差 支持各平台客户端，跨平台性强

  * vpn使用过程中最痛苦的莫过于，公司使用vpn、内网某些资源无法访问，需要频繁切换vpn代理
  * shadowsocks凭借维护的pac文件自动识别是否是别gfw过滤域名，是的话走代理，否则不走代理，这点很方便，不需要你去关注，你只需要想着该google时就google
  * 其他方式比如修改host，一段时间后就被和谐了，很不稳定；GoAgent也是，不稳定，需要频繁部署代理，其实某些时候你只是想要google些资料，却因如何可以用google浪费大量时间。
    * **PS**汇总这些详细方法，见[Google Drive](https://drive.google.com/folderview?id=0B3jQIp1ENRcfUU5xZUVRWUdXRVU&usp=sharing)，也可参考[smartladder](https://code.google.com/p/smartladder/)。
  * 安全系数高，抗封锁能力强，[为什么呢？](https://plus.google.com/u/0/109790703964908675921/posts/TtWFAQmSMVE)？

## 客户端怎么使用？

  * 跨平台支持window、mac、Android、ios、wp [客户端下载地址](https://shadowsocks.com/client.html)
  * 简单的不同平台安装说明
    * 手把手教会你使用ss，列举几篇使用方法介绍文章 [通天塔介绍 MAC OSX 系统下使用方法](http://ttt.tt/150/)、[简书介绍 windows 平台使用](http://www.jianshu.com/p/a04327bcb9a9)、[IOS 系统使用方法](http://shadowsocks.info/shadowsocks-ios-mac-osx/)、[安卓Android平台使用方法](http://www.uudaili.org/android_shadowsocks.html)，另外，mac 最新的客户端已经可以不用Proxy SwitchySharp这个插件了，安装最新版的MAC客户端，默认可以根据pac文件代理所有浏览器的访问，很是方便。
    * 还是不会用？google搜索[shadowsocks使用方法](https://www.google.com.hk/search?q=shadowsocks+%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95&oq=shadowsocks+%E4%BD%BF%E7%94%A8%E6%96%B9%E6%B3%95&aqs=chrome..69i57j0j69i61.6446j0j7&sourceid=chrome&es_sm=119&ie=UTF-8&gws_rd=cr,ssl)
  * 几个常见工具[下载地址](https://milooo.net/download.html)，包括Autoproxy.pac文件、proxy switchsharp、ios openvpn配置等。

## 账号资源

shadowsocks 客户端是很强大、稳定、快速的，跨平台，省去很多麻烦，但这依赖与稳定的服服务端，你可以自己购买vps ，搭建shadowsocks的服务器端，只需要vps的钱即可，shadowsocks 服务端开源免费（还是得感谢shadowsocks作者 [@clowwindy](https://twitter.com/clowwindy)的无私奉献），可以去[github](https://github.com/shadowsocks/shadowsocks)下载搭建，参考[搭建教程](http://www.atgfw.org/2015/01/shadowsocks.html)，也可以购买市场上许多服务商提供的服务，相比自己搭建，还得需要去关心服务器的稳定性， xirong 更推荐使用经济的代理服务商，便宜省事，当然，你也可以到网上到处搜寻免费的 shadowsocks账号，这也是可以的。

**强烈推荐付费购买，省时间、省精力，不用去网上找各种不稳定的免费账号，便宜不贵。**

  * [shadowsocks.com](https://shadowsocks.com/) 线路优质，技术成熟,多线路支持。有年付有普通版的99元，也有高大上的399元高级版套餐可选，美国，新加坡，台湾，日本等各国线路可以选择。
  * [枫叶主机](http://www.fyzhuji.com/aff.php?aff=531) **本人正在使用的付费服务**,目前提供美国，日本，香港，大陆中专、新加坡、台湾等数十条的shadowsocks收费账号，服务稳定，套餐形式以流量为单位，如分40G，60G，150G/每月流量;分别年付价格是50元，80元，120元。适合流量不是很大，要求线路质量高的朋友，价格真心便宜。而且某些公司许多端口被封，需要使用特定的端口，枫叶主机高级套餐支持自定义shadowsocks服务端端口，省去了公司不能使用的烦恼。
  * 其他，据网络资源推荐，不知道效果：
    1. [SSH91](http://my.ssh91.net/) 美国，日本，香港，新加坡一号通的shadowsocks账号，季付30元，年付98元，同时不定期提供18元的美国普及年付账号．选择性更多。
    2. UUDaili 免费的SSH与vpn一月1G流量,注册后可以免费送2个月使用。目前有美国，新加坡，日本的线路，美国为主，价格便宜。
    3. PGfastss、shadowcheap 等，其他的自行发掘吧。

**免费账号网站推荐**

  1. [V2EX](http://pvg.v2ex.com/go/shadowsocks) shadowsocks区经常有人会分享自己的账号，也有些使用方法、心得的讨论，可以常去关注下。
  2. [Shadowsocks公益组织](http://shadowsocks.net/) 一个由民间团体发起的，旨在分享Shadowsocks帐号的平台，你可以在该平台上分享你的ShadowSocks帐号，也可以在该平台上获取免费的帐号。（貌似最近网站上不去了）
  3. [shadowsocks info](http://shadowsocks.info/) 分享shadowsock相关各种知识的网站，比较基础，也有干货！  
2015-06-02 更新
  4. [google + shadowsocks翻墙圈](https://plus.google.com/u/0/communities/106442142549456855872) 可以随时获取别人共享的免费账号

介绍了这么些，如果您想体验下 shadowsocks，那么尽情的使用免费账号吧，如果您感觉到了免费账号的不稳定给您带来的不方便，那么推荐使用付费服务，每年只需要支付一笔很少的费用，即可享受畅快的网络，将精力放在如何利用不受阻的网络来解决自己的问题上面，岂不是更有意义？ 在这里还是推荐下我使用的 `[枫叶主机](http://www.fyzhuji.com/aff.php?aff=531)` 速度快、服务稳定，高级套餐支持自定义端口，使用 `[xirong 的推广链接](http://www.fyzhuji.com/aff.php?aff=531)` 购买可以享受 `10%` 的折扣，稳定、快速，你值得拥有！

# 玩转 Shadowsocks

### 【入门篇】WINDOWS 客户端使用方法

[1、Windows客户端 – shadowsocks-csharp](http://cokebar.info/archives/368)

[2、Chrome+SwitchSharp实现GoAgent与Shadowsocks混合代理](http://cokebar.info/archives/191)

### 【进阶篇】路由器全自动翻墙

**一、进阶的准备工作：**

[1、[强力推荐站点] 鸟哥的Linux私房菜 – 学习Linux](http://vbird.dic.ksu.edu.tw/)

[2、[摘录] 全面学习GFW](http://cokebar.info/archives/253)

**二、路由器翻墙三部曲**

[1、Shadowsocks + ChnRoute 实现 OpenWRT 路由器自动翻墙](http://cokebar.info/archives/664)

[2、Shadowsocks + Redsocks 实现 OpenWRT 路由器自动翻墙](http://cokebar.info/archives/948)

[3、Shadowsocks + GfwList 实现 OpenWRT 路由器自动翻墙](http://cokebar.info/archives/962)

**三、其他**

[1、Shadowsocks for OpenWRT 拾遗](http://cokebar.info/archives/850)

[2、改善DNS解析 – OpenWRT安装配置pdnsd](http://cokebar.info/archives/734)

[3、OpenWRT 自动更新软件包脚本](http://cokebar.info/archives/930)

### 【高级篇】 自己搭建SHADOWSOCKS服务器

[1、shadowsocks – libev 服务端的部署](http://cokebar.info/archives/767)

[2、pdnsd搭建DNS服务器简易教程](http://cokebar.info/archives/720)

[3、利用dnsmasq搭建DNS服务器超简易教程](http://cokebar.info/archives/699)

[4、Ubuntu 后台开启 ss-server 多进程多配置文件的方法](http://cokebar.info/archives/1104)