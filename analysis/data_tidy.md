Site Fidelity and Inter-pool Movement of Spotted Salamanders by the Sea
================
Georgia Lattig
02/25/24

## Packages and Data

``` r
op15 <- read_csv("/cloud/project/data/otter point - 2015.csv")
op16 <- read_csv("/cloud/project/data/otter point - 2016.csv")
op17 <- read_csv("/cloud/project/data/otter point - 2017.csv")
op18 <- read_csv("/cloud/project/data/otter point - 2018.csv")
op19 <- read_csv("/cloud/project/data/otter point - 2019.csv")
op20 <- read_csv("/cloud/project/data/otter point - 2020.csv")
op21 <- read_csv("/cloud/project/data/otter point - 2021.csv")
op22 <- read_csv("/cloud/project/data/otter point - 2022.csv")
sals22 <- read_csv("/cloud/project/data/otter point - 2022_sals.csv")
op23 <- read_csv("/cloud/project/data/otter point - 2023.csv")
```

## Data Tidying

``` r
op15 <- op15 %>% 
  rename(
    date = `Date`,
    pool = `Pool Number`,
    salinity = `Salinity (ppt)`,
    salinity2 = `Second Salinity Noted (lower)`,
    pool_temp = `Temperature (C)`,
    total = Total,
    unmarked = Unmarked,
    yellow = `Yellow (2017)`,
    pink = `Pink (2018)`,
    orange = `Orange (2019)`,
    red = `Red (2021/2020)`,
    dead = `Dead Individuals`,
    eggs = `Eggmasses present`,
    notes = ...14
  )

op15 <- op15 %>% 
  mutate(date = as.Date(date, "%m/%d/%Y")) %>% 
  mutate(pool = as.character(pool)) %>% 
  mutate(salinity = case_when(
    salinity == "0.1 - 0.2" ~ "0.1",
    .default = salinity)) %>%  ## One observation was recorded as a range 0.1-0.2 so I changed it to 0.1
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(salinity2 = as.numeric(salinity2)) %>% 
  mutate(pool_temp = as.numeric(pool_temp)) %>% 
  mutate(total = as.numeric(total)) %>% 
  mutate(unmarked = as.numeric(unmarked)) %>% 
  mutate(yellow = as.numeric(yellow)) %>% 
  mutate(pink = as.numeric(pink)) %>% 
  mutate(orange = as.numeric(orange)) %>% 
  mutate(red = as.numeric(red)) %>% 
  mutate(dead = as.numeric(dead)) %>% 
  mutate(eggs = as.numeric(eggs)) %>% 
  mutate(notes = as.character(notes))

op15 <- op15 %>% 
  subset(select = -c(eggs, notes)) # I am dropping the eggs variable because the data were recorded in different ways across seasons and because I do not need it for the questions I am interested in asking 
```

``` r
op16 <- op16 %>% 
  rename(
    date = `Date`,
    pool = `Pool Number`,
    salinity = `Salinity (ppt)`,
    salinity2 = `Second Salinity Noted (lower)`,
    pool_temp = `Temperature (C)`,
    total = Total,
    unmarked = Unmarked,
    yellow = `Yellow (2017)`,
    pink = `Pink (2018)`,
    orange = `Orange (2019)`,
    red = `Red (2021/2020)`,
    dead = `Dead Individuals`,
    eggs = `Eggmasses present`
  )

op16 <- op16 %>% 
  mutate(date = as.Date(date, "%m/%d/%Y")) %>% 
  mutate(pool = as.character(pool)) %>% 
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(salinity2 = as.numeric(salinity2)) %>% 
  mutate(pool_temp = as.numeric(pool_temp)) %>% 
  mutate(total = as.numeric(total)) %>% 
  mutate(unmarked = as.numeric(unmarked)) %>% 
  mutate(yellow = as.numeric(yellow)) %>% 
  mutate(pink = as.numeric(pink)) %>% 
  mutate(orange = as.numeric(orange)) %>% 
  mutate(red = as.numeric(red)) %>% 
  mutate(dead = as.numeric(dead)) %>% 
  mutate(eggs = as.numeric(eggs))
```

    ## Warning: There was 1 warning in `mutate()`.
    ## ℹ In argument: `eggs = as.numeric(eggs)`.
    ## Caused by warning:
    ## ! NAs introduced by coercion

``` r
op16 <- op16 %>% 
  subset(select = -eggs)
```

``` r
op17 <- op17 %>% 
  rename(
    date = `Date`,
    pool = `Pool Number`,
    salinity = `Salinity (ppt)`,
    salinity2 = `Second Salinity Noted (lower)`,
    pool_temp = `Temperature (C)`,
    total = Total,
    unmarked = Unmarked,
    yellow = `Yellow (2017)`,
    pink = `Pink (2018)`,
    orange = `Orange (2019)`,
    red = `Red (2021/2020)`,
    dead = `Dead Individuals`,
    eggs = `Eggmasses present`
  )

op17 <- op17 %>% 
  mutate(date = as.Date(date, "%m/%d/%Y")) %>% 
  mutate(pool = as.character(pool)) %>% 
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(salinity2 = as.numeric(salinity2)) %>% 
  mutate(pool_temp = as.numeric(pool_temp)) %>% 
  mutate(total = as.numeric(total)) %>% 
  mutate(unmarked = as.numeric(unmarked)) %>% 
  mutate(yellow = as.numeric(yellow)) %>% 
  mutate(pink = as.numeric(pink)) %>% 
  mutate(orange = as.numeric(orange)) %>% 
  mutate(red = as.numeric(red)) %>% 
  mutate(dead = as.numeric(dead)) %>% 
  mutate(eggs = as.numeric(eggs))

op17 <- op17 %>% 
  subset(select = -eggs)
```

``` r
op18 <- op18 %>% 
  rename(
    date = `Date`,
    pool = `Pool Number`,
    salinity = `Salinity (ppt)`,
    salinity2 = `Second Salinity Noted (lower)`,
    pool_temp = `Temperature (C)`,
    total = Total,
    unmarked = Unmarked,
    yellow = `Yellow (2017)`,
    pink = `Pink (2018)`,
    orange = `Orange (2019)`,
    red = `Red (2021/2020)`,
    dead = `Dead Individuals`,
    eggs = `Eggmasses present`,
    returns = `Returns Per Night`,
    color = Color,
    top_returns = `Top # of Returns`
  )

op18 <- op18 %>% 
  subset(select = -c(eggs, returns, color, top_returns))

op18 <- op18 %>% 
  mutate(date = as.Date(date, "%m/%d/%Y")) %>% 
  mutate(pool = as.character(pool)) %>% 
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(salinity2 = as.numeric(salinity2)) %>% 
  mutate(pool_temp = as.numeric(pool_temp)) %>% 
  mutate(total = as.numeric(total)) %>% 
  mutate(unmarked = as.numeric(unmarked)) %>% 
  mutate(yellow = as.numeric(yellow)) %>% 
  mutate(pink = as.numeric(pink)) %>% 
  mutate(orange = as.numeric(orange)) %>% 
  mutate(red = as.numeric(red)) %>% 
  mutate(dead = as.numeric(dead))
```

``` r
op19 <- op19 %>% 
  rename(
    date = `Date`,
    pool = `Pool Number`,
    salinity = `Salinity (ppt)`,
    salinity2 = `Second Salinity Noted (lower)`,
    pool_temp = `Temperature (C)`,
    total = Total,
    unmarked = Unmarked,
    yellow = `Yellow (2017)`,
    pink = `Pink (2018)`,
    orange = `Orange (2019)`,
    red = `Red (2021/2020)`,
    dead = `Dead Individuals`,
    eggs = `Eggmasses present`,
    returns = `Returns Per Night`,
    color = Color
  )

op19 <- op19 %>% 
  subset(select = -c(eggs, returns, color))

op19 <- op19 %>% 
  mutate(date = as.Date(date, "%m/%d/%Y")) %>% 
  mutate(pool = as.character(pool)) %>% 
  mutate(salinity = case_when(
    salinity == "N/A" ~ NA,
    .default = salinity
  )) %>% 
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(salinity2 = as.numeric(salinity2)) %>% 
  mutate(pool_temp = as.numeric(pool_temp)) %>% 
  mutate(total = as.numeric(total)) %>% 
  mutate(unmarked = as.numeric(unmarked)) %>% 
  mutate(yellow = as.numeric(yellow)) %>% 
  mutate(pink = as.numeric(pink)) %>% 
  mutate(orange = as.numeric(orange)) %>% 
  mutate(red = as.numeric(red)) %>% 
  mutate(dead = as.numeric(dead))
```

``` r
op20 <- op20 %>% 
  rename(
    date = `Date`,
    pool = `Pool Number`,
    salinity = `Salinity (ppt)`,
    salinity2 = `Second Salinity Noted (lower)`,
    pool_temp = `Temperature (C)`,
    total = Total,
    unmarked = Unmarked,
    yellow = `Yellow (2017)`,
    pink = `Pink (2018)`,
    orange = `Orange (2019)`,
    red = `Red (2021/2020)`,
    dead = `Dead Individuals`,
    notes = ...14,
    eggs = `Eggmasses present`,
    returns = `Returns per night`,
    color = Color
  )

op20 <- op20 %>% 
  subset(select = -c(eggs, notes, returns, color))

op20 <- op20 %>% 
  mutate(date = as.Date(date, "%m/%d/%Y")) %>% 
  mutate(pool = as.character(pool)) %>% 
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(salinity2 = str_remove(salinity2, "\\(deep\\)")) %>% 
  mutate(salinity2 = as.numeric(salinity2)) %>% 
  mutate(pool_temp = as.numeric(pool_temp)) %>% 
  mutate(total = as.numeric(total)) %>% 
  mutate(unmarked = as.numeric(unmarked)) %>% 
  mutate(yellow = str_remove(yellow, "\\(.*\\d\\)")) %>% 
  mutate(orange = str_remove(orange, "\\(.*\\d\\)")) 
```

    ## Warning: There was 1 warning in `mutate()`.
    ## ℹ In argument: `salinity = as.numeric(salinity)`.
    ## Caused by warning:
    ## ! NAs introduced by coercion

    ## Warning: There was 1 warning in `mutate()`.
    ## ℹ In argument: `pool_temp = as.numeric(pool_temp)`.
    ## Caused by warning:
    ## ! NAs introduced by coercion

``` r
## Something tricky with the data here in that there was only 1 returning salamander but it was unclear whether that salamander was tagged in 2017 (yellow) or 2019 (orange) so it was marked as both. I will be making a "marked" column to account for the difference in total - unmarked.

op20 <- op20 %>% 
  mutate(yellow = as.numeric(yellow)) %>% 
  mutate(pink = as.numeric(pink)) %>% 
  mutate(orange = as.numeric(orange)) %>% 
  mutate(red = as.numeric(red)) %>% 
  mutate(dead = as.numeric(dead))

## The coerced NAs in `salinity` and `temp` are okay because they were "N/A" text
```

``` r
op21 <- op21 %>% 
  rename(
    date = `Date`,
    pool = `Pool Number`,
    salinity = `Salinity (ppt)`,
    salinity2 = `Second Salinity Noted (lower)`,
    pool_temp = `Temperature (C)`,
    total = Total,
    unmarked = Unmarked,
    yellow = `Yellow (2017)`,
    pink = `Pink (2018)`,
    orange = `Orange (2019)`,
    red = `Red (2021/2020)`,
    dead = `Dead Individuals`,
    eggs = `Eggmasses present`,
    returns = `Returns Per Night`,
    color = `Color/Year`,
    top_returns = `Top # of Returns`
  )

op21 <- op21 %>% 
  subset(select = -c(eggs, returns, color, top_returns))

op21 <- op21 %>% 
  mutate(date = case_when(
    date == "4/1" ~ "4/1/21",
    .default = date
  ))

op21 <- op21 %>% 
  mutate(date = as.Date(date, "%m/%d/%Y")) %>% 
  mutate(pool = as.character(pool)) %>% 
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(salinity2 = as.numeric(salinity2)) %>% 
  mutate(pool_temp = as.numeric(pool_temp)) %>% 
  mutate(total = as.numeric(total)) %>% 
  mutate(unmarked = as.numeric(unmarked)) %>% 
  mutate(yellow = str_remove(yellow, "\\?"))
```

    ## Warning: There was 1 warning in `mutate()`.
    ## ℹ In argument: `unmarked = as.numeric(unmarked)`.
    ## Caused by warning:
    ## ! NAs introduced by coercion

``` r
op21 <- op21 %>% 
  mutate(yellow = as.numeric(yellow)) %>% 
  mutate(pink = as.numeric(pink)) %>% 
  mutate(orange = as.numeric(orange)) %>% 
  mutate(red = as.numeric(red)) %>% 
  mutate(dead = as.numeric(dead))

##I am okay with the coerced NAs in `unmarked` as they were "X"s and the data is captured in other columns
```

I am running into a slight issue in that the data for 2022-2023 is in a
very different format, with each observation being an individual
salamander after PIT-tagging was implemented. I’m going to merge the
datasets I just cleaned (op15-op21) which could be used to look at
return rates. I could select out only the same data/variables as the
past years in order to do this kind of analysis but more tidying will
have to be done. For now I will merge the tidied datasets op15-op21 and
do a similar tidying/merge of datasets op22, sals 22 and op23.

``` r
rbind(op15, op16, op17, op18, op19, op20, op21)
```

    ## # A tibble: 355 × 12
    ##    date       pool  salinity salinity2 pool_temp total unmarked   red orange
    ##    <date>     <chr>    <dbl>     <dbl>     <dbl> <dbl>    <dbl> <dbl>  <dbl>
    ##  1 2015-04-14 <NA>      NA        NA        NA      43       NA    NA     NA
    ##  2 2015-04-16 <NA>       0.1      NA        10.4    NA       NA    NA     NA
    ##  3 2015-04-16 <NA>       0.2      NA         8.8    NA       NA    NA     NA
    ##  4 2015-04-18 <NA>      NA        NA        NA      63       NA    NA     NA
    ##  5 2015-04-19 <NA>       0.1      NA        NA     129       NA    NA     NA
    ##  6 2015-04-20 <NA>      NA        NA        NA      87       NA    NA     NA
    ##  7 2015-04-21 <NA>      NA        NA        NA      69       NA    NA     NA
    ##  8 2015-04-21 <NA>      10        NA        NA      NA       NA    NA     NA
    ##  9 2015-04-21 <NA>      24         0.1      NA      NA        1    NA     NA
    ## 10 2015-04-21 <NA>       8        NA        NA      NA        3    NA     NA
    ## # ℹ 345 more rows
    ## # ℹ 3 more variables: pink <dbl>, yellow <dbl>, dead <dbl>
