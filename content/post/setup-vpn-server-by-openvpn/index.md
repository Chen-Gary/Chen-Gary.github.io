---
title: "Setup VPN Server by OpenVPN"
subtitle: ""
summary: 部署VPN服务器
authors:
- admin
tags:
- VPN
categories:
date: 2021-08-12T16:35:50+08:00
featured: false
draft: true

image:
  placement: 2
  caption: ""
  focal_point: ""
  preview_only: false

projects: []
---

## 摘要

基于阿里云服务器搭建OpenVPN Server，并通过client程序连接VPN。



## 环境 & 前置条件

我使用的服务器为：**阿里云 - 轻量应用服务器**，安装了系统镜像**Ubuntu 20.04**。我之前还在这台服务器上通过宝塔面板部署了个人博客（网站），但这并不影响VPN Server的搭建。



## 搭建过程

### 1. 在服务器上“一键”部署OpenVPN 

进入阿里云服务器控制台，选择“远程连接”打开服务器命令行。根据命令行上端的提示，输入`sudo su root`，切换至root账号。

借助[GitHub上别人写好的部署脚本](https://github.com/angristan/openvpn-install)，根据README中的指引，通过命令行下载并运行“一键部署”脚本`openvpn-install.sh`。

第一次运行`openvpn-install.sh`时，你会看到一些有关设置的问题。如果没有特殊需求，阅读后，一路`Enter`使用脚本预设的默认选项即可。当一切部署结束后，你会被要求添加一个client，按指示添加即可。脚本会提示你：`<client_name>.ovpn`被创建在当前目录下，这个文件是用来让client链接至VPN Server的，将它从服务器下载下来（由于`.ovpn`是纯文本，最简单的做法可能是`cat <client_name>.ovpn`，直接复制并保存到电脑）



再次运行`openvpn-install.sh`可以：

* 添加client
* 删除client
* 卸载OpenVPN

### 2. OpenVPN Client

到官网[下载](https://openvpn.net/vpn-client/)对应平台的OpenVPN客户端。（Android在Google Play下载）

打开客户端后，Import Profile中，选择以FILE导入之前的`.ovpn`文件。

理论上，这时已经万事俱备了，但连接VPN却一直显示"Waiting for server"，最终连接timeout。这是因为阿里云服务器出于安全考虑，必须手动打开相应的端口，下一步我们解决这个问题。

### 3. 开放阿里云服务器端口

还是进入阿里云服务器控制台（用于搭建VPN Server的服务器实例页面），进入“安全 > 防火墙”，点击添加规则。如果你在配置VPN Server时保持默认配置，那么按照下方表格添加规则：

| 应用类型 | 协议 | 端口范围 |
| -------- | ---- | -------- |
| 自定义   | UDP  | 1194     |

协议和端口范围都是在运行部署脚本时设置的，由于部署脚本可能更新，强烈建议大家去看[部署脚本](https://github.com/angristan/openvpn-install/blob/master/openvpn-install.sh)里写的默认值，不要直接抄表格。

现在再次尝试连接VPN，一切顺利。

