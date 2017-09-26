# STAT545 Homework -Campbell, Jennifer

##### [Here is the link to my HW2 folder!](https://github.com/Jenncscampbell/STAT545-hw2-Campbell-Jennifer/tree/master/hw02) #####


## Progress Report

### Bringing in rectangular data in 
This part seemed pretty easy since we did it in class. 

### Smell test the data
Getting the results from these questions was fine for the most part. All the code here was provided in lecture. I did get a bit confused in the first two questions which ask if this is a data.frame and what class the data is? The structure code revealed that gapminder was a data.frame but the class code showed it was a tibble and data.frame. I wasn't sure what the difference was between these two. After going to the TAs I found....


### Explore individual variables
I decided to explore the quantitative variables: Country, continent, year and life expectancy. At first I ran the `summary` function on all but realized this didn't tell me much about the country variable since there were so many items. So instead I ran 

### Exploring various plot types
This was a lot of fun. I first just plotted the population and year and then once I realized that there were two population trends I tried to focus on just two countries likely to have different population trends. I then just poked around with some of the other data and continued to filter down groups to compare with. 
Please don't judge my plot decisions to harshly. I was really just playing around with things to do. 
After trying to compare more graphs next to each other I learned that you need to use facet_wrap when you have only a few graphs, facet_grid wont work

## I want to do more
I understand that this is wrong an obviously gives you an incomplete output but I'm not entirely sure why. After the TAs advice here's what I think: 
### Other notes: 
I was having a hard time formatting my output to look cleaner. I found this super useful [site](https://yihui.name/knitr/options/) outlining the options for knitr. 
