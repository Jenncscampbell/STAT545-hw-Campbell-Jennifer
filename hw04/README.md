# This folder contains all my HW04 materials



This [file](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw04/hw4.md) is the .md file for this week's homework.

This [file](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw04/hw4.Rmd) is the .Rmd file for this week's homework.


## Progress Report
Reshaping the data: 
1. Reshaping the data was really easy. I did get a bit confused at first when I mixed up the variables in the `spread` function but I learned through trial and error. 
2. At first glance at the data format I'm not sure how you would plot this. I finally found something that works. In my coding for the plot I originally had put `ggplot(aes(x = year, y=lifeExp ))` shockingly this still worked even though lifeExp had not been piped. I think because I had put new y variables in for the following lines that this over wrote my mistake.


Join, merge, look up
1. I first had issues here because I created a data file (.csv) and imported it into my R but then my knitr wouldn't work because it couldn't find my data. 