---
title: "Git Tricks: Filename Too Long Error"
subtitle: ""
summary: "处理Windows平台下Git: Filename too long报错"
authors:
- admin
tags:
- Git
categories:
- Git
date: 2021-07-20T22:05:22+08:00
featured: false
draft: false

image:
  placement: 2
  caption: ""
  focal_point: ""
  preview_only: false

projects: []
---

在使用Git时，如果远程仓库中含有名字很长的文件，或是某个文件在多层文件夹中，间接导致其“文件名”太长：

Windows下，克隆时会出现 `warning: Clone succeeded, but checkout failed.` 报错

阅读克隆/版本退回的报错信息可以看到类似 `error: unable to create file XXXXXXXXXXXXXXXXXXXX: Filename too long`的信息

解决方法：

1. Start Git Bash **as Administrator**
2. Run command `git config --system core.longpaths true`

Another way (only for this clone):
`git clone -c core.longpaths=true <repo-url>`

(ref: https://stackoverflow.com/questions/52699177/how-to-fix-filename-too-long-error-during-git-clone/52699496)
