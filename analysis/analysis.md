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
    new = Unmarked,
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
    .default = salinity)) %>% 
  mutate(salinity = as.numeric(salinity)) %>% 
  mutate(salinity2 = as.numeric(salinity2)) %>% 
  mutate(temp = as.numeric(temp)) %>% 
  mutate(total = as.numeric(total)) %>% 
  mutate(new = as.numeric(new)) %>% 
  mutate(yellow = as.numeric(yellow)) %>% 
  mutate(pink = as.numeric(yellow)) %>% 
  mutate(orange = as.numeric(yellow)) %>% 
  mutate(red = as.numeric(yellow)) %>% 
  mutate(dead = as.numeric(dead)) %>% 
  mutate(eggs = as.numeric(eggs)) %>% 
  mutate(notes = as.character(notes))
```
