---
title: "Openwrt+Wireguard+udptunnel+DoH旁网关（旁路由）方案记录"
date: 2024-01-25T18:06:41+08:00
draft: false
tags: ["network", "openwrt","wireguard","r2s","小米路由器","旁网关", "DoH", "udptunnel"]
author: ["rikaaa0928"]
categories : ["memo"]
---
# 整体架构

| 家 | 国内 | 国外 |
| --- | --- | --- |
| r2s ( wireguard + udptunnel smartdns) -> ax9000 -> 光猫) | vps ( bind dnscrypt-proxy ）| vps ( caddy wireguard + udptunnel ) |  

整套方案的方针是
1. 减少复杂度，任何情况下不要影响任何不参与其中的设备，因为家里还有其他人用。所以采用旁网关的方式  
2. 尽量采用由可信的第一方直接提供的技术/组件。作者跑路，团队内讧导致使用的版本无人维护，经常出现破坏性变动，作者夹带私货等现象实在是太多了，所以采用wireguard作为vpn方案，其他xray v2ray/v2fly trojan ss ssr之类的通通pass...搞出这么多东西来就足以说明了由多不靠谱  
3. 传输协议方面，伪装>混淆，混淆用的人一多就是死，但换句话说，只要没啥人用可以认为就是安全的...所以个人决定走私人订制混淆方案的路子，低调才是出路  

### VPN方案
家里大部分设备直接通过ax9000上网  
部分设备通过连ax9000的wifi+设置r2s作为网关，所有流量走r2s上面的wireguard  
r2s和国外vps之间的wireguard通过udptunnel互相通信，因为udp被干扰太严重了  

### DNS方案
国外vps上面的caddy代理google dns doh，r2s通过smartdns使用国外vps的doh  
国内vps通过dnscrypt-proxy使用国外vps的doh，通过bind向国内提供未被污染的dns服务（非必要）  
ax9000使用国内vps提供的dns（非必要）  

## 流程记录  
### 设备准备
1. r2s vps买好  
2. r2s刷[官方openwrt](https://wiki.friendlyelec.com/wiki/index.php/NanoPi_R2S/zh#.E4.B8.8B.E8.BD.BD.E5.9B.BA.E4.BB.B6)(后来才知道openwrt官网也有下载，早知道的话我会选择openwrt官网的版本)，23.05的版本换掉了iptable，为了求稳，装的21.02版本  
3. 配置wireguard
