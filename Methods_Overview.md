Color of Coronavirus Methods Overview
================

### by APM Research Lab

**Methods are listed here in the order they are calculated in Notebook_1
and Notebook_2.**

### CHART 1

**Monthly death count time series for US combined, by race/ethnicity
group**

Data downloaded:

-   For mortality counts over time and for crude rates over time
    MONTHLY/NATIONAL -
    <https://data.cdc.gov/NCHS/Provisional-COVID-19-Deaths-Distribution-of-Deaths/pj7m-y5uh>

Looks like this raw (preview using 10 random rows):

``` r
slice_sample(df, n=10)
```

    ##    Data.as.of Start.Date   End.Date Year Month    Group                State
    ## 1  03/09/2022 03/01/2021 03/31/2021 2021     3 By Month                Idaho
    ## 2  03/09/2022 08/01/2021 08/31/2021 2021     8 By Month            Louisiana
    ## 3  03/09/2022 03/01/2022 03/05/2022 2022     3 By Month         Pennsylvania
    ## 4  03/09/2022 11/01/2020 11/30/2020 2020    11 By Month District of Columbia
    ## 5  03/09/2022 01/01/2022 01/31/2022 2022     1 By Month        New Hampshire
    ## 6  03/09/2022 02/01/2021 02/28/2021 2021     2 By Month              Florida
    ## 7  03/09/2022 01/01/2021 01/31/2021 2021     1 By Month              Wyoming
    ## 8  03/09/2022 03/01/2020 03/31/2020 2020     3 By Month           New Mexico
    ## 9  03/09/2022 08/01/2020 08/31/2020 2020     8 By Month           Washington
    ## 10 03/09/2022 04/01/2021 04/30/2021 2021     4 By Month             Virginia
    ##                                  Indicator Non.Hispanic.White
    ## 1                 Count of COVID-19 deaths               66.0
    ## 2                 Count of COVID-19 deaths             1185.0
    ## 3      Distribution of COVID-19 deaths (%)               91.2
    ## 4  Weighted distribution of population (%)               37.7
    ## 5                 Count of COVID-19 deaths              229.0
    ## 6  Weighted distribution of population (%)               38.8
    ## 7                 Count of COVID-19 deaths               89.0
    ## 8  Weighted distribution of population (%)               38.4
    ## 9                 Count of COVID-19 deaths              197.0
    ## 10                Count of COVID-19 deaths              270.0
    ##    Non.Hispanic.Black.or.African.American
    ## 1                                     0.0
    ## 2                                   533.0
    ## 3                                      NA
    ## 4                                    43.8
    ## 5                                      NA
    ## 6                                    17.8
    ## 7                                     0.0
    ## 8                                     2.5
    ## 9                                    14.0
    ## 10                                  142.0
    ##    Non.Hispanic.American.Indian.or.Alaska.Native Non.Hispanic.Asian
    ## 1                                             NA                 NA
    ## 2                                           12.0               13.0
    ## 3                                            0.0                 NA
    ## 4                                            0.2                4.4
    ## 5                                            0.0                 NA
    ## 6                                            0.2                2.8
    ## 7                                             NA                0.0
    ## 8                                            6.8                2.4
    ## 9                                             NA               12.0
    ## 10                                           0.0               29.0
    ##    Non.Hispanic.Native.Hawaiian.or.Other.Pacific.Islander
    ## 1                                                     0.0
    ## 2                                                      NA
    ## 3                                                     0.0
    ## 4                                                     0.0
    ## 5                                                     0.0
    ## 6                                                     0.1
    ## 7                                                     0.0
    ## 8                                                     0.1
    ## 9                                                      NA
    ## 10                                                    0.0
    ##    Non.Hispanic.more.than.one.race Hispanic.or.Latino
    ## 1                              0.0                 NA
    ## 2                              0.0               40.0
    ## 3                              0.0                0.0
    ## 4                              2.4               11.4
    ## 5                              0.0                 NA
    ## 6                              1.5               38.8
    ## 7                              0.0                 NA
    ## 8                              1.9               48.0
    ## 9                               NA               50.0
    ## 10                             0.0               30.0
    ##                                                                                                                      Footnote
    ## 1  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 2  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 3  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 4                                                                                                                            
    ## 5  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 6                                                                                                                            
    ## 7  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 8                                                                                                                            
    ## 9  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 10

Processed in Notebook 1:

-   Filtered such that “Group = By Month”, “State = United States”, and
    “Indicator = Count of COVID-19 deaths”

-   Race/ethnicity names shortened for consistent labeling/ease of
    reading

-   Column created for year-month for ease of use in chart

-   Added column with all races combined for US totals

-   Selected just columns needed for chart (year-month and the 7
    race/ethnicity groups)

Ultimate format - preview of first 10 rows:

``` r
head(chart_1_export, 10)
```

    ##    Year_Month White Black Indigenous Asian Pacific Islander More than one race
    ## 1     2020-01     2     2          0     0                0                  0
    ## 2     2020-02    15     5          0     1                0                  0
    ## 3     2020-03  3258  2184         30   448                6                 19
    ## 4     2020-04 33206 16398        299  3481               41                161
    ## 5     2020-05 21799  7849        439  1652               38                 90
    ## 6     2020-06  8997  3456        385   696               68                 55
    ## 7     2020-07 13944  5603        432   865               95                104
    ## 8     2020-08 15288  5397        334   856               68                 97
    ## 9     2020-09 11561  2995        246   608               68                 72
    ## 10    2020-10 17619  2791        418   524               51                 83
    ##    Latino All Americans
    ## 1       1             5
    ## 2       3            24
    ## 3    1127          7072
    ## 4   11080         64666
    ## 5    6226         38093
    ## 6    4297         17954
    ## 7   10027         31070
    ## 8    7808         29848
    ## 9    3578         19128
    ## 10   3401         24887

### CHART 2

**Monthly crude rates over time, adding in each month for cumulative
rates, for US total**

Data downloaded

-   For national populations by race, all ages combined, 2020 Census via
    CDC WONDER - <https://wonder.cdc.gov/controller/saved/D170/D278F683>

-   Also uses mortality data; same data as for Chart 1.

Population data looks like this raw (preview using first ten rows):

``` r
head(df2, n=10)
```

    ## # A tibble: 10 × 6
    ##    Notes Ethnicity              `Ethnicity Code` Race     `Race Code` Population
    ##    <chr> <chr>                  <chr>            <chr>    <chr>            <dbl>
    ##  1 <NA>  Hispanic or Latino     2135-2           America… 1002-5         1860652
    ##  2 <NA>  Hispanic or Latino     2135-2           Asian    A               645081
    ##  3 <NA>  Hispanic or Latino     2135-2           Black o… 2054-5         3103771
    ##  4 <NA>  Hispanic or Latino     2135-2           Native … NHOPI           230186
    ##  5 <NA>  Hispanic or Latino     2135-2           White    2106-3        53536334
    ##  6 <NA>  Hispanic or Latino     2135-2           More th… M              1936855
    ##  7 Total Hispanic or Latino     2135-2           <NA>     <NA>          61312879
    ##  8 <NA>  Not Hispanic or Latino 2186-5           America… 1002-5         2432338
    ##  9 <NA>  Not Hispanic or Latino 2186-5           Asian    A             19367197
    ## 10 <NA>  Not Hispanic or Latino 2186-5           Black o… 2054-5        41427341

Processed in Notebook 1

-   Filtered population data for just the types of race/ethnicity groups
    needed (Hispanic, Non-Hispanic Black, Non-Hispanic White,
    Non-Hispanic Native American, Non-Hispanic Pacific Islander,
    Non-Hispanic Asian), and renamed into simplified names

-   Merged population data with mortality data

-   Calculated cumulative deaths by month by adding each month to the
    previous month’s cumulative total

-   Calculated cumulative death rates by month by dividing monthly
    cumulative deaths per group over their respective populations and
    multiplying by 100,000

-   Saved full data for combining with state quarterly data for Chart 5
    later

-   Selected just columns needed for chart (year-month and the
    cumulative monthly rates for the 7 race/ethnicity groups)

Ultimate format - preview of first 10 rows:

``` r
head(chart_2_export, 10)
```

    ## # A tibble: 10 × 9
    ##    YearMonth State     White   Black Indigenous   Asian `Pacific Island…  Latino
    ##    <chr>     <chr>     <dbl>   <dbl>      <dbl>   <dbl>            <dbl>   <dbl>
    ##  1 1/2020    United… 1.02e-3 4.83e-3       0    0                  0     1.63e-3
    ##  2 2/2020    United… 8.64e-3 1.69e-2       0    5.16e-3            0     6.52e-3
    ##  3 3/2020    United… 1.66e+0 5.29e+0       1.23 2.32e+0            0.978 1.84e+0
    ##  4 4/2020    United… 1.85e+1 4.49e+1      13.5  2.03e+1            7.66  1.99e+1
    ##  5 5/2020    United… 2.96e+1 6.38e+1      31.6  2.88e+1           13.9   3.01e+1
    ##  6 6/2020    United… 3.42e+1 7.22e+1      47.4  3.24e+1           24.9   3.71e+1
    ##  7 7/2020    United… 4.13e+1 8.57e+1      65.2  3.69e+1           40.4   5.34e+1
    ##  8 8/2020    United… 4.90e+1 9.87e+1      78.9  4.13e+1           51.5   6.62e+1
    ##  9 9/2020    United… 5.49e+1 1.06e+2      89.0  4.44e+1           62.6   7.20e+1
    ## 10 10/2020   United… 6.39e+1 1.13e+2     106.   4.71e+1           70.9   7.75e+1
    ## # … with 1 more variable: More than one race <dbl>

### CHART 4

**Quarterly crude rates over time, adding together each month for
cumulative rates, for US states + Monthly crude rates over time, adding
together each month for cumulative rates, for US total (from Chart 2)**

Data downloaded:

-   For state-level populations by race, all ages combined, 2020 Census
    via CDC WONDER -
    <https://wonder.cdc.gov/controller/saved/D170/D279F330>

-   For counts over time and for crude rates over time
    QUARTERLY/STATES -
    <https://data.cdc.gov/NCHS/AH-Quarterly-Excess-Deaths-by-State-Sex-Age-and-Ra/jqg8-ycmh>

<!-- -->

-   Also uses Chart 2 data for monthly/national statistics.

Population data looks like this before processing:

``` r
head(df3, n=10)
```

    ## # A tibble: 10 × 8
    ##    Notes States  `States Code` Ethnicity   `Ethnicity Code` Race     `Race Code`
    ##    <chr> <chr>   <chr>         <chr>       <chr>            <chr>    <chr>      
    ##  1 <NA>  Alabama 01            Hispanic o… 2135-2           America… 1002-5     
    ##  2 <NA>  Alabama 01            Hispanic o… 2135-2           Asian    A          
    ##  3 <NA>  Alabama 01            Hispanic o… 2135-2           Black o… 2054-5     
    ##  4 <NA>  Alabama 01            Hispanic o… 2135-2           Native … NHOPI      
    ##  5 <NA>  Alabama 01            Hispanic o… 2135-2           White    2106-3     
    ##  6 <NA>  Alabama 01            Hispanic o… 2135-2           More th… M          
    ##  7 Total Alabama 01            Hispanic o… 2135-2           <NA>     <NA>       
    ##  8 <NA>  Alabama 01            Not Hispan… 2186-5           America… 1002-5     
    ##  9 <NA>  Alabama 01            Not Hispan… 2186-5           Asian    A          
    ## 10 <NA>  Alabama 01            Not Hispan… 2186-5           Black o… 2054-5     
    ## # … with 1 more variable: Population <dbl>

Mortality data looks like this:

``` r
slice_sample(df5, n=10)
```

    ##    State     StateName                                          RaceEthnicity
    ## 1     MI      Michigan                              All Race/Ethnicity Groups
    ## 2     NH New Hampshire                                     Non-Hispanic White
    ## 3     KS        Kansas                              All Race/Ethnicity Groups
    ## 4     SD  South Dakota                                     Non-Hispanic Asian
    ## 5     NH New Hampshire                                                  Other
    ## 6     ID         Idaho Non-Hispanic Native Hawaiian or Other Pacific Islander
    ## 7     OH          Ohio                                                  Other
    ## 8     TX         Texas                                     Non-Hispanic Black
    ## 9     HI        Hawaii Non-Hispanic Native Hawaiian or Other Pacific Islander
    ## 10    RI  Rhode Island          Non-Hispanic American Indian or Alaska Native
    ##           Sex    AgeGroup Year
    ## 1  Female (F)  0-14 Years 2016
    ## 2   All Sexes 65-74 Years 2018
    ## 3    Male (M)    All Ages 2020
    ## 4   All Sexes 50-64 Years 2016
    ## 5   All Sexes 75-84 Years 2021
    ## 6    Male (M)         85+ 2020
    ## 7  Female (F)    All Ages 2020
    ## 8  Female (F) 50-54 Years 2020
    ## 9    Male (M)    All Ages 2020
    ## 10 Female (F)         85+ 2016
    ##                                                    Quarter
    ## 1                                                Quarter 4
    ## 2                                                Quarter 2
    ## 3  Cumulative from 2020, Quarter 2 through 2021, Quarter 1
    ## 4                                             All Quarters
    ## 5                                                Quarter 3
    ## 6                                             All Quarters
    ## 7  Cumulative from 2020, Quarter 2 through 2021, Quarter 3
    ## 8                                             All Quarters
    ## 9                                                Quarter 4
    ## 10                                               Quarter 4
    ##                                                YearQuarter Start.Date
    ## 1                                          2016, Quarter 4 10/01/2016
    ## 2                                          2018, Quarter 2 04/01/2018
    ## 3  Cumulative from 2020, Quarter 2 through 2021, Quarter 1 04/01/2020
    ## 4                                       2016, All Quarters 01/01/2016
    ## 5                                          2021, Quarter 3 07/01/2021
    ## 6                                       2020, All Quarters 01/01/2020
    ## 7  Cumulative from 2020, Quarter 2 through 2021, Quarter 3 04/01/2020
    ## 8                                       2020, All Quarters 01/01/2020
    ## 9                                          2020, Quarter 4 10/01/2020
    ## 10                                         2016, Quarter 4 10/01/2016
    ##      End.Date Deaths..weighted. COVID19..weighted. Deaths..unweighted.
    ## 1  12/31/2016               103                  0                 103
    ## 2  06/30/2018               552                  0                 552
    ## 3  03/31/2021             16738               2612               16738
    ## 4  12/31/2016                NA                  0                  NA
    ## 5  09/30/2021                25                 NA                  25
    ## 6  12/31/2020                NA                 NA                  NA
    ## 7  09/30/2021               368                 22                 368
    ## 8  12/31/2020               724                 74                 724
    ## 9  12/31/2020               155                 26                 155
    ## 10 12/31/2016                NA                  0                  NA
    ##    COVID19..unweighted. Time.Period Average.number.of.deaths..weighted.
    ## 1                     0   2015-2019                                 108
    ## 2                     0   2015-2019                                 501
    ## 3                  2612        2021                               16738
    ## 4                     0        2021                                  NA
    ## 5                    NA        2021                                  25
    ## 6                    NA        2021                                  NA
    ## 7                    22        2021                                 368
    ## 8                    74        2021                                 724
    ## 9                    26        2020                                 155
    ## 10                    0   2015-2019                                  NA
    ##    Average.number.of.deaths..unweighted. Number.above.average..weighted.
    ## 1                                    108                              NA
    ## 2                                    501                              NA
    ## 3                                  16738                            3605
    ## 4                                     NA                              NA
    ## 5                                     25                              24
    ## 6                                     NA                              NA
    ## 7                                    368                             218
    ## 8                                    724                              97
    ## 9                                    155                              52
    ## 10                                    NA                              NA
    ##    Percent.above.average..weighted. Number.above.average..unweighted.
    ## 1                                NA                                NA
    ## 2                                NA                                NA
    ## 3                              27.4                              3605
    ## 4                                NA                                NA
    ## 5                            2400.0                                24
    ## 6                                NA                                NA
    ## 7                             145.3                               218
    ## 8                              15.5                                97
    ## 9                              50.5                                52
    ## 10                               NA                                NA
    ##    Percent.above.average..unweighted. AnalysisDate
    ## 1                                  NA   02/20/2022
    ## 2                                  NA   02/20/2022
    ## 3                                27.4   02/20/2022
    ## 4                                  NA   02/20/2022
    ## 5                              2400.0   02/20/2022
    ## 6                                  NA   02/20/2022
    ## 7                               145.3   02/20/2022
    ## 8                                15.5   02/20/2022
    ## 9                                50.5   02/20/2022
    ## 10                                 NA   02/20/2022
    ##                                                                                                                   Suppression
    ## 1                                                                                                                            
    ## 2                                                                                                                            
    ## 3                                                                                                                            
    ## 4  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 5  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 6  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 7                                                                                                                            
    ## 8                                                                                                                            
    ## 9                                                                                                                            
    ## 10 One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ##                                          Footnote
    ## 1                                                
    ## 2                                                
    ## 3                                                
    ## 4                                                
    ## 5  Data may be incomplete in recent time periods.
    ## 6                                                
    ## 7                                                
    ## 8                                                
    ## 9                                                
    ## 10                                               
    ##                                                                 Type
    ## 1                                                Quarterly Estimates
    ## 2                                                Quarterly Estimates
    ## 3  Cumulative Estimates From 2020, Quarter 2 Through 2021, Quarter 1
    ## 4                                                   Annual Estimates
    ## 5                                                Quarterly Estimates
    ## 6                                                   Annual Estimates
    ## 7  Cumulative Estimates From 2020, Quarter 2 Through 2021, Quarter 3
    ## 8                                                   Annual Estimates
    ## 9                                                Quarterly Estimates
    ## 10                                               Quarterly Estimates

Processed in Notebook 1

-   Filtered mortality data to just include the cumulative quarterly
    COVID death counts data where available (e.g. “Cumulative from 2020,
    Quarter 2 through 2021, Quarter 4”,) as well as Quarter 1 and
    Quarter 2 for 2020 data separately, as those did not have a
    cumulative figure. Also filtered such that AgeGroup = All Ages, Sex
    = All Sexes, and Year = 2020-2022.

-   Filtered population data for just the types of race/ethnicity groups
    needed (Hispanic, Non-Hispanic Black, Non-Hispanic White,
    Non-Hispanic Native American, Non-Hispanic Pacific Islander,
    Non-Hispanic Asian), and renamed into simplified names. Combined
    with US totals population data as compiled for Chart 2.

-   Merged population data with mortality data

-   There are ready-made cumulative data points starting with Q2-Q3 of
    2020 (then Q2-Q4 of 2020, then Q2 2020 - Q1 2021, etc. Added Q1
    deaths to totals from rest of time periods to get true cumulative
    figures by quarter

-   New York City and the rest of New York state are reportedly
    separately from CDC - so these are combined into true totals for New
    York state

-   Calculated cumulative death rates by quarter by dividing cumulative
    deaths per group over their respective population

-   Combined quarterly state data with national monthly data, using
    “End.Date” as a common date-time column

-   Selected just columns needed for chart (year-month and the
    cumulative monthly rates for the 7 race/ethnicity groups)

``` r
slice_sample(chart_4_Q_export, n=10)
```

    ## # A tibble: 10 × 11
    ##    End.Date   State         YearQuarter  YearMonth Latino Indigenous Asian Black
    ##    <date>     <chr>         <chr>        <chr>      <dbl>      <dbl> <dbl> <dbl>
    ##  1 2021-03-31 Maryland      Cumulative … 3/2021     129.        75.1  86.0 185. 
    ##  2 2021-12-31 Arizona       Cumulative … 12/2021    291.       709.  169.  240. 
    ##  3 2021-06-30 California    Cumulative … 6/2021     201.       195.  137.  189. 
    ##  4 2020-12-31 Texas         Cumulative … 12/2020    139.        67.0  41.2  96.8
    ##  5 2021-03-31 Maine         Cumulative … 3/2021      NA         NA    NA    48.9
    ##  6 2020-12-31 West Virginia Cumulative … 12/2020     NA         NA    NA    74.4
    ##  7 2021-12-31 Illinois      Cumulative … 12/2021    190.       108.  124.  279. 
    ##  8 2021-12-31 Wyoming       Cumulative … 12/2021    204.       615.   NA    NA  
    ##  9 2020-09-30 Illinois      Cumulative … 9/2020      76.9       51.2  49.6 115. 
    ## 10 2021-12-31 Maine         Cumulative … 12/2021     NA        114.   NA    75.5
    ## # … with 3 more variables: Pacific Islander <dbl>, White <dbl>,
    ## #   More than one race <dbl>

### CHART 5

**Quarterly death counts over time, adding together each month for
cumulative counts, for US states + Monthly death counts over time,
adding together each month for cumulative counts, for US total (from
Chart 2)**

Data downloaded:

-   Uses data created in making Chart 2/Chart 4, but selects cumulative
    counts instead of rates to export

Processed in Notebook 1

``` r
slice_sample(chart_5_export, n=10)
```

    ## # A tibble: 10 × 11
    ##    End.Date   State         YearQuarter      White Latino Black Asian Indigenous
    ##    <date>     <chr>         <chr>            <dbl>  <dbl> <dbl> <dbl>      <dbl>
    ##  1 2021-03-31 Indiana       Cumulative from… 10931    497  1330   116         16
    ##  2 2021-06-30 Kentucky      Cumulative from…  6868    121   672    38         NA
    ##  3 2020-12-31 Hawaii        Cumulative from…    31     22    NA   183         NA
    ##  4 2021-09-30 Texas         Cumulative from… 32238  31578  8008  1398        133
    ##  5 2020-03-31 Nevada        2020, Quarter 1     16     NA    NA    NA          0
    ##  6 2021-09-30 Mississippi   Cumulative from…  5340    107  3774    43        127
    ##  7 2021-09-30 Idaho         Cumulative from…  2647    296    14    32         51
    ##  8 2020-06-30 Connecticut   2020, Quarter 2   3212    421   680    56         NA
    ##  9 2020-09-30 Washington    Cumulative from…  1395    303    64   152         57
    ## 10 2020-02-29 United States <NA>                17      4     7     1          0
    ## # … with 3 more variables: More than one race <dbl>, Pacific Islander <dbl>,
    ## #   End.Date2 <chr>

### CHART 7

**Cumulative death counts for entire pandemic**

Data downloaded:

-   For total counts and cumulative crude rates and age adjusted rates —
    <https://data.cdc.gov/NCHS/Distribution-of-COVID-19-Deaths-and-Populations-by/jwta-jxbg>

``` r
slice_sample(df4, n=10)
```

    ##    Data.as.of Start.Date   End.Date         State
    ## 1  03/09/2022 01/01/2020 03/05/2022      Kentucky
    ## 2  03/09/2022 01/01/2020 03/05/2022         Idaho
    ## 3  03/09/2022 01/01/2020 03/05/2022   Mississippi
    ## 4  03/09/2022 01/01/2020 03/05/2022        Oregon
    ## 5  03/09/2022 01/01/2020 03/05/2022      Missouri
    ## 6  03/09/2022 01/01/2020 03/05/2022        Alaska
    ## 7  03/09/2022 01/01/2020 03/05/2022  Pennsylvania
    ## 8  03/09/2022 01/01/2020 03/05/2022 Massachusetts
    ## 9  03/09/2022 01/01/2020 03/05/2022     Wisconsin
    ## 10 03/09/2022 01/01/2020 03/05/2022      Arkansas
    ##                                      Race.Hispanic.origin
    ## 1                                                Hispanic
    ## 2                                      Non-Hispanic Black
    ## 3  Non-Hispanic Native Hawaiian or Other Pacific Islander
    ## 4           Non-Hispanic American Indian or Alaska Native
    ## 5                                      Non-Hispanic Black
    ## 6                                      Non-Hispanic Asian
    ## 7                                      Non-Hispanic White
    ## 8                                                   Other
    ## 9                                                Hispanic
    ## 10                                                  Other
    ##    Count.of.COVID.19.deaths Distribution.of.COVID.19.deaths....
    ## 1                      11.0                                 8.6
    ## 2                        NA                                  NA
    ## 3                       0.0                                 0.0
    ## 4                      11.0                                 2.2
    ## 5                      82.0                                17.4
    ## 6                      21.0                                 7.8
    ## 7                      60.0                                61.9
    ## 8                      12.3                                 2.0
    ## 9                     144.0                                 8.7
    ## 10                       NA                                  NA
    ##    Unweighted.distribution.of.population....
    ## 1                                        4.6
    ## 2                                        0.2
    ## 3                                        0.0
    ## 4                                        1.1
    ## 5                                       11.5
    ## 6                                        6.0
    ## 7                                       66.3
    ## 8                                        2.1
    ## 9                                        3.3
    ## 10                                       1.9
    ##    Weighted.distribution.of.population....
    ## 1                                      6.5
    ## 2                                      0.1
    ## 3                                      0.0
    ## 4                                      0.8
    ## 5                                     19.8
    ## 6                                      8.7
    ## 7                                     54.0
    ## 8                                      2.1
    ## 9                                      6.0
    ## 10                                     2.2
    ##    Difference.between.COVID.19.and.unweighted.population..
    ## 1                                                      4.0
    ## 2                                                       NA
    ## 3                                                      0.0
    ## 4                                                      1.1
    ## 5                                                      5.9
    ## 6                                                      1.8
    ## 7                                                     -4.4
    ## 8                                                     -0.1
    ## 9                                                      5.4
    ## 10                                                      NA
    ##    Difference.between.COVID.19.and.weighted.population..               AgeGroup
    ## 1                                                    2.1            25-34 years
    ## 2                                                     NA            75-84 years
    ## 3                                                    0.0             0-24 years
    ## 4                                                    1.4 All ages, standardized
    ## 5                                                   -2.4            35-44 years
    ## 6                                                   -0.9            75-84 years
    ## 7                                                    7.9             0-24 years
    ## 8                                                   -0.1 All ages, standardized
    ## 9                                                    2.7            55-64 years
    ## 10                                                    NA            25-34 years
    ##                Suppression
    ## 1                         
    ## 2  Suppressed (counts <10)
    ## 3                         
    ## 4                         
    ## 5                         
    ## 6                         
    ## 7                         
    ## 8                         
    ## 9                         
    ## 10 Suppressed (counts <10)

Processed in Notebook 2

-   Filtered for all ages (un-adjusted), selected variables needed
    (state, race/ethnicity, count of deaths), and renamed race/ethnicity
    groups

-   New York City and the rest of New York state are reportedly
    separately from CDC - so these are combined into true totals for New
    York state

-   Selected variables needed (End Date, State, Race/Ethnicity and Total
    Deaths) and exported

``` r
slice_sample(chart_7_export, n=10)
```

    ##      End.Date         State   Race.Ethnicity Count.of.COVID.19.deaths
    ## 1  03/05/2022      Colorado            Black                      538
    ## 2  03/05/2022     Tennessee Pacific Islander                       18
    ## 3  03/05/2022        Nevada            White                    5,784
    ## 4  03/05/2022          Iowa           Latino                      278
    ## 5  03/05/2022       Arizona       Indigenous                    2,192
    ## 6  03/05/2022 United States       Indigenous                   10,568
    ## 7  03/05/2022 Massachusetts           Latino                    1,437
    ## 8  03/05/2022      Maryland            Asian                      508
    ## 9  03/05/2022  South Dakota Pacific Islander                       NA
    ## 10 03/05/2022      Virginia       Indigenous                       27

### KEY FINDINGS

**Cumulative stats to date, for US total**

Data downloaded:

-   Same mortality data as for chart 7, same population data as for
    chart 2

Processed in Notebook 2

-   Combined mortality data from chart 7 with US total population data,
    processed the same as it was for chart 2.

-   Calculated crude rates by dividing count of death per population and
    multiplying by 100,000, and calculated one in X number of people
    died by dividing population by count of deaths.

-   Extracted data points and wrote text file.

``` r
text
```

    ## [1] "As of the week ending 2022-03-05"                                                                                                                                                                                                                                                                                                                                                                                                            
    ## [2] "1 in 394 Hispanic Americans has died (or 254 per 100,000)"                                                                                                                                                                                                                                                                                                                                                                                   
    ## [3] "1 in 319 White Americans has died (or 313 per 100,000)"                                                                                                                                                                                                                                                                                                                                                                                      
    ## [4] "1 in 303 Black Americans has died (or 330 per 100,000)"                                                                                                                                                                                                                                                                                                                                                                                      
    ## [5] "1 in 230 Indigenouss has died (or 434 per 100,000)"                                                                                                                                                                                                                                                                                                                                                                                          
    ## [6] "1 in 298 Pacific Islander Americans has died (or 336 per 100,000)"                                                                                                                                                                                                                                                                                                                                                                           
    ## [7] "1 in 641 Asian Americans has died (or 156 per 100,000)"                                                                                                                                                                                                                                                                                                                                                                                      
    ## [8] "Of the 957483 cumulative U.S. deaths catalogued in this Color of Coronavirus update, these are the known numbers of lives lost by group: \n                 Asian (30236), \n                 Black (136818), \n                 Indigenous (10568), \n                 Latino (155531), \n                 Pacific Islander (2061) and \n                 White Americans (616025). Additionally, (6244) deaths are recorded as other race."

### CHART 6

**Cumulative crude rates, by state and for US total + Age adjusted
rates, by state and for US total**

Date downloaded:

-   For age adjustment, national population by age groups, 2020 Census
    via CDC WONDER -

    -   Non Hispanic:
        <https://wonder.cdc.gov/controller/saved/D170/D279F896>

    -   Hispanic:
        <https://wonder.cdc.gov/controller/saved/D170/D279F900>

Non Hispanic as example:

``` r
slice_sample(df6, n=10)
```

    ## # A tibble: 10 × 8
    ##    Notes     Ethnicity   `Ethnicity Code` Race      `Race Code` `Ten-Year Age G…
    ##    <chr>     <chr>       <chr>            <chr>     <chr>       <chr>           
    ##  1 <NA>      Not Hispan… 2186-5           Black or… 2054-5      85+ years       
    ##  2 <NA>      Not Hispan… 2186-5           Native H… NHOPI       55-64 years     
    ##  3 <NA>      Not Hispan… 2186-5           American… 1002-5      1-4 years       
    ##  4 <NA>      Not Hispan… 2186-5           Native H… NHOPI       < 1 year        
    ##  5 <NA>      Not Hispan… 2186-5           White     2106-3      5-14 years      
    ##  6 <NA>      Not Hispan… 2186-5           White     2106-3      < 1 year        
    ##  7 Total     Not Hispan… 2186-5           Asian     A           <NA>            
    ##  8 <NA>      Not Hispan… 2186-5           American… 1002-5      65-74 years     
    ##  9 Ethnicit… <NA>        <NA>             <NA>      <NA>        <NA>            
    ## 10 ---       <NA>        <NA>             <NA>      <NA>        <NA>            
    ## # … with 2 more variables: Ten-Year Age Groups Code <chr>, Population <dbl>

-   For age adjustment, state populations by age groups, 2020 Census via
    CDC WONDER -

    -   Non hispanic:
        <https://wonder.cdc.gov/controller/saved/D170/D279F915>

    -   Hispanic:
        <https://wonder.cdc.gov/controller/saved/D170/D279F916>

Hispanic as example:

``` r
slice_sample(df9, n=10)
```

    ## # A tibble: 10 × 6
    ##    Notes States    `States Code` `Ten-Year Age Gr… `Ten-Year Age Gro… Population
    ##    <chr> <chr>     <chr>         <chr>             <chr>                   <dbl>
    ##  1 <NA>  Delaware  10            85+ years         85+                       555
    ##  2 <NA>  Wisconsin 55            45-54 years       45-54                   43823
    ##  3 <NA>  New York  36            75-84 years       75-84                  116664
    ##  4 <NA>  Idaho     16            5-14 years        5-14                    48324
    ##  5 <NA>  Mississi… 28            35-44 years       35-44                   15939
    ##  6 <NA>  Arkansas  05            25-34 years       25-34                   37075
    ##  7 <NA>  Maine     23            65-74 years       65-74                    1056
    ##  8 <NA>  Illinois  17            55-64 years       55-64                  180065
    ##  9 <NA>  Texas     48            5-14 years        5-14                  2069289
    ## 10 <NA>  District… 11            1-4 years         1-4                      6179

-   Imported mortality data from Chart 7

-   Same state population data as Chart 4

Processed in Notebook 2

-   **Crude rates:**

    -   Combined mortality data from Chart 7 with population data as
        also calculated in Chart 4 to get mortality rates per 100,000
        for each race/ethnicity group in each state

    -   Saved as dataframe

-   **Indirect age adjustment**

    -   See [tutorial
        here](http://papp.iussp.org/sessions/papp101_s06/PAPP101_s06_010_010.html)
        on age adjustments, as well as [this helpful
        video](https://www.youtube.com/watch?v=DOEstU62D4w)

    -   First calculated crude COVID-19 mortality rates per age bracket,
        at the national level for all race/ethnicity groups combined -
        this is the “standard” mortality rate per age group

        -   Loaded population data separated by age groups (hispanic and
            non-hispanic first loaded separately then combined).

        -   Combined population data to get age groupings used in
            mortality data - 0-24, 25-34, 35-44, 45-54, 55-64, 65-74,
            75-84, 85+

        -   Loaded mortality data – same underlying data as for chart 7,
            but instead of all groups combined we want the
            dis-aggregated age groupings, for the US as a whole

        -   Summed mortality data from each race/ethnicity group to get
            the combined mortality rate per age bracket (i.e. added
            together Latino, White, Black, Asian, Pacific Islander and
            Indigenous deaths from the 55-64 age bracket to get the
            total deaths from this age bracket, and repeated for the
            other age brackets). This become the ‘crude standard’ used
            to calculate ‘estimated deaths’.

    -   Indirect age adjustment - loading data (these steps for national
        and state level data):

        -   Loaded population data separated by age groups (hispanic and
            non-hispanic first loaded separately then combined).

        -   Combined population data to get age groupings, by
            race/ethnicity group and for each state and nationally, as
            used in mortality data - 0-24, 25-34, 35-44, 45-54, 55-64,
            65-74, 75-84, 85+

    -   Indirect age adjustment - calculation:

        -   For all states and nationally, calculated estimated deaths
            per race and age group by multiplying the ‘crude standard’
            by the actual population in each race/age grouping. This
            gives an estimate of how many deaths would be expected in a
            race/age grouping if the mortality rate were the same as at
            the national level at that age grouping, for all races.

        -   Added together estimated death rates of age groups, for each
            race group separately, for all states/national (e.g. add
            together death rates by age group for all Hispanic people in
            Iowa to get a total estimated death rate for Hispanics in
            Iowa).

        -   Merged with data on actual deaths from chart_7 file and
            calculate standardized mortality ratio (SMR), which is the
            ratio of actual deaths by race over estimated deaths by race
            (e.g. actual rate of Hispanic Iowans who died over the the
            estimated rate of Hispanic Iowans who died).

        -   Multiplied each racial group’s SMR by the overall national
            crude rate of deaths to get age adjusted mortality by race.

-   **Direct age adjustment**

    -   Direct age adjustment - loading data:

        -   Loaded mortality data – same underlying data as for chart 7,
            but instead of all groups combined we want the
            dis-aggregated age groupings, for the US as a whole and for
            states separately

        -   New York City and the rest of New York state are reportedly
            separately from CDC - so these are combined into true totals
            for New York state

        -   Filtered for just the race/ethnicity groups by state for
            which there are no NAs - meaning every age bracket within a
            race/state group must have either 0 deaths or more than 9
            deaths.

        -   Merged with population data for the remaining race/age/state
            groupings

    -   Direct age adjustment - calculation:

        -   Calculated the crude mortality rate for each race/age/state
            grouping

        -   Calculated the population weighting for each age grouping
            (based on population of national age groups divided by total
            national population)

        -   Multiplied the crude mortality rate for each race/age/state
            grouping (i.e. a row in the below preview) by the population
            weighting of the age group nationally, this gives a
            “weighted deaths” measure for that race/age/state

        ``` r
        head(age_adjusted_direct, n=10)
        ```

            ## # A tibble: 10 × 11
            ## # Groups:   State [1]
            ##    State   Race.Ethnicity sumNA Data.as.of End.Date   Count.of.COVID.1… AgeGroup
            ##    <chr>   <chr>          <int> <chr>      <chr>                  <dbl> <chr>   
            ##  1 Alabama Black              0 03/09/2022 03/05/2022               104 25-34 y…
            ##  2 Alabama Black              0 03/09/2022 03/05/2022                23 0-24 ye…
            ##  3 Alabama Black              0 03/09/2022 03/05/2022               274 35-44 y…
            ##  4 Alabama Black              0 03/09/2022 03/05/2022               547 45-54 y…
            ##  5 Alabama Black              0 03/09/2022 03/05/2022              1070 55-64 y…
            ##  6 Alabama Black              0 03/09/2022 03/05/2022               653 85+ yea…
            ##  7 Alabama Black              0 03/09/2022 03/05/2022              1369 65-74 y…
            ##  8 Alabama Black              0 03/09/2022 03/05/2022               998 75-84 y…
            ##  9 Alabama White              0 03/09/2022 03/05/2022               104 25-34 y…
            ## 10 Alabama White              0 03/09/2022 03/05/2022                19 0-24 ye…
            ## # … with 4 more variables: Population <dbl>, crude_rate_group <dbl>,
            ## #   pop_weight <dbl>, weighted_deaths_by_age <dbl>

        -   Summed the weighted deaths for each race/state to get the
            direct age adjusted rate for a race and state

-   Exporting

    -   Combined crude, indirect age adjusted and direct age adjusted
        rates into one dataframe

    -   Created a variable for a final age adjusted rate, using direct
        where available and indirect otherwise. Remove indirect age
        adjusted rates where it’s based on less than 200 deaths, since
        statistical method may not be as accurate.

    -   Created a variable indicating whether direct or indirect method
        was used as the final age adjusted rate

    -   Selected just relevant variables for chart 6 and export. Removed
        ‘other’ race/ethnicity since population data not available for
        this racial definition. Made data ‘wide’ for viz purposes.

``` r
slice_sample(chart_6_export, n=10)
```

    ##      End.Date         State   Race.Ethnicity Number of COVID-19 Deaths
    ## 1  03/05/2022       Vermont            Black                        NA
    ## 2  03/05/2022       Montana            White                     2,801
    ## 3  03/05/2022 Massachusetts           Latino                     1,437
    ## 4  03/05/2022      Nebraska           Latino                       301
    ## 5  03/05/2022        Kansas            Black                       524
    ## 6  03/05/2022    California           Latino                    40,703
    ## 7  03/05/2022     Wisconsin            Black                       953
    ## 8  03/05/2022      Illinois Pacific Islander                        NA
    ## 9  03/05/2022      Delaware            Asian                        29
    ## 10 03/05/2022       Arizona            White                    14,704
    ##    Population Crude Rate age_adjusted_rate_direct age_adjusted_rate_indirect
    ## 1        8225         NA                       NA                         NA
    ## 2      925921        303                       NA                   259.0855
    ## 3      867425        166                 371.2328                   350.7747
    ## 4      225592        133                       NA                   389.3747
    ## 5      167190        313                       NA                   457.5700
    ## 6    15569780        261                 466.5393                   476.6689
    ## 7      373222        255                       NA                   458.1329
    ## 8        3701         NA                       NA                         NA
    ## 9       40773         71                       NA                         NA
    ## 10    3993464        368                 251.3304                   253.7610
    ##    Direct_Available Age-Adjusted Rate
    ## 1             FALSE                NA
    ## 2             FALSE               259
    ## 3              TRUE               371
    ## 4             FALSE               389
    ## 5             FALSE               458
    ## 6              TRUE               467
    ## 7             FALSE               458
    ## 8             FALSE                NA
    ## 9             FALSE                NA
    ## 10             TRUE               251

### CHART 3

**Age-adjusted rates, for US total**

Use same data calculated in Chart 6, just export US national numbers
only. Uses direct age adjusted calculation.

``` r
chart_3_export
```

    ##     End.Date         State   Race.Ethnicity Crude Rate Age-Adjusted Rate
    ## 1 03/05/2022 United States            White        313               256
    ## 2 03/05/2022 United States            Black        330               428
    ## 3 03/05/2022 United States       Indigenous        434               532
    ## 4 03/05/2022 United States            Asian        156               192
    ## 5 03/05/2022 United States Pacific Islander        336               449
    ## 6 03/05/2022 United States           Latino        254               460
    ##   Number of COVID-19 Deaths
    ## 1                   616,025
    ## 2                   136,818
    ## 3                    10,568
    ## 4                    30,236
    ## 5                     2,061
    ## 6                   155,531

### MAPS

**Maps with age adjusted rates + number of deaths on hover**

Data downloaded:

-   Used chart 6 data

Processed in Notebook 2

-   Filter data to create different dataset for each race/ethnicity
    group

-   Export

Example from Hispanic dataset

``` r
slice_sample(hispanic, n=10)
```

    ##            State Race.Ethnicity Crude Rate Age-Adjusted Rate
    ## 1  New Hampshire         Latino         92                NA
    ## 2     New Jersey         Latino        316               527
    ## 3         Kansas         Latino        191               495
    ## 4       Oklahoma         Latino        201               551
    ## 5        Vermont         Latino         NA                NA
    ## 6   North Dakota         Latino        162                NA
    ## 7        Arizona         Latino        321               615
    ## 8      Minnesota         Latino        114               342
    ## 9   Pennsylvania         Latino        168               397
    ## 10  Rhode Island         Latino        125               271
    ##    Number of COVID-19 Deaths
    ## 1                         53
    ## 2                      5,929
    ## 3                        693
    ## 4                        910
    ## 5                         NA
    ## 6                         54
    ## 7                      7,597
    ## 8                        368
    ## 9                      1,737
    ## 10                       220

  
