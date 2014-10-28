---
layout: post
title:  "Practice saving and loading data"
date:   2014-10-28
categories: homework R
author: khondula
---

## Homework assignment

Main concepts to review:

* loading a spreadsheet file into RStudio
* identifying parts of a data frame
* basic plotting

### Loading a spreadsheet file into RStudio

Recall that the network file storage is where your individual "name-data" folder and the "public-data/Ed" (Ed for education) folder exist, and that these folders are accessible from the RStudio server. The Ed folder is where we have saved files for you to work with. You can read from but not save things to this folder. 

If you want to find these folders and look at their contents in your file browser,
* on a PC: Open a file browser window and type "\\storage.research.sesync.org" into the address bar (click in the address bar to type into it)
* on a Mac:

Note that the files in the Ed folder have the .csv file extension. We recommend saving your Excel files as a .csv in order to load them into R for analysis. This assumes that your first row has column headings.

In order to load your file into R, use a function like read.csv(). This function is similar to the more general read.table() function but has default parameters "header=TRUE" (the first row is column headings), and "sep="," (comma-separated values). Take a look at the data input help menu by running the command ?read.csv or by typing read.csv and pressing the F1 key. Note that the bottom of the help documentation has some examples of usage. 

Use the arrow notation to save the table as a data frame object with a name so you can use it. 

Compare the difference between:
{% highlight R %}
read.csv("/nfs/public-data/Ed/UAWG_AberjonaHydro.csv")
{% endhighlight %}

{% highlight R %}
mydataframe <- read.csv("/nfs/public-data/Ed/UAWG_AberjonaHydro.csv")
{% endhighlight %}

After running the second line, look at the upper right window of RStudio in the "Environment" tab to see that your data frame is stored as an object. You can view the data frame by clicking on the icon on the right hand side. 

![image here]({{ http://sesync-ci.github.io/ }} brown-bag-lessons/_posts/_assets/rstudioSchematic.jpg)

2. Format columns 1 and 6 as Years
3. Create new variable “RunoffRatio” and calculate the Runoff Ratio for each year (storm/precip)
4. Plot a time series of runoff ratios (scatter plot with a line connecting the points)
5. Add the building density record to this plot on a second axis
6. Test to see if there is a significant increase in runoff ratios over this time period

 {% highlight R %}

# use the function read.csv() to read in the table that is located at "/nfs/public-data/Ed/UAWG_AberjonaHydro.csv"

# look at the structure of the data 

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
