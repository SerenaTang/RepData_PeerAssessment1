---
title: "Reproducible Research: Peer Assessment 1"
output: 
  html_document:
    keep_md: true
---


## Loading and preprocessing the data

```r
setwd("/Users/serenatang/Coursera/RepData_PeerAssessment1")
# Reads data from zip and csv
unzip("activity.zip")
activity <- read.csv("activity.csv")

# Shows what read data looks like
library(xtable)
head.activity <- xtable(head(activity))
print(head.activity, type="html")
```

<!-- html table generated in R 3.4.2 by xtable 1.8-2 package -->
<!-- Mon Jan  1 17:06:21 2018 -->
<table border=1>
<tr> <th>  </th> <th> steps </th> <th> date </th> <th> interval </th>  </tr>
  <tr> <td align="right"> 1 </td> <td align="right">  </td> <td> 2012-10-01 </td> <td align="right">   0 </td> </tr>
  <tr> <td align="right"> 2 </td> <td align="right">  </td> <td> 2012-10-01 </td> <td align="right">   5 </td> </tr>
  <tr> <td align="right"> 3 </td> <td align="right">  </td> <td> 2012-10-01 </td> <td align="right">  10 </td> </tr>
  <tr> <td align="right"> 4 </td> <td align="right">  </td> <td> 2012-10-01 </td> <td align="right">  15 </td> </tr>
  <tr> <td align="right"> 5 </td> <td align="right">  </td> <td> 2012-10-01 </td> <td align="right">  20 </td> </tr>
  <tr> <td align="right"> 6 </td> <td align="right">  </td> <td> 2012-10-01 </td> <td align="right">  25 </td> </tr>
   </table>

  
## What is mean total number of steps taken per day?

```r
# 1a. Calculates the total number of steps taken per day
stepsPerDay <- with(activity, tapply(steps, date, sum, na.rm=TRUE))
head.stepsPerDay <- xtable(as.data.frame(head(stepsPerDay)))
print(head.stepsPerDay, type="html")
```

<!-- html table generated in R 3.4.2 by xtable 1.8-2 package -->
<!-- Mon Jan  1 17:06:21 2018 -->
<table border=1>
<tr> <th>  </th> <th> head(stepsPerDay) </th>  </tr>
  <tr> <td align="right"> 2012-10-01 </td> <td align="right">   0 </td> </tr>
  <tr> <td align="right"> 2012-10-02 </td> <td align="right"> 126 </td> </tr>
  <tr> <td align="right"> 2012-10-03 </td> <td align="right"> 11352 </td> </tr>
  <tr> <td align="right"> 2012-10-04 </td> <td align="right"> 12116 </td> </tr>
  <tr> <td align="right"> 2012-10-05 </td> <td align="right"> 13294 </td> </tr>
  <tr> <td align="right"> 2012-10-06 </td> <td align="right"> 15420 </td> </tr>
   </table>

```r
# 1b. Draws historgram of total number of steps taken each day
hist(stepsPerDay, 
        main = "Distribution of Total Number of Steps Per Day", 
        xlab="Steps Per Day", 
        ylab="Number of Days")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png)<!-- -->

```r
# 2a. Calculates and report the mean total number of 
#     steps taken per day
mean(stepsPerDay)
```

[1] 9354.23

```r
# 2b. Calculates and report the median total number of 
#     steps taken per day
median(stepsPerDay)
```

[1] 10395


## What is the average daily activity pattern?

```r
#Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and #the average number of steps taken, averaged across all days (y-axis)

#Which 5-minute interval, on average across all the days in the dataset, contains #the maximum number of steps?
```
## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
