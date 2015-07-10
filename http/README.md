# 简介

### 起步走

如果你跟大多数人一样，那么到现在你应该已经使用了很长时间的互联网了。每次都在浏览器顶部输入那些讨厌的 URL 网址，先写个 HTTP 啊，然后冒号，斜杠斜杠，然后三个大不留 (w)，接着是一串所谓域名的东西，每次上网都重复这，但是你从来不知道这些到底代表了什么。

HTTP 是 web 的核心，也是动态 web 应用的核心。理解 HTTP 是理解现代 web 应用如何工作和如何构建的核心。本书会讲一些与 HTTP 相关的基本概念，通过本书你会更好的理解 web 和 web 应用是怎么工作的。

### 适合读者

这本书是写给那些经常使用互联网，但是从来没有自己动手构建过动态 web 应用的人。写给那些对 web 应用工作原理感兴趣的人，为学习更高级的 web 应用开发概念打下基础。

### 怎样阅读这本书

本书关注可读性，没有很多练习，因为主要是一本讲概念的书。不过呢，书中的例子还是请你边学边跟着做，毕竟要真正的理解一个知识点，动手做做是最好的方法。

# 背景

### 概述和历史回顾

当你在浏览器地址栏输入 URL 的时候，你希望看到在你的浏览器里显示这个网站。当你点了一个链接，或者提交了一个表单，你的浏览器可能会显示下一个页面，或者在你的表单中显示一些错误提示，以便你能纠正它们并再次提交。你的浏览器就是一个接口，或者说一扇窗，通过她你就可以与万维网进行互动与交互。

在你的浏览器的背后，有一堆文件 -- CSS，HTML，Javascript，视频文件，图片文件等等 -- 这些文件构成了你所看到的页面。所有这些东西都是通过一个叫做 HTTP 的传输协议从**服务器**传输到你的浏览器，也就是**客户端**里（所以你现在知道为什么在浏览器地址栏输地址的时候前面加的是 `http://` 了吧）。

HTTP，或者超文本传输协议，是上世纪80年代由蒂姆.伯纳斯.李发明的。它是一个规则系统，是一种协议，把应用程序和超文本文档之间的传输联系起来。换句话说，HTTP 就是机器之间彼此沟通的一个协议，或者说一个消息格式。HTTP 遵循一个简单的模型：从客户端发出请求到服务器并等待响应。因此它也被认为是一种“请求--响应协议”。请求和响应都是文本信息，或者说是字符串，信息写法遵循着一个规则，能保证其他机器能够理解上面的内容。

HTTP 协议从创立之初已经经过了一些变化。最开始的时候这个协议仅仅返回 HTML 页面。在 1991年，第一个文档 HTTP/0.9 发布。1992年，HTTP/1.0 发布，并支持传输不同的文件类型，比如 CSS 文件，视频，脚本和图片。1995年，HTTP/1.1 介绍了连接复用和其他的一些特性。1999年又对 HTTP/1.1 做了一些改进，我们现在看到的就是这一版本。在撰写本文时，HTTP/2 正处于开发初期。

### 互联网是如何工作的

互联网是由数以百万计的互相连接的网络构成，网络中计算机和其他设备可以互相通信。按照惯例，网络内的所有设备都提供独特的标签。这种标签的总称是互联网协议地址或 IP 地址，是类似于在互联网上的计算机的电话号码。此外，IP 地址还有端口号，这会提供更多关于如何与其交流的细节 (类似于分机号码)。IP 地址一般都长这样：
    
    192.168.0.1
    

当需要一个端口号的时候，这样：
    
    192.168.0.2:1234
    

IP 地址是`192.168.0.2`，端口号是`1234`。 IP 地址是设备或服务器的标识符，可以包含数以千计的端口，每个端口都用于不同的交互目标。

互联网是比网络更大的一个概念，互联网上每个设备都有 [互联网服务供应商 (ISP)](http://en.wikipedia.org/wiki/Internet_service_provider) 提供的公网 IP 地址，通过这些地址，它们可以进行通信。当我们想访问 Google 的主页的时候，我们并没有在浏览器里输入它的 IP 地址，我们只是输入 Google 的 URL [http://www.google.com](http://www.google.com/)，但是像 [http://www.google.com](http://www.google.com/) 这样一个地址，你的电脑是怎么知道它的 IP 地址的呢？

### DNS

URL 和 IP 地址之间的对应由域名解析系统也就是常说的 DNS 来控制。DNS 是一个分布式数据库，把像[http://www.google.com](http://www.google.com/) 这样的域名翻译成 IP 地址，并将请求映射到远程服务器。换句话说，DNS 在互联网上记录 URL 和它对应的 IP 地址。所以像 [http://www.google.com](http://www.google.com/) 这样的域名会被解析成一个 IP 地址`197.251.230.45`。顺便提一下，通过在浏览器地址栏里敲 IP 地址也能访问网站。

不过，比起记一串数字来说，大多数人还是喜欢使用一个用户友好的地址如 [http://www.google.com](http://www.google.com/) 这样的。DNS 数据库被安装在叫做 DNS 服务器的设备上。重要的一点是，DNS 服务器集群是分层级的，没有任何一个单一的 DNS 服务器中包含所有数据。如果一个 DNS 服务器里没有一个请求需要的域名，这个 DNS 服务器就会把请求转发给这个集群上更上一层节点的 DNS 服务器。最终，这个域名会在某个 DNS 服务器上的数据库里被发现，然后它对应的 IP 地址所代表的设备就会来接受这个请求。

你通过浏览器与互联网交互的一个典型实例是这样的：

  1. 在浏览器里输入类似 [http://www.google.com](http://www.google.com/) 这样的地址。
  2. 你的请求被发送到你设备的网络接口。
  3. 这个请求的互联网之旅从搜索 [http://www.google.com](http://www.google.com/) 的 IP 地址开始。在屏幕后面，[http://www.google.com](http://www.google.com/) 代表了一个与某个远程服务器关联的 IP 地址的人类友好的名称。
  4. 远程服务器接受请求并将响应通过互联网发送到你的网络接口，并把它交给你的浏览器。
  5. 最终，浏览器把这个响应作为一个网页的形式呈现在你面前。

有一点你要明白，当你的浏览器发出请求的时候，它只是发送了一些文本到一个 IP 地址。因为客户端 (浏览器) 和服务器 (请求接收者) 之间有一个 HTTP 形式的约定，或者叫协议，这样服务器才可以分析请求，了解其组成并将响应发送回 web 浏览器。然后，web 浏览器将响应字符串处理成你能理解的内容。浏览像 Facebook，Google 和 Twitter 这样的网站，就意味着你一直在使用 HTTP。这些细节都被隐藏了，你的浏览器会自动处理好请求和响应。互联网的不同部分看起来像是这样的：

![](http://7q5cfr.com1.z0.glb.clouddn.com/@/http/h1.png)

### 客户端和服务器

最常见的客户端是你每天与之交互，被称为 Web 浏览器的应用程序。Web 浏览器常见的有 Internet Explorer、 火狐、 Safari，包括移动版本。Web 浏览器的职责是发送 HTTP 请求，并将响应处理成人类友好的形式显示在你的显示器上。web 浏览器并不是唯一的客户端，有很多工具或者应用都能发送 HTTP 请求。

你的请求的内容最终的接收者是被称为服务器的远程计算机。服务器也没啥神秘的，就是处理请求的设备，它们的工作就是发送一个响应回去。通常情况下，服务器发送回去的响应里面都包含了请求中指定的一些数据。

![](http://7q5cfr.com1.z0.glb.clouddn.com/@/http/h2.png)

### 资源 (Resources)

资源是一个通用术语，指的是互联网上你通过 URL 与其交互的东西。包括了图片，视频，网页和其他文件。资源并不限于文件或者网页。资源也可能是一个软件，一个炒股的软件，一个游戏。互联网上有无数的资源。

![](http://7q5cfr.com1.z0.glb.clouddn.com/@/http/h3.png)

### 无状态的 (statelessness)

当一个协议设计成每一个请求/响应周期与前一个都是互相独立的话，我们就说这个协议是无状态的。对于 HTTP 要知道的一点就是，无状态协议对于服务器资源和易用性的影响。HTTP 协议下，服务器不需要在各次请求之间保留状态信息。结果就是如果一次请求出了问题，系统不必做任何清理。以上两个原因让 HTTP 协议变的很灵活，但同时也变的很难构建有状态的应用。因为 HTTP 本质上是个无状态的互联网协议，这就意味着 web 开发人员在构建有状态应用的时候，不得不努力想办法来模拟 web 应用中的有状态体验。 举个例子，当你上 Facebook 的时候，你先登录，然后你看到了一个 Facebook 的网页。这就是一个完整的请求/响应周期。你点了一张照片 -- 另一个请求/响应周期 -- 但是在第二个动作之后你并没有退出登录。如果 HTTP 是无状态的，它是怎么维持状态并且知道你刚刚已经登录过了呢？事实上，如果 HTTP 是无状态的，Facebook 是怎么知道哪个请求是你发出的？它是怎么区分你和其他用户的？这些都是 web 开发人员和 web 开发框架耍的小诡计，让 web 应用看起来像是有状态的，不过这些小诡计不在本书的讨论范围内。你所要记住的就是，尽管你觉得这个应用是有状态的，但是在它背后，这个 web 应用是构建在 HTTP，一个无状态协议之上的。以上，就是为什么 web 如此灵活和去中心化，同时又特别难控制，也是为什么 web 的安全性难以保证，为什么在 web 上构建应用不是易事。

### 小结

本章用一种简单的描述解释了互联网如何工作和几个术语。你也学到了无状态对 web 应用的影响。在下一章，我们会深入探讨 [http://www.google.com](http://www.google.com/) 这样的地址到底是什么以及它各部分的作用。

# 什么是 URL？

### 简介

当你想去某人家里的时候，你要知道他家的地址。如果你想给你朋友打电话，你要知道你朋友的电话号码。没有这些信息，你想去别人家或者给人打电话都是不可能的。换句话说，如果你有别人的住址或者电话号码，你能立刻知道谁是谁，因为地址和电话号码都有其唯一性。

在互联网上寻找和访问服务器也是同样的一个概念。当你想上 Facebook 的游戏站的时候，你会打开浏览器然后输入 [http://www.facebook.com/games](http://www.facebook.com/games)。web 浏览器向这个地址发送一个 HTTP 请求，然后拿回这个地址的响应结果。你刚刚输入的那个地址，[http://www.facebook.com/games](http://www.facebook.com/games) 就是所谓的统一资源定位符 (Uniform Resource Locator) 或 URL。URL 就像是你跟你朋友沟通所需要的电话号码或者地址一样的存在。URL 应该是统一资源标识符 (Uniform Resource Identifier) 这个笼统的概念的一种最常见的形式。本章我们讨论什么是 URL 及其组成部分，和对你这个 web 开发者来说 URL 意味着什么。

### URL 组成部分

当你看到一个 URL，比如`http://www.example.com/home`，其实是由几个组件构成的。我们可以把这个 URL 分解成 3 部分：

  * `http`：通常被称为 URL 模式（ scheme ）。总是出现在冒号和两个斜杠之前，作用是告诉 web 客户端怎样去访问一个资源。在本例中，它告诉 web 客户端使用超文本传输协议也就是 HTTP 去发起一个请求。常见的 URL 模式还有`ftp`，`mailto`和`git`。
  * `www.example.com`：URL 的第二个部分，就是资源路径或主机 (host)。它告诉客户端，资源的确切位置。
  * `/home/`：URL 的第三个部分就是 URL 路径。它代表了客户端正在请求什么样的本地资源 (对于服务器来说)。

![](http://7q5cfr.com1.z0.glb.clouddn.com/@/http/h4.png)

有时候，这个路径指向了一个主机上特定的资源。比如，`www.example.com/home/index.html`指向了 example.com 服务器上的一个 HTML 文件。

另外，URL 可以包含一个主机用来监听 HTTP 请求的端口号。一个`http://localhost:3000/profile`这样的 URL，通过 3000 端口去监听 HTTP 请求。web 客户端用来监听 HTTP 请求的默认端口号是 80，如果一个 URL 中没有指定其他的端口号，那就等价于写了80 **除非指定了其他的端口号代替，不然端口号80会被默认用于正常的 HTTP 请求**。

### 查询字符串 / 参数

一个查询字符串或者参数是 URL 的一部分并且通常都包含一些要发往至服务器的各种类型的数据。一个简单的带查询字符串的 URL 长这样：
    
    http://www.example.com?search=ruby&results=10
    

让我们拆开来看看：

查询字符串组件描述

?
这是个保留字，标识着查询字符串的开始

search=ruby
这是一个参数的键/值对儿

&
这是个保留字，需要给查询字符串添加参数时使用

results=10
这也是一个参数的键/值对儿

现在我们再来看一个例子。假设我们有下面这个 URL:
    
    http://www.phoneshop.com?product=iphone&size=32gb&color=white
    

![](http://7q5cfr.com1.z0.glb.clouddn.com/@/http/h5.png)

在上面这个例子里，键/值对儿`product=iphone`，`size=32gb`，`color=white` 通过 URL 传给了服务器。这个请求告诉`www.phoneshop.com`的服务器，把要请求的资源条件限制在`产品 iphone`，`大小 32gb`和`颜色白色`。服务器怎么样使用这些参数取决于服务端的应用的处理逻辑。

另一个经常见到查询字符串的情况是当你在搜索引擎上搜索东西的时候。**因为查询字符串是通过 URL 传递的，他们仅使用 HTTP 的 GET 请求**。在本书后面的章节里我们会讨论不同的 HTTP 请求，但是现在你所需要知道的是，当你不论什么时候在浏览器的地址栏里输入网址进行浏览的时候，你就是在发起 HTTP 的 GET 请求。大部分超链接都是 HTTP 的 GET 请求，偶尔会有一些例外。

![](http://7q5cfr.com1.z0.glb.clouddn.com/@/http/h6.png)

使用查询字符串向服务器传递附加信息是个很棒的方法，但是对于查询字符串的使用，以下是一些限制：

  * 查询字符串有最大长度。所以，如果你大量的数据需要传输，还是不要用查询字符串的好。
  * 查询字符串中使用的键/值对儿是显示在 URL 上的。所以，不推荐用查询字符串传输敏感信息比如用户名或密码。
  * 查询字符串中无法使用空格和特殊字符比如`&`。它们必须用 URL 编码代替，我们接下来会讨论这个。

### URL 编码 (URL Encoding)

URL 在设计的时候就默认只接受 ASCII 码。因此，不安全的或者不是 ASCII 码的字符就要进行转义或者编码来适应这个格式。URL 编码的原理是将不符合格式的字符替换成`%`开头后面跟着两个十六进制数字代表的 ASCII 码的一串字符。

下面是一些常见的 URL 编码和实例 URL：

字符ASCII 码URL

space
020
[http://www.thedesignshop.com/shops/tommy%020hilfiger.html](http://www.thedesignshop.com/shops/tommy%020hilfiger.html)

!
041
[http://www.thedesignshop.com/moredesigns%041.html](http://www.thedesignshop.com/moredesigns%041.html)

+
053
[http://www.thedesignshop.com/shops/spencer%053.html](http://www.thedesignshop.com/shops/spencer%053.html)

符合下列条件的字符都要进行编码处理：

  1. 没有对应的 ASCII 码。
  2. 字符的使用是不安全的。比如`%`就是不安全的，因为它经常用于对其它字符进行转义。
  3. 字符是有特殊用途的 URL 模式保留字。有些字符用于保留字是有着特殊的意义；它们在 URL 中的存在具有特殊用途。比如`/`，`?`，`:`，和`&`，都是需要进行编码的保留字。

比如`&`被保留用于查询字符串的分隔符。`:`也被保留用于分隔主机/端口号和用户名/密码。

那么什么样的字符能在 URL 里安全地使用呢？只有字母表里的和`$-_.+!'()，"`这些字符可以。如果保留字符被用于它应有的特殊用途，那么是可以不用编码的，不然也是必须要编码的。

### 小结

本章，我们讨论了什么是 URL。也认识了 URL 的组件并以对 URL 编码的探索结尾。在准备工作章节之后，我们会稍微深入一点，一起去看看请求和响应，还有它们的构成。


# 准备工作

对于 HTTP 的基础做了些概览之后，让我们来熟悉一下会在本书中用到，用于展示 HTTP 如何工作的工具。其实，阅读本书的时候，使用什么工具都无所谓，所以挑一个你用着顺手的就好。

### 浏览器插件

Google 的 Chrome 浏览器有几个插件你可以用，比如 [Postman](https://chrome.google.com/webstore/search/Postman?hl=en-US) 和 [REST HTTP API Client](https://chrome.google.com/webstore/detail/dhc-resthttp-api-client/aejoelaoggembcahagimdiliamlcdmfm)。

### HTTP GUI 工具

在本书中我们会经常使用图形化的 HTTP 工具。说到 HTTP 工具这个话题那能说的就太多了，所以长话短说，我们使用 [Paw2](http://luckymarmot.com/paw).虽然这是一个 Mac App Store 里的付费应用，不过它也有免费试用期，够你看这本书的时候用了。

尽管如此，还有很多其他备选方案。简单介绍几个很棒的吧: [HTTP Client](http://ditchnet.org/httpclient/)，[Fiddler](http://www.telerik.com/fiddler) 和 [Cocoa Rest Client](http://ditchnet.org/httpclient/)。

### HTTP 命令行工具

[curl](http://curl.haxx.se/) 是一个免费的命令行工具，经常被用于发送 HTTP 请求。

#### Mac OS X/Linux:

OS X 和大部分的 Linux 发行版应该都预装了 curl，你可以在命令行里非常方便的使用它，类似这样：
    
    $ curl www.usa.gov
    

#### Windows:

> #### 警告
> 
> 以下操作需要对 Windows 些底层工具比较熟悉。 如果你在使用 Windows 并且对以下安装操作感到不适，强烈推荐你使用 GUI 工具，不论是浏览器插件还是安装到你系统上的软件都行。 下面的操作不是必须的，跳过这些你也可以良好的阅读本书。

Windows 用户可以参照以下步骤安装`curl`:

  1. 安装 [Visual C++ 2008 Redistributable Package](http://www.microsoft.com/en-us/download/details.aspx?id=15336)。
  2. 安装 [Visual C++ 2010 Redistributable Package](http://www.microsoft.com/en-us/download/details.aspx?id=14632)。
  3. 接下来安装 [OpenSSL](http://www.shininglightpro.com/products/Win32OpenSSL.html):
    * 32 位系统: Win32 OpenSSL v1.0.1j Light
    * 64 位系统: Win64 OpenSSL v1.0.1j Light
  4. 现在去 curl 的 [主页](http://curl.haxx.se/) 并选择 [下载](http://curl.haxx.se/download.html)。
  5. 在下载页面，找到 Windows 相关的地方，然后点击基于你自己系统的 binary SSL-enabled 版本进行下载:![windows_curl_download](http://book.haoduoshipin.com/tealeaf-http/images/curl_download.png)下载这个文件，然后把`curl.exe`放到一个新的文件夹里。
  6. 从 [这里](http://curl.haxx.se/docs/caextract.html) 安装一个 CA 证书.确保右键另存`cacert.pem`这个链接，并且把文件存成`.pem`格式的:![CA](http://book.haoduoshipin.com/tealeaf-http/images/ca_cert_curl.png)把这个证书拷贝到你刚才放`curl.exe`的文件夹里
  7. 最后打开你的控制台，进入到你放`curl.exe`的文件夹然后跑下面这个命令: `curl -I GET "http://www.reddit.com/" -m 30 -v`

# 准备工作

对于 HTTP 的基础做了些概览之后，让我们来熟悉一下会在本书中用到，用于展示 HTTP 如何工作的工具。其实，阅读本书的时候，使用什么工具都无所谓，所以挑一个你用着顺手的就好。

### 浏览器插件

Google 的 Chrome 浏览器有几个插件你可以用，比如 [Postman](https://chrome.google.com/webstore/search/Postman?hl=en-US) 和 [REST HTTP API Client](https://chrome.google.com/webstore/detail/dhc-resthttp-api-client/aejoelaoggembcahagimdiliamlcdmfm)。

### HTTP GUI 工具

在本书中我们会经常使用图形化的 HTTP 工具。说到 HTTP 工具这个话题那能说的就太多了，所以长话短说，我们使用 [Paw2](http://luckymarmot.com/paw).虽然这是一个 Mac App Store 里的付费应用，不过它也有免费试用期，够你看这本书的时候用了。

尽管如此，还有很多其他备选方案。简单介绍几个很棒的吧: [HTTP Client](http://ditchnet.org/httpclient/)，[Fiddler](http://www.telerik.com/fiddler) 和 [Cocoa Rest Client](http://ditchnet.org/httpclient/)。

### HTTP 命令行工具

[curl](http://curl.haxx.se/) 是一个免费的命令行工具，经常被用于发送 HTTP 请求。

#### Mac OS X/Linux:

OS X 和大部分的 Linux 发行版应该都预装了 curl，你可以在命令行里非常方便的使用它，类似这样：
    
    $ curl www.usa.gov
    

#### Windows:

> #### 警告
> 
> 以下操作需要对 Windows 些底层工具比较熟悉。 如果你在使用 Windows 并且对以下安装操作感到不适，强烈推荐你使用 GUI 工具，不论是浏览器插件还是安装到你系统上的软件都行。 下面的操作不是必须的，跳过这些你也可以良好的阅读本书。

Windows 用户可以参照以下步骤安装`curl`:

  1. 安装 [Visual C++ 2008 Redistributable Package](http://www.microsoft.com/en-us/download/details.aspx?id=15336)。
  2. 安装 [Visual C++ 2010 Redistributable Package](http://www.microsoft.com/en-us/download/details.aspx?id=14632)。
  3. 接下来安装 [OpenSSL](http://www.shininglightpro.com/products/Win32OpenSSL.html):
    * 32 位系统: Win32 OpenSSL v1.0.1j Light
    * 64 位系统: Win64 OpenSSL v1.0.1j Light
  4. 现在去 curl 的 [主页](http://curl.haxx.se/) 并选择 [下载](http://curl.haxx.se/download.html)。
  5. 在下载页面，找到 Windows 相关的地方，然后点击基于你自己系统的 binary SSL-enabled 版本进行下载:![windows_curl_download](http://book.haoduoshipin.com/tealeaf-http/images/curl_download.png)下载这个文件，然后把`curl.exe`放到一个新的文件夹里。
  6. 从 [这里](http://curl.haxx.se/docs/caextract.html) 安装一个 CA 证书.确保右键另存`cacert.pem`这个链接，并且把文件存成`.pem`格式的:![CA](http://book.haoduoshipin.com/tealeaf-http/images/ca_cert_curl.png)把这个证书拷贝到你刚才放`curl.exe`的文件夹里
  7. 最后打开你的控制台，进入到你放`curl.exe`的文件夹然后跑下面这个命令: `curl -I GET "http://www.reddit.com/" -m 30 -v`

http://7q5cfr.com1.z0.glb.clouddn.com/@/http/h9.png

可以的话，书中会展示用`curl`发起请求的命令，以帮助使用`curl`的读者。


可以的话，书中会展示用`curl`发起请求的命令，以帮助使用`curl`的读者。

