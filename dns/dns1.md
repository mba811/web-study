# EnableDNS免费开源的DNS服务器搭建方法:Django,bind9安装与配置

![](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_00.gif)

DNS服务主要的功能是将域名转换为相应的IP地址，提供DNS服务的系统就是DNS服务器，DNS服务器可以分为3种，主域名服务器（Master DNS）、辅助域名服务器（Slave DNS）和高速缓存服务器（Cache-only server）。

想要自己搭建一个DNS服务器，一般要用bind软件来搭建。虽然说bind9在Linux中安装挺方便的，但是配置起来却是非常地麻烦，不容易成功。本篇文章就来分享一下EnableDNS这个开源的DNS服务器系统，它的方便之处在于一键安装。

EnableDNS本身是一个提供DNS域名解析服务的服务商，[EnableDNS](http://www.freehao123.com/tag/enabledns/)是他们在github上发布的开源项目，采用Django、MysqL和[bind9](http://www.freehao123.com/tag/bind9/)，你可以自己手动一步一步搭建和配置好EnableDNS，也可以使用一键安装的方法快速搭建好EnableDNS服务器。

如果你很讨厌那些限制过多又不稳定的第三方的邮局、相册、博客等服务，不防尝试着自己手动搭建一个，爱怎么用就怎么用：

  * 1、搭建邮局：[Postfix邮件系统安装与配置:Postfix,Cyrus-IMAP,Cyrus-sasl,Dovecot和SPF](http://www.freehao123.com/postfix-cyrus/)
  * 2、图片相册系统：[免费开源相册系统Piwigo安装使用评测:打造个人专属网络相册](http://www.freehao123.com/piwigo/)
  * 3、个人博客：[Ghost博客安装与使用教程-Node.js,Nginx,MySQL,Ghost搭建与配置](http://www.freehao123.com/ghost-node-js/)

**EnableDNS免费开源的DNS服务器搭建方法:Django,bind9安装与配置**

**一、EnableDNS免费DNS服务**

1、EnableDNS官网：

  * 1、官方网站：https://enabledns.com/

2、EnableDNS本身也提供DNS域名解析服务，页面简洁，最多可以添加五个域名，还有丰富的API可供使用。（点击放大）

[![EnableDNS管理面板](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_20-500x240.jpg)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_20.jpg)

3、这是EnableDNS的DNS解析记录设置页面，支持A、CNAME、MX、AAAA、TXT等记录。（点击放大）

[![EnableDNS添加解析记录](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_21-500x240.jpg)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_21.jpg)

**二、EnableDNS开源的DNS服务器安装**

1、EnableDNS项目：

  * 1、项目首页：https://github.com/ROHOST/enableDNS

2、EnableDNS已经提供了手动安装的方法了，显麻烦的话，可以直接使用EnableDNS的一键安装。执行以下命令：

    wget https://github.com/ROHOST/enableDNS/blob/master/autoinstall-edns.sh
    chmod 777 ./autoinstall-edns.sh 
    ./autoinstall-edns.sh
    

3、用Wget下载autoinstall-edns.sh的方法可能会失败，请直接手动将官网的autoinstall-edns.sh下载到本地，然后再上传到服务器上。

4、安装的过程中首先会要求你提供一个EnableDNS的密码。

[![EnableDNS提供密码](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_01.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_01.gif)

5、选择程序安装的路径。

[![EnableDNS安装路径](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_02.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_02.gif)

6、接着要求为EnableDNS的MysqL数据库设置好密码。

[![EnableDNS设置MysqL密码](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_03.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_03.gif)

7、之后，还会要求你提供一次数据库密码，就是之前设置好的。

[![EnableDNS安装密码](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_04.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_04.gif)

8、最后还要为Django设置好账号和密码等。

[![EnableDNS设置好账号](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_05.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_05.gif)

9、这是EnableDNS安装成功的提示。

[![EnableDNS安装成功](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_06.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_06.gif)

**三、EnableDNS开源DNS服务器使用**

1、进入http://XXXX:8080/admin是管理员界面，而http://xxxx:8080/api/v1.0/api-auth/login/是API信息。

[![EnableDNS查看API信息](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_07.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_07.gif)

2、使用你在安装的过程中设置的密码登录到EnableDNS Django系统中。

[![EnableDNS登录到系统中](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_09.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_09.gif)

3、这是EnableDNS Django的DNS系统页面，主要有用户、DNSZone等等。

[![EnableDNS操作界面](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_10.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_10.gif)

4、为EnableDNS [Django](http://www.freehao123.com/tag/django/)添加用户组时，可以设置好用户组权限。

[![EnableDNS设置用户组权限](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_11.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_11.gif)

5、然后可以为EnableDNS Django添加新用户。

[![EnableDNS添加新的用户](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_12.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_12.gif)

6、也可以单独为用户组设置权限。

[![EnableDNS单独设置权限](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_13.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_13.gif)

7、EnableDNS Django添加域名DNS前，需要先添加域名。

[![EnableDNS添加域名](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_14.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_14.gif)

8、在User Profiles设置好域名拥有者和解析数等。

[![EnableDNS设置解析数](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_15.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_15.gif)

9、在DNS Zone中设置好名称。

[![EnableDNS设置zone名称](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_16.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_16.gif)

10、在Zone Meta中设置好记录数。

[![EnableDNS调整解析记录数](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_17.gif)](http://img.freehao123.com/wp-content/uploads/2014/08/enableDNS_17.gif)

**四、EnableDNS安装与使用小结**

1、EnableDNS提供的免费DNS服务操作简单方便，官网界面也很清爽，如果有需要找国外的免费DNS服务的话，除之前分享的[十大免费DNS域名解析服务](http://www.freehao123.com/ten-dns/)，还可以试试EnableDNS DNS服务。

2、EnableDNS免费开源DNS服务器系统安装时要注意相关的组件是否已经成功安装完成，否则会出现错误提示。另外EnableDNS不是一个完整的DNS服务平台，你需要搭配其它的DNS服务综合使用。
