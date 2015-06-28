# Shadowsocks 配合 GoAgentX 科学上网

![](http://7q5cfr.com1.z0.glb.clouddn.com/kxsw1.png)

前一段时间的gmail事件可以通过这个种方法很好的解决，YouTube，twitter，你懂的。。。。。。

## 科普

**[Shadowsocks](http://maoshu.cc/tag/shadowsocks) 是什么技术？**

> **[Shadowsocks](http://maoshu.cc/tag/shadowsocks) **实质上也是一种 SOCKS5 代理服务，类似于 SSH 代理。与 VPN 的全局代理不同，**[Shadowsocks](http://maoshu.cc/tag/shadowsocks) **仅针对浏览器代理，不能代理应用软件，比如 Youtube、Twitter 客户端软件。

**ta和 VPN 有何区别？**

> Shadowsocks 本质上就是 SOCKS5 代理，可以做到根据网址判断自动开启，也可以全局代理；而 VPN 无法直接根据网址来判断，一般可以用 IP 路由判断，即国内 IP 不走 VPN，国外 IP 走 VPN。

## 哪里能获得 Shadowsocks 账号？

有许多人利用 Shadowsocks 的开源架构方案「[教程](https://github.com/shadowsocks/shadowsocks)」在自己的 VPS 主机上部署 Shadowsocks 网优，这种方式也只适合个人使用或小圈子共享，有许多人在网络社区里共享，传播这类 SS 账号，你可以碰碰运气，不过稳定性就大打折扣了，对方会随时关门大吉，你就得跟游击队似的折腾搬家了，小编在这里推荐一家商用的 SS 服务商吧：「[戳这里](https://shadowsocks.com/)」，价格还算公道，不限流量，比一般小 VPN 服务商速度快，连接稳定，价格又比 Astrill 这类 VPN 便宜许多，支持一台设备的普通版账号年付 99 RMB， 支持 5 台设备的高级版账号年付 399 RMB，而且比普通版多 5 个 VIP 节点，价格是 399 RMB 年付。「[购买地址](https://shadowsocks.com/)」

## 在 [GoAgentX](http://maoshu.cc/tag/goagentx) 的部署步骤

> [GoAgentX](http://maoshu.cc/tag/goagentx) 是一个在 Mac OS X 下使用代理服务的图形界面控制软件，方便一般用户在 Mac OS X 上配置和使用 GoAgent、West-Chamber-Season-3「西厢」、SSH、Stunnel 及 Shadowsocks。

大家知不知道，Shadowsocks 是一种局部代理结构，需要配合特定的客户端才能发挥效应，比如安装 Autoproxy 的火狐浏览器或者官方推荐的 ShadowsocksX Mac 客户端，后者是支持全局代理的，即你可以让 Tweetbot 这类客户端 bypass GFW，这次我们推荐另一种流行的全局代理工具：[GoAgentX](http://maoshu.cc/tag/goagentx)，操作同样简单，来看步骤：

  * 安装 GoAgentX 客户端「[下载地址](https://github.com/ohdarling/GoAgentX/archive/master.zip)」
  * 在 Menubar 上单击软件图标，弹出主窗口，在「服务」栏左边栏点击「+」添加「连接」
  * 「服务类型」选择「shadowsocks」，名称自定义：

![](http://7q5cfr.com1.z0.glb.clouddn.com/kxsw2.png)

  * 最后就是关键的参数填写环节，「本地端口」留空，填入 SS 服务器地址，端口，服务密码，加密方式选择「aes-256-cfb」即可：

![](http://7q5cfr.com1.z0.glb.clouddn.com/kxsw3.png)

  * 配置完毕，启动即可。

## 使用问题

如果你在 GoAgentX 启动 SS 后遇到这种提示信息“Error: server recv:Connection reset by peer”，请忽略，不会影响你的正常使用。
