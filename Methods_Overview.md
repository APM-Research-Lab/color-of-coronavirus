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

    ##    Data.as.of Start.Date   End.Date Year Month    Group         State
    ## 1  03/09/2022 03/01/2020 03/31/2020 2020     3 By Month      Kentucky
    ## 2  03/09/2022 12/01/2021 12/31/2021 2021    12 By Month     Louisiana
    ## 3  03/09/2022 02/01/2021 02/28/2021 2021     2 By Month      Oklahoma
    ## 4  03/09/2022 02/01/2021 02/28/2021 2021     2 By Month      Illinois
    ## 5  03/09/2022 06/01/2020 06/30/2020 2020     6 By Month      Virginia
    ## 6  03/09/2022 07/01/2020 07/31/2020 2020     7 By Month          Utah
    ## 7  03/09/2022 08/01/2021 08/31/2021 2021     8 By Month      Illinois
    ## 8  03/09/2022 05/01/2020 05/31/2020 2020     5 By Month New Hampshire
    ## 9  03/09/2022 02/01/2020 02/29/2020 2020     2 By Month      Maryland
    ## 10 03/09/2022 09/01/2020 09/30/2020 2020     9 By Month     Tennessee
    ##                                    Indicator Non.Hispanic.White
    ## 1    Weighted distribution of population (%)               67.7
    ## 2  Unweighted distribution of population (%)               58.1
    ## 3  Unweighted distribution of population (%)               64.4
    ## 4        Distribution of COVID-19 deaths (%)               64.9
    ## 5    Weighted distribution of population (%)               51.4
    ## 6    Weighted distribution of population (%)               71.5
    ## 7                   Count of COVID-19 deaths              541.0
    ## 8    Weighted distribution of population (%)               85.1
    ## 9  Unweighted distribution of population (%)               49.5
    ## 10       Distribution of COVID-19 deaths (%)               77.0
    ##    Non.Hispanic.Black.or.African.American
    ## 1                                    20.3
    ## 2                                    32.4
    ## 3                                     7.4
    ## 4                                    15.0
    ## 5                                    14.9
    ## 6                                     1.7
    ## 7                                   131.0
    ## 8                                     2.2
    ## 9                                    30.1
    ## 10                                   19.4
    ##    Non.Hispanic.American.Indian.or.Alaska.Native Non.Hispanic.Asian
    ## 1                                            0.1                3.2
    ## 2                                            0.6                1.8
    ## 3                                            8.5                2.3
    ## 4                                            0.0                3.2
    ## 5                                            0.2               15.1
    ## 6                                            0.7                4.0
    ## 7                                            0.0               14.0
    ## 8                                            0.2                4.0
    ## 9                                            0.2                6.7
    ## 10                                           0.0                 NA
    ##    Non.Hispanic.Native.Hawaiian.or.Other.Pacific.Islander
    ## 1                                                     0.1
    ## 2                                                     0.0
    ## 3                                                     0.2
    ## 4                                                      NA
    ## 5                                                     0.1
    ## 6                                                     1.6
    ## 7                                                     0.0
    ## 8                                                     0.0
    ## 9                                                     0.1
    ## 10                                                     NA
    ##    Non.Hispanic.more.than.one.race Hispanic.or.Latino
    ## 1                              2.5                6.1
    ## 2                              1.6                5.4
    ## 3                              5.8               11.4
    ## 4                               NA               16.3
    ## 5                              3.3               14.9
    ## 6                              2.4               18.2
    ## 7                              0.0               54.0
    ## 8                              1.7                6.7
    ## 9                              2.6               10.8
    ## 10                              NA                2.7
    ##                                                                                                                      Footnote
    ## 1                                                                                                                            
    ## 2                                                                                                                            
    ## 3                                                                                                                            
    ## 4  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 5                                                                                                                            
    ## 6                                                                                                                            
    ## 7                                                                                                                            
    ## 8                                                                                                                            
    ## 9                                                                                                                            
    ## 10 One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.

Processed in Notebook 1:

-   Filtered such that “Group = By Month”, “State = United States”, and
    “Indicator = Count of COVID-19 deaths”

-   Race/ethnicity names shortened for consistent labeling/ease of
    reading

-   Column created for year-month for ease of use in Flourish

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
    cumulative deaths per group over their respective populations  and
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
    ## 1     SD  South Dakota                                     Non-Hispanic Black
    ## 2     MA Massachusetts                              All Race/Ethnicity Groups
    ## 3     AL       Alabama Non-Hispanic Native Hawaiian or Other Pacific Islander
    ## 4     MS   Mississippi                              All Race/Ethnicity Groups
    ## 5     GA       Georgia                                               Hispanic
    ## 6     CT   Connecticut                                     Non-Hispanic Black
    ## 7     NJ    New Jersey                                     Non-Hispanic White
    ## 8     CA    California                              All Race/Ethnicity Groups
    ## 9     AZ       Arizona                                     Non-Hispanic Asian
    ## 10    AR      Arkansas          Non-Hispanic American Indian or Alaska Native
    ##           Sex    AgeGroup Year
    ## 1    Male (M) 50-64 Years 2016
    ## 2  Female (F) 50-54 Years 2017
    ## 3    Male (M) 30-49 Years 2016
    ## 4  Female (F) 50-64 Years 2020
    ## 5  Female (F)         85+ 2016
    ## 6    Male (M) 65-74 Years 2017
    ## 7   All Sexes 30-49 Years 2020
    ## 8   All Sexes 50-54 Years 2020
    ## 9   All Sexes 65-74 Years 2020
    ## 10  All Sexes         85+ 2021
    ##                                                    Quarter
    ## 1                                                Quarter 4
    ## 2                                                Quarter 4
    ## 3                                                Quarter 3
    ## 4  Cumulative from 2020, Quarter 2 through 2021, Quarter 2
    ## 5                                                Quarter 1
    ## 6                                                Quarter 4
    ## 7  Cumulative from 2020, Quarter 2 through 2021, Quarter 1
    ## 8                                                Quarter 3
    ## 9  Cumulative from 2020, Quarter 2 through 2020, Quarter 4
    ## 10                                               Quarter 4
    ##                                                YearQuarter Start.Date
    ## 1                                          2016, Quarter 4 10/01/2016
    ## 2                                          2017, Quarter 4 10/01/2017
    ## 3                                          2016, Quarter 3 07/01/2016
    ## 4  Cumulative from 2020, Quarter 2 through 2021, Quarter 2 04/01/2020
    ## 5                                          2016, Quarter 1 01/01/2016
    ## 6                                          2017, Quarter 4 10/01/2017
    ## 7  Cumulative from 2020, Quarter 2 through 2021, Quarter 1 04/01/2020
    ## 8                                          2020, Quarter 3 07/01/2020
    ## 9  Cumulative from 2020, Quarter 2 through 2020, Quarter 4 04/01/2020
    ## 10                                         2021, Quarter 4 10/01/2021
    ##      End.Date Deaths..weighted. COVID19..weighted. Deaths..unweighted.
    ## 1  12/31/2016                NA                  0                  NA
    ## 2  12/31/2017               174                  0                 174
    ## 3  09/30/2016                NA                  0                  NA
    ## 4  06/30/2021              3066                511                3066
    ## 5  03/31/2016                34                  0                  34
    ## 6  12/31/2017                73                  0                  73
    ## 7  03/31/2021              2478                183                2478
    ## 8  09/30/2020              2986                434                2986
    ## 9  12/31/2020               154                 34                 154
    ## 10 12/31/2021                NA                  0                  NA
    ##    COVID19..unweighted. Time.Period Average.number.of.deaths..weighted.
    ## 1                     0   2015-2019                                  NA
    ## 2                     0   2015-2019                                 179
    ## 3                     0   2015-2019                                  NA
    ## 4                   511        2021                                3066
    ## 5                     0   2015-2019                                  44
    ## 6                     0   2015-2019                                  72
    ## 7                   183        2021                                2478
    ## 8                   434        2020                                2986
    ## 9                    34        2021                                 154
    ## 10                    0        2021                                  NA
    ##    Average.number.of.deaths..unweighted. Number.above.average..weighted.
    ## 1                                     NA                              NA
    ## 2                                    179                              NA
    ## 3                                     NA                              NA
    ## 4                                   3066                             617
    ## 5                                     44                              NA
    ## 6                                     72                              NA
    ## 7                                   2478                             193
    ## 8                                   2986                             619
    ## 9                                    154                              49
    ## 10                                    NA                              NA
    ##    Percent.above.average..weighted. Number.above.average..unweighted.
    ## 1                                NA                                NA
    ## 2                                NA                                NA
    ## 3                                NA                                NA
    ## 4                              25.2                               617
    ## 5                                NA                                NA
    ## 6                                NA                                NA
    ## 7                               8.4                               193
    ## 8                              26.2                               619
    ## 9                              46.7                                49
    ## 10                               NA                                NA
    ##    Percent.above.average..unweighted. AnalysisDate
    ## 1                                  NA   02/20/2022
    ## 2                                  NA   02/20/2022
    ## 3                                  NA   02/20/2022
    ## 4                                25.2   02/20/2022
    ## 5                                  NA   02/20/2022
    ## 6                                  NA   02/20/2022
    ## 7                                 8.4   02/20/2022
    ## 8                                26.2   02/20/2022
    ## 9                                46.7   02/20/2022
    ## 10                                 NA   02/20/2022
    ##                                                                                                                   Suppression
    ## 1  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 2                                                                                                                            
    ## 3  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 4                                                                                                                            
    ## 5                                                                                                                            
    ## 6                                                                                                                            
    ## 7                                                                                                                            
    ## 8                                                                                                                            
    ## 9                                                                                                                            
    ## 10 One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ##                                          Footnote
    ## 1                                                
    ## 2                                                
    ## 3                                                
    ## 4                                                
    ## 5                                                
    ## 6                                                
    ## 7                                                
    ## 8                                                
    ## 9                                                
    ## 10 Data may be incomplete in recent time periods.
    ##                                                                 Type
    ## 1                                                Quarterly Estimates
    ## 2                                                Quarterly Estimates
    ## 3                                                Quarterly Estimates
    ## 4  Cumulative Estimates From 2020, Quarter 2 Through 2021, Quarter 2
    ## 5                                                Quarterly Estimates
    ## 6                                                Quarterly Estimates
    ## 7  Cumulative Estimates From 2020, Quarter 2 Through 2021, Quarter 1
    ## 8                                                Quarterly Estimates
    ## 9  Cumulative Estimates From 2020, Quarter 2 Through 2020, Quarter 4
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
    ##  1 2021-06-30 Nebraska      Cumulative … 6/2021      98.9      130.   48.3 119. 
    ##  2 2020-12-31 South Dakota  Cumulative … 12/2020     50.5      275.  123.   NA  
    ##  3 2021-09-30 Montana       Cumulative … 9/2021     138.       499.  116.  240. 
    ##  4 2020-12-31 Ohio          Cumulative … 12/2020     52.2       44.2  47.0 130. 
    ##  5 2020-05-31 United States <NA>         5/2020      30.1       31.6  28.8  63.8
    ##  6 2020-06-30 Montana       2020, Quart… 6/2020      NA         NA     0     0  
    ##  7 2021-12-31 Alaska        Cumulative … 12/2021     57.9      229.  170.   88.9
    ##  8 2021-03-31 Florida       Cumulative … 3/2021     140.        84.4  73.3 161. 
    ##  9 2022-01-31 United States <NA>         1/2022     247.       420.  151.  322. 
    ## 10 2020-09-30 Kansas        Cumulative … 9/2020      34.0       65.1  16.5  64.6
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
    ##    End.Date   State         YearQuarter     White Latino  Black Asian Indigenous
    ##    <date>     <chr>         <chr>           <dbl>  <dbl>  <dbl> <dbl>      <dbl>
    ##  1 2021-12-31 United States <NA>           536183 142521 123023 27247       9621
    ##  2 2021-09-30 Indiana       Cumulative fr…  13450    637   1659   129         20
    ##  3 2021-10-31 United States <NA>           478301 133840 115966 25942       8641
    ##  4 2021-06-30 New Hampshire Cumulative fr…   1284     33     13    15          0
    ##  5 2020-06-30 Connecticut   2020, Quarter…   3212    421    680    56         NA
    ##  6 2021-09-30 Maine         Cumulative fr…   1129     NA     12    NA         NA
    ##  7 2020-03-31 Delaware      2020, Quarter…     NA     NA     NA     0          0
    ##  8 2020-06-30 New York      2020, Quarter…  12502   8112   7749  2451         20
    ##  9 2021-03-31 Alaska        Cumulative fr…    122     15     NA    35        111
    ## 10 2020-03-31 Ohio          2020, Quarter…     82     NA     14     0          0
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

    ##    Data.as.of Start.Date   End.Date        State
    ## 1  03/09/2022 01/01/2020 03/05/2022       Alaska
    ## 2  03/09/2022 01/01/2020 03/05/2022 Pennsylvania
    ## 3  03/09/2022 01/01/2020 03/05/2022   New Jersey
    ## 4  03/09/2022 01/01/2020 03/05/2022  Mississippi
    ## 5  03/09/2022 01/01/2020 03/05/2022    Tennessee
    ## 6  03/09/2022 01/01/2020 03/05/2022     Colorado
    ## 7  03/09/2022 01/01/2020 03/05/2022         Iowa
    ## 8  03/09/2022 01/01/2020 03/05/2022     Virginia
    ## 9  03/09/2022 01/01/2020 03/05/2022     Colorado
    ## 10 03/09/2022 01/01/2020 03/05/2022      Florida
    ##                                      Race.Hispanic.origin
    ## 1                                                   Other
    ## 2  Non-Hispanic Native Hawaiian or Other Pacific Islander
    ## 3           Non-Hispanic American Indian or Alaska Native
    ## 4                                      Non-Hispanic Black
    ## 5                                      Non-Hispanic White
    ## 6                                      Non-Hispanic Asian
    ## 7                                      Non-Hispanic Black
    ## 8                                      Non-Hispanic White
    ## 9           Non-Hispanic American Indian or Alaska Native
    ## 10                                                  Other
    ##    Count.of.COVID.19.deaths Distribution.of.COVID.19.deaths....
    ## 1                        NA                                  NA
    ## 2                        NA                                  NA
    ## 3                        NA                                  NA
    ## 4                     967.0                                45.8
    ## 5                      49.0                                50.5
    ## 6                      12.0                                 3.7
    ## 7                      13.0                                20.3
    ## 8                     640.2                                44.5
    ## 9                        NA                                  NA
    ## 10                     51.0                                 0.3
    ##    Unweighted.distribution.of.population....
    ## 1                                        2.0
    ## 2                                        0.0
    ## 3                                        0.1
    ## 4                                       34.9
    ## 5                                       65.4
    ## 6                                        4.1
    ## 7                                        5.8
    ## 8                                       59.6
    ## 9                                        0.8
    ## 10                                       0.7
    ##    Weighted.distribution.of.population....
    ## 1                                      1.4
    ## 2                                      0.0
    ## 3                                      0.1
    ## 4                                     42.1
    ## 5                                     47.3
    ## 6                                      4.4
    ## 7                                      8.2
    ## 8                                     52.2
    ## 9                                      0.6
    ## 10                                     0.7
    ##    Difference.between.COVID.19.and.unweighted.population..
    ## 1                                                       NA
    ## 2                                                       NA
    ## 3                                                       NA
    ## 4                                                     10.9
    ## 5                                                    -14.9
    ## 6                                                     -0.4
    ## 7                                                     14.5
    ## 8                                                    -15.1
    ## 9                                                       NA
    ## 10                                                    -0.4
    ##    Difference.between.COVID.19.and.weighted.population..               AgeGroup
    ## 1                                                     NA            75-84 years
    ## 2                                                     NA            65-74 years
    ## 3                                                     NA            55-64 years
    ## 4                                                    3.7            55-64 years
    ## 5                                                    3.2             0-24 years
    ## 6                                                   -0.7            35-44 years
    ## 7                                                   12.1            25-34 years
    ## 8                                                   -7.7 All ages, standardized
    ## 9                                                     NA            25-34 years
    ## 10                                                  -0.4            65-74 years
    ##                Suppression
    ## 1  Suppressed (counts <10)
    ## 2  Suppressed (counts <10)
    ## 3  Suppressed (counts <10)
    ## 4                         
    ## 5                         
    ## 6                         
    ## 7                         
    ## 8                         
    ## 9  Suppressed (counts <10)
    ## 10

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

    ##      End.Date        State   Race.Ethnicity Count.of.COVID.19.deaths
    ## 1  03/05/2022    Wisconsin            White                   12,200
    ## 2  03/05/2022     Virginia            Other                      118
    ## 3  03/05/2022     Nebraska           Latino                      301
    ## 4  03/05/2022       Nevada            Other                      107
    ## 5  03/05/2022    Wisconsin            Asian                      252
    ## 6  03/05/2022      Vermont           Latino                       NA
    ## 7  03/05/2022 South Dakota            White                    2,496
    ## 8  03/05/2022     Colorado            Asian                      314
    ## 9  03/05/2022       Kansas Pacific Islander                       13
    ## 10 03/05/2022     New York            Asian                    4,806

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
    ##    Notes       Ethnicity   `Ethnicity Code` Race    `Race Code` `Ten-Year Age G…
    ##    <chr>       <chr>       <chr>            <chr>   <chr>       <chr>           
    ##  1 <NA>        Not Hispan… 2186-5           Native… NHOPI       5-14 years      
    ##  2 <NA>        Not Hispan… 2186-5           Americ… 1002-5      45-54 years     
    ##  3 single-rac… <NA>        <NA>             <NA>    <NA>        <NA>            
    ##  4 Show Zero … <NA>        <NA>             <NA>    <NA>        <NA>            
    ##  5 <NA>        Not Hispan… 2186-5           Americ… 1002-5      85+ years       
    ##  6 <NA>        Not Hispan… 2186-5           Native… NHOPI       55-64 years     
    ##  7 <NA>        Not Hispan… 2186-5           Black … 2054-5      65-74 years     
    ##  8 <NA>        Not Hispan… 2186-5           White   2106-3      5-14 years      
    ##  9 <NA>        Not Hispan… 2186-5           Americ… 1002-5      15-24 years     
    ## 10 <NA>        Not Hispan… 2186-5           Native… NHOPI       75-84 years     
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
    ##    Notes States   `States Code` `Ten-Year Age Gro… `Ten-Year Age Gro… Population
    ##    <chr> <chr>    <chr>         <chr>              <chr>                   <dbl>
    ##  1 <NA>  Kansas   20            35-44 years        35-44                   48230
    ##  2 <NA>  Connect… 09            15-24 years        15-24                  101486
    ##  3 <NA>  Wiscons… 55            35-44 years        35-44                   60278
    ##  4 <NA>  North D… 38            1-4 years          1-4                      3731
    ##  5 <NA>  Iowa     19            35-44 years        35-44                   27740
    ##  6 <NA>  Michigan 26            < 1 year           1                        8420
    ##  7 <NA>  Missouri 29            35-44 years        35-44                   38673
    ##  8 <NA>  Missouri 29            65-74 years        65-74                    9752
    ##  9 <NA>  Massach… 25            65-74 years        65-74                   36533
    ## 10 <NA>  Rhode I… 44            < 1 year           1                        3173

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

    ##      End.Date          State   Race.Ethnicity Number of COVID-19 Deaths
    ## 1  03/05/2022 North Carolina            Black                     6,040
    ## 2  03/05/2022         Nevada            Asian                       992
    ## 3  03/05/2022       New York           Latino                    13,475
    ## 4  03/05/2022        Indiana            Asian                       149
    ## 5  03/05/2022     Washington            Asian                       656
    ## 6  03/05/2022       Oklahoma           Latino                       910
    ## 7  03/05/2022         Kansas            Asian                       117
    ## 8  03/05/2022      Wisconsin            Asian                       252
    ## 9  03/05/2022           Ohio            Asian                       318
    ## 10 03/05/2022       Illinois Pacific Islander                        NA
    ##    Population Crude Rate age_adjusted_rate_direct age_adjusted_rate_indirect
    ## 1     2259862        267                 328.2908                   334.7663
    ## 2      266907        372                       NA                   359.3290
    ## 3     3738921        360                 526.7414                   529.2791
    ## 4      175596         85                       NA                         NA
    ## 5      738981         89                       NA                   119.3306
    ## 6      452487        201                 551.2005                   588.3936
    ## 7       90899        129                       NA                         NA
    ## 8      179656        140                       NA                   315.1474
    ## 9      300068        106                       NA                   177.5033
    ## 10       3701         NA                       NA                         NA
    ##    Direct_Available Age-Adjusted Rate
    ## 1              TRUE               328
    ## 2             FALSE               359
    ## 3              TRUE               527
    ## 4             FALSE                NA
    ## 5             FALSE               119
    ## 6              TRUE               551
    ## 7             FALSE                NA
    ## 8             FALSE               315
    ## 9             FALSE               178
    ## 10            FALSE                NA

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

    ##                   State Race.Ethnicity Crude Rate Age-Adjusted Rate
    ## 1  District of Columbia         Latino        266               579
    ## 2          Pennsylvania         Latino        168               397
    ## 3               Wyoming         Latino        227                NA
    ## 4                  Ohio         Latino        151               346
    ## 5                Hawaii         Latino         66                NA
    ## 6                  Utah         Latino        135               366
    ## 7               Vermont         Latino         NA                NA
    ## 8             Wisconsin         Latino        153               419
    ## 9            New Mexico         Latino        295               386
    ## 10             Maryland         Latino        168               366
    ##    Number of COVID-19 Deaths
    ## 1                        216
    ## 2                      1,737
    ## 3                        137
    ## 4                        739
    ## 5                        101
    ## 6                        635
    ## 7                         NA
    ## 8                        653
    ## 9                      3,085
    ## 10                     1,097

  
