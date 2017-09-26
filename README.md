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
This was a lot of fun. I first just plotted the population and year and then once I realized that there were two population trends I tried to focus on just two countries likely to have different population trends. I did initially have a tiny issue with my piping but I got it working. I then tried to create a density plot with population I got a bin warning, changed my bin length and then my R crashed. I suspect I gave it a incompatible command or something too long and hard to compute. 

### Other notes: 
I was having a hard time formatting my output to look cleaner. I found this super useful [site](https://yihui.name/knitr/options/) outlining the options for knitr. 
