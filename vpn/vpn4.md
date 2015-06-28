# VPN 在 Mac 上的分步指南 (使用 OpenVPN)

本文档描述了如何使用 **[Tunnelblick](http://code.google.com/p/tunnelblick/)** 连接到 VPN Gate 中继 VPN 服务器。Tunnelblick 是适用于 Mac OS X 的 OpenVPN Client 的一个 GUI 版本。

在该指南中，每个屏幕截图均来自 Mac OS X 山狮版。Mac OS X 其他版本的配置方法类似，但在用户界面上会有少许不同。

这些截屏来自 Mac OS X 的英文版。如果你使用其他语言，你可能通过参考以下指南很轻松地配置。

  * [在 Mac OS X 里 L2TP/IPsec 非常容易使用。](http://www.vpngate.net/cn/howto_l2tp.aspx)  
OpenVPN VPN Client 软件嵌入在 Mac。L2TP 比 OpenVPN 容易配置。我们推荐在尝试 OpenVPN 前试试 L2TP/IPsec。一些防火墙可能会滤 L2TP/IPsec 数据包。在这种网络中，你应该使用 OpenVPN。

 

#### 1. 安装 Tunnelblick (只需在第一次时安装一次)

从以下链接下载和安装 Tunnelblick。你应该下载最新版本 (如果有试用版的话) 来使用。

  * [**http://code.google.com/p/tunnelblick/**](http://code.google.com/p/tunnelblick/)

安装应按照屏幕上的说明来进行。

![](http://www.vpngate.net/images/ss/openvpn_mac/01.jpg)

安装完成后，将显示以下屏幕。点击 **"I have configuration files"** 。

![](http://www.vpngate.net/images/ss/openvpn_mac/02.jpg)

点击 **"OpenVPN Configuration (s)"** 按钮。

![](http://www.vpngate.net/images/ss/openvpn_mac/03.jpg)

点击 **"Create Tunnelblick VPN Configuration"** 按钮。

![](http://www.vpngate.net/images/ss/openvpn_mac/04.jpg)

一个新的文件夹，**"Empty Tunnelblick VPN Configuration"**, 将在桌面上创建。

#### 2. 下载并安装 OpenVPN 的连接配置文件 (.ovpn file) (只需在第一次时安装一次)

通过使用 OpenVPN 为了连接到一个 VPN Gate 公共 VPN 中继服务器，你必须下载一个 OpenVPN 连接设置文件 (.ovpn)。

  *  OpenVPN 连接设置文件从** [公共 VPN 中继服务器列表页面](http://www.vpngate.net/cn/) **下载。  
选择一个你想要连接的 VPN 服务器，并点击 ".ovpn" 文件下载到桌面。

.ovpn 文件的图标如以下图片。

![](http://www.vpngate.net/images/ss/openvpn_mac/05.jpg)

移动和复制此 OpenVPN 连接设置文件 (.ovpn 文件) 到上一步在桌面上自动创建的 **"Empty Tunnelblick VPN Configuration"** 文件夹。

![](http://www.vpngate.net/images/ss/openvpn_mac/06.jpg)

下一步，重命名桌面上 **"Empty Tunnelblick VPN Configuration"** 文件夹为 **"anyname.tblk"** 。("anyname"的部分可以变化。) 重命名后，你必须指定后缀 ".tblk" 。  
当你要重命名时，将显示以下消息。点击 **"Add"** 按钮。

![](http://www.vpngate.net/images/ss/openvpn_mac/07.jpg)

双击 .tblk 文件夹，将显示以下屏幕。点击 **"Only Me"** 。

![](http://www.vpngate.net/images/ss/openvpn_mac/08.jpg)

你将输入 Mac OS X 的用户名和密码。

![](http://www.vpngate.net/images/ss/openvpn_mac/09.jpg)

上述步骤导入 OpenVPN 连接设置文件 (.ovpn 文件) 至 Tunnelblick 里。

#### 3. 连接 VPN

点击 Mac OS X 菜单栏的 Tunnelblick 图标，并点击 **"Connect vpn"** 。( "vpn" 部分可以变化。) VPN 连接将被发起。

![](http://www.vpngate.net/images/ss/openvpn_mac/10.jpg)

VPN 连接状态屏幕显示如下。

![](http://www.vpngate.net/images/ss/openvpn_mac/11.jpg)

在 VPN 连接建立后， Tunnelblick 的主屏幕显示 **"Connected"** 。

![](http://www.vpngate.net/images/ss/openvpn_mac/12.jpg)

#### 4. 通过 VPN 中继享受互联网

当 VPN 建立时，所有到互联网的通讯将通过 VPN 服务器转发。  
您还可以访问 **[VPN Gate 顶部页面](http://www.vpngate.net/cn/) **来查看当前的全球 IP 地址。如果你连接到一个位于海外国家的 VPN 服务器，您可以看到您的来源国或地区已更改为其他的。

![](http://www.vpngate.net/images/ss/l2tp_mac/08.jpg)

当你的 VPN 连接建立时，享受 YouTube、Facebook 或 Twitter 吧。  
Facebook、Twitter 和 Gmail 使用 HTTPS (SSL) 加密的通信协议。无论是否通过 VPN ，没有人可以窃听这些加密通信。

### VPN 在 iPhone / iPad 上的分步指南 (使用 OpenVPN)

本文档描述了如何使用 OpenVPN 连接到 VPN Gate 中继 VPN 服务器。[**OpenVPN Connect**](https://itunes.apple.com/us/app/openvpn-connect/id590379981) 是由 [OpenVPN 科技有限公司](http://openvpn.net/) 开发的适用于 iOS 的一个 OpenVPN Client。

在该指南中，每个屏幕截图均来自 iOS 6 版。Mac OS X 其他版本的配置方法类似，但在用户界面上会有少许不同。

这些截屏来自 iOS 的英文版。如果你使用其他语言，你可能通过参考以下指南很轻松地配置。

  * [在 iOS 里 L2TP/IPsec 非常容易使用。](http://www.vpngate.net/cn/howto_l2tp.aspx)  
OpenVPN VPN Client 软件嵌入在 iOS。L2TP 比 OpenVPN 容易配置。我们推荐在尝试 OpenVPN 前试试 L2TP/IPsec。一些防火墙可能会滤 L2TP/IPsec 数据包。在这种网络中，你应该使用 OpenVPN。

#### 1. 安装 OpenVPN Connect (只需在第一次时安装一次)

开启 **"App Store"** ，搜索并下载 **"OpenVPN Connect"** 。

  * 如果你正在 iPhone / iPad 浏览网站，**[点击这里](https://itunes.apple.com/us/app/openvpn-connect/id590379981) **来安装它。

[![01.jpg (114379 バイト)](http://www.vpngate.net/images/ss/openvpn_ios/ss/01_small.jpg)](http://www.vpngate.net/images/ss/openvpn_ios/01.jpg)

#### 2. 下载并安装 OpenVPN 的连接配置文件 (.ovpn file) (只需在第一次时安装一次)

通过使用 OpenVPN 为了连接到一个 VPN Gate 公共 VPN 中继服务器，你必须下载一个 OpenVPN 连接设置文件 (.ovpn)。

  * OpenVPN 连接设置文件从**[公共 VPN 中继服务器列表页面](http://www.vpngate.net/cn/) **下载。

在你安装 OpenVPN Connect 以后，你可以打开** [公共 VPN 中继服务器列表页面](http://www.vpngate.net/cn/)**，点击.ovpn 文件并直接导入到 OpenVPN Connect。

你也可以在你的电脑打开 **[公共 VPN 中继服务器列表页面](http://www.vpngate.net/cn/)**，下载一个 .ovpn 文件，在邮件里附上它发送到 iPhone / iPad。

[![02.jpg (147284 バイト)](http://www.vpngate.net/images/ss/openvpn_ios/ss/02_small.jpg)](http://www.vpngate.net/images/ss/openvpn_ios/02.jpg) [![03.jpg (49669 バイト)](http://www.vpngate.net/images/ss/openvpn_ios/ss/03_small.jpg)](http://www.vpngate.net/images/ss/openvpn_ios/03.jpg)

当你尝试在 iOS 上打开.ovpn 文件时， OpenVPN Connect 将自动开启。您是否要安装.ovpn 文件的问题显示出来。  
点击 **"+"** 按钮安装.ovpn 文件。

[![04.jpg (104643 バイト)](http://www.vpngate.net/images/ss/openvpn_ios/ss/04_small.jpg)](http://www.vpngate.net/images/ss/openvpn_ios/04.jpg)

#### 3. 连接 VPN

连接一个 VPN ，开启 OpenVPN Connect ，选择一个已导入的.ovpn 文件，并点击 **"OFF"** 按钮。

VPN 建立后， **"Connected"** 状态显示如下。

[![05.jpg (94287 バイト)](http://www.vpngate.net/images/ss/openvpn_ios/ss/05_small.jpg)](http://www.vpngate.net/images/ss/openvpn_ios/05.jpg) [![06.jpg (115309 バイト)](http://www.vpngate.net/images/ss/openvpn_ios/ss/06_small.jpg)](http://www.vpngate.net/images/ss/openvpn_ios/06.jpg)

#### 4. 通过 VPN 中继享受互联网

当 VPN 建立时，所有到互联网的通讯将通过 VPN 服务器转发。  
您还可以访问 **[VPN Gate 顶部页面](http://www.vpngate.net/cn/) **来查看当前的全球 IP 地址。如果你连接到一个位于海外国家的 VPN 服务器，您可以看到您的来源国或地区已更改为其他的。

当 VPN 建立时， iOS 在屏幕最上面一栏显示 **"VPN"** 指标。

![](http://www.vpngate.net/images/ss/openvpn_ios/07.jpg)

当你的 VPN 连接建立时，享受 YouTube、Facebook 或 Twitter 吧。  
Facebook、Twitter 和 Gmail 使用 HTTPS (SSL) 加密的通信协议。无论是否通过 VPN ，没有人可以窃听这些加密通信。

### VPN 在安卓上的分步指南 (使用 OpenVPN)

本文档描述了如何使用 OpenVPN Connect 到 VPN Gate 中继 VPN 服务器。**[OpenVPN Connect](https://play.google.com/store/apps/details?id=net.openvpn.openvpn&hl=en)** 是由 [OpenVPN 科技有限公司](http://openvpn.net/) 开发的适用于安卓的一个 OpenVPN Client。

在该指南中，每个屏幕截图均来自安卓 4.x 版。安卓 4.x 其他版本的配置方法类似，但在用户界面上会有少许不同。这些截屏来自安卓英文版。如果你使用其他语言，你可能通过参考以下指南很轻松地配置。

  * [在安卓里 L2TP/IPsec 非常容易使用。](http://www.vpngate.net/cn/howto_l2tp.aspx)  
OpenVPN VPN Client 软件嵌入在安卓。L2TP 比 OpenVPN 容易配置。我们推荐在尝试 OpenVPN 前试试 L2TP/IPsec。一些防火墙可能会滤 L2TP/IPsec 数据包。在这种网络中，你应该使用 OpenVPN。

#### 1. 安装 OpenVPN Connect (只需在第一次时安装一次)

开始 **"Google Play Store"** ，搜索 **"OpenVPN Connect"** 应用并下载它。

  *  如果你正在安卓上浏览此网站，**[点击这里下载它](https://play.google.com/store/apps/details?id=net.openvpn.openvpn&hl=en)**。

[![01.jpg (116719 バイト)](http://www.vpngate.net/images/ss/openvpn_android/ss/01_small1.jpg)](http://www.vpngate.net/images/ss/openvpn_android/01.jpg)

#### 2. 下载并安装 OpenVPN 的连接配置文件 (.ovpn file) (只需在第一次时安装一次)

通过使用 OpenVPN 为了连接到一个 VPN Gate 公共 VPN 中继服务器，你必须下载一个 OpenVPN 连接设置文件 (.ovpn)。

  * OpenVPN 连接设置文件从 **[公共 VPN 中继服务器列表页面](http://www.vpngate.net/cn/)** 下载。

在你安装 OpenVPN Connect 以后，你可以打开 **[公共 VPN 中继服务器列表页面](http://www.vpngate.net/cn/)**，点击.ovpn 文件并直接导入到 OpenVPN Connect。

你也可以在你的电脑打开 **[公共 VPN 中继服务器列表页面](http://www.vpngate.net/cn/)**，下载一个.ovpn 文件，在邮件里附上它发送到安卓。

[![03.jpg (164579 バイト)](http://www.vpngate.net/images/ss/openvpn_android/ss/03_small1.jpg)](http://www.vpngate.net/images/ss/openvpn_android/03.jpg) [![04.jpg (63514 バイト)](http://www.vpngate.net/images/ss/openvpn_android/ss/04_small1.jpg)](http://www.vpngate.net/images/ss/openvpn_android/04.jpg) [![05.jpg (69165 バイト)](http://www.vpngate.net/images/ss/openvpn_android/ss/05_small1.jpg)](http://www.vpngate.net/images/ss/openvpn_android/05.jpg) [![06.jpg (139644 バイト)](http://www.vpngate.net/images/ss/openvpn_android/ss/06_small1.jpg)](http://www.vpngate.net/images/ss/openvpn_android/06.jpg)

#### 3. 连接 VPN

连接一个 VPN ，开启 OpenVPN Connect ，选择一个已导入的 .ovpn 文件，并点击 **"Connect"** 按钮。  
VPN 建立后， **"Connected"** 状态显示如下。

[![02.jpg (166675 バイト)](http://www.vpngate.net/images/ss/openvpn_android/ss/02_small1.jpg)](http://www.vpngate.net/images/ss/openvpn_android/02.jpg) [![07.jpg (103226 バイト)](http://www.vpngate.net/images/ss/openvpn_android/ss/07_small.jpg)](http://www.vpngate.net/images/ss/openvpn_android/07.jpg)

#### 4. 通过 VPN 中继享受互联网

当 VPN 建立时，所有到互联网的通讯将通过 VPN 服务器转发。  
您还可以访问 **[VPN Gate 顶部页面](http://www.vpngate.net/cn/) **来查看当前的全球 IP 地址。如果你连接到一个位于海外国家的 VPN 服务器，您可以看到您的来源国或地区已更改为其他的。

![](http://www.vpngate.net/images/ss/openvpn_android/08.jpg)

当你的 VPN 连接建立时，享受 YouTube、Facebook 或 Twitter 吧。  
Facebook、Twitter 和 Gmail 使用 HTTPS (SSL) 加密的通信协议。无论是否通过 VPN ，没有人可以窃听这些加密通信。

### 使用 OpenVPN 的任何错误 ?

  * 确保该目标主机名称或 IP 地址是正确的，查看 [VPN 服务器列表页](http://www.vpngate.net/cn/)。
  * 如果你导入 .ovpn 文件的主机名称或 IP 地址数据太旧了，你必须再下载.ovpn 文件的最新版本。
  * 在某些国家或地区，指定 DDNS 主机名称 (.opengw.net) 可能会失败。在这样的环境中，直接指定 IP 地址来代替 DDNS 主机名称。
  * 你的本地防火墙可能会过滤所有 OpenVPN 数据包。在这种网络中， OpenVPN 不能被使用。如果你使用 Windows ，[尝试使用 SoftEther VPN Client](http://www.vpngate.net/cn/howto_softether.aspx)。Mac、iOS 或安卓，[尝试使用 L2TP/IPsec](http://www.vpngate.net/cn/howto_l2tp.aspx)。

**Copyright © 2015 VPN Gate 学术实验项目 @ 日本国立筑波大学。保留所有权利。**  
VPN Gate is based on SoftEther VPN Software which is developed by [SoftEther VPN Project](http://www.softether.org/).  
[国家国旗图标供应商](http://icondrawer.com/) | [什么是 VPN Gate](http://www.vpngate.net/cn/about_us.aspx) | [支持论坛](http://www.vpngate.net/cn/forum.aspx) | [镜像站点列表](http://www.vpngate.net/cn/sites.aspx) | [VPN Gate 反滥用政策](http://www.vpngate.net/cn/about_abuse.aspx) | [配合特定区域行政法规实施的声明](http://www.vpngate.net/cn/about_us.aspx#comply) | [日本国立筑波大学网站](http://www.tsukuba.ac.jp/chinese/)