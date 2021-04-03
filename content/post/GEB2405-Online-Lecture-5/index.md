---
title: "GEB2405 Online Lecture 5 - ggplot2 I (One Variable)"
date: 2021-03-12T12:13:27+08:00
categories:
    - GEB2405
tags:
    - R
---

# On-line Lecture 5 - Data visualization - Graphing a continuous or discrete variable

 Package used

```R
library(ggplot2)
```

Table of contents:

(Graph for one variable)

* For **continuous/numeric** variables, creating, editing, coloring **histogram**
* For **discrete/categorical/factor** variables, creating, editing, coloring **bar plot**



## Basic `ggplot2` grammar

![](img_1.png)

```R
ggplot(data, aes(x,y,options)) + geom_typegraph(option)

# add labels
ggplot(data, aes(x,y,options)) + geom_typegraph(option) + labs(x=..., y=..., title=...)
```

```R
# examples (very ugly)
ggplot(mtcars,aes(x=mpg)) + geom_histogram() # mtcars$mpg
ggplot(mtcars,aes(x=cyl)) + geom_histogram() # mtcars$cyl

ggplot(mtcars,aes(x=mpg)) + geom_dotplot()
```



## Graphing ==an== unique continuous data (==histogram==)

* `binwidth=nbr`: change the bar width
* `fill="name_of_color"`: change the color with which the bar is filled
* `colour="name_of_color"`: change the outline of the bar
* `alpha=nbr`: change the transparency of the color

```R
ggplot(mtcars,aes(x=mpg))+geom_histogram(fill="skyblue",
                                         alpha=0.7,
                                         binwidth=5,
                                         colour="grey"
                                         )
```

```R
# modifying the aesthetic part using fill=Gender to have different colors
# see graph in 27:14
ggplot(SEE_students_data_2,aes(x=BMI,fill=Gender))+geom_density(colour="black",alpha=0.5)

ggplot(SEE_students_data_2,aes(x=BMI, fill=Gender))+
	geom_area(stat="bin", colour="black",alpha=0.5,binwidth=1)
```

```R
# add a title and change axis names
ggplot(SEE_students_data_2,aes(x=BMI, fill=Gender))+
  geom_density(colour="black",alpha=0.5)+
  labs(title="Body Mass index per Gender\nSEE Students", y="Frequency",x="Body Mass Index")
```



## Graphing ==univariate== categorical/factor data

```R
ggplot(SEE_students_data_2,aes(x=Gender))+geom_bar()

#adding color to the bar using a set, a given color, manually defined colors
# example 1
ggplot(SEE_students_data_2,aes(x=Gender, fill=Gender))+
  geom_bar(alpha=0.5)+
  scale_fill_brewer(palette="Set1") # predefined color set

# example 2
ggplot(SEE_students_data_2,aes(x=Gender, fill=Gender))+
  geom_bar()+
  scale_fill_brewer(palette = "Blues") # predefined color set

# example 3
ggplot(SEE_students_data_2,aes(x=Gender,fill=Gender))+
  geom_bar(alpha=0.75)+
  scale_fill_manual(values=c("pink","blue")) # manually defined color set
```



### Organize the bar in the right order

```R
library(forcats)
```

Two useful options in `forcats`:

* `fct_infreq(x)`:  to arrange the results depending on the frequency
* `fct_reorder(x)`: to arrange the results according to another variable

```R
ggplot(CUHKSZ_employment_survey_1, aes(x=fct_infreq(Occupation), fill=Occupation))+
  geom_bar(alpha=0.75)+
  scale_fill_brewer(palette="Blues")

# OR simply
ggplot(CUHKSZ_employment_survey_1, aes(fct_infreq(Occupation), fill=Occupation))+
  geom_bar(alpha=0.75)+
  scale_fill_brewer(palette="Blues")
```

