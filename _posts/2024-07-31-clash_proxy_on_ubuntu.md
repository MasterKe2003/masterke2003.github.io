---
title: 在Ubuntu上使用clash
date: 2024-07-31 23:59:12 +0800
tags: [linux,clash,网络]
---

在这之前我一般都是启动一个服务，然后监听7890端口，局域网内的PC设置一下http代理即可使用，但是最近总发现设置代理之后国内的一些网站打开都变慢了，一点受不了，就找到了一些其他的解决方案。

> [tpclash](https://github.com/TPClash/tpclash)

项目地址：https://github.com/TPClash/tpclash

项目介绍：TPClash(Transparent proxy tool for Clash)，是一个用于 Clash 的透明代理辅助工具, 由于众所周知的原因~~手笨~~而创建的。

> [clash-for-linux](https://github.com/wnlen/clash-for-linux)

项目地址：https://github.com/wnlen/clash-for-linux

项目介绍：此项目是通过使用开源项目[clash](https://github.com/Dreamacro/clash)作为核心程序，再结合脚本实现简单的代理功能。

主要是为了解决我们在服务器上下载GitHub等一些国外资源速度慢的问题。