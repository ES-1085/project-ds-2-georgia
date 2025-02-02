Project proposal: Site Fidelity and Inter-pool Movement of Spotted
Salamanders by the Sea
================
Georgia Lattig
02/14/24

## 1. Introduction

The aim of this project is to organize, synthesize and begin to analyze
data from the past nine seasons of data collection for the Otter Point
Salamander project. The Otter Point Salamander project (unofficial
title) is a long-term monitoring project that is focused on a population
of Spotted Salamanders (Ambystoma maculatum) that breeds on a rocky
headland by the Atlantic Ocean. This population is unique because they
breed in a series of freshwater pools in the granite headland, so close
to the ocean that the pools are occasionally flushed with full-strength
seawater during stochastic storm events. The project was initiated by
Dr. Stephen Ressel in 2015 with efforts to quantify the environmental
salinities that these salamanders were experiencing during the breeding
season. In 2017, Dr. Ressel implemented a mark-recapture study to gauge
the rate of salamander returns to this unusual breeding site.

In 2022, a new and exciting aspect was added to the study by COA alum
Jasper White. The original methods for mark-recapture were through the
use of Visible Implant Elastomer (VIE) tags. To tag salamanders with VIE
tags, we would inject a small amount of colorful, fluorescing polymer
under the salamander’s skin at the base of their tail. Unique colors
were used for each unique year so, for example, if a salamander had a
yellow tag that means it was initially marked in 2017. There are limits
to this type of tagging, however, because we were only able to mark
cohorts from a given year rather than uniquely identify individual
salamanders. In 2022, Jasper implemented PIT-tagging as a method of
marking individual salamanders. PIT tags are small microchip tags that
are inserted into the body cavity of the salamanders, assigning each
individual a unique barcode of numbers. PIT-tagging continued last
spring (2023) and will continue this coming spring (2024).

Both the quantity and type of data that has been collected on the Otter
Point population for the past nine years opens many possible questions.
With my final project, I am specifically interested in beginning to look
at the site fidelity of individuals across seasons and the movement of
individuals between breeding pools within each season. For both of these
questions, I will be working with data from more recent years
(2022-2023) and will hopefully set up the code so that this coming
spring’s data can easily be incorporated. Another major goal of mine in
working with these data is that, in the lengthy process of data-cleaning
and tidying that this project will require, I will come up with a
standardized method of data collection and ideally design a data sheet
for use in the field for future seasons.

I will work with one dataset that contains 9 years (currently separate
data sheets) of data. There is a lot of data cleaning that still needs
to be done because there are 10 different sheets, one sheet for each
season, except for the 2022 season which for some reason has two. Each
sheet has a slightly different number and configuration of variables.
The variables are as follows:

#### op15

`Date`, `Pool Number`, `Salinity(ppt)`, `Second Salinity Noted (lower)`,
`Temperature (C)`, `Total`, `Unmarked`, `Red (2021/2020)`,
`Orange (2019)`, `Pink (2018)`, `Yellow (2017)`, `Dead Individuals`,
`Eggmasses Present`, `Notes`

#### op16

`Date`, `Pool Number`, `Salinity(ppt)`, `Second Salinity Noted (lower)`,
`Temperature (C)`, `Total`, `Unmarked`, `Red (2021/2020)`,
`Orange (2019)`, `Pink (2018)`, `Yellow (2017)`, `Dead Individuals`,
`Eggmasses Present`

#### op17

`Date`, `Pool Number`, `Salinity(ppt)`, `Second Salinity Noted (lower)`,
`Temperature (C)`, `Total`, `Unmarked`, `Red (2021/2020)`,
`Orange (2019)`, `Pink (2018)`, `Yellow (2017)`, `Dead Individuals`,
`Eggmasses Present`

#### op18

`Date`, `Pool Number`, `Salinity(ppt)`, `Second Salinity Noted (lower)`,
`Temperature (C)`, `Total`, `Unmarked`, `Red (2021/2020)`,
`Orange (2019)`, `Pink (2018)`, `Yellow (2017)`, `Dead Individuals`,
`Eggmasses Present`, `Returns Per Night`, `Color`, `Top # of Returns`

#### op19

`Date`, `Pool Number`, `Salinity(ppt)`, `Second Salinity Noted (lower)`,
`Temperature (C)`, `Total`, `Unmarked`, `Red (2021/2020)`,
`Orange (2019)`, `Pink (2018)`, `Yellow (2017)`, `Dead Individuals`,
`Eggmasses Present`, `Returns Per Night`, `Color`

#### op20

`Date`, `Pool Number`, `Salinity(ppt)`, `Second Salinity Noted (lower)`,
`Temperature (C)`, `Total`, `Unmarked`, `Red (2021/2020)`,
`Orange (2019)`, `Pink (2018)`, `Yellow (2017)`, `Dead Individuals`,
`Eggmasses Present`, `extra..14`, `Returns Per Night`, `Color`

#### op21

`Date`, `Pool Number`, `Salinity(ppt)`, `Second Salinity Noted (lower)`,
`Temperature (C)`, `Total`, `Unmarked`, `Red (2021/2020)`,
`Orange (2019)`, `Pink (2018)`, `Yellow (2017)`, `Dead Individuals`,
`Eggmasses Present`, `Returns Per Night`, `Color/Year`,
`Top # of Returns`

#### op22

`date`, `recapture`, `pool_num`, `pit_num`, `image`, `color`, `sex`,
`year`, `air_temp_c`, `salinity_ppt`, `pool_temp_c`, `notes`,
`extra..13`, `extra..14`

#### sals22

`date`, `svl`, `pool_num`, `pit_num`, `image`, `sex`, `color`, `year`,
`air_temp_c`, `salinity_ppt`, `pool_temp_c`, `spermatophores`, `eggs`,
`notes`

#### op23

`date`, `recapture`, `pool_num`, `new_pit`, `pit_num`, `color`, `sex`,
`year`, `air_temp_c`, `salinity_ppt`, `pool_temp_c`, `2nd_pool_temp_c`,
`notes`

## 2. Data

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

#### Data Skim

To give you an idea of the data in its current form, I glimpsed the
first data sheet from 2015 and the most recent data sheet from last
season, 2023.

``` r
glimpse(op15)
```

    ## Rows: 40
    ## Columns: 14
    ## $ Date                            <chr> "4/14/2015", "4/16/2015", "4/16/2015",…
    ## $ `Pool Number`                   <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ `Salinity (ppt)`                <chr> NA, "0.1", "0.2", NA, "0.1 - 0.2", NA,…
    ## $ `Second Salinity Noted (lower)` <dbl> NA, NA, NA, NA, NA, NA, NA, NA, 0.1, N…
    ## $ `Temperature (C)`               <dbl> NA, 10.4, 8.8, NA, NA, NA, NA, NA, NA,…
    ## $ Total                           <dbl> 43, NA, NA, 63, 129, 87, 69, NA, NA, N…
    ## $ Unmarked                        <dbl> NA, NA, NA, NA, NA, NA, NA, NA, 1, 3, …
    ## $ `Red (2021/2020)`               <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ `Orange (2019)`                 <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ `Pink (2018)`                   <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ `Yellow (2017)`                 <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA…
    ## $ `Dead Individuals`              <dbl> NA, NA, NA, NA, NA, NA, 2, 2, NA, NA, …
    ## $ `Eggmasses present`             <dbl> 2, 2, NA, 2, NA, NA, NA, NA, NA, NA, 3…
    ## $ ...14                           <chr> "2 females laying", NA, NA, NA, NA, NA…

``` r
glimpse(op23)
```

    ## Rows: 291
    ## Columns: 13
    ## $ date              <chr> "4/16/23", "4/16/23", "4/16/23", "4/16/23", "4/16/23…
    ## $ recapture         <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
    ## $ pool_num          <dbl> 0, 0, 0, 0, 1, 1, 1, 1, 2, 2, 2, 2, 2, 2, 7, 7, 7, 7…
    ## $ new_pit           <chr> "n", "n", "y", "y", "n", "n", "n", "y", "n", "n", "n…
    ## $ pit_num           <dbl> 3262, 3228, 4745, 4854, 3404, 3286, 3279, 4764, 3403…
    ## $ color             <chr> "orange", NA, NA, NA, NA, NA, NA, NA, "red", "pink",…
    ## $ sex               <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
    ## $ year              <dbl> 2019, 2022, 2023, 2023, 2022, 2022, 2022, 2023, 2021…
    ## $ air_temp_c        <lgl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
    ## $ salinity_ppt      <dbl> NA, NA, NA, NA, 0.14, 0.14, 0.14, 0.14, 0.17, 0.17, …
    ## $ pool_temp_c       <dbl> NA, NA, NA, NA, 10.4, 10.4, 10.4, 10.4, 10.7, 10.7, …
    ## $ `2nd_pool_temp_c` <dbl> NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, NA, …
    ## $ notes             <chr> NA, NA, "no color", "above pool 2", NA, NA, NA, NA, …

## 3. Ethics review

Data collection for this project is done in partnership with Acadia
National Park and our research methods have gone through IACUC
(Institutional Animal Care and Use Committee) review and approval.

Limitations in Data Sources?

Reason for Using the Data?

Positive Effects?

Negative Effects?

Minimizing Negative Impact?

## 4. Data analysis plan

Below are a few of the questions that I am most interested in answering
through this project:

- Which pools are most frequently visited across all seasons? (confirm
  Steve’s assumption)
- Rate of salamander returns using VIE color tags for year cohorts (n =
  9 seasons): What is the proportion of returning salamanders to new
  recruits each season?
- Site/Pool Fidelity of individual salamanders across 2 seasons (2022,
  2023): Are individual salamanders returning to the same pools each
  season?
- Inter-pool movement of individual salamanders across 2 seasons (2022,
  2023): How much are individual salamanders moving between pools within
  a given season?
- What is the most efficient way to collect these data in the field?
  (Prepare streamlined datasheet for data collection in future seasons)
