# This folder contains all my HW03 materials



[This file has my nice output from r](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw03/hw3_gapminder_exploration.md)

[But here is the raw code to see what I did to get my tables and graphs](https://github.com/Jenncscampbell/STAT545-hw-Campbell-Jennifer/blob/master/hw03/hw3%20gapminder%20exploration.Rmd)



## Progress Report

### Task 1: Get the maximum and minimum of GDP per capita for all continents.
Creating the table for this was really easy. I really wanted to have a bar graph with the maximum and minimum values stacked or clustered but this proved to be very difficult. I found some help on a [stackoverflow page](https://stackoverflow.com/questions/10212106/creating-grouped-bar-plot-of-multi-column-data-in-r) which showed me how to melt my two variables together into a single column. This then allows for you to cluster according to max and min gpd. I changed the axis titles fine but had trouble changing my legend title. I finally realized that I was using the `scale_colour_discrete` and had to change it to `scale_fill_discrete` to get my title to change. 

### Task 2: Look at the spread of GDP per capita within the continents.
In constructing the table, I struggled a bit to get the spread for each continent. At first I kept getting the summary function for the whole variable as oppose to it being separated for each conintnent. So instead I had r create new varibles with the summarize function for each of the summary statistics that I wanted. I got the minimum, maximum, mean, standard deviation and each of the quartiles. For the quartiles I had to use a separate funciton for each, there is probably a much easier way to get all of them at once but my search was fruitless in that respect. The graph for this was very easy to create though. 

### Task 3: Compute a weighted mean of life expectancy for different years. Here life expectancy is weighted by GDP per Capita.
I had a lot mutating my variables for this weighted mean. I spent a lot of time trying to get the scaled scores. For a long time I was using the `scale` function which appeared create a vector of z-scores for the entire gapminder data frame. Several times I tried to change the order of operations so that it was only using variables within the 12x4 dataframe (12 time points). This was even happening when I created new dataframes of only the 12 time points that I wanted. Finally, I abandoned the `scale` function and just wrote out the formula for z-scores and it worked perfectly. I realize that there must be a way to do this with the scale function but after most of an hour working on this I gave up. 

### Task 4: Report the absolute and/or relative abundance of countries with low life expectancy over time by continent: Compute some measure of worldwide life expectancy – you decide – a mean or median or some other quantile or perhaps your current age. Then determine how many countries on each continent have a life expectancy less than this benchmark, for each year.

## I decided to compute the number of countries within each continent which have a median life expectancy below 40
It was pretty easy to create the mutate functions to count all the countries with life expectancies below 40. It took me forever to get a correct frequency count. I finally modified code from this [stackoverflow page](https://stackoverflow.com/questions/25293045/count-number-of-rows-in-a-data-frame-in-r-based-on-group) 
I had some issues on this graph. ggplot really didn't like my data.frame. I couldn't get the line to show up. I tried several functions but kept getting errors about there only being one observation per group. 
