# This folder contains all my HW05 materials



This [file](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw05/hw5.md) has my nice output from r. 

But [here](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw05/hw5.Rmd) is the raw code to see what I did to get my tables and graphs.



## Progress Report

## Factor Management

**Factorize.** Transform some of the variable in the `singer_locations` dataframe into factors: pay attention at what levels you introduce and their order. Try and consider the difference between the base R `as.factor` and the `forcats`-provided functions.

This part was a bit tricky. I was getting errors from my factoring code. After asking google, it seems that the base r factoring pack struggles with na values. I then removed the NA values and it all seemed to work fine after that. I decided to use the `forcats` pack also to see if there were order differences in this case it all seems the same. But since `forcats` wont change the order this seems safer. 


