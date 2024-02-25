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

## Data Cleaning

``` r
op15 <- op15 %>% 
  rename(
    date = `Date`,
    pool = `Pool Number`,
    salinity = `Salinity (ppt)`,
    salinity2 = `Second Salinity Noted (lower)`,
    temp = `Temperature (C)`,
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
  mutate(temp = as.numeric(temp)) %>% 
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
  subset(select = -eggs) # I am dropping the eggs variable because the data were recorded in different ways across seasons and because I do not need it for the questions I am interested in asking 
```

``` r
op16 <- op16 %>% 
  rename(
    date = `Date`,
    pool = `Pool Number`,
    salinity = `Salinity (ppt)`,
    salinity2 = `Second Salinity Noted (lower)`,
    temp = `Temperature (C)`,
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
  mutate(temp = as.numeric(temp)) %>% 
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
    temp = `Temperature (C)`,
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
  mutate(temp = as.numeric(temp)) %>% 
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
    temp = `Temperature (C)`,
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
  mutate(temp = as.numeric(temp)) %>% 
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
    temp = `Temperature (C)`,
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
  mutate(temp = as.numeric(temp)) %>% 
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
    temp = `Temperature (C)`,
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
  mutate(temp = as.numeric(temp)) %>% 
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
    ## ℹ In argument: `temp = as.numeric(temp)`.
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
