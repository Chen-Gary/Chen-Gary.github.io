---
title: "GEB2405 Online Lecture 7"
date: 2021-03-30T11:59:21+08:00
categories:
    - GEB2405
tags:
    - R
---

# Online Lecture 7

* Pie chart

* Faceting (Multiple bars)

```R
# packages used
library(ggplot2)
library(gmodels) # for `CrossTable`
```

## Pie Chart

Preparatory stage:

```R
library(gmodels)

#Make the CrossTable
Crosstable(object,prop.t=TRUE)
#Cross table to know the proportion
CrossTable(smoking_and_drug_use_amongst_English_pupils$CgStat2,prop.t=TRUE)

#create a small dataframe with the key value
count.smokers<-data.frame(smoke=c("NA","never smoked","smoked and then stopped","tried once","occasional smoker","light smoker","regular smoker"),
                          n=c(51,5900,326,779,223,119,191),
                          prop=c(0.007,0.777,0.043,0.103,0.029,0.016,0.025))

> count.smokers # a table will be printed out
```

Visualization stage:

```R
#create a pie char
ggplot(<the_samall_dataframe>,aes(x="",y=??,fill=??))+
  geom_bar(width=1,stat="identity",color="??")+
  coord_polar("y")

#create a pie chart
ggplot(count.smokers,aes(x="",y=prop,fill=smoke))+
  geom_bar(width=1,stat="identity",color="white")+
  coord_polar("y",start=0)

##Add the percentage to the pie chart with geom_text
+geom_text(aes(label=paste0(round(prop*100),"%")),position=position_stack(vjust=0.5)) #`prop` is the variable name
##Remove the theme elements
+theme(panel.background = element_blank(),axis.text = element_blank(),axis.line = element_blank(),axis.ticks = element_blank(),axis.title = element_blank(),plot.title = element_blank())
##add title
+theme(panel.background = element_blank(),axis.text = element_blank(),axis.line = element_blank(),axis.ticks = element_blank(),axis.plot.title = element_blank()) #Remember to remove axis.title = element_blank()!!!
+labs(title="hello_world")
```

```R
# complete example
ggplot(count.occupation,aes(x="",y=prop,fill=Occupation))+
  geom_bar(width=1,stat="identity",color="white")+
  coord_polar("y",start=0)+
  geom_text(aes(label=paste0(round(prop*100),"%")),position=position_stack(vjust=0.5))+
  theme(panel.background = element_blank(),axis.text = element_blank(),axis.line = element_blank(),axis.ticks = element_blank(),axis.title = element_blank())+
  labs(title = "Occupation of CUHK SZ students after graduation")
```



## Multiple Bars Chart / Faceting

(Display information about **three** different variables)

previous bar chart -- two factor var ===> split it according to a third factor var

`+facet_wrap(~third_var)` 

```R
# pay attention to the parameter `fill` and `x`, make sure you understand which is which
# see the graph in video 32:34
ggplot(Student_BMI_2,aes(fill=`place of birth`,x=Dpt))+
  geom_bar(position="dodge")+   # can also be "fill" or "stack"
  facet_wrap(~Gender)

ggplot(Student_BMI_2,aes(fill=Gender,x=BMI))+
  geom_histogram(position="stack", alpha=0.5,binwidth=2)+
  facet_wrap(~Dpt) # not necessarily split bar chart, it can split histogram or geom_density as well
```

---

`subset()` 

```R
subset(Survey$Followed_GEC_fac, Survey$Gender_fac=="Male")
```

```R
Survey_GE_class_choice_1_men<-subset(Survey_GE_class_choice_1,Gender=="Male")
```

