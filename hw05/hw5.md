Homework 5
================

I decided to work with the singer dataset for a change :smile:

Factor Management
-----------------

### Factorize

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
