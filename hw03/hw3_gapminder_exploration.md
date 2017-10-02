HW 3 Gapminder Exploration
================

Task 1: Get the maximum and minimum of GDP per capita for all continents:
-------------------------------------------------------------------------

First I created a basic table with each continents's maximum and minimum GDP per capita:

| continent |  Max\_gdpPercap|  Min\_gdpPercap|
|:----------|---------------:|---------------:|
| Africa    |        21951.21|        241.1659|
| Americas  |        42951.65|       1201.6372|
| Asia      |       113523.13|        331.0000|
| Europe    |        49357.19|        973.5332|
| Oceania   |        34435.37|      10039.5956|

Then I created a new dataframe object with just the data I was interested in.

    ## # A tibble: 5 x 3
    ##   continent Max_gdpPercap Min_gdpPercap
    ##      <fctr>         <dbl>         <dbl>
    ## 1    Africa      21951.21      241.1659
    ## 2  Americas      42951.65     1201.6372
    ## 3      Asia     113523.13      331.0000
    ## 4    Europe      49357.19      973.5332
    ## 5   Oceania      34435.37    10039.5956

This table seems to show that Asia has the largest maximum GDP per capita and that Africa has the lowest. In terms of the minimum GDP per capita, Africa has the lowest while Oceania has the highest.

Since I want r to cluster my max and min gdp per capitals, I need to put these into a single variable which r can then graph by colour. To do this I used the `melt` function.

![](hw3_gapminder_exploration_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-5-1.png)

This layout is still a bit tricky to read because of the large differences in gdp. So I put the y-axis on a log scale of 10 before cleaning up the graph.

![](hw3_gapminder_exploration_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-6-1.png) \`\`\`

In this graph we can see the maximum and minimum GDP per capita levels clearly for each continent. Overall, Asia appears to have the largest difference between the maximum and minimum GDP per capita in the records. However, Asia also has the highest maximum GDP per capita in the records. We can also see that Oceania has the smallest difference between its maximum and minimum GDP per capita levels. The highest minimum GDP per capita level belongs to Oceania while the lowest belongs to Africa.

Task 2: Look at the spread of GDP per capita within the continents.
-------------------------------------------------------------------

| continent |       Mean|         Min|        Max|     StdDev|        Q25|        Q50|        Q75|
|:----------|----------:|-----------:|----------:|----------:|----------:|----------:|----------:|
| Africa    |   2193.755|    241.1659|   21951.21|   2827.930|    761.247|   1192.138|   2377.417|
| Americas  |   7136.110|   1201.6372|   42951.65|   6396.764|   3427.779|   5465.510|   7830.210|
| Asia      |   7902.150|    331.0000|  113523.13|  14045.373|   1056.993|   2646.787|   8549.256|
| Europe    |  14469.476|    973.5332|   49357.19|   9355.213|   7213.085|  12081.749|  20461.386|
| Oceania   |  18621.609|  10039.5956|   34435.37|   6358.983|  14141.859|  17983.304|  22214.117|

This table is really hard to read. There is a lot of information. We can see that Europe and Oceania have higher means than the other continent but China has a much higher maximum than the rest.

The best way I think to plot data distributions like this is with box plots:

![](hw3_gapminder_exploration_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-8-1.png)

This is still very hard to read so I decided to have plot the log10 of the y-axis.

![](hw3_gapminder_exploration_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-9-1.png)

This graph is much easier to read. Here we can easily compare the means and tell that Oceania and Europe have higher overall GDP per capita than Africa and Asia. However, the distribution is much more spread out for Asia than any of the other continents with Oceania showing little variation in GDP per capita than the other continents. We can also see that the maximum values are higher for Asia than the other continents.

Task 3: Compute a weighted mean of life expectancy for different years. Since we found in task 2 there is a huge difference in GDP per capita, I decided to create a weighted score of life expectancy by GPD per capita.
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

First I tried to just weight life expectancy by GDP per capita:

|  year|    meangdp|  meanLife|  meanWlife|
|-----:|----------:|---------:|----------:|
|  1952|   3725.276|  49.05762|   182753.2|
|  1957|   4299.408|  51.50740|   221451.4|
|  1962|   4725.812|  53.60925|   253347.3|
|  1967|   5483.653|  55.67829|   305320.4|
|  1972|   6770.083|  57.64739|   390277.6|
|  1977|   7313.166|  59.57016|   435646.5|
|  1982|   7518.902|  61.53320|   462662.1|
|  1987|   7900.920|  63.21261|   499437.8|
|  1992|   8158.609|  64.16034|   523459.1|
|  1997|   9090.175|  65.01468|   590994.8|
|  2002|   9917.848|  65.69492|   651552.3|
|  2007|  11680.072|  67.00742|   782651.5|

After creating this table I realized how hard it was to interpret the weighted life expectancy because of gdp per capita being so large. So instead I decided to weight life expectancy by the z-scores of gdp per capita.

|  year|    meangdp|  meanscaledgdp|  meanLife|   meanWLife|
|-----:|----------:|--------------:|---------:|-----------:|
|  1952|   3725.276|     -0.3540520|  49.05762|  -14.177437|
|  1957|   4299.408|     -0.2958085|  51.50740|  -11.542735|
|  1962|   4725.812|     -0.2525515|  53.60925|   -9.491577|
|  1967|   5483.653|     -0.1756715|  55.67829|   -5.192780|
|  1972|   6770.083|     -0.0451683|  57.64739|    2.990565|
|  1977|   7313.166|      0.0099254|  59.57016|    6.453591|
|  1982|   7518.902|      0.0307964|  61.53320|    7.959544|
|  1987|   7900.920|      0.0695507|  63.21261|   11.005671|
|  1992|   8158.609|      0.0956922|  64.16034|   13.338016|
|  1997|   9090.175|      0.1901960|  65.01468|   20.699275|
|  2002|   9917.848|      0.2741602|  65.69492|   27.418707|
|  2007|  11680.072|      0.4529308|  67.00742|   40.963615|

This makes it a bit easier to read. Note: the weighted variable was created prior to the summarized table of means so the meanWLife is not equal to the meanscaledgdp X meanLife.

After creating this table, I realized that the intrepretation is still a bit tricky because gdp and lifeExp increase with time even with a scaled gdp factored in.

Here is a plot to make things clearer:

``` r
gapminder %>% 
   mutate(Scalegdp=((gdpPercap-mean(gdpPercap))/sd(gdpPercap))) %>%
   mutate(WLife= ((gdpPercap-mean(gdpPercap))/sd(gdpPercap)) * lifeExp) %>%
   group_by(year) %>%
   summarize(meangdp =mean(gdpPercap), meanscaledgdp =mean(Scalegdp), meanLife= mean(lifeExp), meanWLife =mean(WLife)) %>% 
   ggplot(aes(x=year, y=meanWLife)) +
   geom_line(alpha=0.5, shape=21) + 
   labs(x="Year", 
          y="Weighted Life Expectancy",
          title="Life Expectancy Weighted by GDP per capita")
```

    ## Warning: Ignoring unknown parameters: shape

![](hw3_gapminder_exploration_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-12-1.png)

Well this is kind of boring but it does satify the "one graph for one idea" criteria. Even after accounting for GDP per capita, we see a steady increase of life expectancy as time goes on.

### Task 4: Report the absolute and/or relative abundance of countries with low life expectancy over time by continent: Compute some measure of worldwide life expectancy – you decide – a mean or median or some other quantile or perhaps your current age. Then determine how many countries on each continent have a life expectancy less than this benchmark, for each year.

I decided to compute the number of countries within each continent which have a median life expectancy below 40
---------------------------------------------------------------------------------------------------------------
