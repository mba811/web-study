# GoAgent

###Mac系统翻墙-GoAgent的安装和使用图文教程（mac系统最好的翻墙工具）


**苹果软件盒子小编亲测可用，速度很快！让收费vpn到一边凉快****去****吧~**

专用的番墙软件基本都河蟹了，让我们自力更生通过自己的代理服务器访问网络。

一、申请个人appid（[http://appengine.google.com](http://appengine.google.com/)）

![1405140036839141f041952752.png](http://www.macappbox.com/d/file/tips/2014/4321f7a092404b8c772cc98f7f00055b.png)

 

二、**在“应用程序”→“实用工具”里找到“终端” 来安装goagent依赖库**

1.        安装brew

在终端执行(复制粘贴即可)：ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"

2.        安装libevent

在终端执行：brew install libevent

3.        安装pip

在终端执行：sudo easy_install pip

4.        安装cython

在终端执行：sudo ARCHFLAGS=-Wno-error=unused-command-line-argument-hard-error-in-future pip install cython

5.        安装greenlet

在终端执行：sudo ARCHFLAGS=-Wno-error=unused-command-line-argument-hard-error-in-future pip install greenlet

6.        安装gevent

在终端执行：sudo pip install gevent

7.        安装pycrypto

在终端执行：sudo ARCHFLAGS=-Wno-error=unused-command-line-argument-hard-error-in-future easy_install pycrypto

 

三、安装goagent 

1.下载goagent（[http://code.google.com/p/goagent/](http://code.google.com/p/goagent/)）

2. 解压缩文件并复制到/Application(应用程序目录)/goagent/目录

3. 修改/Application/goagent/local目录中的proxy.ini文件

a. 修改[gae]节中的appid值为你申请的个人appid

b. 如果希望使用google dns server，修改[dns]节中的enable值为1

4. 在“应用程序”→“使用工具”里找到并打开“钥匙串访问”工具，导入/Application/goagent/local目录中的CA.crt证书文件到“系统”类别下，设置此证书的信任为“总是信任”（双击CA.crt文件会导入到“登录”类别，而不是“系统”类别）

5. 上传uploader.zip文件到GAE

a. 打开终端, 切换到/Application/goagent/server目录

b. 执行：python uploader.zip update ./

 

四、使用goagent

1. 创建新的网络位置

打开系统偏好设置->网络，点击“位置：”下拉列表框中的“编辑位置…”项，新建网络位置。例如：新建名为“goagent代理”，并勾选Web代理、安全Web代理，代理服务器地址为127.0.0.1,端口为8087

![1405141325f1b0551bebb63903.png](http://www.macappbox.com/d/file/tips/2014/e502f73127e345a9a7d7afff0bc44c90.png)

![1405141325f1b0551bebb63903.png](http://www.macappbox.com/d/file/tips/2014/e502f73127e345a9a7d7afff0bc44c90.png)

2.切换网络位置

点击“苹果菜单”中的“位置”项目进行网络位置的切换

![1405132307b4042453729fd56a.png](http://www.macappbox.com/d/file/tips/2014/94f7e92c3de0bc885109ff5c4c2e66d8.png)

3. 激活goagent代理

a. 打开终端, 切换到/Application/goagent/local/目录

b. 执行：sudo python proxy.py

**  
**

**让我们一起来感受真正的互联网吧！**

 

4. 关闭goagent代理

a. 切换到 “自动”网络位置

b. 关闭终端程序
