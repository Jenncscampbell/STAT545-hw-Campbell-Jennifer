Home Work 4
================

Activity \#3
------------

1.  Compute the mean life expectancy for all possible combinations of continent and year.

``` r
gapminder %>% 
  group_by(continent, year) %>% 
  summarize(Mean_lifeExp=mean(lifeExp))
```

    ## # A tibble: 60 x 3
    ## # Groups:   continent [?]
    ##    continent  year Mean_lifeExp
    ##       <fctr> <int>        <dbl>
    ##  1    Africa  1952     39.13550
    ##  2    Africa  1957     41.26635
    ##  3    Africa  1962     43.31944
    ##  4    Africa  1967     45.33454
    ##  5    Africa  1972     47.45094
    ##  6    Africa  1977     49.58042
    ##  7    Africa  1982     51.59287
    ##  8    Africa  1987     53.34479
    ##  9    Africa  1992     53.62958
    ## 10    Africa  1997     53.59827
    ## # ... with 50 more rows

1.  Reshape that to have one row per continent and one variable per year.

``` r
gapminder %>% 
  group_by(continent, year) %>% 
  summarize(Mean_lifeExp=mean(lifeExp)) %>% 
  spread(year, Mean_lifeExp)
```

    ## # A tibble: 5 x 13
    ## # Groups:   continent [5]
    ##   continent   `1952`   `1957`   `1962`   `1967`   `1972`   `1977`   `1982`
    ## *    <fctr>    <dbl>    <dbl>    <dbl>    <dbl>    <dbl>    <dbl>    <dbl>
    ## 1    Africa 39.13550 41.26635 43.31944 45.33454 47.45094 49.58042 51.59287
    ## 2  Americas 53.27984 55.96028 58.39876 60.41092 62.39492 64.39156 66.22884
    ## 3      Asia 46.31439 49.31854 51.56322 54.66364 57.31927 59.61056 62.61794
    ## 4    Europe 64.40850 66.70307 68.53923 69.73760 70.77503 71.93777 72.80640
    ## 5   Oceania 69.25500 70.29500 71.08500 71.31000 71.91000 72.85500 74.29000
    ## # ... with 5 more variables: `1987` <dbl>, `1992` <dbl>, `1997` <dbl>,
    ## #   `2002` <dbl>, `2007` <dbl>

This actually looks really ugly so I think I'll do it by one row per year and one variable for each continent.

``` r
gapminder %>% 
  group_by(continent, year) %>% 
  summarize(Mean_lifeExp=mean(lifeExp)) %>% 
  spread(continent, Mean_lifeExp)
```

    ## # A tibble: 12 x 6
    ##     year   Africa Americas     Asia   Europe Oceania
    ##  * <int>    <dbl>    <dbl>    <dbl>    <dbl>   <dbl>
    ##  1  1952 39.13550 53.27984 46.31439 64.40850 69.2550
    ##  2  1957 41.26635 55.96028 49.31854 66.70307 70.2950
    ##  3  1962 43.31944 58.39876 51.56322 68.53923 71.0850
    ##  4  1967 45.33454 60.41092 54.66364 69.73760 71.3100
    ##  5  1972 47.45094 62.39492 57.31927 70.77503 71.9100
    ##  6  1977 49.58042 64.39156 59.61056 71.93777 72.8550
    ##  7  1982 51.59287 66.22884 62.61794 72.80640 74.2900
    ##  8  1987 53.34479 68.09072 64.85118 73.64217 75.3200
    ##  9  1992 53.62958 69.56836 66.53721 74.44010 76.9450
    ## 10  1997 53.59827 71.15048 68.02052 75.50517 78.1900
    ## 11  2002 53.32523 72.42204 69.23388 76.70060 79.7400
    ## 12  2007 54.80604 73.60812 70.72848 77.64860 80.7195

1.  Use knitr::kable() to make these tables look pretty in your rendered homework.

``` r
kable(gapminder %>% 
  group_by(continent, year) %>% 
  summarize(Mean_lifeExp=mean(lifeExp)) %>% 
  spread(continent, Mean_lifeExp))
```

|  year|    Africa|  Americas|      Asia|    Europe|  Oceania|
|-----:|---------:|---------:|---------:|---------:|--------:|
|  1952|  39.13550|  53.27984|  46.31439|  64.40850|  69.2550|
|  1957|  41.26635|  55.96028|  49.31854|  66.70307|  70.2950|
|  1962|  43.31944|  58.39876|  51.56322|  68.53923|  71.0850|
|  1967|  45.33454|  60.41092|  54.66364|  69.73760|  71.3100|
|  1972|  47.45094|  62.39492|  57.31927|  70.77503|  71.9100|
|  1977|  49.58042|  64.39156|  59.61056|  71.93777|  72.8550|
|  1982|  51.59287|  66.22884|  62.61794|  72.80640|  74.2900|
|  1987|  53.34479|  68.09072|  64.85118|  73.64217|  75.3200|
|  1992|  53.62958|  69.56836|  66.53721|  74.44010|  76.9450|
|  1997|  53.59827|  71.15048|  68.02052|  75.50517|  78.1900|
|  2002|  53.32523|  72.42204|  69.23388|  76.70060|  79.7400|
|  2007|  54.80604|  73.60812|  70.72848|  77.64860|  80.7195|

1.  Is there a plot that is easier to make with the data in this shape versis the usual form? If so (or you think so), try it! Reflect. It is not immediately inutitive how to plot this all on one graph. It is easy to say do year and the mean life expectancy for one continent, like here I did it for Africa. I had to change the axis names since it defaulted to just say Africa (our column title) which is really uninformative.

``` r
gapminder %>% 
  group_by(continent, year) %>% 
  summarize(Mean_lifeExp=mean(lifeExp)) %>% 
  spread(continent, Mean_lifeExp) %>% 
  ggplot(aes(x = year,y = Africa)) + 
  geom_point() +
  geom_smooth(alpha=0.5) + 
  labs(x="Year", 
          y="Mean Life Expectancy",
          title="Mean Life Expectancy Africa Over Time")
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](hw4_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-6-1.png)

I did realize that one cool thing that you can do with this is plot countries life expectancies against each other. But I'm not sure that it is easy for readers to interpret since this is data by year but the graph in now way tells you that

``` r
gapminder %>% 
  group_by(continent, year) %>% 
  summarize(Mean_lifeExp=mean(lifeExp)) %>% 
  spread(continent, Mean_lifeExp) %>% 
  ggplot(aes(x = Asia,y = Africa)) + 
  geom_point() +
  geom_smooth(alpha=0.5) + 
  labs(x="Mean life expectancy of Asia", 
          y="Mean Life Expectancy of Africa",
          title="Mean Life Expectancy of Asia and Africa")
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](hw4_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-7-1.png) I then remembered that I could convey the years by color though. At least that is a less misleading graph.

``` r
gapminder %>% 
  group_by(continent, year) %>% 
  summarize(Mean_lifeExp=mean(lifeExp)) %>% 
  spread(continent, Mean_lifeExp) %>% 
  ggplot(aes(x = Asia,y = Africa)) + 
  geom_point(mapping= aes(colour= year), alpha=0.5, size=2) +
  geom_smooth(alpha=0.5, size=.5, se = FALSE, color= "pink") + 
  labs(x="Mean life expectancy of Asia", 
          y="Mean Life Expectancy of Africa",
          title="Mean Life Expectancy of Asia and Africa")
```

    ## `geom_smooth()` using method = 'loess' and formula 'y ~ x'

![](hw4_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-8-1.png)

Finally, to get it all on a single I resorted to adding a geom\_point for each continent. It is really inefficient coding. I feel like this really only works because there are only five continents, if there were more then this would be a nightmare.

``` r
gapminder %>% 
  group_by(continent, year) %>% 
  summarize(Mean_lifeExp=mean(lifeExp)) %>% 
  spread(continent, Mean_lifeExp) %>% 
  ggplot(aes(x = year )) + 
  geom_point(aes(y = Asia, colour ="Asia")) +
  geom_point(aes(y = Europe, colour ="Europe")) +
  geom_point(aes(y = Africa, colour ="Africa")) +
  geom_point(aes(y = Oceania, colour ="Oceania")) +
  geom_point(aes(y = Americas, colour ="Americas")) +
  labs(x="Year", 
          y="Mean Life Expectancy",
          title="Mean Life Expectancy Across Time")
```

![](hw4_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-9-1.png)
