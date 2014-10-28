---
layout: post
title:  "Practice saving and loading data"
date:   2014-10-28
categories: homework R
author: khondula
---

## Homework assignment

Log into rstudio.sesync.org with you sesync user name and password. Either continue working in your "practice" project, or make a new project in your "name-data" storage directory for this homework assignment. 

Main objectives:

* loading a spreadsheet file into RStudio
* identifying parts of a data frame
* basic plotting

### Loading a spreadsheet file into RStudio

Recall that the network file storage is where your individual "name-data" folder and the "public-data/Ed" (Ed for education) folder exist, and that these folders are accessible from the RStudio server. The Ed folder is where we have saved files for you to work with. You can read from but not save things to this folder. 

If you want to find these folders and look at their contents in your file browser,

* on a PC: Open a file browser window and type '\\storage.research.sesync.org' into the address bar (click in the address bar to type into it)
* on a Mac:

Note that the files in the Ed folder have the .csv file extension. We recommend saving your Excel files as a .csv in order to load them into R for analysis. This assumes that your first row has column headings.

In order to load your file into R, use a function like read.csv(). This function is similar to the more general read.table() function but has default parameters "header=TRUE" (the first row is column headings), and "sep="," (comma-separated values). Take a look at the data input help menu by running the command ?read.csv or by typing read.csv and pressing the F1 key, or on the R help page online here: https://stat.ethz.ch/R-manual/R-devel/library/utils/html/read.table.html. Note that the bottom of the help documentation has some examples of usage. 

Use the arrow notation to save the table as a data frame object with a name so you can use it. 

Compare the difference between:
{% highlight R %}
read.csv("/nfs/public-data/Ed/UAWG_AberjonaHydro.csv")
{% endhighlight %}

{% highlight R %}
mydataframe <- read.csv("/nfs/public-data/Ed/UAWG_AberjonaHydro.csv")
{% endhighlight %}

After running the second line, look at the upper right window of RStudio in the "Environment" tab to see that your data frame is stored as an object. You can view the data frame by clicking on the icon on the right hand side. 

For the rest of the homework practice, copy and paste everything in the gray window below into your R script. There are step-by-step instructions for what to do. Refer back to the other class notes pages from the list here (http://sesync-ci.github.io/brown-bag-lessons/) when you need to. 


 {% highlight R %}

# use the function read.csv() to read in the table that is located at "/nfs/public-data/Ed/UAWG_AberjonaHydro.csv"

# look at the structure of the data and some summary information to determine:
### how many rows and columns does the data frame have?
### what are the names of the columns? 
### what is the average baseflow_mm? 

# use the mean() function to find the mean building density (BuildDen)
# what additional argument do you have to use because there are NA values?

# make two new data frames to separate the flow data (first 5 columns) 
# from the building density data (last 2 columns)
# think of several different ways that you could identify each of 
# those 2 parts of the dataframe in order to accomplish this
# Only include the first 14 rows of building density data,
# i.e. do not include the NAs in your building density data frame

# Optional challenge: use the merge() function to combine
# your 2 new data frames into a single dataframe based on the "year" column
# see help: https://stat.ethz.ch/R-manual/R-devel/library/base/html/merge.html
# or here: http://www.statmethods.net/management/merging.html

# Calculate the runoff ratio (stormflow_mm divided by precip_mm) 
# as a new column of the flow data frame

# use plot() to make a scatterplot of runoff ratio vs flowyr 

# plot building density vs building year

# plot building density and runoff ratio on the same plot
# over the time period 1900 to 2011
# use different plotting characters and colors for runoff ratio and building density

# use the mfrow argument in the par() function to plot building density vs year and 
# runoff ratio vs year side-by-side or one above the other. 
# use the xlim argument in plot() function to have the same time period showing in 
# both plots

# use abline() to add a vertical or horizontal line to your plot
# use lwd, lty, and col to adjust the line width, type (dash, dot, etc.), and color

# Optional challenge: use the legend() function to put a legend on your plot
# see help: https://stat.ethz.ch/R-manual/R-devel/library/graphics/html/legend.html
# or here (scroll down): http://www.statmethods.net/advgraphs/axes.html

# save one of your plots as a .png file
# either click "export" in the lower right side plotting window
# or, try to use the png() function with the argument file to give it a file name
# To do this, you will need to run the png function, then the plotting function,
# and the you will also need to "turn off the graphics device" by running dev.off() 
# with no arguments
# see help: https://stat.ethz.ch/R-manual/R-devel/library/grDevices/html/png.html

# for example,

png("myplot.png", width=480, height=480)
plot(mydata$xvariable, mydata$yvariable, col="red", pch=21)
dev.off()

# png width and height specifications are in pixels by default
# whereas pdf width and height specifications are in inches by default
# Or, you can use the units argument to specify inches, cm, etc.  

{% endhighlight %}
