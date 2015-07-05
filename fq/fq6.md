# GoAgent 

>windows

 ## [一、用谷歌账号创建Application](id:anchor1)

进入https://appengine.google.com/ （没有谷歌账号就申请一个,需用手机号验证哦~）  
![appid1](http://ww4.sinaimg.cn/large/61bf40fagw1eedamucgl5j20dw02vmx9.jpg)  
点击红框内的英文  
![appid2](http://ww3.sinaimg.cn/large/61bf40fagw1eedaoo2xg6j20dw08x758.jpg)  
注意！红框内的最重要，输入了什么一定要记住，等等填Appid要用，填完点右边的Check Availability检查有没有被使用过。

蓝框内随便填，不重要，就是这个Application的名字。下面黄底的那些英文直接跳过，不用填！  
![appid3](http://ww3.sinaimg.cn/large/61bf40fagw1eedar3z08qj20dv03haah.jpg)  
往下拉橙色框内的复选框勾上。点击绿色框内的英文。  
![appid4](http://ww3.sinaimg.cn/large/61bf40fagw1eedarl6ffqj20dw04gmxf.jpg)  
不出意外就是红框内的英文显示成功了。我在这里就范例一个，其余9个可以自己再重复步骤申请！

## [二、下载GoAgent](id:anchor2)

下载请[点击此处](http://cl.ly/0j2f2d1w0T2H)

## [三、上传APPID](id:anchor3)

打开goagent文件夹下server/uploader.bat  
![APPID](http://ww4.sinaimg.cn/large/61bf40fagw1eedccv65q9j20dw094dgd.jpg)  
看图操作

先填Applicaiton Identifier（APPID）填进去，注意提示：多个APPID请用 | 号分开，填完回车。

填完APPID以后提示你填邮箱，填完回车。

然后填邮箱密码，填完回车。注意：此处输入密码不会显示出来，只要确认密码输入正确即可回车。

不出意外它就开始上传APPID，全部上传成功以后会有提示，按照提示操作即可！如下图

## [四、把上传好的APPID填至goagent/local/proxy.ini](id:anchor4)

![proxy.ini](http://ww3.sinaimg.cn/large/61bf40fagw1eedces4udhj20dw08vaak.jpg)  
如上图，我直接把Mac下的图片搬运来了（相同）

根据路径打开goagent/local/proxy.ini填入我抹掉的地方即可，格式和上传时一样，多个APPID请用 | 符号分开。完成后关闭。

## [五、设置浏览器或者网络（个人建议修改浏览器）](id:anchor5)

在这里我以Chrome浏览器为例，GoAgent+Proxy SwitchySharp是Chrome科学上网的最好方法。

Proxy SwitchySharp在/local/文件夹下，打开Chrome扩展程序界面，拖入下载好的文件，提示是否安装，点击安装。

SwitchyOptions.bak同样在/local/文件夹下。

打开Proxy SwitchySharp选项  
![Switchysharp](http://ww2.sinaimg.cn/large/61bf40fagw1eedcfx1b5pj20dw08x0t6.jpg)  
选择从文件恢复，选择下载好的SwitchyOptions.bak，是否覆盖，点击确定！

OK，到情景模式里选择_GoAgent PAC_。

#### 在这里我说一下GoAgent和GoAgent PAC的区别：GoAgent是所有网站都走GAE流量（速度较慢，但是所有网站都能上。）GoAgent PAC是根据pac文件检索地址需要使用GAE时才会使用（速度较快，但是有些网站会上不去）我还是推荐PAC，PAC上不去时再用GoAgent(省GAE流量，速度也快！）

## [六、添加证书](id:anchor6)

![certification](http://ww2.sinaimg.cn/large/61bf40fagw1eedcgpjyu2j20dw08cwev.jpg)

Chrome进入设置-显示高级设置，到HTTPS/SSL，点管理证书，接下来的看图操作，证书在local/CA.crt

## [七、开启GoAgent，开始畅游，呼吸墙外新鲜空气！](id:anchor7)

#### 首次运行请右键GoAgent以管理员身份运行

> 以后如果GoAgent有更新直接下载下来覆盖即可！

![update](http://ww4.sinaimg.cn/large/61bf40fagw1eedb2nr1mvj20dw02y0t2.jpg)  
如图，日期后有【否】的话，不需要上传APPID，日期后有【是】的话，需要重新上传APPID才可使用哦！

## [八、小技巧：让GoAgent开启自启动](id:anchor8)

打开local里的addto-startup.vbs提示点【是】即可！

>Mac OS X

## [一、用谷歌账号创建Application](id:anchor1)

进入https://appengine.google.com/ （没有谷歌账号就申请一个,需用手机号验证哦~）  
![appid1](http://ww4.sinaimg.cn/large/61bf40fagw1eedamucgl5j20dw02vmx9.jpg)  
点击红框内的英文  
![appid2](http://ww3.sinaimg.cn/large/61bf40fagw1eedaoo2xg6j20dw08x758.jpg)  
注意！红框内的最重要，输入了什么一定要记住，等等填Appid要用，填完点右边的Check Availability检查有没有被使用过。

蓝框内随便填，不重要，就是这个Application的名字。下面黄底的那些英文直接跳过，不用填！  
![appid3](http://ww3.sinaimg.cn/large/61bf40fagw1eedar3z08qj20dv03haah.jpg)  
往下拉橙色框内的复选框勾上。点击绿色框内的英文。  
![appid4](http://ww3.sinaimg.cn/large/61bf40fagw1eedarl6ffqj20dw04gmxf.jpg)  
不出意外就是红框内的英文显示成功了。我在这里就范例一个，其余9个可以自己再重复步骤申请！

## [二、下载安装python](id:anchor2)

python下载请[点击此处](http://www.python.org/ftp/python/2.7.3/python-2.7.3-macosx10.6.dmg)，然后安装，这个很简单哦！

## [三、下载GoAgent](id:anchor3)

下载请[点击此处](http://cl.ly/0j2f2d1w0T2H)，下载完毕，打开ZIP文件，把名字超长的文件夹名字改成goagent然后放在如图位置  
![apple](http://ww2.sinaimg.cn/large/61bf40fagw1eedatuvllij20dw09s75d.jpg)  
apple是用户名，不同的电脑不同的用户名（有人可能找不到，请在Finder的偏好设置-边栏，找到你所对应的用户名勾上）

## [四、利用Python上传Appid至GAE](id:anchor4)

打开终端，输入
    
    cd goagent/server
    

_回车_
    
    python uploader.zip
    

_回车_

会出现这样的界面  
![gae](http://ww1.sinaimg.cn/large/61bf40fagw1eedaw00fyaj20dw08egmh.jpg)  
你就可以把你申请的Applicaiton Identifier（APPID）填进去，注意提示：多个APPID请用 | 号分开，填完回车。

填完APPID以后提示你填邮箱，填完回车。

然后填邮箱密码，填完回车。注意：此处输入密码不会显示出来，只要确认密码输入正确即可回车。

不出意外它就开始上传APPID，全部上传成功以后会有提示，按照提示操作即可！

## [五、把上传好的APPID填至goagent/local/proxy.ini](id:anchor5)

![proxy.ini](http://ww1.sinaimg.cn/large/61bf40fagw1eedax61t8uj20dw08vaak.jpg)  
根据路径打开goagent/local/proxy.ini填入我抹掉的地方即可，格式和上传时一样，多个APPID请用 | 符号分开。完成后关闭。

## [六、下载GoAgentMac，修改设置](id:anchor6)

下载GoAgentMac请[点击此处](http://pan.baidu.com/share/link?shareid=353475&uk=2502473732)

下载完将GoAgentMac拖入Application

进入应用程序-GoAgentMac，右键显示包内容-Contents，打开Info.plist

找到GoAgentPath

修改/Users/（这里填你电脑的用户名，找不到请看第三步骤）/goagent/local/proxy.py

## [七、设置浏览器或者网络（个人建议修改浏览器）](id:anchor7)

在这里我以Chrome浏览器为例，GoAgent+Proxy SwitchySharp是Chrome科学上网的最好方法。

Proxy SwitchySharp在/local/文件夹下，打开Chrome扩展程序界面，拖入下载好的文件，提示是否安装，点击安装。

SwitchyOptions.bak同样在/local/文件夹下。

打开Proxy SwitchySharp选项  
![Switchysharp](http://ww4.sinaimg.cn/large/61bf40fagw1eedaz5msjij20dw08x0t6.jpg)  
选择从文件恢复，选择下载好的SwitchyOptions.bak，是否覆盖，点击确定！

OK，到情景模式里选择_GoAgent PAC_。

#### 在这里我说一下GoAgent和GoAgent PAC的区别：GoAgent是所有网站都走GAE流量（速度较慢，但是所有网站都能上。）GoAgent PAC是根据pac文件检索地址需要使用GAE时才会使用（速度较快，但是有些网站会上不去）我还是推荐PAC，PAC上不去时再用GoAgent(省GAE流量，速度也快！）

## [八、添加证书](id:anchor8)

![certification](http://ww3.sinaimg.cn/large/61bf40fagw1eedb0nw1sqj20dw0b20tm.jpg)  
找到local/CA.crt双击，看图操作！

## [九、开启GoAgentMac程序，呼吸墙外新鲜空气！](id:anchor9)

一切大功告成，一点都不难！

> 以后如果GoAgent有更新直接下载下来覆盖即可！

![update](http://ww4.sinaimg.cn/large/61bf40fagw1eedb2nr1mvj20dw02y0t2.jpg)  
如图，日期后有【否】的话，不需要上传APPID，日期后有【是】的话，需要重新上传APPID才可使用哦！

## [十、小技巧：让GoAgent开启自启动](id:anchor10)

打开系统偏好设置，进入用户与群组，进入登陆项  
![auto-startup](http://ww4.sinaimg.cn/large/61bf40fagw1eedb437tq8j20dw0azq3g.jpg)  
![auto-startup](http://ww1.sinaimg.cn/large/61bf40fagw1eedb4w1frtj20dw0az0tg.jpg)  
点+号，选择应用程序，找到GoAgentMac添加即可！


>proxy.ini各项参数介绍

```
[listen]  
#监听ip，如果需要允许局域网/公网使用，设为0.0.0.0即可  
ip = 127.0.0.1  
#使用GAE服务端的默认8087端口，如有需要你可以修改成其他的  
port = 8087  
#启动后goagent窗口是否可见，0为不可见（最小化至托盘），1为不最小化  
visible = 1  
#是否显示详细debug信息  
debuginfo = 0

#GAE服务端的配置  
[gae]  
#你的Google app engine AppID,也就是服务器部署的APPID，配置多ID用|隔开  
appid = goagent  
#密码,默认为空,你可以在server目录的wsgi.py设定,如果设定了,此处需要与wsgi,py保持一致  
password = 123456  
#服务端路径,一般不用修改,如果不懂也不要修改.  
path = /2  
#使用http还是https(SSL加密传输)连接至GAE  
mode = https  
#填ipv6则使用[ipv6/hosts][ipv6/http]，默认ipv4使用[ipv4/hosts][ipv4/http]设置  
#此项设置意义与之前版本不同。非IPv6环境无需考虑，请勿随意修改  
profile = ipv4  
#ip评优算法每次选出的ip数量  
window = 4  
#是否开启流量混淆  
obfuscate = 0  
#是否对服务器证书进行验证  
validate = 0  
# 如果设置为 rc4 则开启rc4加密，需在password设置密码，否则不开启，一般mode为https时无需开启  
options =

# 用于连接GAE的IP列表  
[iplist]  
google_cn = 203.208.46.131|203.208.46.132|203.208.46.133|203.208.46.134|203.208.46.135|203.208.46.136|203.208.46.137|203.208.46.138  
google_hk = www.google.com|mail.google.com|www.google.com.hk|www.google.com.tw|www.l.google.com|mail.l.google.com  
google_ipv6 = 2404:6800:4005:c00::64|2404:6800:4005:c00::65|2404:6800:4005:c00::5e|2404:6800:4005:c00::67|2404:6800:4005:c00::2f

# 匹配的会使用crlf并且直连，=后留空则使用远程DNS解析，也可以手动指定IP防止因解析失败而无法使用，将IP写等号后面。  
# google_hk则表示使用[iplist]中的google_hk下的IP，google_cn则表示使用[iplist]中的google_cn下的IP  
[ipv4/hosts]  
s0.googleusercontent.com = google_hk  
s1.googleusercontent.com = google_hk  
s2.googleusercontent.com = google_hk  
s3.googleusercontent.com = google_hk  
s4.googleusercontent.com = google_hk  
s5.googleusercontent.com = google_hk  
s6.googleusercontent.com = google_hk  
gp0.googleusercontent.com = google_hk  
gp1.googleusercontent.com = google_hk  
gp2.googleusercontent.com = google_hk  
gp3.googleusercontent.com = google_hk  
gp4.googleusercontent.com = google_hk  
gp5.googleusercontent.com = google_hk  
gp6.googleusercontent.com = google_hk  
themes.googleusercontent.com = google_hk  
producer.googleusercontent.com = google_hk  
mail-attachment.googleusercontent.com = google_cn  
code.google.com = google_cn  
talk.google.com =  
talk.l.google.com =  
talkx.l.google.com =  
.google.com = google_hk  
.google.com.hk = google_hk  
.googleapis.com = google_hk  
.android.com = google_hk  
.appspot.com = google_hk  
.googlegroups.com = google_hk  
.googlesource.com = google_hk  
.googleusercontent.com = google_cn  
.google-analytics.com = google_cn  
.googlecode.com = google_cn  
.gstatic.com = google_cn  
.dropbox.com:443 =  
.box.com:443 =  
.copy.com:443 =  
https?://.+\.c\.youtube\.com/liveplay = google_hk  
;https?://www\.youtube\.com/watch = google_hk

[ipv4/http]  
crlfsites = .youtube.com|.google.com  
#匹配以此开头的域名强制跳转到https的网站  
forcehttps = groups.google.com|code.google.com|docs.google.com  
#使用伪造的证书，可以用来避免出现证书错误警告  
fakehttps = www.google.com  
#通过GAE的地址  
withgae = play.google.com

# 针对IPv6的设置  
[ipv6/hosts]  
talk.google.com =  
talk.l.google.com =  
talkx.l.google.com =  
.google.com = google_ipv6  
.googleusercontent.com = google_ipv6  
.googleapis.com = google_ipv6  
.google-analytics.com = google_ipv6  
.googlecode.com = google_ipv6  
.google.com.hk = google_ipv6  
.googlegroups.com = google_ipv6  
.googlesource.com = google_ipv6  
.appspot.com = google_ipv6  
.android.com = google_ipv6  
.dropbox.com:443 =  
.box.com:443 =  
.copy.com:443 =

[ipv6/http]  
crlfsites = .youtube.com|.google.com  
forcehttps = groups.google.com|code.google.com|docs.google.com  
fakehttps =  
withgae = play.google.com

#代理自动配置脚本(Proxy auto-config)设定  
[pac]  
#是否启用，若启用，浏览器代理自动配置地址填http://127.0.0.1:8086/proxy.pac  
enable = 1  
# pacserver的监听地址  
ip = 127.0.0.1  
port = 8086  
# pac文件的名称  
file = proxy.pac  
#被墙规则订阅地址  
gfwlist = http://autoproxy-gfwlist.googlecode.com/svn/trunk/gfwlist.txt  
#广告拦截规则订阅地址  
adblock = http://adblock-chinalist.googlecode.com/svn/trunk/adblock.txt  
#自动更新间隔时间  
expired = 86400

#对应php server 的设置  
[php]  
enable = 0  
password = 123456  
crlf = 0  
validate = 0  
listen = 127.0.0.1:8089  
fetchserver = https://.cm/  
usehosts = 1

#二级代理,一般内网会用到  
[proxy]  
#是否启用  
enable = 0  
autodetect = 1  
#代理服务器地址  
host = 10.64.1.63  
#代理服务器端口  
port = 8080  
#代理服务器登录用户名  
username = username  
#密码  
password = 123456

# 自动分段下载，需远程服务器支持Rang  
[autorange]  
#匹配以下域名时自动下载  
hosts = *.c.youtube.com|*.atm.youku.com|*.googlevideo.com|*av.vimeo.com|smile-*.nicovideo.jp|video.*.fbcdn.net|s*.last.fm|x*.last.fm|*.x.xvideos.com|*.edgecastcdn.net|*.d.rncdn3.com|cdn*.public.tube8.com|videos.flv*.redtubefiles.com|cdn*.public.extremetube.phncdn.com|cdn*.video.pornhub.phncdn.com|*.mms.vlog.xuite.net|vs*.thisav.com|archive.rthk.hk|video*.modimovie.com|*.c.docs.google.com  
# 自动对列表中文件类型启用分段下载功能  
endswith = .f4v|.flv|.hlv|.m4v|.mp4|.mp3|.ogg|.avi|.exe|.zip|.iso|.rar|.bz2|.xz|.dmg  
# 禁用分段下载的文件类型  
noendswith = .xml|.json|.html|.php|.py|.js|.css|.jpg|.jpeg|.png|.gif|.ico|.webp  
# 线程数  
threads = 3  
#一次最大下载量  
maxsize = 1048576  
#首次读写量  
waitsize = 524288  
#后续读写量  
bufsize = 8192

#DNS模块，可以用来防止DNS劫持/污染  
[dns]  
enable = 0  
#DNS监听地址，使用时将系统DNS设置为127.0.0.1  
listen = 127.0.0.1:53  
#远程DNS查询服务器  
remote = 8.8.8.8|8.8.4.4|114.114.114.114|114.114.115.115  
#缓存大小  
cachesize = 5000  
#超时时间  
timeout = 2

#模拟用户浏览器类型,在User-Agent里提交给服务器你的浏览器操作系统等信息  
[useragent]  
#是否启用  
enable = 0  
#可自行修改的，前提是你知道怎么改  
string = Mozilla/5.0 (iPhone; U; CPU like Mac OS X; en) AppleWebKit/420+ (KHTML, like Gecko) Version/3.0 Mobile/1A543a Safari/419.3

[fetchmax]  
local =  
server =

#不用理会,显示在控制台上方的公益广告  
[love]  
#不愿意看到这广告就把1改成0  
enable = 1  
timestamp = 1347983481  
tip = \u8bf7\u5173\u6ce8\u5317\u4eac\u5931\u5b66\u513f\u7ae5~~

```

>进阶适用于OS X MAC

众所周知GoAgent是一款支持科学上网的利器，但是用户都不知道其实GoAgent的完整配置应该是python+gevent+pyOpenSSL

py是一个平台，依靠这个平台来安装gevent+pyOpenSSL， gevent可以加快速度，pyOpenSSL是提高保密性。

* * *

  
本人是MAC用户，所以就先拿OS X说事！（WIN等过几天研究，不过exe文件目测直接打开。。）

  * 先把GoAgent装上，这个会不多费口舌了
  * 下载Gevent [MAC用](http://pan.baidu.com/share/link?shareid=336151&uk=2502473732) ，下载完把它解压到如图位置  
![Finder](http://ww1.sinaimg.cn/large/61bf40fagw1eea1nhzu5cj20dw0aqt9w.jpg)  
apple是用户名，不同的电脑不同的用户名（有人可能找不到，请在Finder的偏好设置-边栏，找到你所对应的用户名勾上）  
解压出来的文件夹改名为Gevent
  * 使用终端命令开启Gevent（只需知道步骤，无需知道原理，越简单越好！）  
打开终端

    1. 输入cd gevent回车
    2. 输入python fetch_libevent.py回车
    3. 输入python setup.py build回车，会有很多很多的代码，不用管，等它停下了继续输
    4. 输入sudo su 要求输入Password，这里的Password是指ROOT密码，简单！输入sudo passwd root设置密码（输完sudo passwd root后它会要求你输入用户登陆密码，一定要设置一个密码，不然无法继续！）
    5. 输入python setup.py install回车，OK，大功告成！  
其实很简单！

* * *

  1. 注：适用于已能使用GoAgent科学上网 [↩](http://goagent.w1nd.me/gevent1/#fnref-20:1)


>进阶 2 适用于OS X MAC

其实呢，这个可以不算阶段二，这只是（一）的第二种方法。

这是GoAgent的_官方安装方法_

* * *

  
安装方法：

首页下载最新的GoAgent版本

gevent文件：[点击此处下载](http://pan.baidu.com/share/link?shareid=353478&uk=2502473732)

把 gevent egg 文件放到 goagent/local 文件夹，然后重启 GoAgent 即可启用 gevent 依赖包

很简单，比我原来的简单多了！

* * *

  1. 注：适用于已能使用GoAgent科学上网 [↩](http://goagent.w1nd.me/gevent/#fnref-18:1)


>进阶 3 适用于OS X MAC

前两篇讲了如何在OS X下安装gevent，这次我继续讲另一个pyOpenSSL的安装教程。

* * *

OpenSSL：为网络通信提供安全及数据完整性的一种安全协议。也就是说装了这个会是我们使用GoAgent上网更安全（因为GoAgent本身保密性比较弱）。而前面的py只是因为它是用python语言写的，取其py前缀。

* * *

  
下面我就来说这个安装教程，其实和安装gevent是差不多的。

安装GoAgent就不说了，标题上就写了这是**进阶篇**  
使用终端安装pyOpenSSL 点击[此处下载](http://pan.baidu.com/share/link?shareid=339501&uk=2502473732)

  * 解压文件，移动文件夹
    1. apple是用户名，不同的电脑不同的用户名（有人可能找不到，请在Finder的偏好设置-边栏，找到你所对应的用户名勾上）
    2. 解压出来的文件夹改名为pyOpenSSL  
![Finder](http://ww2.sinaimg.cn/large/61bf40fagw1eea0t1puu7j20dv09575a.jpg)
  * 打开终端开始工作！
    1. 第一句：输入cd pyOpenSSL回车
    2. 第二句：输入sudo su 要求输入Password，输密码时是没有显示的，输完就回车。  
没有密码请看这里>>>>这里的Password是指ROOT密码，简单！输入sudo passwd root设置密码（输完sudo passwd root后它会要求你输入用户登陆密码，一定要设置一个密码，不然无法继续！）
    3. 第三句：输入python setup.py install回车，OK，完成了，很简单！

* * *

  1. 注：适用于已能使用GoAgent科学上网 [↩](http://goagent.w1nd.me/pyopenssl/#fnref-14:1)

  