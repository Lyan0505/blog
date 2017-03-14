---
title: Mac下安装及配置ProxyChains-NG实现终端下代理
date: 2016-09-10 17:10:11
tags: [mac]
---


ProxyChains-NG
<!--more-->
项目主页:[https://github.com/rofl0r/proxychains-ng](https://github.com/rofl0r/proxychains-ng)  
官方说明:  

> proxychains ng (new generation) - a preloader which hooks calls to sockets in dynamically linked programs and redirects it through one or more socks/http proxies. continuation of the unmaintained proxychains project.  
#### 安装

使用 Homebrew 安装  
`brew install proxychains-ng`  
#### 配置

`vim /usr/local/etc/proxychains.conf`

在 [ProxyList] 下面（也就是末尾）加入代理类型，代理地址和端口例如使用 TOR 代理，注释掉原来的代理并添加  
`socks5 127.0.0.1 9050`(本机使用的端口，自行修改)  

如果所在的网络很复杂，可能需要在配置文件中启用  

dynamic_chain - 按照列表中出现的代理服务器的先后顺序组成一条链，如果有代理服务器失效，则自动将其排除，但至少要有一个是有效的
然后在 [ProxyList] 下添加多个代理  

默认是：  

strict_chain - 按照后面列表中出现的代理服务器的先后顺序组成一条链，要求所有的代理服务器都是有效的  
#### 使用

`proxychains4 curl twitter.com`

配合 wget 和 curl 来下载，非常好用
