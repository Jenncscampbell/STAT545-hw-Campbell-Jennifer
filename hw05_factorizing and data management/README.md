# This folder contains all my HW05 materials



This [file](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw05/hw5.md) has my nice output from r. 

But [here](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw05/hw5.Rmd) is the raw code to see what I did to get my tables and graphs.



## Progress Report

## Factor Management

**Factorize.** Transform some of the variable in the `singer_locations` dataframe into factors: pay attention at what levels you introduce and their order. Try and consider the difference between the base R `as.factor` and the `forcats`-provided functions.

This part was a bit tricky. I was getting errors from my factoring code. After asking google, it seems that the base r factoring pack struggles with na values. I tried to remove my na values but ran into some issues, after talking with my ta ------ I decided to use the `forcats` pack instead since that won't reorder our variables and so is a bit better. 


