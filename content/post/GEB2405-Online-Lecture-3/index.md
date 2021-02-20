---
title: "GEB2405 Online Lecture 3 - Clean the data before analysis"
date: 2021-02-20T12:09:09+08:00
categories:
    - GEB2405
tags:
    - R
---


Problems: 

* var in wrong format, e.g. numeric, char, factor (transform data type)
* not properly coded `NA`, e.g. Non answer is coded as "-1" or "a." instead of `NA` 
* levels are not correctly **ordered**, e.g. income levels not organized in a progressive order
* some levels need to be **merged**. e.g. only 0.2% of respondents are in a given income category



The levels are not correctly **ordered**. e.g. income levels are not organized in a progressive order, we want

```
lowest
middle
highest
```

but the data are organized 

```
middle
highest
lowest
```



packages used: `psych`, `Hmisc`, `dplyr`

---

## var in the wrong format

```R
load("C:/Users/86188/Desktop/GEB2405/Week3/online3/Golf_trainer_short.RData") # load .RData file
str(CGA_golf_train_short)
```

```R
library("dplyr")

modified_obj <- as.factor(original_obj)
modified_obj <- as.numeric(original_obj)
modified_obj <- as.character(original_obj)
```

```R
# example
CGA_golf_train_short$operation_worker <- as.factor( CGA_golf_train_short$operation_worker )

# do not modify the original var!!
CGA$year_birth_factor <- as.factor(CGA$Year_birth)

# see an example in the video 17:45 about transform factor to numeric!!
```



## Code the non answer properly

```R
library("dplyr")

# the var we want to modify is numerical
modified object <- na_if(original object, specific value to be replaced)

CGA$Year_birth <- na_if(CGA$Year_birth, -1)

# the var we want to modify is a factor (or categorical)
modified object <- na_if(original object, "specific value to be replaced")

# see an example of `droplevels`, `table`, `na_if`
# in the video 24:53
# note that we need `droplevels` only when we are dealing with factor var!!
object <- droplevels(object)
```



## Reordering levels of a factor var

(Note that we can use `levels` and `table` to see the info of factor var, example in video 26:23)

```R
new object <- factor(old object, levels=c("first level","second level","nth level"))

CGA$diploma2 <- factor(CGA$diploma, levels=c("PhD","Master","Bachelor","high-school and below"))
```



## Recode a var (merge levels of a factor var)

```R
library("dplyr")

new object <- recode(old object, "level1 to recode"="new level")

# example 1
CGA$trainer_exp_5cat <- recode(CGA$trainer_exp_5cat, "21 years or more"="11 years or more", "11 to 20 years"="11 years or more")

# example 2
CGA_golf_train_short$earning_3cat<-CGA_golf_train_short$annual_earning
CGA_golf_train_short$earning_3cat<-recode(CGA_golf_train_short$earning_3cat, "20 000 to 30 000"="20 000 or more","30 000 to 50 000"="20 000 or more","up to 50 000"="20 000 or more")
table(CGA_golf_train_short$earning_3cat)
CGA_golf_train_short$earning_3cat<-factor(CGA_golf_train_short$earning_3cat, levels=c("Less than 10 000","10 000 to 20 000","20 000 or more"))
```

---

## Tutorial 3

Import excel/Stata file to R environment:

File > import data set > from excel

---

```R
#Exercise 3 Question 5
#many step are necessary for this question
#Step 1 creat the variabale year of birth (date of the survey - age of respondent at the time of the survey)
gfk_cleaned_eul$year_birth<-2014-gfk_cleaned_eul$age
#step 2 create a new categorical variable
gfk_cleaned_eul$year_birth_cat<-gfk_cleaned_eul$year_birth
#recode the categories using the cut function
#run describe to know the min and max value
describe(gfk_cleaned_eul$year_birth_cat)
# for the cut function cut(object, breaks=c(min, val1, val2,valn, max))
gfk_cleaned_eul$year_birth_cat<-cut(gfk_cleaned_eul$year_birth_cat,breaks = c(1929,1945,1964,1984,1996,1997))
table(gfk_cleaned_eul$year_birth_cat)
gfk_cleaned_eul$year_birth_cat<-recode(gfk_cleaned_eul$year_birth_cat,"(1929,1945]"="Born before 1945","(1945,1964]"="Boomers","(1964,1984]"="GenerationX","(1984,1996]"="Millenium","(1996,1997]"="GenerationZ")
table(gfk_cleaned_eul$year_birth_cat)
```

