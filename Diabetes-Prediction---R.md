---
title: "Diabetes Prediction using R"
output: 
  html_document:
    keep_md: true
---


```r
## Loading required libraries
library(mlbench)
```

```
## Warning: package 'mlbench' was built under R version 4.0.5
```

```r
library(ggplot2)
```

```
## Warning: package 'ggplot2' was built under R version 4.0.5
```

```r
library(dplyr)
```

```
## Warning: package 'dplyr' was built under R version 4.0.5
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
library(GGally)
```

```
## Warning: package 'GGally' was built under R version 4.0.5
```

```
## Registered S3 method overwritten by 'GGally':
##   method from   
##   +.gg   ggplot2
```

```r
library(knitr)
```

```
## Warning: package 'knitr' was built under R version 4.0.5
```

```r
library(e1071)
```

```
## Warning: package 'e1071' was built under R version 4.0.5
```

```r
library(caTools)
```

```
## Warning: package 'caTools' was built under R version 4.0.5
```

```r
library(ROCR)
```

```
## Warning: package 'ROCR' was built under R version 4.0.5
```

```r
library(caret)
```

```
## Warning: package 'caret' was built under R version 4.0.5
```

```
## Loading required package: lattice
```

```r
library(lattice)
library(rpart)
library(rpart.plot)
```

```
## Warning: package 'rpart.plot' was built under R version 4.0.5
```

```r
library(tree)
```

```
## Warning: package 'tree' was built under R version 4.0.5
```

```r
library(heatmaply)
```

```
## Warning: package 'heatmaply' was built under R version 4.0.5
```

```
## Loading required package: plotly
```

```
## Warning: package 'plotly' was built under R version 4.0.5
```

```
## 
## Attaching package: 'plotly'
```

```
## The following object is masked from 'package:ggplot2':
## 
##     last_plot
```

```
## The following object is masked from 'package:stats':
## 
##     filter
```

```
## The following object is masked from 'package:graphics':
## 
##     layout
```

```
## Loading required package: viridis
```

```
## Warning: package 'viridis' was built under R version 4.0.5
```

```
## Loading required package: viridisLite
```

```
## Warning: package 'viridisLite' was built under R version 4.0.5
```

```
## Registered S3 methods overwritten by 'registry':
##   method               from 
##   print.registry_field proxy
##   print.registry_entry proxy
```

```
## 
## ======================
## Welcome to heatmaply version 1.2.1
## 
## Type citation('heatmaply') for how to cite the package.
## Type ?heatmaply for the main documentation.
## 
## The github page is: https://github.com/talgalili/heatmaply/
## Please submit your suggestions and bug-reports at: https://github.com/talgalili/heatmaply/issues
## Or contact: <tal.galili@gmail.com>
## ======================
```

```r
library(factoextra)
```

```
## Warning: package 'factoextra' was built under R version 4.0.5
```

```
## Welcome! Want to learn more? See two factoextra-related books at https://goo.gl/ve3WBa
```

```r
library(rattle)
```

```
## Warning: package 'rattle' was built under R version 4.0.5
```

```
## Loading required package: tibble
```

```
## Warning: package 'tibble' was built under R version 4.0.5
```

```
## Loading required package: bitops
```

```
## Warning: package 'bitops' was built under R version 4.0.5
```

```
## Rattle: A free graphical interface for data science with R.
## Version 5.4.0 Copyright (c) 2006-2020 Togaware Pty Ltd.
## Type 'rattle()' to shake, rattle, and roll your data.
```

## Importing the dataset


```r
data(PimaIndiansDiabetes)
df = PimaIndiansDiabetes
```


## Changing the column names


```r
colnames(df) = c("Pregnant","Glucose", "Pressure", "Triceps","Insulin", "Mass","Pedigree","Age","Diabetes")
```


```r
summary(df)
```

```
##     Pregnant         Glucose         Pressure         Triceps     
##  Min.   : 0.000   Min.   :  0.0   Min.   :  0.00   Min.   : 0.00  
##  1st Qu.: 1.000   1st Qu.: 99.0   1st Qu.: 62.00   1st Qu.: 0.00  
##  Median : 3.000   Median :117.0   Median : 72.00   Median :23.00  
##  Mean   : 3.845   Mean   :120.9   Mean   : 69.11   Mean   :20.54  
##  3rd Qu.: 6.000   3rd Qu.:140.2   3rd Qu.: 80.00   3rd Qu.:32.00  
##  Max.   :17.000   Max.   :199.0   Max.   :122.00   Max.   :99.00  
##     Insulin           Mass          Pedigree           Age        Diabetes 
##  Min.   :  0.0   Min.   : 0.00   Min.   :0.0780   Min.   :21.00   neg:500  
##  1st Qu.:  0.0   1st Qu.:27.30   1st Qu.:0.2437   1st Qu.:24.00   pos:268  
##  Median : 30.5   Median :32.00   Median :0.3725   Median :29.00            
##  Mean   : 79.8   Mean   :31.99   Mean   :0.4719   Mean   :33.24            
##  3rd Qu.:127.2   3rd Qu.:36.60   3rd Qu.:0.6262   3rd Qu.:41.00            
##  Max.   :846.0   Max.   :67.10   Max.   :2.4200   Max.   :81.00
```



















