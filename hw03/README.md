# This folder contains all my HW03 materials


## Progress Report

### Task 1: Get the maximum and minimum of GDP per capita for all continents.
Creating the table for this was really easy. I really wanted to have a bar graph with the maximum and minimum values stacked or clustered but this proved to be very difficult. I found some help on a [stackoverflow page](https://stackoverflow.com/questions/10212106/creating-grouped-bar-plot-of-multi-column-data-in-r) which showed me how to melt my two variables together into a single column. This then allows for you to cluster according to max and min gpd. I changed the axis titles fine but had trouble changing my legend title. I finally realized that I was using the `scale_colour_discrete` and had to change it to `scale_fill_discrete` to get my title to change. 

### Task 2: Look at the spread of GDP per capita within the continents.
In constructing the table, I struggled a bit to get the spread for each continent. At first I kept getting the summary function for the whole variable as oppose to it being separated for each conintnent. So instead I had r create new varibles with the summarize function for each of the summary statistics that I wanted. I got the minimum, maximum, mean, standard deviation and each of the quartiles. For the quartiles I had to use a separate funciton for each, there is probably a much easier way to get all of them at once but my search was fruitless in that respect. 