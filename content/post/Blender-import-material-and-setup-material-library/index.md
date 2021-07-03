---
title: "Blender Import Material and Setup Material Library"
subtitle: ""
summary: Blender导入material，并建立material library
authors:
- admin
tags:
- Blender
categories:
- Blender
date: 2021-02-18T20:57:29+08:00
featured: false
draft: false

image:
  placement: 2
  caption: ""
  focal_point: ""
  preview_only: false

projects: []
---


## 使用material library的原因

多人合作时，方便颜色统一（尤其针对统一玻璃之类的复杂材质）

## 如何导入material

1. 打开想要导入material的 blender file
2. 导航栏选择 File > Append
3. 找到`material_template_lib.blend`，并双击进入
4. 进入`Material`文件夹，并双击选择想导入的material

![gif](https://camo.githubusercontent.com/548ea9bd6677b3840b98c2b3ef078787dfec0306e47559ad475b4419735de6bc/68747470733a2f2f692e737461636b2e696d6775722e636f6d2f6141584f772e676966)

![pic](img_1.png)

这样在Material selector中应该就能找到刚刚导入的material

（注意**重命名**导入的material）

（ref https://blender.stackexchange.com/questions/63018/how-to-import-downloaded-materials-files/63055）

## *合作方式

比如我负责选定玻璃的材质，那么我就

* 下载最新的`material_template_lib.blend`
* 新建一个cube，后新建并附上调好的玻璃材质
* commit回GitHub，更新`material_template_lib.blend`
