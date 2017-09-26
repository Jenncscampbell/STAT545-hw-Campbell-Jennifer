Gapminder Exploration
================
JC
2017-09-25

Smell test the data
-------------------

We can see from the `structure` command that GapMinder is a data.frame

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    1704 obs. of  6 variables:
    ##  $ country  : Factor w/ 142 levels "Afghanistan",..: 1 1 1 1 1 1 1 1 1 1 ...
    ##  $ continent: Factor w/ 5 levels "Africa","Americas",..: 3 3 3 3 3 3 3 3 3 3 ...
    ##  $ year     : int  1952 1957 1962 1967 1972 1977 1982 1987 1992 1997 ...
    ##  $ lifeExp  : num  28.8 30.3 32 34 36.1 ...
    ##  $ pop      : int  8425333 9240934 10267083 11537966 13079460 14880372 12881816 13867957 16317921 22227415 ...
    ##  $ gdpPercap: num  779 821 853 836 740 ...

We see that Gapminder is a tibble data frame.

``` r
class(gapminder)
```

    ## [1] "tbl_df"     "tbl"        "data.frame"

GapMinder has 6 columns (variables) and 1704 rows of data.

    ## [1] 6

    ## [1] 1704

Another way to get this information about extent and size is to use the `dim` function. This will give the dimensions in a single line of code which may save you time.

    ## [1] 1704    6

If you just want the number of variables, you could also use the `str` funciton (demonstrated above). The first line of output tells you the number of observations and variables. The `length` funciton (below) will give the number of variables

    ## [1] 6

Also if you just type in "gampminder" you will get a data preview which will give you all the variables and their names and tell you the number of rows and tell you the type of each variable.

    ## # A tibble: 1,704 x 6
    ##        country continent  year lifeExp      pop gdpPercap
    ##         <fctr>    <fctr> <int>   <dbl>    <int>     <dbl>
    ##  1 Afghanistan      Asia  1952  28.801  8425333  779.4453
    ##  2 Afghanistan      Asia  1957  30.332  9240934  820.8530
    ##  3 Afghanistan      Asia  1962  31.997 10267083  853.1007
    ##  4 Afghanistan      Asia  1967  34.020 11537966  836.1971
    ##  5 Afghanistan      Asia  1972  36.088 13079460  739.9811
    ##  6 Afghanistan      Asia  1977  38.438 14880372  786.1134
    ##  7 Afghanistan      Asia  1982  39.854 12881816  978.0114
    ##  8 Afghanistan      Asia  1987  40.822 13867957  852.3959
    ##  9 Afghanistan      Asia  1992  41.674 16317921  649.3414
    ## 10 Afghanistan      Asia  1997  41.763 22227415  635.3414
    ## # ... with 1,694 more rows

At the top of each row we can view the data type of each variable: | **Variable** | **Data Type** | |-----------------|------------| | Country | Factor | | Continent | Factor | | Year | Integer | | LifeExp | Double | | Pop | Integer | | GdpPercap | Double |

Explore individual variables
----------------------------

Here I will explore the variables Continent, year and life expectancy

|     |   continent  |     year     |    lifeExp    |
|-----|:------------:|:------------:|:-------------:|
|     |  Africa :624 |  Min. :1952  |  Min. :23.60  |
|     | Americas:300 | 1st Qu.:1966 | 1st Qu.:48.20 |
|     |   Asia :396  | Median :1980 | Median :60.71 |
|     |  Europe :360 |  Mean :1980  |  Mean :59.47  |
|     | Oceania : 24 | 3rd Qu.:1993 | 3rd Qu.:70.85 |
|     |      NA      |  Max. :2007  |  Max. :82.60  |

From this output we can see that Continent has 6 possible values with Africa having the most data points and Oceania having the least. The Year variable tells us that the data was collected between 1952 and 2007 with the mean year being 1980, the distribution of years is relatively uniform. The mean life expectancy across regions and years was 59.47 with a range between 23.60 and 82.60.

To better see the distribution of Life Expectancy, I created a histogram ![](Gapminder_explore_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-9-1.png)

This distribution shows a negative skew.

To explore the variable country, I asked for a summary. From this summary, we can see that each country has 12 data points with data being collected from 142 countries.

    ## # A tibble: 142 x 2
    ##        country `n_distinct(year)`
    ##         <fctr>              <int>
    ##  1 Afghanistan                 12
    ##  2     Albania                 12
    ##  3     Algeria                 12
    ##  4      Angola                 12
    ##  5   Argentina                 12
    ##  6   Australia                 12
    ##  7     Austria                 12
    ##  8     Bahrain                 12
    ##  9  Bangladesh                 12
    ## 10     Belgium                 12
    ## # ... with 132 more rows

Explore various plot types
--------------------------

![](Gapminder_explore_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-11-1.png)

This plot between population and year seems to be quite interesting. This plot seems to reveal that there are two distinct sub populations here. We see that the vast majority of data points have a low population regarless of year but a few data points show a drastic increase in population over just a few years.

To further explore this, I created a plot of the population over years for China and Canada. Here we can more easily see how population has grown over the years differently across these two countries

![](Gapminder_explore_files/figure-markdown_github-ascii_identifiers/unnamed-chunk-12-1.png)

To explore the population
