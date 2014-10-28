---
layout: post
title:  "Practice saving and loading data"
date:   2014-10-28
categories: homework R
author: khondula
---

## Homework assignment

Main concepts:

* loading a spreadsheet file into RStudio
* identifying parts of a data frame
* basic plotting

### Loading a spreadsheet file into RStudio

![image here]({{ site.url }}/_posts/_assets/rstudioSchematic.jpg)


1. Load the data
2. Format columns 1 and 6 as Years
3. Create new variable “RunoffRatio” and calculate the Runoff Ratio for each year (storm/precip)
4. Plot a time series of runoff ratios (scatter plot with a line connecting the points)
5. Add the building density record to this plot on a second axis
6. Test to see if there is a significant increase in runoff ratios over this time period

 {% highlight R %}

# file path is: "/nfs/public-data/Ed/UAWG_AberjonaHydro.csv"
# save the file as a .csv file (why?)
# read in the file from the public data Ed folder
# use the function "read.csv()"
# look at the structure

# separate the building year data into a separate data frame

# optional: merge back into a single dataframe

# Calculate runoff ratio in a new column 

# plot runoff ratio vs flowyr 

# plot building density vs building year

# plot building density and runoff ratio on the same plot

# convert the building density data into a time series

# find which column is called runoff ratio and make that into a ts object

# look at stationary mean and variance

{% endhighlight %}
