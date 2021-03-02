---
title: "GEB2405 Online Lecture 4 - Merge data collected by different interviewers"
date: 2021-03-02T14:11:04+08:00
categories:
    - GEB2405
tags:
    - R
---


* how to merge answer collected by different coders **(merge rows)**
* how to add new variables in a dataset by matching the ID **(add/merge columns)**
* how to manually add observation (one single respondent) in an existing dataframe **(add a row)**

## 1. merge

Before import the excel data files, make sure the name of the variables are exactly the same in all data files, e.g. one var named `Rank` in file A, while the corresponding var in file B is named `Ranking`.

```R
# solution 1

# create new var
Survey_GE_class_choice_2$Rank <- Survey_GE_class_choice_2$Ranking
# delete the improperly named variable
Survey_GE_class_choice_2 <- Survey_GE_class_choice_2 [,-7]
# bind the two dataset
cuhksz_GE_choice <- rbind(Survey_GE_class_choice_1, Survey_GE_class_choice_2)
```



`rbind`:

the two dataframe should have the same variables, but they do not have to be in the same order

-----> if it is not the case:

* delete the extra var in one dataframe

* add the extra var in another dataframe with `NA` 

  ```R
  df$new_var <- NA
  ```

  

```R
name_of_the_new_dataframe <- rbind(dataframeA, dataframeB)

cuhksz_student_health<-rbind(SSE_students_data,SME_students_data)
```



## 2. add new variables (add/merge a column)

Before merging we need to make sure we can find a way to match the information correctly.

In `CUHKSZ_employment_survey-1.xls` and `CUHKSZ_employment_survey-1b.xls`, the `ID` is unique to each respondent and correspond in the two dataframe.



```R
name_of_the_new_dataframe <- merge(dataframeA, dataframeB, by="variable to identify respondent")

CUHK_employement_1<-merge(CUHKSZ_employment_survey_1,CUHKSZ_employment_survey_1b, by="ID")
```



## 3. add observation (one single respondent) in an existing dataframe (add a row)

```R
fix(dataframe_name)
```

click + arrow

double click ----> access already input data

---



# Tutorial 4

Exercise3 Q3: Create a new variable displaying how many kinds of coffee each student drink during the week

```R
# Arithmetic transformation in Tutorial 1!!!
test$total <- test$Cappuccin + test$CafeLatte + test$Americano + test$Expresso
```



Exercise3 Q4: Create a new variable indicating the different combination of coffee drunk by the students (ex: Americano only, Americano and Capuccino….etc) 

```R
df$newFactor <- with(df, interaction(df$factorA, df$factorB, df$factorC))
```

