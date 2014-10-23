---
layout: post
title:  "R Class Notes 23 Oct 2014"
date:   2014-10-23
categories: lessons R
author: khondula
---

+ character strings
+ numeric data
+ colnames
+ functions

generic | more specific
--------| -------------
read.table() | read.csv()
paste() | paste0()

The more specific example of the function is similar to the generic function but has some specific default arguments. 
- read.csv() uses commas as separators and header=TRUE
- paste0 does not put spaces between the things you are combining

+ look for this information in the help documentation of each function

+ special characters like %
![alt text](http://imgs.xkcd.com/comics/exploits_of_a_mom.png   )	

+ data frames
	- columns are all the same length
	- each column has the same type of data within that column
+ identifying column names with $
+ identifying rows and columns with [ ]
+ replace strings with NA
	- na.strings=c()
	- colClasses=c()
	- is.na()

	


![alt text](http://imgs.xkcd.com/comics/the_general_problem.png  )

