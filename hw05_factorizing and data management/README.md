# This folder contains all my HW05 materials



This [file](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw05/hw5.md) has my nice output from r. 

But [here](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw05/hw5.Rmd) is the raw code to see what I did to get my tables and graphs.



## Progress Report

## Factor Management

**Factorize.** Transform some of the variable in the `singer_locations` dataframe into factors: pay attention at what levels you introduce and their order. Try and consider the difference between the base R `as.factor` and the `forcats`-provided functions.

This part was a bit tricky. I was getting errors from my factoring code. After asking google, it seems that the base r factoring pack struggles with na values. I then removed the NA values and it all seemed to work fine after that. I realized afterwards that I had been using `as_factors` which was used in the class live coding demo. After rereading the instructutions I saw that I was suppose to be using `as.factor`. I left my error in the .Rmd though as a lesson. I decided to use the `forcats` pack also to see if there were order differences in this case it all seems the same. But since `forcats` wont change the order this seems safer. 


**Drop 0.** This part was easy except for when I tried to filter out mulitple values at once. I tried a number of form for sytax and ran into errors on each attempt. I eventually just decided to write a line for each separate one even though this is very inefficient.  Here I alsoran into problems because I realized that although my unused data was removed my unused factor levels were still there. I did a bit of hunting though and found a solution. 

**Reorder the levels of `year`, `artist_name` or `title`.** 
I ran into two problem at this step: 
- I tried to create my summary statistic and then reorder and got this error: : Column `artist_name_factor` can't be modified because it's a grouping variable. 
-I also ran into an issue when I tried to fct_reorder on the whole dataset if you don't summarize first. This seemed to cause issues when there were multiple artists with multiple maximum durations. I ended up focusing on a few data points for the plot anyway but this is something to keep in mind. 




