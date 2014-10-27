---
layout: post
title:  "Basic plotting"
date:   2014-10-23
categories: lessons R
author: khondula
---

+ Review homework assignment

Import the data file using the read.csv() function

{% highlight R %}
data <- read.csv(file="/nfs/public-data/Ed/HW1_data.csv")
{% endhighlight %}

Find out some simple things about your data frame

{% highlight R %}
str(data)
dim(data)
summary(data)
ncol(data)
names(data)
{% endhighlight %}

Modify the read.csv function to take the argument na.strings 

{% highlight R %}
data<-read.csv(file=filename,
               na.strings=c("Dry"))
{% endhighlight %}

Plot a scatterplot showing WVSCI scores (Y) by conductivity (X)

{% highlight R %}

plot(y=data$wvsciFall,
     x=data$condFall,
     ylim=c(0,100),
     xlim=c(0,2100),
     xlab="Conductivity",
     ylab="WVSCI (Fall 2000)",
     pch=21,
     bg="red",
     cex=1.5)
{% endhighlight %}


the threshold for biological impairment is at wvsci=68. draw a horizontal dashed line on your plot to show that

{% highlight R %}
abline(h=68, lty=2, col="blue")
{% endhighlight %}

Multi-panel figures

- par() is the function that controls the plotting region parameters like margins
- there are many many graphical parameters that you can control
- use par+F1 or ?par to read about it in the help window
- we're going to use mfrow, which allows for plotting multiple plots in one layout
- the argument mfrow takes a vector with the dimensions of rows and columns
- for example, c(1,2) is 1 row, 2 columns

{% highlight R %}

par(mfrow=c(1,2))

{% endhighlight %}

- nothing happens when you run this command, but you will notice it once you draw a plot
- draw the same plot you had before and see that it takes up half of the plotting region

{% highlight R %}

plot(y=data$wvsciFall,
     x=data$condFall,
     ylim=c(0,100),
     xlim=c(0,2100),
     xlab="Conductivity",
     ylab="WVSCI (Fall 2000)",
     pch=21,
     bg="red",
     cex=1.5)

	 
{% endhighlight %}


- now instead of using plot(), use points() to add new data to the same plot
- points takes many of the same arguments as plot: x and y values, pch, cex, col

Make your first plot:
{% highlight R %}

plot(y=data[,3],
     x=data[,5],
     ylim=c(0,100),
     xlim=c(0,2100),
     xlab="Conductivity",
     ylab="WVSCI (Spring 2001)",
     pch=21,
     bg="green",
     cex=1.5)
	 
{% endhighlight %}

Now add the second data set onto your plot: 
{% highlight R %}

points(x=data[,5],
       y=data[,3],
       bg="green",
       pch=21,
       cex=1.5)
	 
{% endhighlight %}



More data sets to practice with:

{% highlight R %}
cond<-read.csv("/nfs/public-data/Ed/conductivity.csv")
sulfate<-read.csv("/nfs/public-data/Ed/sulfate.csv")
{% endhighlight %}


* [Guides and Tutorials](https://collab.sesync.org/sites/support)

