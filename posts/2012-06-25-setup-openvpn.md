---
layout: post
title: 配置OpenVPN
date: 2012-06-25 14:30:35
category: linux
tags: 
---

最近更换了Bust.net的vps, 选了最便宜的VPS PACKAGE #1($5.95/mo), 这个vps是OpenVZ实现的, 目前BurstNET的VPS还不支持搭建PPTP VPN, 所以
只能安装openvpn.

安装过程就不详细介绍了, google一下一大把, 需要注意的是在启用openvpn前需要在vps管理页面打开tap/tun支持, 或者直接联系客服帮你开启tap/tun
支持.

在服务器上生成客户端证书后将ca.crt xxxx.crt xxxx.key下载到客户机. 在ubuntu 10.04客户机上直接安装openvpn, 修改下客户端配置即可连接到服务器了.

开启vpn后客户端所有网络流量默认将走vpn, 导致访问国内的服务器很慢, 解决方案是:

    1. 在服务器端推送路由
    2. 在客户端建立vpn连接后加入自定义路由表

具体的做法可以google下, 网上很多这样的文章.


