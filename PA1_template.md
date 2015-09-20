---
title: "PA1_template"
author: "Ryan Brown"
date: "Sunday, September 20, 2015"
output: html_document
---


## Loading and preprocessing the data

1.First, load the file:


```r
data <- read.csv("activity.csv", stringsAsFactors=FALSE)
```


## What is mean total number of steps taken per day?

1.Calculate total number of steps taken per day:


```r
stepsByDay  <- aggregate(data$steps, by=list(data$date), FUN=sum, na.rm=TRUE)
names(stepsByDay)  <- c("date", "steps")
```
2.Plot histogram of steps per day:


```r
library(ggplot2)
ggplot(stepsByDay, aes(x=date,y=steps))+geom_bar(stat="identity")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3-1.png) 

3. Find mean and median of the total number of steps taken per day


```r
mean  <- mean(stepsByDay$steps, na.rm=TRUE)
median  <- median(stepsByDay$steps, na.rm=TRUE)

mean
```

```
## [1] 9354.23
```

```r
median
```

```
## [1] 10395
```
