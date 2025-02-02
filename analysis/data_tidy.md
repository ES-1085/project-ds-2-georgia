Data Tidying: Salamanders by the Sea
================
Georgia Lattig
02/25/24

## Packages and Data

``` r
op15 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2015.csv")
op16 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2016.csv")
op17 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2017.csv")
op18 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2018.csv")
op19 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2019.csv")
op20 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2020.csv")
op21 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2021.csv")
op22 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2022.csv")
sals22 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2022_sals.csv")
op23 <- read_csv("/Users/georgialattig/seaside salamanders/data/raw_data/otter point - 2023.csv")
```

## Data Tidying

### op15-21: Environmental Salinities and Coarse CMR

In these datasets (op15-op21), each observation is a unique pool on a
given night. For each pool, salinity and temperature were recorded and
the salamanders within were counted and, beginning in 2017, tagged with
visible implant elastomer (VIE) tags.

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
  subset(select = -c(eggs, notes)) # I am dropping the eggs variable because the data were recorded in different ways across seasons and because I do not need it for the questions I am interested in asking. I am also dropping the notes column because there is minimal information there which I do not need for my analysis 
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

# `{r tidy-22} # nights22 <- op22 %>%  #   select(date, pool_num, pit_num, color, sex, year, salinity_ppt, pool_temp_c, notes) #`

# `{r tidy-23} # nights23 <- op23 %>%  #   select(date, pool_num, pit_num, color, sex, year, salinity_ppt, pool_temp_c, notes) #`

``` r
pools <- rbind(op15, op16, op17, op18, op19, op20, op21)

write_csv(pools, "/Users/georgialattig/seaside salamanders/data/tidy_data/pools.csv")
```

### 2022-2023 Tracking Individual Salamanders (PIT CMR)

Tidy and merge 2022 and 2023 data about uniquely PIT-tagged salamanders.

``` r
individuals22 <- op22 %>% 
  mutate(pit_num = str_remove_all(pit_num, "90004300024")) %>% 
  select(date, pool_num, pit_num, color, sex, year, salinity_ppt, pool_temp_c, notes) %>% 
  rename(
    pool = `pool_num`,
    salinity = `salinity_ppt`,
    pit = `pit_num`,
    first_year = year,
    pool_temp = `pool_temp_c`)

individuals22 <- individuals22 %>% 
  mutate(first_year = case_when(
    color == "yellow" ~ "2017",
    color == "pink" ~ "2018",
    color == "orange" ~ "2019",
    color == "red" ~ "2020_2021",
    .default = first_year
  )) %>% 
  mutate(color = case_when(
    first_year == "2022" ~ "blue", #assign 2022-marked salamanders a color (even though they don't have VIE tags, this will help with the code and data QAQC)
    .default = color
  )) %>% 
  mutate(recap = case_when(
    first_year == "2017" ~ "yes",
    first_year == "2018" ~ "yes",
    first_year == "2019" ~ "yes",
    first_year == "2020_2021" ~ "yes",
    first_year == "2022" ~ "no"
  )) %>% 
  mutate(date = as.Date(date, "%m/%d/%Y")) %>% 
  mutate(pool = as.character(pool)) %>% 
  mutate(pit = as.character(pit)) %>% 
  mutate(color = as.character(color)) %>% 
  mutate(sex = as.factor(sex)) %>% 
  mutate(first_year = as.character(first_year)) %>% 
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(pool_temp = as.numeric(pool_temp)) %>% 
  mutate(recap = as.factor(recap))

# Create pit_year variable for the year that PIT tag was given

pits22 <- individuals22 %>% 
  filter(str_detect(pit,"\\d"))

individuals22 <- individuals22 %>% 
  mutate(pit_year = case_when(
    pit %in% pits22$pit ~ "2022"
  ))

individuals23 <- op23 %>% 
  mutate(pit_num = str_remove_all(pit_num, "90004300024")) %>% 
   mutate(color = case_when(
     new_pit == "y" ~ "green", #assign 2023-marked salamanders a color (even though they don't have VIE tags, this will help with the code and data QAQC)
     .default = color
   )) %>% 
  mutate(pit_year = case_when( # Create pit_year variable for the year that PIT tag was given
    new_pit == "y" ~ "2023" # Later will need to recode as there are a few errors in new_pit variable
  )) %>% 
  #Remove 11-digit repeating number sequence before the unique 4-digit combination at the end of PIT IDs
  select(date, pool_num, pit_num, color, sex, year, salinity_ppt, pool_temp_c, notes, pit_year) %>% 
  rename(
    pool = `pool_num`,
    salinity = `salinity_ppt`,
    pit = `pit_num`,
    first_year = year,
    pool_temp = `pool_temp_c`)

individuals23 <- individuals23 %>% 
  mutate(first_year = as.character(first_year)) %>%
  mutate(first_year = case_when(
    color == "yellow" ~ "2017",
    color == "pink" ~ "2018",
    color == "orange" ~ "2019",
    color == "red" ~ "2020_2021",
    color == "blue" ~ "2022",
    color == "green" ~ "2023",
    .default = first_year
  )) %>% 
  mutate(first_year = case_when(
    first_year == "2021" ~ "2020_2021", #Red VIE tags were used both in 2020 and 2021
    .default = first_year
  )) %>% 
  mutate(recap = case_when(
    first_year == "2017" ~ "yes",
    first_year == "2018" ~ "yes",
    first_year == "2019" ~ "yes",
    first_year == "2020_2021" ~ "yes",
    first_year == "2022" ~ "yes",
    first_year == "2023" ~ "no"
  )) %>% 
  mutate(date = as.Date(date, "%m/%d/%Y")) %>% 
  mutate(pool = as.character(pool)) %>% 
  mutate(pit = as.character(pit)) %>% 
  mutate(color = as.character(color)) %>% 
  mutate(sex = as.factor(sex)) %>% 
  mutate(first_year = as.character(first_year)) %>% 
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(pool_temp = as.numeric(pool_temp)) %>% 
  mutate(recap = as.factor(recap))
```

``` r
sals <- rbind(individuals22, individuals23)

write_csv(sals, "/Users/georgialattig/seaside salamanders/data/tidy_data/sals.csv")
```
