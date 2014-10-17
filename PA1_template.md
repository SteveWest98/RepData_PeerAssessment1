# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

We need to load the data into R, so we pull the data out of the zip file and load it as a csv:

```r
initdata <- read.csv(unz(description = "activity.zip", filename = "activity.csv"))
```

Then we do some processing/transforming to get it in the format we need


## What is mean total number of steps taken per day?

1. Make a histogram of the total number of steps taken each day


```r
hist(initdata$steps,main="Histogram of Number of Steps Taken per Day",xlab="Steps per Day")
```

![](./PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

2. Calculate and report the mean and median total number of steps taken per day


```r
mean(initdata$steps,na.rm=TRUE)
```

```
## [1] 37.3826
```

```r
median(initdata$steps,na.rm=TRUE)
```

```
## [1] 0
```

## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
