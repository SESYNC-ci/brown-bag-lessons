---
layout: post
title:  "Data frames"
date:   2014-10-20
categories: lessons R
author: khondula
---

**Data frames**


Basic features:

* Data frames have rows and columns, like a spreadsheet in Excel. 
* All of the columns must be the same length.
* Within each column, all of the data must be the same type or "class" such as numeric or character
	- If a column of numbers has a word such as "missing data", that column will default to all character data
	- Use colClasses= or na.strings= to change that on import, or you can replace unwanted/missing data once your data is imported

How to identify parts of your data frame:

* Columns can be identified by their name
{% highlight R %} 
mydata$columnname
{% endhighlight %}
+ Bracket notation identifies rows and/or columns

{% highlight R %} 
mydata[2,1]
{% endhighlight %}

{% highlight R %} 
mydata[2,]
{% endhighlight %}

{% highlight R %} 
mydata[,3]
{% endhighlight %}

{% highlight R %} 
mydata[,"col3"]
{% endhighlight %}

{% highlight R %} 
mydata[,ncol(mydata)]
{% endhighlight %}

