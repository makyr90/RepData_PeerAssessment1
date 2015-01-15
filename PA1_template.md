<title> 1st Peer Assignement </title>
<font color="blue">Reproducible Reacearh Peer assesment 1 </font>
=================================================================

<br>

**Load Activity Monitoring dataset**  


```r
mydata <- read.csv("activity.csv",header = TRUE)
```
**Total number of steps taken each day**  


```r
stepsperDay<-tapply(mydata$steps,mydata$date,sum,na.rm=TRUE)
stepsperDaydf<-data.frame(Date=names(stepsperDay),Total.Steps=stepsperDay)
ExclNA_stepsperDaydf<-stepsperDaydf[which(stepsperDaydf$Total.Steps>0),]
par(mar=c(0,5,1,2))
par(las=2)
x<-barplot(ExclNA_stepsperDaydf$Total.Steps,horiz=TRUE,names.arg=ExclNA_stepsperDaydf$Date,cex.names=0.7,
main ="Total Steps per Day",col="red", xaxt="n",)
text(x= ExclNA_stepsperDaydf$Total.Steps+750, y= x, labels=as.character(ExclNA_stepsperDaydf$Total.Steps),
cex=0.7,xpd=TRUE)
```

<img src="figure/plot histogram-1.png" title="plot of chunk plot histogram" alt="plot of chunk plot histogram" style="display: block; margin: auto;" />
<br>
**Mean and Median of steps taken each day** 


```r
MeanstepsperDay<-tapply(mydata$steps,mydata$date,mean)
MeanstepsperDaydf<-data.frame(Date=names(MeanstepsperDay),Mean.Steps=MeanstepsperDay)
MeanExclNAN_stepsperDaydf<-MeanstepsperDaydf[which(!(is.na(MeanstepsperDaydf$Mean.Steps))),]
MedianstepsperDay<-tapply(mydata$steps,mydata$date,median)
MedianstepsperDaydf<-data.frame(Date=names(MedianstepsperDay),Median.Steps=MedianstepsperDay)
MedianExclNAN_stepsperDaydf<-MedianstepsperDaydf[which(!(is.na(MedianstepsperDaydf$Median.Steps))),]
TableData<-merge(x = MeanExclNAN_stepsperDaydf, y = MedianExclNAN_stepsperDaydf, by = "Date", all = TRUE)
library(xtable)
xt<-xtable(TableData)
print(xt,type="html", include.rownames = FALSE)
```

<!-- html table generated in R 3.1.1 by xtable 1.7-4 package -->
<!-- Fri Jan 16 01:23:31 2015 -->
<table border=1>
<tr> <th> Date </th> <th> Mean.Steps </th> <th> Median.Steps </th>  </tr>
  <tr> <td> 2012-10-02 </td> <td align="right"> 0.44 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-03 </td> <td align="right"> 39.42 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-04 </td> <td align="right"> 42.07 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-05 </td> <td align="right"> 46.16 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-06 </td> <td align="right"> 53.54 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-07 </td> <td align="right"> 38.25 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-09 </td> <td align="right"> 44.48 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-10 </td> <td align="right"> 34.38 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-11 </td> <td align="right"> 35.78 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-12 </td> <td align="right"> 60.35 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-13 </td> <td align="right"> 43.15 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-14 </td> <td align="right"> 52.42 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-15 </td> <td align="right"> 35.20 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-16 </td> <td align="right"> 52.38 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-17 </td> <td align="right"> 46.71 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-18 </td> <td align="right"> 34.92 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-19 </td> <td align="right"> 41.07 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-20 </td> <td align="right"> 36.09 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-21 </td> <td align="right"> 30.63 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-22 </td> <td align="right"> 46.74 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-23 </td> <td align="right"> 30.97 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-24 </td> <td align="right"> 29.01 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-25 </td> <td align="right"> 8.65 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-26 </td> <td align="right"> 23.53 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-27 </td> <td align="right"> 35.14 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-28 </td> <td align="right"> 39.78 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-29 </td> <td align="right"> 17.42 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-30 </td> <td align="right"> 34.09 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-31 </td> <td align="right"> 53.52 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-02 </td> <td align="right"> 36.81 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-03 </td> <td align="right"> 36.70 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-05 </td> <td align="right"> 36.25 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-06 </td> <td align="right"> 28.94 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-07 </td> <td align="right"> 44.73 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-08 </td> <td align="right"> 11.18 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-11 </td> <td align="right"> 43.78 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-12 </td> <td align="right"> 37.38 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-13 </td> <td align="right"> 25.47 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-15 </td> <td align="right"> 0.14 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-16 </td> <td align="right"> 18.89 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-17 </td> <td align="right"> 49.79 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-18 </td> <td align="right"> 52.47 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-19 </td> <td align="right"> 30.70 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-20 </td> <td align="right"> 15.53 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-21 </td> <td align="right"> 44.40 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-22 </td> <td align="right"> 70.93 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-23 </td> <td align="right"> 73.59 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-24 </td> <td align="right"> 50.27 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-25 </td> <td align="right"> 41.09 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-26 </td> <td align="right"> 38.76 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-27 </td> <td align="right"> 47.38 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-28 </td> <td align="right"> 35.36 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-29 </td> <td align="right"> 24.47 </td> <td align="right"> 0.00 </td> </tr>
   </table>

<br>
**Average steps per 5-minute Interval**

```r
MeanInterval<-tapply(mydata$steps,mydata$interval,mean,na.rm=TRUE)
MeanIntervaldf <-data.frame(Interval=names(MeanInterval),Mean.Steps=MeanInterval) 
MeanIntervaldf$Interval<-as.character(MeanIntervaldf$Interval)
plot(MeanIntervaldf$Interval,MeanIntervaldf$Mean.Steps,type="l",col="red",axes=FALSE, xaxt="n",ann=FALSE)
axis(1, at = seq(0, 2250, by = 250), las=2)
axis(2, las=1)
box()
title(main="Average Steps per each Interval", col.main="black", font.main=4)
title(xlab="5-Minute Interval")
title(ylab="Average Steps")
```

<img src="figure/Avg steps per Interval-1.png" title="plot of chunk Avg steps per Interval" alt="plot of chunk Avg steps per Interval" style="display: block; margin: auto;" />
<br>
**5-minute Interval with max average steps**

```r
MeanIntervaldf2<-MeanIntervaldf[order(MeanIntervaldf$Mean.Steps, decreasing = TRUE),]
MeanIntervaldf2$Interval[1]
```

```
[1] "835"
```
<br>
**Total number of dataset NA rows**

```r
length(which(is.na(mydata)))
```

```
[1] 2304
```
<br>
**Replication of original dataset and treatment of  NA values**  
-1st aproach in order to treat NAs is to replace them with the mean
value of the subsequent day.

```r
mydataTreatNa<-mydata
for (x in 1:nrow(mydataTreatNa)){
        if (is.na(mydataTreatNa[x,1])){
            mydataTreatNa[x,1]<- MeanstepsperDaydf$Mean.Steps[which(
                    MeanstepsperDaydf$Date==mydataTreatNa[x,2])]    
        }
}
```
<br>
**Check the results of the above aproach for NAs treatment**

```r
length(which(is.na(mydataTreatNa)))
```

```
[1] 2304
```
<br>
**There is no change in terms of NAs substitution**  
This means that  the NA values derives from Dates where all of its observation on the  steps variable are NAs
<br>
-2nd aproach is the replacement of NA values with the mean value of the  
subsequent intervall in which belong

```r
for (x in 1:nrow(mydataTreatNa)){
        if (is.na(mydataTreatNa[x,1])){
            mydataTreatNa[x,1]<- MeanIntervaldf$Mean.Steps[which(
                    MeanIntervaldf$Interval==mydataTreatNa[x,3])]    
        }
}
```
<br>
**Check the results of the 2nd aproach for NAs treatment**

```r
length(which(is.na(mydataTreatNa)))
```

```
[1] 0
```
**All the NA values have successfully substituted in our new dataset**
<br>
<br>
**Total number of steps taken each day(NAs treated dataset)**  


```r
stepsperDay<-tapply(mydataTreatNa$steps,mydataTreatNa$date,sum,na.rm=TRUE)
stepsperDaydf<-data.frame(Date=names(stepsperDay),Total.Steps=stepsperDay)
par(mar=c(0,5,1,2))
par(las=2)
x<-barplot(stepsperDaydf$Total.Steps,horiz=TRUE,names.arg=stepsperDaydf$Date,cex.names=0.7,
main ="Total Steps per Day",col="blue", xaxt="n",)
text(x= stepsperDaydf$Total.Steps+750, y= x, labels=as.character(round(stepsperDaydf$Total.Steps,0)),
cex=0.7,xpd=TRUE)
```

<img src="figure/plot sbst NAS histogram-1.png" title="plot of chunk plot sbst NAS histogram" alt="plot of chunk plot sbst NAS histogram" style="display: block; margin: auto;" />
<br>
**Mean and Median of steps taken each day(NAs treated dataset)** 


```r
MeanstepsperDay<-tapply(mydataTreatNa$steps,mydataTreatNa$date,mean)
MeanstepsperDaydf<-data.frame(Date=names(MeanstepsperDay),Mean.Steps=MeanstepsperDay)
MedianstepsperDay<-tapply(mydataTreatNa$steps,mydataTreatNa$date,median)
MedianstepsperDaydf<-data.frame(Date=names(MedianstepsperDay),Median.Steps=MedianstepsperDay)
TableData<-merge(x = MeanstepsperDaydf, y = MedianstepsperDaydf, by = "Date", all = TRUE)
library(xtable)
xt<-xtable(TableData)
print(xt,type="html", include.rownames = FALSE)
```

<!-- html table generated in R 3.1.1 by xtable 1.7-4 package -->
<!-- Fri Jan 16 01:23:35 2015 -->
<table border=1>
<tr> <th> Date </th> <th> Mean.Steps </th> <th> Median.Steps </th>  </tr>
  <tr> <td> 2012-10-01 </td> <td align="right"> 37.38 </td> <td align="right"> 34.11 </td> </tr>
  <tr> <td> 2012-10-02 </td> <td align="right"> 0.44 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-03 </td> <td align="right"> 39.42 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-04 </td> <td align="right"> 42.07 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-05 </td> <td align="right"> 46.16 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-06 </td> <td align="right"> 53.54 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-07 </td> <td align="right"> 38.25 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-08 </td> <td align="right"> 37.38 </td> <td align="right"> 34.11 </td> </tr>
  <tr> <td> 2012-10-09 </td> <td align="right"> 44.48 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-10 </td> <td align="right"> 34.38 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-11 </td> <td align="right"> 35.78 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-12 </td> <td align="right"> 60.35 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-13 </td> <td align="right"> 43.15 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-14 </td> <td align="right"> 52.42 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-15 </td> <td align="right"> 35.20 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-16 </td> <td align="right"> 52.38 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-17 </td> <td align="right"> 46.71 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-18 </td> <td align="right"> 34.92 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-19 </td> <td align="right"> 41.07 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-20 </td> <td align="right"> 36.09 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-21 </td> <td align="right"> 30.63 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-22 </td> <td align="right"> 46.74 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-23 </td> <td align="right"> 30.97 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-24 </td> <td align="right"> 29.01 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-25 </td> <td align="right"> 8.65 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-26 </td> <td align="right"> 23.53 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-27 </td> <td align="right"> 35.14 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-28 </td> <td align="right"> 39.78 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-29 </td> <td align="right"> 17.42 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-30 </td> <td align="right"> 34.09 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-10-31 </td> <td align="right"> 53.52 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-01 </td> <td align="right"> 37.38 </td> <td align="right"> 34.11 </td> </tr>
  <tr> <td> 2012-11-02 </td> <td align="right"> 36.81 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-03 </td> <td align="right"> 36.70 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-04 </td> <td align="right"> 37.38 </td> <td align="right"> 34.11 </td> </tr>
  <tr> <td> 2012-11-05 </td> <td align="right"> 36.25 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-06 </td> <td align="right"> 28.94 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-07 </td> <td align="right"> 44.73 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-08 </td> <td align="right"> 11.18 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-09 </td> <td align="right"> 37.38 </td> <td align="right"> 34.11 </td> </tr>
  <tr> <td> 2012-11-10 </td> <td align="right"> 37.38 </td> <td align="right"> 34.11 </td> </tr>
  <tr> <td> 2012-11-11 </td> <td align="right"> 43.78 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-12 </td> <td align="right"> 37.38 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-13 </td> <td align="right"> 25.47 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-14 </td> <td align="right"> 37.38 </td> <td align="right"> 34.11 </td> </tr>
  <tr> <td> 2012-11-15 </td> <td align="right"> 0.14 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-16 </td> <td align="right"> 18.89 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-17 </td> <td align="right"> 49.79 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-18 </td> <td align="right"> 52.47 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-19 </td> <td align="right"> 30.70 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-20 </td> <td align="right"> 15.53 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-21 </td> <td align="right"> 44.40 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-22 </td> <td align="right"> 70.93 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-23 </td> <td align="right"> 73.59 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-24 </td> <td align="right"> 50.27 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-25 </td> <td align="right"> 41.09 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-26 </td> <td align="right"> 38.76 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-27 </td> <td align="right"> 47.38 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-28 </td> <td align="right"> 35.36 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-29 </td> <td align="right"> 24.47 </td> <td align="right"> 0.00 </td> </tr>
  <tr> <td> 2012-11-30 </td> <td align="right"> 37.38 </td> <td align="right"> 34.11 </td> </tr>
   </table>
<br>
<font color="red"> <b>Impact of imputing missing data on the above estimates:</b></font>
<br>
-On the total steps per day histogram, the only difference from the  initial histogram(without imputing the NA values) is the presence  of some more days which have excluded from the initial histogram  due to the fact that the subsequent number of total steps for that days  was NA. On the current histogram the value for that days is the summary  of the mean of each interval across all the days.
<br>
-On the mean and median report, the only difference is also the presence of some more days which have excluded from the initial report  due to the fact that the subsequent number of mean and median total steps for that days  was NA. On the current report the mean value for that days is the mean among the means of all the Intervals and the median is the median among all the means off all Intervals. The fact that the median has zero value among the most days is normal due to the fact that over the half of variable steps observations have the zero as value.
<br>

```r
paste(round((length(which(mydataTreatNa$steps==0))/nrow(mydataTreatNa) *100),0), "%", sep="")
```

```
[1] "64%"
```
<br>
**Create a new factor variable in the dataset with two levels – “Weekday” and “weekend” indicating whether a given date is a weekday or Weekend day**

```r
mydataTreatNa$date<-as.Date(mydataTreatNa$date, format = "%Y-%m-%d")
Sys.setlocale("LC_TIME", "English")
mydataTreatNa$WeakDay<-weekdays(mydataTreatNa$date)
mydataTreatNa$WeakdayFactor<-ifelse(mydataTreatNa$WeakDay=="Monday"|
mydataTreatNa$WeakDay=="Tuesday" |mydataTreatNa$WeakDay=="Wednesday" |
mydataTreatNa$WeakDay=="Thursday" | mydataTreatNa$WeakDay=="Friday" , 
"Weekday","Weekend")
```
<br>
**Reshape data and plot a time series(lattice) of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all weekday days or weekend days (y-axis)**

```r
library(reshape2)
MeltData<-melt(mydataTreatNa,id=c(3,5),measure.vars = 1)
plotdata<-dcast(MeltData,interval+WeakdayFactor~variable,mean)
library(lattice)
xyplot(steps ~ interval | WeakdayFactor, data = plotdata,type="l",  
layout = c(1, 2),xlab="Interval",ylab="Number of steps")
```

<img src="figure/lattice plot-1.png" title="plot of chunk lattice plot" alt="plot of chunk lattice plot" style="display: block; margin: auto;" />
