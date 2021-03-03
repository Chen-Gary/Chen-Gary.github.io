---
title: "如何使用CMake编译"
date: 2021-03-03T15:54:26+08:00
categories:
tags:
    - CMake
    - C++
---

在使用CLion编写C++项目后，IDE会自动生成CMakeLists.txt文件。那么如何手动编译我们写的代码呢？

步骤如下

* 将项目中的所有源文件 + 自动生成的CMakeLists.txt 传入Linux虚拟机（的同一目录下）

* ```shell
  mkdir build
  cd build
  cmake ..		# 用cmake命令将CMakeLists.txt文件转化为make所需要的makefile文件
  make			# 用make命令编译源码生成可执行程序
  ```

* 运行

  ```shell
  ./name_of_executable
  ```



(ref: https://www.cnblogs.com/cv-pr/p/6206921.html)