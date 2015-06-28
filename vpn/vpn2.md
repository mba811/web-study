# shadowvpn

## ShadowVPN

[![Build Status](https://camo.githubusercontent.com/1c31e1bd96fa87894a015b5651962050587bfcbe/68747470733a2f2f7472617669732d63692e6f72672f636c6f7777696e64792f536861646f7756504e2e7376673f6272616e63683d6d6173746572)](https://travis-ci.org/clowwindy/ShadowVPN)

ShadowVPN 是一个基于 libsodium 的高速、安全的 VPN。特别为低端硬件，如 OpenWRT 路由器设计。

更多详情见[这里](https://github.com/clowwindy/ShadowVPN/wiki/Compared-to-Shadowsocks-and-OpenVPN)。

[基本原理简介](https://github.com/clowwindy/ShadowVPN/wiki/ShadowVPN-%E5%8E%9F%E7%90%86%E7%AE%80%E8%A6%81%E8%AF%B4%E6%98%8E)。

目前处在完善阶段，仍有[许多需要做的](https://github.com/clowwindy/ShadowVPN/issues?state=open)。如果你希望使用稳定的版本，可以过段时间再过来看看。

## [](https://github.com/clowwindy/ShadowVPN/wiki/ShadowVPN-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E#%E5%AE%89%E8%A3%85)安装

Linux:

用 git clone 项目，然后编译。 请确保 configure 时使用了 `--sysconfdir=/etc` 参数。
    
    sudo apt-get install build-essential automake libtool
    git clone https://github.com/clowwindy/ShadowVPN.git
    git submodule update --init
    ./autogen.sh
    ./configure --enable-static --sysconfdir=/etc
    make && sudo make install
    

OpenWRT:

[下载预编译版](https://github.com/clowwindy/ShadowVPN/releases)： ar71xx, brcm63xx, brcm47xx, ramips_24kec.

或者自行编译： 进入 [SDK](http://wiki.openwrt.org/doc/howto/obtain.firmware.sdk) 根目录，然后：
    
    pushd package
    git clone https://github.com/clowwindy/ShadowVPN.git
    popd
    make menuconfig # select Network/ShadowVPN
    make V=s
    scp bin/xxx/ShadowVPN-xxx-xxx.ipk root@192.168.1.1
    # then log in your box and use opkg to install that ipk file
    

## [](https://github.com/clowwindy/ShadowVPN/wiki/ShadowVPN-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E#%E9%85%8D%E7%BD%AE)配置

  * 可以在 `/etc/shadowvpn` 目录下找到所有配置文件。
  * 对于客户端，编辑 `client.conf`。
  * 对于服务器端，编辑 `server.conf`。
  * 修改配置文件中的 `server` 和 `password` 字段。
  * `up` 字段指定的脚本会在 VPN 启动后执行。
  * `down` 字段指定的脚本会在 VPN 退出后执行。
  * 如果需要自定义路由，可以修改上面两个脚本。在脚本最后有一段注释， 可以把修改路由的命令放在相应的位置。

需要注意的是 ShadowVPN 是一个点对点 VPN。意味着对于每个客户端，需要一个对应的服务端。 可以开启多个服务端进程，用 `-c` 参数指定不同的配置文件。请确保对于不同的服务端和客户端， 在 `up` 和 `down` 脚本中指定了不同的 IP。

## [](https://github.com/clowwindy/ShadowVPN/wiki/ShadowVPN-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E#%E4%BD%BF%E7%94%A8)使用

服务器：
    
    sudo shadowvpn -c /etc/shadowvpn/server.conf -s start
    sudo shadowvpn -c /etc/shadowvpn/server.conf -s stop
    

客户端：
    
    sudo shadowvpn -c /etc/shadowvpn/client.conf -s start
    sudo shadowvpn -c /etc/shadowvpn/client.conf -s stop
    

客户端（OpenWRT）：
    
    /etc/init.d/shadowvpn start
    /etc/init.d/shadowvpn stop
    

对于 DNS 污染，可以直接使用 Google DNS 8.8.8.8，或者使用 [ChinaDNS](https://github.com/clowwindy/ChinaDNS-C) 综合使用国内外 DNS 得到更好的解析结果。

可选： OpenWRT 用户可以看看 [LuCI Configuration](https://github.com/clowwindy/ShadowVPN/wiki/Configure-Via-LuCI-on-OpenWRT)。

## [](https://github.com/clowwindy/ShadowVPN/wiki/ShadowVPN-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E#wiki)Wiki

所有的文档可以在 wiki 中找到: [https://github.com/clowwindy/ShadowVPN/wiki](https://github.com/clowwindy/ShadowVPN/wiki)

## [](https://github.com/clowwindy/ShadowVPN/wiki/ShadowVPN-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E#license)License

MIT

## [](https://github.com/clowwindy/ShadowVPN/wiki/ShadowVPN-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E#bugs-and-issues)Bugs and Issues

  * [Issue Tracker](https://github.com/clowwindy/ShadowVPN/issues?state=open)
  * [Mailing list](http://groups.google.com/group/shadowsocks)

   [18]: http
----
##A fast, safe VPN based on lib sodium 

[View the Project on GitHub clowwindy/ShadowVPN][1]

   [1]: https://github.com/clowwindy/ShadowVPN

  * [Download **Source**][2]
  * [View **Wiki**][3]
  * [View On **GitHub**][4]

   [2]: https://github.com/clowwindy/ShadowVPN/releases
   [3]: https://github.com/clowwindy/ShadowVPN/wiki
   [4]: https://github.com/clowwindy/ShadowVPN

[![Build Status][5]][6]

   [5]: https://travis-ci.org/clowwindy/ShadowVPN.svg?branch=master
   [6]: https://travis-ci.org/clowwindy/ShadowVPN

[中文说明][7]

   [7]: https://github.com/clowwindy/ShadowVPN/wiki/ShadowVPN-%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E

ShadowVPN is a fast, safe VPN based on libsodium. Designed for low end devices, i.e. OpenWRT routers. 

For more details, [check here][8]. 

   [8]: https://github.com/clowwindy/ShadowVPN/wiki/Compared-to-Shadowsocks-and-OpenVPN

## Install 

#### Debian & Ubuntu 

For Debian 7 and Ubuntu 12+, add the following line to `/etc/apt/sources.list`
    
    deb http://shadowvpn.org/debian wheezy main
    

Then 
    
    apt-get update
    apt-get install shadowvpn
    service shadowvpn restart
    

Or see [Build deb Package][9]. 

   [9]: https://github.com/clowwindy/ShadowVPN/wiki/Building-deb-Package

#### Unix 

Currently Linux, FreeBSD and OS X are supported. Clone the repo and build. Make sure to set `--sysconfdir=/etc`. You'll find conf files under `/etc`. 
    
    # For Debian-based Linux
    sudo apt-get install build-essential automake libtool
    git clone https://github.com/clowwindy/ShadowVPN.git
    git submodule update --init
    ./autogen.sh
    ./configure --enable-static --sysconfdir=/etc
    make && sudo make install
    

#### OpenWRT 

[Download precompiled][10] for OpenWRT trunk and CPU: ar71xx, brcm63xx, brcm47xx, ramips_24kec. 

   [10]: https://github.com/clowwindy/ShadowVPN/releases

Or build yourself: cd into [SDK][11] root, then 
    
       [11]: http://wiki.openwrt.org/doc/howto/obtain.firmware.sdk

pushd package
    git clone https://github.com/clowwindy/ShadowVPN.git
    popd
    make menuconfig # select Network/ShadowVPN
    make V=s
    scp bin/xxx/ShadowVPN-xxx-xxx.ipk root@192.168.1.1
    # then log in your box and use opkg to install that ipk file
    

#### Windows 

You need to install the TUN/TAP driver first: 

  * [For 32-bit Windows][12]
  * [For 64-bit Windows][13]

   [12]: http://build.openvpn.net/downloads/releases/tap-windows-9.9.2_3.exe
   [13]: http://build.openvpn.net/downloads/releases/tap-windows-9.21.0.exe

Currently only MinGW compilers are supported. You can compile in Msys or cross-compile in Linux or Cygwin with 32-bit or 64-bit MinGW toolchains. 

For example, if using 64-bit Cygwin, install `libtool`, `autoconf`, `git` and `mingw64-x86_64-gcc-g++` by Cygwin installer. Then build from Cygwin terminal by the following commands: 
    
    git clone --recursive https://github.com/clowwindy/ShadowVPN.git
    cd ShadowVPN
    ./autogen.sh
    ./configure --enable-static --host=x86_64-w64-mingw32
    make && make install DESTDIR="$HOME/shadowvpn-build"
    

Executables will be generated in `$HOME/shadowvpn-build`. 

## Configuration 

  * You can find all the conf files under `/etc/shadowvpn`.
  * For the client, edit `client.conf`.
  * For the server, edit `server.conf`.
  * Update `server` and `password` in those files.
  * The script file specified by `up` will be executed after VPN is up.
  * The script file specified by `down` will be executed after VPN is down.
  * If you need to specify routing rules, modify those scripts. You'll see a placeholder at the end of those scripts.
  * If you are using Windows, the IP address of TUN/TAP device `tunip` is required to be specified in the conf file.

Notice ShadowVPN is a peer-to-peer VPN, which means you'll have one server for one client. If you have multiple clients, you should start multiple server instances, which can be controlled by different configuration files via `-c` argument. Make sure to use different IP for each instance in each `up` and `down` scripts. 

## Usage 

Server: 
    
    sudo shadowvpn -c /etc/shadowvpn/server.conf -s start
    sudo shadowvpn -c /etc/shadowvpn/server.conf -s stop
    

If you installed using apt-get, you can use `sudo service shadowvpn start` instead. 

Client: 
    
    sudo shadowvpn -c /etc/shadowvpn/client.conf -s start
    sudo shadowvpn -c /etc/shadowvpn/client.conf -s stop
    

Client(OpenWRT): 
    
    /etc/init.d/shadowvpn start
    /etc/init.d/shadowvpn stop
    

You can also read [LuCI Configuration][14]. 

   [14]: https://github.com/clowwindy/ShadowVPN/wiki/Configure-Via-LuCI-on-OpenWRT

## Wiki 

You can find all the documentation in the wiki: [https://github.com/clowwindy/ShadowVPN/wiki][15]

   [15]: https://github.com/clowwindy/ShadowVPN/wiki