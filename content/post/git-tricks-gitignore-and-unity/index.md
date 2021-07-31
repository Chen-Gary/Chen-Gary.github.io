---
title: "Git Tricks: Set .gitignore for Unity Project & Clear git-ignored files"
subtitle: ""
summary: ".gitignore在Unity工程中的使用 & 清除已被Git追踪但现在处于.gitignore中的文件"
authors:
- admin
tags:
- Unity
- Git
categories:
- Unity
- Git
date: 2021-07-31T23:08:49+08:00
featured: false
draft: false

image:
  placement: 2
  caption: ""
  focal_point: ""
  preview_only: false

projects: []
---



## 1. gitignore在Unity工程中的使用

Unity工程在第一次commit前一定要在工程根目录下放置[正确的`.gitignore`文件](https://github.com/github/gitignore/blob/master/Unity.gitignore)。

如果第一次commit时没有添加`.gitignore`或`.gitignore`放置位置不对，会导致project中许多不必要的中间文件也被版本控制，比如Library文件夹

> **As a user, you should never have to alter the Library folder manually and attempting to do so may affect the functioning of the project in the Unity editor.** However, it is always safe to delete the Library folder (while the project is not open in Unity) as all its data is generated from what is stored in the Assets and ProjectSettings folders. **This also means that the Library folder should not be included in version control .**

(ref: https://stackoverflow.com/questions/59742994/should-i-push-the-unity-library-folder-to-github)

进而导致以下可能的后果：

* 在拉下仓库最新提交后，部分文件无法被unity识别，图标变成空白
* 单纯用unity打开project，即使没有做任何修改，git status也会提示有改动
* Git会记录很多奇怪的修改。比如，git显示我们删掉了一个文件，并原封不动地加了回来。同时，这些奇怪而不必要的修改大多发生在Library文件夹。



## 2. 清除已被Git追踪，但现在处于.gitignore中的文件

How to make Git “forget” about a file that was tracked but is now in .gitignore?

```
git rm -r --cached .
git add .
git commit -am "Remove ignored files"
```

(ref: https://stackoverflow.com/questions/1274057/how-to-make-git-forget-about-a-file-that-was-tracked-but-is-now-in-gitignore)

