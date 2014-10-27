---
layout: post
title:  "Data frames"
date:   2014-10-20
categories: lessons R
author: khondula
---

## Basic features:

* Data frames have rows and columns, like a spreadsheet in Excel. 
* A convenient layout for rows and columns is to have rows be individual data points or observations, and each column contains information about that observation (date, categories, value, etc.). The melt() function in the reshape2 package can help get your data in the right format.
* All of the columns must be the same length.
* Within each column, all of the data must be the same type or "class". 
	- If a column of numbers has a word such as "missing data", that column will import as all character data by default
	- Use colClasses= or na.strings= to change that on import, or you can replace unwanted/missing data once your data is imported

## Importing from Excel
* We recommend saving your file as a .csv and using read.csv() but there are also other options.

## Subscripts and indices: How to identify parts of your data frame

Use square brackets and/or the $ to identify rows and columns of your dataframe. 

* Columns can be identified by their name
{% highlight R %} 
mydata$columnname
{% endhighlight %}
+ Bracket notation identifies rows and/or columns

{% highlight R %} 
mydata[2,1]
{% endhighlight %}
Not calling a row or column will select that entire row or column. This notation refers to the entire 2nd row:
{% highlight R %} 
mydata[2,]
{% endhighlight %}
* This notation refrs to the entire 3rd column:
{% highlight R %} 
mydata[,3]
{% endhighlight %}
* You can also use the name of that column
{% highlight R %} 
mydata[,"col3"]
{% endhighlight %}
* What column would this refer to?
{% highlight R %} 
mydata[,ncol(mydata)]
{% endhighlight %}

* Use c() to refer to multiple rows and/or columns
{% highlight R %} 
mydata[c(1,3:5),c("col2", "col4")]
{% endhighlight %}

## Selecting parts of your data frame based on a condition

* Use conditional arguments
* subset() function
* which() function
* order or sort and choose 1st or last row

## Merging and combining dataframes

*cbind()
*rbind()
*merge(dataframeA, dataframeB, by.x=, by.y=, all.x=TRUE, all.y=TRUE)
