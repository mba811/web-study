# hosts

**hosts文件**是一个用于储存[计算机网络](https://zh.wikipedia.org/wiki/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%BD%91%E7%BB%9C)中各节点信息的计算机文件。这个文件负责将[主机名](https://zh.wikipedia.org/w/index.php?title=%E4%B8%BB%E6%9C%BA%E5%90%8D&action=edit&redlink=1)映射到相应的[IP地址](https://zh.wikipedia.org/wiki/IP%E5%9C%B0%E5%9D%80)。hosts文件通常用于补充或取代网络中[DNS](https://zh.wikipedia.org/wiki/DNS)的功能。和DNS不同的是，计算机的用户可以直接对hosts文件进行控制。

## 历史

在[Internet](https://zh.wikipedia.org/wiki/Internet)的前身[ARPANET](https://zh.wikipedia.org/wiki/ARPANET)中并没有对网络中各节点的地址使用DNS进行解析。由于当时对于这个用途并没有中心化的系统，每个网络节点都使用自有的网络节点地图，并指派相应的名称方便用户记忆，当时并没有任何系统来保证网络中的所有系统都用同样的名称表示，也没有方法来读取其他用户的hosts文件并自动复制。

ARPANET的规模较小，这样就也就允许了在很多情况使用hosts文件来命名一些事先约定的名称。其中典型的网络节点都有一个地址，并可能有多个名称。但是当个人网络不断庞大之后，对hosts文件进行管理的难度也越来越大。

## 文件位置及默认内容

hosts文件在不同[操作系统](https://zh.wikipedia.org/wiki/%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F)（甚至不同Windows版本）的位置都不大一样：

  * [Windows NT](https://zh.wikipedia.org/wiki/Windows_NT)/[2000](https://zh.wikipedia.org/wiki/Windows_2000)/[XP](https://zh.wikipedia.org/wiki/Windows_XP)/[Vista](https://zh.wikipedia.org/wiki/Windows_Vista)/[7](https://zh.wikipedia.org/wiki/Windows_7)/[8](https://zh.wikipedia.org/wiki/Windows_8)（即微软NT系列操作系统）：默认位置为`%SystemRoot%\system32\drivers\etc\hosts`，但也可以改变。动态目录由[注册表](https://zh.wikipedia.org/wiki/%E6%B3%A8%E5%86%8C%E8%A1%A8)键`\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters\DataBasePath`决定。
  * [Windows 95](https://zh.wikipedia.org/wiki/Windows_95)/[98](https://zh.wikipedia.org/wiki/Windows_98)/[Me](https://zh.wikipedia.org/wiki/Windows_Me)：`%WinDir%\hosts`
  * [Linux](https://zh.wikipedia.org/wiki/Linux)及其他[类Unix操作系统](https://zh.wikipedia.org/wiki/%E7%B1%BBUnix%E6%93%8D%E4%BD%9C%E7%B3%BB%E7%BB%9F)：`/etc/hosts`
  * [Mac OS 9](https://zh.wikipedia.org/wiki/Mac_OS_9)及更早的系统：System Folder: Preferences或System folder（文件格式可能与Windows和Linux所对应的文件不同）
  * [Mac OS X](https://zh.wikipedia.org/wiki/Mac_OS_X)：`/private/etc/hosts`（使用BSD风格的hosts文件）
  * [OS/2](https://zh.wikipedia.org/wiki/OS/2)及[eComStation](https://zh.wikipedia.org/wiki/EComStation)：`"bootdrive":\mptn\etc\hosts`
  * [Android](https://zh.wikipedia.org/wiki/Android)：`/system/etc/hosts`
  * [Symbian](https://zh.wikipedia.org/wiki/Symbian)第1/2版手机：`C:\system\data\hosts`
  * Symbian第3版手机：`C:\private\10000882\hosts`，只能使用具有AllFiles权限的文件浏览器（也就是塞班系统的最高权限）访问，而绝大部分文件浏览器都不行（如X-plore和ActiveFile）[[1]](https://zh.wikipedia.org/wiki/Hosts%E6%96%87%E4%BB%B6#cite_note-1)。
  * iOS：`/private/etc/hosts`
  * webOS：`/etc/hosts`

  
在Windows中，默认的hosts文件通常是空白的或包含了[注释语句](https://zh.wikipedia.org/w/index.php?title=%E6%B3%A8%E9%87%8A%E8%AF%AD%E5%8F%A5&action=edit&redlink=1)并使用了一条默认规则：
    
    127.0.0.1       localhost
    ::1             localhost

## hosts文件的其它用途

hosts文件也可以用于其它情况，例如可以将已知的广告服务器重定向到无广告的机器（通常是本地的IP地址：127.0.0.1）上来过滤[广告](https://zh.wikipedia.org/wiki/%E7%BD%91%E7%BB%9C%E5%B9%BF%E5%91%8A)。同时也可以通过不下载网络广告，从而减少带宽。使用hosts文件还可以减少对DNS服务器的访问来加快访问速度并减少带宽消耗。

hosts文件的另一个重要用途就是用于拦截一些恶意网站的请求，从而防止访问欺诈网站或感染一些[病毒](https://zh.wikipedia.org/wiki/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%97%85%E6%AF%92)或[恶意软件](https://zh.wikipedia.org/wiki/%E6%81%B6%E6%84%8F%E8%BD%AF%E4%BB%B6)。但同时，这个文件也可能被病毒或恶意软件所利用来阻止用户更新杀毒软件或访问特定网站。

在中国大陆，由于[防火长城](https://zh.wikipedia.org/wiki/%E9%98%B2%E7%81%AB%E9%95%BF%E5%9F%8E)的[DNS劫持](https://zh.wikipedia.org/wiki/%E5%9F%9F%E5%90%8D%E6%9C%8D%E5%8A%A1%E5%99%A8%E7%BC%93%E5%AD%98%E6%B1%A1%E6%9F%93)，有一些网民也借使用hosts文件来强制将特定网站指定到未封锁的IP上。例如网络上有很多教授修改hosts文件来访问[Google搜索](https://zh.wikipedia.org/wiki/Google%E6%90%9C%E7%B4%A2)的教程。比如就有[维基媒体基金会](https://zh.wikipedia.org/wiki/%E7%BB%B4%E5%9F%BA%E5%AA%92%E4%BD%93%E5%9F%BA%E9%87%91%E4%BC%9A)的图片服务器IP地址被[ISP](https://zh.wikipedia.org/wiki/ISP)[封锁](https://zh.wikipedia.org/wiki/%E4%B8%AD%E5%8D%8E%E4%BA%BA%E6%B0%91%E5%85%B1%E5%92%8C%E5%9B%BD%E7%BD%91%E7%BB%9C%E5%AE%A1%E6%9F%A5)，通过修改hosts文件以正常显示图片的方法流传。


## 参见

  * [Adblock](https://zh.wikipedia.org/wiki/Adblock)
  * [ARPANET](https://zh.wikipedia.org/wiki/ARPANET)
  * [计算机病毒](https://zh.wikipedia.org/wiki/%E8%AE%A1%E7%AE%97%E6%9C%BA%E7%97%85%E6%AF%92)
  * [DNS](https://zh.wikipedia.org/wiki/DNS)
  * [Resolv.conf](https://zh.wikipedia.org/w/index.php?title=Resolv.conf&action=edit&redlink=1)
  * [恶意软件](https://zh.wikipedia.org/wiki/%E6%81%B6%E6%84%8F%E8%BD%AF%E4%BB%B6)
  * [间谍软件](https://zh.wikipedia.org/wiki/%E9%97%B4%E8%B0%8D%E8%BD%AF%E4%BB%B6)
  * [TCP/IP协议](https://zh.wikipedia.org/wiki/TCP/IP%E5%8D%8F%E8%AE%AE)
  * [特洛伊木马 (电脑)](https://zh.wikipedia.org/wiki/%E7%89%B9%E6%B4%9B%E4%BC%8A%E6%9C%A8%E9%A9%AC_(%E7%94%B5%E8%84%91))
  * [类Unix系统](https://zh.wikipedia.org/wiki/%E7%B1%BBUnix%E7%B3%BB%E7%BB%9F)
  * [Microsoft Windows](https://zh.wikipedia.org/wiki/Microsoft_Windows)

## 参考文献及注释

  1. **[^](https://zh.wikipedia.org/wiki/Hosts%E6%96%87%E4%BB%B6#cite_ref-1)** [Hosts file on S60 3.x Devices](http://wiki.forum.nokia.com/index.php/Hosts_file_on_S60_3.x_Devices). 2007-12-02 [2008-02-26] （英文）.

## 外部链接

  * （英文）[Why Should You Wait for Internet Propagation?](http://www.hackernotcracker.com/2007-01/why-should-you-wait-for-internet-propagation.html) – hosts的另一个用途
  * （英文）[Using a hosts file to remove ads without getting broken images](http://cubicspot.blogspot.com/2006/02/eliminating-web-advertisements.html) - 使用hosts文件来更方便地浏览网站
  * （英文）[一个示例文件](http://vlaurie.com/computers2/Articles/hosts.htm)

### 自定义hosts文件[[编辑](https://zh.wikipedia.org/w/index.php?title=Hosts%E6%96%87%E4%BB%B6&action=edit&section=7)]

  * （英文）[Most Valuable Professional (MVP) site](http://www.mvps.org/winhelp2002/hosts.htm) 每月更新的自定义HOSTS文件
  * （英文）[Dan Pollock's hosts file](http://someonewhocares.org/hosts/) 几乎每天更新的hosts文件
  * （英文）[Andrew Short’s Hosts file project](http://hostsfile.mine.nu/) – 内容全面的hosts文件
  * （英文）[HPHosts](http://www.hosts-file.net/?s=Download) – 用于广告拦截的hosts文件
  * （英文）[The Security Now! podcast page on the hosts file](http://www.grc.com/sn/notes-045.htm)
  * （英文）[Mikes Ad-Blocking hosts file](http://www.everythingisnt.com/hosts.html) – 可直接下载合并或使用安装程序
  * （英文）[SCoooBY’s Hosts File](http://members.dialmaine.com/drdole/#hosts) – 较大的广告服务器列表
  * （英文）[Ad Blocking Lists](http://pgl.yoyo.org/adservers/index.php) – Peter Lowe的列表
  * （法文） [Airelle Lists](http://rlwpx.free.fr/WPFF/hosts.htm) – 超过500,000个网站的Hosts文件黑名单
  * （简体中文） [SmartHosts](https://code.google.com/p/smarthosts) – 收录被屏蔽网站服务器信息的hosts文件

### 管理hosts的应用程序[[编辑](https://zh.wikipedia.org/w/index.php?title=Hosts%E6%96%87%E4%BB%B6&action=edit&section=8)]

  * （简体中文）[HostsX](https://code.google.com/p/hostsx/) – 记事本风格、支持自动更新 Hosts 文件的免费软件
  * （英文）[Abelhadigital's HostsMan 3.1.55](http://hostsman.abelhadigital.com/) – 可自动更新hosts文件的免费软件
  * （英文）[Kimberly's Hosts Manager](http://www.bluetack.co.uk/forums/index.php?act=dscript&CODE=showdetails&f_id=5) – 管理hosts文件的免费软件
  * （英文）[Funkytoad's HostsXpert v4.0](http://www.funkytoad.com/content/view/13/31/) – 用于排列并整理hosts文件的免费软件
  * （英文）[Mike Meyer's HostsToggle 2.1](http://www.accs-net.com/hosts/HostsToggle/) – 开放源代码的hosts文件工具
  * （英文）[KH Blocker](http://www.khempire.co.uk/) – 管理广告拦截的hosts文件管理器
  * （英文）[Ray Marron's Hostess](http://www.raymarron.com/hostess/) – 免费的hosts文件管理器