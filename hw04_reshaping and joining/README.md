# This folder contains all my HW04 materials



This [file](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw04/hw4.md) is the .md file for this week's homework.

This [file](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw04/hw4.Rmd) is the .Rmd file for this week's homework.


## Progress Report
Reshaping the data: 
1. Reshaping the data was really easy. I did get a bit confused at first when I mixed up the variables in the `spread` function but I learned through trial and error. 
2. At first glance at the data format I'm not sure how you would plot this. I finally found something that works. In my coding for the plot I originally had put `ggplot(aes(x = year, y=lifeExp ))` shockingly this still worked even though lifeExp had not been piped. I think because I had put new y variables in for the following lines that this over wrote my mistake.


Join, merge, look up
1. I first had issues here because I created a data file (.csv) and imported it into my R but then my knitr wouldn't work because it couldn't find my data. After googling I realized that I need to upload my data to github and then have a `read_csv` line in r. Otherwise this was pretty straight forward. I did notice that in my case the `inner_join` and `semi_join` were returning the same values since there were no multiples. So then I decided to join by year just for fun. This finally returned different datasets for `inner_join` and `semi_join`. But since the year factors mean different things, it is totally uninterpretable. 

Bonus comparisons: 
The `merge` was as expected. But the `match` function yeilded interesting results. When I performed match for gapminder and nato dataset, it returned a vector of NAs equal to the number of variables in gapminder. But when I performed a match for nato and natoRenamed (only a variable renamed here), it returned a vector with 1 and 2. I had to google this to figure out what it means. It doesn't seem like it is a very different funciton than join/merge, because it is really just a check for anything that matches. 