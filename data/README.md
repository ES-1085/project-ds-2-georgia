# Data

These data were collected as part of the Otter Point Salamander Project (unofficial name) which has been monitoring a population of Spotted Salamanders (Ambystoma maculatum) that breed in a series of rocky cliff pools by the Atlantic Ocean for the past 9 years. The datasets that I will be using for my final project include all 9 years worth of data about salamander presence/absence, returns, and environmental conditions (salinity, temperature) of the breeding pools for each night of fieldwork. The most recent seasons (2022 & 2023) include data about individual salamanders marked with unique numeric microchips called PIT tags. Across these two most recent seasons, interesting questions arise about the site fidelity and interpool movement of individual salamanders. 

Data collection has changed quite a bit over the 9 years of this study. The pools were not uniquely numbered until 2016. Mark/recapture with color-coded VIE tags did not begin until 2017 and PIT tagging of individuals did not begin until 2022. Between the years of 2016 and 2021, the data are a bit more "coarse" because each observation (row) represents a unique pool on a given night, with recorded environmental data (temperature, salinity) and counts of total salamanders (unmarked and marked yearly cohorts). Between the years of 2022 and 2023, the data are a bit finer because each observation (row) represents a salamander on a given night, with recorded information about the pool it was found in (pool number, temperature, salinity) as well as information about the individual salamander (pit tag, vie tag/year that the salamander was first observed and tagged). 

For this reason, I will be working with two different datasets to explore different questions.
The first dataset is called `pools` and was tidied and merged from datasets op15-op21. 
`pools` contains information about the breeding pools (#0-15) on each survey night, including the environmental conditions and salamander counts of each pool surveyed. 
The second dataset is called `sals` and was tidied and merged from datasets op22-op23.
`sals` contains information about individually-tagged salamanders on each survey night, including the environmental conditions of the breeding pool they were found in and information about the individual salamanders. 

## pools
This dataset has 12 variables and 355 observations. Each observation represents a breeding pool on a given night. 
- `date`: date of the observation
- `pool`: number of the breeding pool (0-15)
- `salinity`: salinity measurement of the breeding pool
- `salinity2`: second salinity measurement of the breeding pool (if taken)
- `pool_temp`: temperature of the breeding pool
- `total`: total number of salamanders observed in the breeding pool
- `unmarked`: number of unmarked salamanders observed in the breeding pool
- `red`: number of returning salamanders observed in the breeding pool that were marked in 2020 or 2021
- `orange`: number of returning salamanders observed in the breeding pool that were marked in 2019
- `pink`: number of returning salamanders observed in the breeding pool that were marked in 2018
- `yellow`: number of returning salamanders observed in the breeding pool that were marked in 2017
- `dead`: how many dead individuals were observed in the breeding pool

## sals
This dataset has 10 variables and 1006 observations. Each observation represents a salamander on a given night.
- `date`: date of the observation
- `pool`: number of the breeding pool (0-15) that the salamander was found in
- `pit`: the unique numeric PIT tag implanted in the salamander
- `color`: the color of the VIE tag implanted in the salamander (corresponding to the first year it was observed and tagged)
- `year`: the first year that the salamander was observed and tagged
- `salinity`: salinity measurement of the breeding pool that the salamander was found in
- `pool_temp`: temperature of the breeding pool that the salamander was found in
- `notes`: additional information recorded about the salamander or breeding pool
- `recap`: whether or not the salamander was a recapture (previously tagged) when it was found
