# Data

These data were collected as part of the Otter Point Salamander Project (unofficial name) which has been monitoring a population of Spotted Salamanders (Ambystoma maculatum) that breed in a series of rocky cliff pools by the Atlantic Ocean for the past 9 years. The datasets that I will be using for my final project include all 9 years worth of data about salamander presence/absence, returns, and environmental conditions (salinity, temperature) of the breeding pools for each night of fieldwork. The most recent seasons (2022 & 2023) include data about individual salamanders marked with unique numeric microchips called PIT tags. Across these two most recent seasons, interesting questions arise about the site fidelity and interpool movement of individual salamanders. 

Data collection has changed quite a bit over the 9 years of this study. The pools were not uniquely numbered until 2016. Mark/recapture with color-coded VIE tags did not begin until 2017 and PIT tagging of individuals did not begin until 2022. Between the years of 2016 and 2021, the data are a bit more "coarse" because each observation (row) represents a unique pool on a given night, with recorded environmental data (temperature, salinity) and counts of total salamanders (unmarked and marked yearly cohorts). Between the years of 2022 and 2023, the data are a bit finer because each observation (row) represents a salamander on a given night, with recorded information about the pool it was found in (pool number, temperature, salinity) as well as information about the individual salamander (pit tag, vie tag/year that the salamander was first observed and tagged). 

For this reason, I will be working with two different datasets to explore different questions:
1) The first dataset is called `pools` and was tidied and merged from datasets op15-op21. 
`pools` contains information about the breeding pools (#0-15) on each survey night, including the environmental conditions and salamander counts of each pool surveyed. 
2) The second dataset is called `sals` and was tidied and merged from datasets op22-op23.
`sals` contains information about individually-tagged salamanders on each survey night, including the environmental conditions of the breeding pool they were found in and information about the individual salamanders. 

## op15
- `Date`: date of the observation
- `Pool Number`: number of the breeding pool (0-15) in which observation took place
- `Salinity(ppt)`: salinity measurement of the observed breeding pool
- `Second Salinity Noted (lower)`: second salinity measurement of the observed breeding pool (if taken)
- `Temperature (C)`: temperature of the observed breeding pool
- `Total`: total number of salamanders observed
- `Unmarked`: number of unmarked salamanders
- `Red (2021/2020)`: number of returning salamanders marked in 2020 or 2021
- `Orange (2019)`: number of returning salamanders marked in 2019
- `Pink (2018)`: number of returning salamanders marked in 2018
- `Yellow (2017)`: number of returning salamanders marked in 2017
- `Dead Individuals`: how many dead individuals were observed that night
- `Eggmasses Present`: how many eggmasses were present that night
- `Notes`: additional written observations/remarks

## op 16
`Date`:
`Pool Number`:
`Salinity(ppt)`:
`Second Salinity Noted (lower)`:
`Temperature (C)`:
`Total`:
`Unmarked`:
`Red (2021/2020)`:
`Orange (2019)`:
`Pink (2018)`:
`Yellow (2017)`:
`Dead Individuals`:
`Eggmasses Present`:

## op17
`Date`:
`Pool Number`:
`Salinity(ppt)`:
`Second Salinity Noted (lower)`:
`Temperature (C)`:
`Total`:
`Unmarked`:
`Red (2021/2020)`:
`Orange (2019)`:
`Pink (2018)`:
`Yellow (2017)`:
`Dead Individuals`:
`Eggmasses Present`:

## op18
`Date`:
`Pool Number`:
`Salinity(ppt)`:
`Second Salinity Noted (lower)`:
`Temperature (C)`:
`Total`:
`Unmarked`:
`Red (2021/2020)`:
`Orange (2019)`:
`Pink (2018)`:
`Yellow (2017)`:
`Dead Individuals`:
`Eggmasses Present`:
`Returns Per Night`:
`Color`:
`Top # of Returns`:

## op19
`Date`:
`Pool Number`:
`Salinity(ppt)`:
`Second Salinity Noted (lower)`:
`Temperature (C)`:
`Total`:
`Unmarked`:
`Red (2021/2020)`:
`Orange (2019)`:
`Pink (2018)`:
`Yellow (2017)`:
`Dead Individuals`:
`Eggmasses Present`:
`Returns Per Night`:
`Color`:

## op20
`Date`:
`Pool Number`:
`Salinity(ppt)`:
`Second Salinity Noted (lower)`:
`Temperature (C)`:
`Total`:
`Unmarked`:
`Red (2021/2020)`:
`Orange (2019)`:
`Pink (2018)`:
`Yellow (2017)`:
`Dead Individuals`:
`Eggmasses Present`:
`extra..14`:
`Returns Per Night`:
`Color`:

## op21
`Date`:
`Pool Number`:
`Salinity(ppt)`:
`Second Salinity Noted (lower)`:
`Temperature (C)`:
`Total`:
`Unmarked`:
`Red (2021/2020)`:
`Orange (2019)`:
`Pink (2018)`:
`Yellow (2017)`:
`Dead Individuals`:
`Eggmasses Present`:
`Returns Per Night`:
`Color/Year`:
`Top # of Returns`:

## op22
`date`:
`recapture`:
`pool_num`:
`pit_num`:
`image`:
`color`:
`sex`:
`year`:
`air_temp_c`:
`salinity_ppt`:
`pool_temp_c`:
`notes`:
`extra..13`:
`extra..14`:

## sals22
`date`:
`svl`:
`pool_num`:
`pit_num`:
`image`:
`sex`:
`color`:
`year`:
`air_temp_c`:
`salinity_ppt`:
`pool_temp_c`:
`spermatophores`:
`eggs`:
`notes`:

## op23 
`date`:
`recapture`:
`pool_num`:
`new_pit`:
`pit_num`:
`color`:
`sex`:
`year`:
`air_temp_c`:
`salinity_ppt`:
`pool_temp_c`:
`2nd_pool_temp_c`:
`notes`:
