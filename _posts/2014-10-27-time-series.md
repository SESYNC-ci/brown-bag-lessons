---
layout: post
title:  "Data types"
date:   2014-10-23
categories: lessons R
author: khondula
---

## Review - importing data 

A simple way to read data into RStudio is to save your spreadsheet as a .csv file and use the function read.csv(). The RStudio server can read files from the network file share (recommended), or files that you upload directly to the RStudio Server. 

Files for R Lessons are in the network file share in the public data folder. You can read files from this folder but not save things there. Save your own files to your data folder (or your project's folder). 

## Special characters

![alt text](http://imgs.xkcd.com/comics/exploits_of_a_mom.png   )	

Certain characters are interpreted by the computer as a signal to treat what follows that character in a special way, like punctuation. It is advisable to not use these characters in column names or file names if you can avoid it. 

Some examples of special characters to watch out for:

+ %
+ /
+ "
+ $

Single quotes and double quotes are both used for character strings but mean slightly different things. Use single quotes if you want the entire text inside of the quotes to be interpreted as characters, for example if you have a string that includes a quotation. 

For example, perhaps you are plotting the number of times something was said.

Which one(s) of these would correctly label the y axis as *Number of times "hi" was spoken*?

{% highlight R %}
ylab="Number of times "hi" was spoken"
{% endhighlight %}

{% highlight R %}
ylab='Number of times "hi" was spoken'
{% endhighlight %}

{% highlight R %}
ylab="Number of times \"hi\" was spoken"
{% endhighlight %}



## Review of data frames
	- columns are all the same length
	- each column has the same type of data within that column (numeric, character, factor)
+ identifying column names with $
+ identifying rows and columns with [ , ]
+ replace strings with NA
	- na.strings=c()
	- colClasses=c()
	- is.na()

	


![alt text](http://imgs.xkcd.com/comics/the_general_problem.png  )



Material for Monday:

1. Load the data
2. Format columns 1 and 6 as Years
3. Create new variable “RunoffRatio” and calculate the Runoff Ratio for each year (storm/precip)
4. Plot a time series of runoff ratios (scatter plot with a line connecting the points)
5. Add the building density record to this plot on a second axis
6. Test to see if there is a significant increase in runoff ratios over this time period

 {% highlight R %}

# save the file as a .csv file (why?)
# read in the file from the public data Ed folder

# use the function "read.csv()"
# this is a specific type of "read.table()" function with the default argument sep="," and header=TRUE
# is it necessary to write "file=" in the function?
# what do you use to separate arguments in a function?

# something about na.strings, colClasses
hydro<-read.csv(file="/nfs/public-data/Ed/UAWG_AberjonaHydro.csv")


# look at the structure

str(hydro2)

# separate the building year data into a separate table

yearlyHydro<-hydro[,c(1:5)]
buildingDen<-hydro[is.na(hydro$BuildYr)==FALSE,c(6,7)]

# can merge back into a single dataframe

hydro2<-merge(yearlyHydro, buildingDen, by.x="FlowYr", by.y="BuildYr", all.x=TRUE, all.y=TRUE)

hydro2$RunoffRatio<-hydro2$Stormflow_mm/hydro2$Precip_mm

par(mfrow=c(2,1))
par(mar=c(3,4.5,1,1))
plot(hydro2$BuildDen~hydro2$FlowYr)
plot(hydro2$RunoffRatio~hydro2$FlowYr)

summary(lm(hydro2$RunoffRatio~hydro2$FlowYr))

# time series

# convert the building density data into a time series
hydro2$RunoffRatio

# find which column is called runoff ratio and make that into a ts object

runoffratioTS<-ts(hydro2[c(5:nrow(hydro2)),7],
                  start=c(1940,1),
                  end=c(2011,1),
                  frequency=1)

plot.ts(runoffratioTS)
plot(runoffratioTS, type="o")

acf(runoffratioTS)

# look for stationary mean and variance
# can test for stationarity using "unit root tests" in the fUnitRoots package

plot.ts(diff(runoffratioTS, differences=1))
{% endhighlight %}

