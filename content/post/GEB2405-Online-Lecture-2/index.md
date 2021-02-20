---
title: "GEB2405 Online Lecture 2"
date: 2021-02-20T12:08:00+08:00
categories:
    - GEB2405
tags:
    - R
---


## On-line Lecture 2

explore some data depositories

* UK Data Service https://www.ukdataservice.ac.uk/ 

  > I have an account for it.

  * GBCS (Great British Class Survey)
  * CCSE (Cultural Capital and Social Exclusion)

* CNSDA 中国国家调查数据库 ~~http://cnsda.edu.cn/index.php~~ / http://cnsda.ruc.edu.cn/

  > I have an account for it.

  * CGSS (China General Social Survey) 中国综合社会调查
  * CRS (The Chinese Religion Survey)

* 北京大学开放研究数据平台 https://opendata.pku.edu.cn/

---

## Tutorial 2

Some definitions:

* **"Levels"** are the **different attributes** that a **==factor/categorical variable==** ==(only for these two types of data)== can have. For example: The variable *gender* has usually two levels, *male* and *female*
* **"Not well ordered variable"** is a variable whose levels **should be rearranged** in increasing order or decreasing order. For example, you have a question: Do you like coffee? The levels are in the following order: Like a lot, dislike a lot, Like, neither, Dislike. This is not very rational and need to be reordered from Dislike a lot to like a lot



```R
library(psych)
describe(USArrests$Murder)		# improved version of summary(USArrests$Murder)
								# with `sd` (standard dev.) included
```

Other commands to see info of data

* `summary`: knowing **basic information** about the distribution of **continuous variable** which are named **numeric** in R. However this command ==does not work for factor and character variable==. Different command are necessary to explore different type of variable
* `str(object)`: When the variable is **numeric**, **integer**, **factor** or **character** the command `str` can be use 
* `describe(object)`: When you have a **numeric** or **integer** the command `describe` can be used
* `levels(object)`: When the variable is **factor**, I can know the possible “label” of the answers using the command `levels(object)`
* `table(object)`: When the variable is **factor**, you can use the command `table` to explore the variable (see example of `table` and `levels` in online lec 3 video 26:23)

---

## Tutorial 2 - Data type

`Data Types and Structures-v2.docx`

### Data types:

* character
* numeric (real or decimal)
* integer
* factor (has a certain number of possible answers ---- see details in the `docx` file)
* ~~logical (TRUE, FALSE)~~ (not covered in this course)
* ~~complex~~ (not covered in this course)

see examples in the `docx` file



### Commands to check the data type:

* class (object)
* str(object) -------- covered in tut2
* mode(object)



### Data structures

During the first tutorial, we create **individual vectors (or variables)**. Those vectors can be combined together into a **data frame**.

(see more details in the `docx` file)

Data structures:

* data frame
* matrix
* list
* ...


