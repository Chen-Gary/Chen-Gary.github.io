---
title: "GEB2405 Online Lecture 1"
description: "Page description"
date: 2021-02-09T16:09:54+08:00
categories:
    - GEB2405
tags:
    - R
---

## On-line Lecture 1

```R
data(mtcars)	# data(name of the dataset)

head(mtcars)

View(mtcars)    # capital V
```



Summarize

```R
summary(data frame name$variable name)
summary(mtcars$cyl)

# summary of all the variable
summary(data frame name)
summary(mtcars)
```



Standard Deviation

```R
sd(object)
sd(mtcars$cyl)
```



Display all the information for a given object

```R
> object
> mtcars$cyl
```



```R
install.packages("forcats")		# install the package

library("forcats")				# load the package installed
```



Deal with NA (Non-answer)

```R
mean(mtcars$cyl, na.rm=TRUE)	# remove NA when encountering it
sd(gss_cat$tvhours, na.rm = TRUE)
```



Using "Plots" menu in R studio

```
demo("graphics")
```



About working directory

```R
getwd() 	# get the working directory
```

---



## Tutorial 1

Create a vector

* numerical

  ```R
  Name of the vector/variable <- c (component1, component2, component3) 
  
  ID<-c(1,2,3,4,5,6,7,8,9,10)
  ```

* categorical

  ```R
  Name of the vector/variable <- c (“component1”, “component2”, “component3”) 
  ```

  (quotation mark)

  

remove an object

```R
rm (vector name)
```



Arithmetic transformation (tut1_ppt_page_5)

e.g. Create a new vector from two existing vectors 

```R
# `weight`, `height` are vectors
BMI<-c(weight/(height*height))
```

---

Clear the Console: `Ctrl` + `L`



---

Some required packages

* tidyverse
* dplyr
* Hmisc
* psych
* forcats