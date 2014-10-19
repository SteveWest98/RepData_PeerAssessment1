# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

We need to load the data into R, so we pull the data out of the zip file and load it as a csv:

```r
initdata <- read.csv(unz(description = "activity.zip", filename = "activity.csv"))
```

Then we do some processing to calculate the various items we need


```r
library(plyr)
stepsperday <- ddply(initdata, .(date), summarize, steps = sum(steps, na.rm=TRUE))
fivemininterval <- ddply(initdata, .(interval/100), summarize, meansteps = mean(steps, na.rm=TRUE))
```

## What is mean total number of steps taken per day?

1. Make a histogram of the total number of steps taken each day


```r
hist(stepsperday$steps, main="Number of Steps Taken per Day", xlab="Steps per Day")
```

![](./PA1_template_files/figure-html/unnamed-chunk-3-1.png) 

2. Calculate and report the mean and median total number of steps taken per day


```r
mean(stepsperday$steps, na.rm=TRUE)
```

```
## [1] 9354.23
```

```r
median(stepsperday$steps, na.rm=TRUE)
```

```
## [1] 10395
```

## What is the average daily activity pattern?

1. Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)

We assume the package "plyr" has been installed before running this code.


```r
plot(fivemininterval,type="l", xaxt='n', main = "Average Number of Steps Taken Per Hour", xlab = "Hour of Day", ylab = "Number of Steps")
axis(side=1, at=seq(0,24,by=2))
```

![](./PA1_template_files/figure-html/unnamed-chunk-5-1.png) 


2. Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?

```r
fivemininterval[which.max(fivemininterval$meansteps),1]
```

```
## [1] 8.35
```

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
