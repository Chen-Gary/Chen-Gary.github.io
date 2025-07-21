---
title: "Nginx Crash Course"
subtitle: "Nginx 基础教程"
summary: Nginx 基础教程
authors:
- admin
tags:
- Web
categories:
- 
date: 2023-08-20T11:07:31+08:00
featured: false
draft: false

image:
  placement: 2
  caption: ""
  focal_point: ""
  preview_only: false

projects: []
toc: true
---



安装

* Linux

  ```
  sudo apt install nginx
  ```

* Windows: 官网下载压缩包，直接解压即可 http://nginx.org/en/download.html



服务启停

* Windows: 双击 `nginx.exe` 打开即可，可在任务管理器查看到 Nginx 的进程

* Linux:

  ```shell
  nginx
  
  ps -ef|grep nginx    # 查看 Nginx 进程
  lsof -i:80           # 查看 80 端口占用
  ```

  ```shell
  nginx -s quit    # 优雅停止
  nginx -s stop    # 立即停止
  nginx -s reload  # 重载配置文件
  nginx -s reopen  # 重新打开日志文件
  ```



```shell
nginx -V    # 查看 Nginx 安装目录/配置文件位置等
nginx -t    # 查看 Nginx 配置文件位置
```

* 配置文件位置: `--conf-path=/etc/nginx/nginx.conf`
* 安装目录: `--prefix=/usr/share/nginx`



```
#gzip  on;
```

```
/etc/nginx/sites-enabled
/etc/nginx/conf.d
/usr/share/nginx
/var/www/
```



References:

* [30分钟Nginx入门教程](https://www.bilibili.com/video/BV1mz4y1n7PQ/)
* [Unity导出WebGL工程，并部署本地web服务器](https://blog.csdn.net/shaobing32/article/details/129089513)
* [Nginx一个server配置多个location](http://www.manongjc.com/detail/60-mcvitakuxlvylyj.html)
