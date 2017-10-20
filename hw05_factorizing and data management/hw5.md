Homework 5
================

I decided to work with the singer dataset for a change :smile:

Factor Management
-----------------

**Factorize.** Transform some of the variable in the `singer_locations` dataframe into factors: pay attention at what levels you introduce and their order. Try and consider the difference between the base R `as.factor` and the `forcats`-provided functions.

First I just want to inspect the data:

``` r
data("singer_locations")
kable(head(singer_locations))
```

| track\_id          | title                 | song\_id           | release             | artist\_id         | artist\_name                   |  year|  duration|  artist\_hotttnesss|  artist\_familiarity|  latitude|  longitude| name          | city         |
|:-------------------|:----------------------|:-------------------|:--------------------|:-------------------|:-------------------------------|-----:|---------:|-------------------:|--------------------:|---------:|----------:|:--------------|:-------------|
| TRWICRA128F42368DB | The Conversation (Cd) | SOSURTI12A81C22FB8 | Even If It Kills Me | ARACDPV1187FB58DF4 | Motion City Soundtrack         |  2007|  170.4485|           0.6410183|            0.8230522|        NA|         NA| NA            | NA           |
| TRXJANY128F42246FC | Lonely Island         | SODESQP12A6D4F98EF | The Duke Of Earl    | ARYBUAO1187FB3F4EB | Gene Chandler                  |  2004|  106.5530|           0.3937627|            0.5700167|  41.88415|  -87.63241| Gene Chandler | Chicago, IL  |
| TRIKPCA128F424A553 | Here's That Rainy Day | SOQUYQD12A8C131619 | Imprompture         | AR4111G1187B9B58AB | Paul Horn                      |  1998|  527.5947|           0.4306226|            0.5039940|  40.71455|  -74.00712| Paul Horn     | New York, NY |
| TRYEATD128F92F87C9 | Rego Park Blues       | SOEZGRC12AB017F1AC | Still River         | ARQDZP31187B98D623 | Ronnie Earl & the Broadcasters |  1995|  695.1179|           0.3622792|            0.4773099|        NA|         NA| NA            | NA           |
| TRBYYXH128F4264585 | Games                 | SOPIOCP12A8C13A322 | Afro-Harping        | AR75GYU1187B9AE47A | Dorothy Ashby                  |  1968|  237.3220|           0.4107520|            0.5303468|  42.33168|  -83.04792| Dorothy Ashby | Detroit, MI  |
| TRKFFKR128F9303AE3 | More Pipes            | SOHQSPY12AB0181325 | Six Yanks           | ARCENE01187B9AF929 | Barleyjuice                    |  2006|  192.9400|           0.3762635|            0.5412950|  40.99471|  -77.60454| Barleyjuice   | Pennsylvania |

First I tried to factorize city with the but that didn't work. This seems to be due to the existance of NA values. (Here I presented the code as a block quote since knitr wont render a file with code errors.)

> sl\_fac &lt;-singer\_locations %&gt;% mutate(city\_factor = as\_factor(city))

> Output: Error in mutate\_impl(.data, dots) : Evaluation error: `idx` must contain one integer for each level of `f`.

Remove NA's and then run:

``` r
singer_locations %>% 
  filter(!is.na(city)) %>% 
  mutate(city_factor = as_factor(city)) 
```

    ## Warning: package 'bindrcpp' was built under R version 3.3.2

    ## # A tibble: 4,129 x 15
    ##              track_id                            title            song_id
    ##                 <chr>                            <chr>              <chr>
    ##  1 TRXJANY128F42246FC                    Lonely Island SODESQP12A6D4F98EF
    ##  2 TRIKPCA128F424A553            Here's That Rainy Day SOQUYQD12A8C131619
    ##  3 TRBYYXH128F4264585                            Games SOPIOCP12A8C13A322
    ##  4 TRKFFKR128F9303AE3                       More Pipes SOHQSPY12AB0181325
    ##  5 TRWKTVW12903CE5ACF                      Indian Deli SOGYBYQ12AB0188586
    ##  6 TRUWFXF128E0795D22                    Miss Gorgeous SOTEIQB12A6702048D
    ##  7 TRYKVFW128F4243264                      Lahainaluna SOUZVTG12A8C1308FB
    ##  8 TRUNSOU12903CC52BD         The Ingenue (LP Version) SOJESNI12AB0186408
    ##  9 TRBNFTT128F92FB599 The Unquiet Grave (Child No. 78) SOTSNHW12AB0182A9D
    ## 10 TREGTHP128F4286994                       The Breaks SORKAVQ12A8C137E9C
    ## # ... with 4,119 more rows, and 12 more variables: release <chr>,
    ## #   artist_id <chr>, artist_name <chr>, year <int>, duration <dbl>,
    ## #   artist_hotttnesss <dbl>, artist_familiarity <dbl>, latitude <dbl>,
    ## #   longitude <dbl>, name <chr>, city <chr>, city_factor <fctr>

``` r
kable(head(singer_locations %>% 
  filter(!is.na(city)) %>% 
  mutate(city_factor = as_factor(city)) ))
```

| track\_id          | title                 | song\_id           | release                            | artist\_id         | artist\_name                                |  year|  duration|  artist\_hotttnesss|  artist\_familiarity|  latitude|   longitude| name                     | city         | city\_factor |
|:-------------------|:----------------------|:-------------------|:-----------------------------------|:-------------------|:--------------------------------------------|-----:|---------:|-------------------:|--------------------:|---------:|-----------:|:-------------------------|:-------------|:-------------|
| TRXJANY128F42246FC | Lonely Island         | SODESQP12A6D4F98EF | The Duke Of Earl                   | ARYBUAO1187FB3F4EB | Gene Chandler                               |  2004|  106.5530|           0.3937627|            0.5700167|  41.88415|   -87.63241| Gene Chandler            | Chicago, IL  | Chicago, IL  |
| TRIKPCA128F424A553 | Here's That Rainy Day | SOQUYQD12A8C131619 | Imprompture                        | AR4111G1187B9B58AB | Paul Horn                                   |  1998|  527.5947|           0.4306226|            0.5039940|  40.71455|   -74.00712| Paul Horn                | New York, NY | New York, NY |
| TRBYYXH128F4264585 | Games                 | SOPIOCP12A8C13A322 | Afro-Harping                       | AR75GYU1187B9AE47A | Dorothy Ashby                               |  1968|  237.3220|           0.4107520|            0.5303468|  42.33168|   -83.04792| Dorothy Ashby            | Detroit, MI  | Detroit, MI  |
| TRKFFKR128F9303AE3 | More Pipes            | SOHQSPY12AB0181325 | Six Yanks                          | ARCENE01187B9AF929 | Barleyjuice                                 |  2006|  192.9400|           0.3762635|            0.5412950|  40.99471|   -77.60454| Barleyjuice              | Pennsylvania | Pennsylvania |
| TRWKTVW12903CE5ACF | Indian Deli           | SOGYBYQ12AB0188586 | Beat Konducta Vol. 3 & 4: In India | AR17D2T1187FB4DBC2 | Madlib                                      |  2007|  107.7808|           0.5339732|            0.7640263|  34.20034|  -119.18044| Madlib                   | Oxnard, CA   | Oxnard, CA   |
| TRUWFXF128E0795D22 | Miss Gorgeous         | SOTEIQB12A6702048D | Music Monks                        | ARDNZL61187B98F42D | Seeed's Pharaoh Riddim Feat. General Degree |  2003|  195.9702|           0.4800612|            0.3086738|  50.73230|     7.10169| Seeed feat. Elephant Man | Bonn         | Bonn         |

Before deciding to remove NA's I'll just use `forcats` since we probably don't want to be reordering our factor anyway.

``` r
sl_fac <- singer_locations %>% 
  mutate(city_factor = factor(city))
kable(head(sl_fac))
```

| track\_id          | title                 | song\_id           | release             | artist\_id         | artist\_name                   |  year|  duration|  artist\_hotttnesss|  artist\_familiarity|  latitude|  longitude| name          | city         | city\_factor |
|:-------------------|:----------------------|:-------------------|:--------------------|:-------------------|:-------------------------------|-----:|---------:|-------------------:|--------------------:|---------:|----------:|:--------------|:-------------|:-------------|
| TRWICRA128F42368DB | The Conversation (Cd) | SOSURTI12A81C22FB8 | Even If It Kills Me | ARACDPV1187FB58DF4 | Motion City Soundtrack         |  2007|  170.4485|           0.6410183|            0.8230522|        NA|         NA| NA            | NA           | NA           |
| TRXJANY128F42246FC | Lonely Island         | SODESQP12A6D4F98EF | The Duke Of Earl    | ARYBUAO1187FB3F4EB | Gene Chandler                  |  2004|  106.5530|           0.3937627|            0.5700167|  41.88415|  -87.63241| Gene Chandler | Chicago, IL  | Chicago, IL  |
| TRIKPCA128F424A553 | Here's That Rainy Day | SOQUYQD12A8C131619 | Imprompture         | AR4111G1187B9B58AB | Paul Horn                      |  1998|  527.5947|           0.4306226|            0.5039940|  40.71455|  -74.00712| Paul Horn     | New York, NY | New York, NY |
| TRYEATD128F92F87C9 | Rego Park Blues       | SOEZGRC12AB017F1AC | Still River         | ARQDZP31187B98D623 | Ronnie Earl & the Broadcasters |  1995|  695.1179|           0.3622792|            0.4773099|        NA|         NA| NA            | NA           | NA           |
| TRBYYXH128F4264585 | Games                 | SOPIOCP12A8C13A322 | Afro-Harping        | AR75GYU1187B9AE47A | Dorothy Ashby                  |  1968|  237.3220|           0.4107520|            0.5303468|  42.33168|  -83.04792| Dorothy Ashby | Detroit, MI  | Detroit, MI  |
| TRKFFKR128F9303AE3 | More Pipes            | SOHQSPY12AB0181325 | Six Yanks           | ARCENE01187B9AF929 | Barleyjuice                    |  2006|  192.9400|           0.3762635|            0.5412950|  40.99471|  -77.60454| Barleyjuice   | Pennsylvania | Pennsylvania |

**Drop 0.** Filter the `singer_locations` data to remove observations associated with the uncorrectly inputed `year` 0. Additionally, remove unused factor levels. Provide concrete information on the data before and after removing these rows and levels; address the number of rows and the levels of the affected factors.

First I removed any data with the year 0: Prior to removal there were 10100 observations

``` r
str(sl_fac)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    10100 obs. of  15 variables:
    ##  $ track_id          : chr  "TRWICRA128F42368DB" "TRXJANY128F42246FC" "TRIKPCA128F424A553" "TRYEATD128F92F87C9" ...
    ##  $ title             : chr  "The Conversation (Cd)" "Lonely Island" "Here's That Rainy Day" "Rego Park Blues" ...
    ##  $ song_id           : chr  "SOSURTI12A81C22FB8" "SODESQP12A6D4F98EF" "SOQUYQD12A8C131619" "SOEZGRC12AB017F1AC" ...
    ##  $ release           : chr  "Even If It Kills Me" "The Duke Of Earl" "Imprompture" "Still River" ...
    ##  $ artist_id         : chr  "ARACDPV1187FB58DF4" "ARYBUAO1187FB3F4EB" "AR4111G1187B9B58AB" "ARQDZP31187B98D623" ...
    ##  $ artist_name       : chr  "Motion City Soundtrack" "Gene Chandler" "Paul Horn" "Ronnie Earl & the Broadcasters" ...
    ##  $ year              : int  2007 2004 1998 1995 1968 2006 2003 2007 1966 2006 ...
    ##  $ duration          : num  170 107 528 695 237 ...
    ##  $ artist_hotttnesss : num  0.641 0.394 0.431 0.362 0.411 ...
    ##  $ artist_familiarity: num  0.823 0.57 0.504 0.477 0.53 ...
    ##  $ latitude          : num  NA 41.9 40.7 NA 42.3 ...
    ##  $ longitude         : num  NA -87.6 -74 NA -83 ...
    ##  $ name              : chr  NA "Gene Chandler" "Paul Horn" NA ...
    ##  $ city              : chr  NA "Chicago, IL" "New York, NY" NA ...
    ##  $ city_factor       : Factor w/ 1316 levels "?, Illinois",..: NA 225 804 NA 305 910 NA NA NA NA ...

But after there were only 1000 observations

``` r
filter(sl_fac, year != "0") %>% 
    str(sl_fac)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    10000 obs. of  15 variables:

    ## Warning in Ops.factor(left, right): '<' not meaningful for factors

    ##  $ track_id          : chr  "TRWICRA128F42368DB" "TRXJANY128F42246FC" "TRIKPCA128F424A553" "TRYEATD128F92F87C9" ...
    ##  $ title             : chr  "The Conversation (Cd)" "Lonely Island" "Here's That Rainy Day" "Rego Park Blues" ...
    ##  $ song_id           : chr  "SOSURTI12A81C22FB8" "SODESQP12A6D4F98EF" "SOQUYQD12A8C131619" "SOEZGRC12AB017F1AC" ...
    ##  $ release           : chr  "Even If It Kills Me" "The Duke Of Earl" "Imprompture" "Still River" ...
    ##  $ artist_id         : chr  "ARACDPV1187FB58DF4" "ARYBUAO1187FB3F4EB" "AR4111G1187B9B58AB" "ARQDZP31187B98D623" ...
    ##  $ artist_name       : chr  "Motion City Soundtrack" "Gene Chandler" "Paul Horn" "Ronnie Earl & the Broadcasters" ...
    ##  $ year              : int  2007 2004 1998 1995 1968 2006 2003 2007 1966 2006 ...
    ##  $ duration          : num  170 107 528 695 237 ...
    ##  $ artist_hotttnesss : num  0.641 0.394 0.431 0.362 0.411 ...
    ##  $ artist_familiarity: num  0.823 0.57 0.504 0.477 0.53 ...
    ##  $ latitude          : num  NA 41.9 40.7 NA 42.3 ...
    ##  $ longitude         : num  NA -87.6 -74 NA -83 ...
    ##  $ name              : chr  NA "Gene Chandler" "Paul Horn" NA ...
    ##  $ city              : chr  NA "Chicago, IL" "New York, NY" NA ...
    ##  $ city_factor       : Factor w/ 1316 levels "?, Illinois",..: NA 225 804 NA 305 910 NA NA NA NA ...

Then I removed any unused factor levels- NA values for `city_factor`.

``` r
sl_fac %>% 
    filter(!is.na(city)) %>% 
  str(sl_fac)
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    4129 obs. of  15 variables:

    ## Warning in Ops.factor(left, right): '<' not meaningful for factors

    ##  $ track_id          : chr  "TRXJANY128F42246FC" "TRIKPCA128F424A553" "TRBYYXH128F4264585" "TRKFFKR128F9303AE3" ...
    ##  $ title             : chr  "Lonely Island" "Here's That Rainy Day" "Games" "More Pipes" ...
    ##  $ song_id           : chr  "SODESQP12A6D4F98EF" "SOQUYQD12A8C131619" "SOPIOCP12A8C13A322" "SOHQSPY12AB0181325" ...
    ##  $ release           : chr  "The Duke Of Earl" "Imprompture" "Afro-Harping" "Six Yanks" ...
    ##  $ artist_id         : chr  "ARYBUAO1187FB3F4EB" "AR4111G1187B9B58AB" "AR75GYU1187B9AE47A" "ARCENE01187B9AF929" ...
    ##  $ artist_name       : chr  "Gene Chandler" "Paul Horn" "Dorothy Ashby" "Barleyjuice" ...
    ##  $ year              : int  2004 1998 1968 2006 2007 2003 2003 1989 1964 2008 ...
    ##  $ duration          : num  107 528 237 193 108 ...
    ##  $ artist_hotttnesss : num  0.394 0.431 0.411 0.376 0.534 ...
    ##  $ artist_familiarity: num  0.57 0.504 0.53 0.541 0.764 ...
    ##  $ latitude          : num  41.9 40.7 42.3 41 34.2 ...
    ##  $ longitude         : num  -87.6 -74 -83 -77.6 -119.2 ...
    ##  $ name              : chr  "Gene Chandler" "Paul Horn" "Dorothy Ashby" "Barleyjuice" ...
    ##  $ city              : chr  "Chicago, IL" "New York, NY" "Detroit, MI" "Pennsylvania" ...
    ##  $ city_factor       : Factor w/ 1316 levels "?, Illinois",..: 225 804 305 910 891 120 461 645 1103 938 ...

Now there are only 4129 observations but with 1316 factor levels for city\_factor.

In examining the data though there are a few odd factors like "?, Illinois, 020, 27, 310 Lousiana, 732 New Jersey" I decided to remove these as well.

``` r
sl_new <- (sl_fac %>% 
filter( city_factor != "?, Illinois")  %>% 
  filter( city_factor != "020") %>% 
  filter( city_factor != "310, Louisiana") %>% 
  filter( city_factor != "732, NEW JERSEY, USA") %>% 
  filter( city_factor != "27")) 
    str(sl_new) 
```

    ## Classes 'tbl_df', 'tbl' and 'data.frame':    4122 obs. of  15 variables:
    ##  $ track_id          : chr  "TRXJANY128F42246FC" "TRIKPCA128F424A553" "TRBYYXH128F4264585" "TRKFFKR128F9303AE3" ...
    ##  $ title             : chr  "Lonely Island" "Here's That Rainy Day" "Games" "More Pipes" ...
    ##  $ song_id           : chr  "SODESQP12A6D4F98EF" "SOQUYQD12A8C131619" "SOPIOCP12A8C13A322" "SOHQSPY12AB0181325" ...
    ##  $ release           : chr  "The Duke Of Earl" "Imprompture" "Afro-Harping" "Six Yanks" ...
    ##  $ artist_id         : chr  "ARYBUAO1187FB3F4EB" "AR4111G1187B9B58AB" "AR75GYU1187B9AE47A" "ARCENE01187B9AF929" ...
    ##  $ artist_name       : chr  "Gene Chandler" "Paul Horn" "Dorothy Ashby" "Barleyjuice" ...
    ##  $ year              : int  2004 1998 1968 2006 2007 2003 2003 1989 1964 2008 ...
    ##  $ duration          : num  107 528 237 193 108 ...
    ##  $ artist_hotttnesss : num  0.394 0.431 0.411 0.376 0.534 ...
    ##  $ artist_familiarity: num  0.57 0.504 0.53 0.541 0.764 ...
    ##  $ latitude          : num  41.9 40.7 42.3 41 34.2 ...
    ##  $ longitude         : num  -87.6 -74 -83 -77.6 -119.2 ...
    ##  $ name              : chr  "Gene Chandler" "Paul Horn" "Dorothy Ashby" "Barleyjuice" ...
    ##  $ city              : chr  "Chicago, IL" "New York, NY" "Detroit, MI" "Pennsylvania" ...
    ##  $ city_factor       : Factor w/ 1316 levels "?, Illinois",..: 225 804 305 910 891 120 461 645 1103 938 ...

The structure now indicates that there are only 4122 observations. However, it does still list ?, Illinois. Just to check I tried to call up one of the removed items.

``` r
sl_new %>% 
filter(city_factor == "?, Illinois") 
```

    ## # A tibble: 0 x 15
    ## # ... with 15 variables: track_id <chr>, title <chr>, song_id <chr>,
    ## #   release <chr>, artist_id <chr>, artist_name <chr>, year <int>,
    ## #   duration <dbl>, artist_hotttnesss <dbl>, artist_familiarity <dbl>,
    ## #   latitude <dbl>, longitude <dbl>, name <chr>, city <chr>,
    ## #   city_factor <fctr>

It did indead remove the value but I guess it still remembers it as a factor that did exist at one point.

**Reorder the levels of `year`, `artist_name` or `title`.** Use the forcats package to change the order of the factor levels, based on a principled summary of one of the quantitative variables. Consider experimenting with a summary statistic beyond the most basic choice of the median.
