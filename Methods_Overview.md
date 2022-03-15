Color of Coronavirus Methods Overview
================

### by APM Research Lab

**Methods are listed here in the order they are calculated in Notebook_1
and Notebook_2.**

## Notebook 1

**Metrics over time since the start of the COVID-19 pandemic** (Charts
1, 2, 4 and 5)

### CHART 1

**Monthly deaths count time series for US combined, by race/ethnicity
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
    ## 1  03/09/2022 12/01/2020 12/31/2020 2020    12 By Month        Hawaii
    ## 2  03/09/2022 11/01/2021 11/30/2021 2021    11 By Month West Virginia
    ## 3  03/09/2022 08/01/2021 08/31/2021 2021     8 By Month      Arkansas
    ## 4  03/09/2022 10/01/2021 10/31/2021 2021    10 By Month       Vermont
    ## 5  03/09/2022 11/01/2021 11/30/2021 2021    11 By Month  Rhode Island
    ## 6  03/09/2022 06/01/2020 06/30/2020 2020     6 By Month       Arizona
    ## 7  03/09/2022 08/01/2021 08/31/2021 2021     8 By Month        Nevada
    ## 8  03/09/2022 03/01/2021 03/31/2021 2021     3 By Month      Maryland
    ## 9  03/09/2022 10/01/2020 10/31/2020 2020    10 By Month  Pennsylvania
    ## 10 03/09/2022 04/01/2021 04/30/2021 2021     4 By Month       Alabama
    ##                                    Indicator Non.Hispanic.White
    ## 1        Distribution of COVID-19 deaths (%)                 NA
    ## 2        Distribution of COVID-19 deaths (%)               96.4
    ## 3  Unweighted distribution of population (%)               71.7
    ## 4        Distribution of COVID-19 deaths (%)               97.6
    ## 5                   Count of COVID-19 deaths               62.0
    ## 6    Weighted distribution of population (%)               53.8
    ## 7    Weighted distribution of population (%)               41.5
    ## 8  Unweighted distribution of population (%)               49.5
    ## 9        Distribution of COVID-19 deaths (%)               87.5
    ## 10       Distribution of COVID-19 deaths (%)               61.1
    ##    Non.Hispanic.Black.or.African.American
    ## 1                                     0.0
    ## 2                                     2.7
    ## 3                                    15.4
    ## 4                                     0.0
    ## 5                                      NA
    ## 6                                     5.5
    ## 7                                    11.7
    ## 8                                    30.1
    ## 9                                     6.7
    ## 10                                   36.6
    ##    Non.Hispanic.American.Indian.or.Alaska.Native Non.Hispanic.Asian
    ## 1                                            0.0               31.4
    ## 2                                            0.0                 NA
    ## 3                                            0.8                1.7
    ## 4                                             NA                0.0
    ## 5                                             NA                 NA
    ## 6                                            1.7                4.3
    ## 7                                            0.5               10.0
    ## 8                                            0.2                6.7
    ## 9                                            0.0                1.7
    ## 10                                           0.0                 NA
    ##    Non.Hispanic.Native.Hawaiian.or.Other.Pacific.Islander
    ## 1                                                    31.4
    ## 2                                                     0.0
    ## 3                                                     0.4
    ## 4                                                     0.0
    ## 5                                                     0.0
    ## 6                                                     0.2
    ## 7                                                     0.7
    ## 8                                                     0.1
    ## 9                                                     0.0
    ## 10                                                    0.0
    ##    Non.Hispanic.more.than.one.race Hispanic.or.Latino
    ## 1                               NA                 NA
    ## 2                              0.0                 NA
    ## 3                              2.0                8.0
    ## 4                              0.0                0.0
    ## 5                               NA                 NA
    ## 6                              2.3               32.1
    ## 7                              4.0               31.6
    ## 8                              2.6               10.8
    ## 9                              0.0                4.1
    ## 10                              NA                 NA
    ##                                                                                                                      Footnote
    ## 1  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 2  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 3                                                                                                                            
    ## 4  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 5  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
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

    ##    State  StateName                                 RaceEthnicity        Sex
    ## 1     UT       Utah Non-Hispanic American Indian or Alaska Native   Male (M)
    ## 2     NM New Mexico                     All Race/Ethnicity Groups Female (F)
    ## 3     MO   Missouri                                         Other Female (F)
    ## 4     VA   Virginia                                         Other   Male (M)
    ## 5     LA  Louisiana                            Non-Hispanic Asian   Male (M)
    ## 6     TN  Tennessee                            Non-Hispanic White Female (F)
    ## 7     NY   New York Non-Hispanic American Indian or Alaska Native   Male (M)
    ## 8     MT    Montana Non-Hispanic American Indian or Alaska Native   Male (M)
    ## 9     MD   Maryland                            Non-Hispanic White Female (F)
    ## 10    MD   Maryland                     All Race/Ethnicity Groups  All Sexes
    ##       AgeGroup Year                                                 Quarter
    ## 1  50-64 Years 2020 Cumulative from 2020, Quarter 2 through 2021, Quarter 4
    ## 2  75-84 Years 2017                                               Quarter 3
    ## 3  50-54 Years 2021                                               Quarter 1
    ## 4  50-64 Years 2016                                               Quarter 3
    ## 5          85+ 2021                                               Quarter 3
    ## 6  75-84 Years 2020                                               Quarter 4
    ## 7  65-74 Years 2020 Cumulative from 2020, Quarter 2 through 2021, Quarter 4
    ## 8   0-14 Years 2017                                               Quarter 3
    ## 9  50-54 Years 2016                                               Quarter 2
    ## 10    All Ages 2016                                               Quarter 2
    ##                                                YearQuarter Start.Date
    ## 1  Cumulative from 2020, Quarter 2 through 2021, Quarter 4 04/01/2020
    ## 2                                          2017, Quarter 3 07/01/2017
    ## 3                                          2021, Quarter 1 01/01/2021
    ## 4                                          2016, Quarter 3 07/01/2016
    ## 5                                          2021, Quarter 3 07/01/2021
    ## 6                                          2020, Quarter 4 10/01/2020
    ## 7  Cumulative from 2020, Quarter 2 through 2021, Quarter 4 04/01/2020
    ## 8                                          2017, Quarter 3 07/01/2017
    ## 9                                          2016, Quarter 2 04/01/2016
    ## 10                                         2016, Quarter 2 04/01/2016
    ##      End.Date Deaths..weighted. COVID19..weighted. Deaths..unweighted.
    ## 1  12/31/2021                54                 13                  54
    ## 2  09/30/2017               412                  0                 412
    ## 3  03/31/2021                NA                  0                  NA
    ## 4  09/30/2016                17                  0                  17
    ## 5  09/30/2021                NA                  0                  NA
    ## 6  12/31/2020              2705                617                2705
    ## 7  12/31/2021                62                 15                  62
    ## 8  09/30/2017                NA                  0                  NA
    ## 9  06/30/2016               103                  0                 103
    ## 10 06/30/2016             11872                  0               11872
    ##    COVID19..unweighted. Time.Period Average.number.of.deaths..weighted.
    ## 1                    13        2021                                  54
    ## 2                     0   2015-2019                                 438
    ## 3                     0        2021                                  NA
    ## 4                     0   2015-2019                                  16
    ## 5                     0        2021                                  NA
    ## 6                   617        2020                                2705
    ## 7                    15        2021                                  62
    ## 8                     0   2015-2019                                  NA
    ## 9                     0   2015-2019                                  99
    ## 10                    0   2015-2019                               11926
    ##    Average.number.of.deaths..unweighted. Number.above.average..weighted.
    ## 1                                     54                              18
    ## 2                                    438                              NA
    ## 3                                     NA                              NA
    ## 4                                     16                              NA
    ## 5                                     NA                              NA
    ## 6                                   2705                             743
    ## 7                                     62                              16
    ## 8                                     NA                              NA
    ## 9                                     99                              NA
    ## 10                                 11926                              NA
    ##    Percent.above.average..weighted. Number.above.average..unweighted.
    ## 1                              50.0                                18
    ## 2                                NA                                NA
    ## 3                                NA                                NA
    ## 4                                NA                                NA
    ## 5                                NA                                NA
    ## 6                              37.9                               743
    ## 7                              34.8                                16
    ## 8                                NA                                NA
    ## 9                                NA                                NA
    ## 10                               NA                                NA
    ##    Percent.above.average..unweighted. AnalysisDate
    ## 1                                50.0   02/20/2022
    ## 2                                  NA   02/20/2022
    ## 3                                  NA   02/20/2022
    ## 4                                  NA   02/20/2022
    ## 5                                  NA   02/20/2022
    ## 6                                37.9   02/20/2022
    ## 7                                34.8   02/20/2022
    ## 8                                  NA   02/20/2022
    ## 9                                  NA   02/20/2022
    ## 10                                 NA   02/20/2022
    ##                                                                                                                   Suppression
    ## 1                                                                                                                            
    ## 2                                                                                                                            
    ## 3  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 4                                                                                                                            
    ## 5  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 6                                                                                                                            
    ## 7                                                                                                                            
    ## 8  One or more data cells have counts between 1-9 and have been suppressed in accordance with NCHS confidentiality standards.
    ## 9                                                                                                                            
    ## 10                                                                                                                           
    ##                                          Footnote
    ## 1                                                
    ## 2                                                
    ## 3  Data may be incomplete in recent time periods.
    ## 4                                                
    ## 5  Data may be incomplete in recent time periods.
    ## 6                                                
    ## 7                                                
    ## 8                                                
    ## 9                                                
    ## 10                                               
    ##                                                                 Type
    ## 1  Cumulative Estimates From 2020, Quarter 2 Through 2021, Quarter 4
    ## 2                                                Quarterly Estimates
    ## 3                                                Quarterly Estimates
    ## 4                                                Quarterly Estimates
    ## 5                                                Quarterly Estimates
    ## 6                                                Quarterly Estimates
    ## 7  Cumulative Estimates From 2020, Quarter 2 Through 2021, Quarter 4
    ## 8                                                Quarterly Estimates
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
    ##    End.Date   State          YearQuarter YearMonth Latino Indigenous Asian Black
    ##    <date>     <chr>          <chr>       <chr>      <dbl>      <dbl> <dbl> <dbl>
    ##  1 2020-12-31 Florida        Cumulative… 12/2020    100.        55.0  48.0 118. 
    ##  2 2021-09-30 New Hampshire  Cumulative… 9/2021      60.9        0    36.4  72.8
    ##  3 2021-12-31 South Carolina Cumulative… 12/2021    127.       257.  106.  327. 
    ##  4 2021-03-31 Massachusetts  Cumulative… 3/2021     120.        96.1  85.8 196. 
    ##  5 2021-12-31 Utah           Cumulative… 12/2021    104.       408.  106.   65.7
    ##  6 2020-06-30 Indiana        2020, Quar… 6/2020      21.3       NA    17.7  83.2
    ##  7 2021-03-31 New Jersey     Cumulative… 3/2021     252.       117.  155.  329. 
    ##  8 2021-06-30 Texas          Cumulative… 6/2021     217.       103.   78.5 165. 
    ##  9 2021-09-30 Alaska         Cumulative… 9/2021      39.2      172.  140.   55.0
    ## 10 2021-03-31 Utah           Cumulative… 3/2021      77.8      309.   82.5  49.9
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
    ##  1 2021-03-31 Ohio          Cumulative from… 18374    377  2713   193         13
    ##  2 2020-09-30 Oklahoma      Cumulative from…   932    100    93    23        159
    ##  3 2021-06-30 Montana       Cumulative from…  1311     45    11    NA        291
    ##  4 2020-03-31 Wisconsin     2020, Quarter 1     20     NA    20    NA          0
    ##  5 2021-03-31 Minnesota     Cumulative from…  6165    210   354   285         97
    ##  6 2020-06-30 Kansas        2020, Quarter 2    177     44    58    NA         NA
    ##  7 2020-01-31 United States <NA>                 2      1     2     0          0
    ##  8 2021-12-31 Pennsylvania  Cumulative from… 32180   1497  4338   627         23
    ##  9 2020-09-30 Vermont       Cumulative from…    61      0     0    NA          0
    ## 10 2020-12-31 Texas         Cumulative from… 13038  16262  3472   629         64
    ## # … with 3 more variables: More than one race <dbl>, Pacific Islander <dbl>,
    ## #   End.Date2 <chr>

------------------------------------------------------------------------

## Notebook 2

**Cumulative numbers over the course of the COVID-19 pandemic** (Chart
7, Key Findings, Chart 6, Chart 3 and Maps)

### CHART 7

**Cumulative death counts for entire pandemic**

Data downloaded:

-   For total counts and cumulative crude rates and age adjusted rates —
    <https://data.cdc.gov/NCHS/Distribution-of-COVID-19-Deaths-and-Populations-by/jwta-jxbg>

``` r
slice_sample(df4, n=10)
```

    ##    Data.as.of Start.Date   End.Date         State
    ## 1  03/09/2022 01/01/2020 03/05/2022 United States
    ## 2  03/09/2022 01/01/2020 03/05/2022      Illinois
    ## 3  03/09/2022 01/01/2020 03/05/2022    New Jersey
    ## 4  03/09/2022 01/01/2020 03/05/2022       Georgia
    ## 5  03/09/2022 01/01/2020 03/05/2022    New Mexico
    ## 6  03/09/2022 01/01/2020 03/05/2022  Pennsylvania
    ## 7  03/09/2022 01/01/2020 03/05/2022 West Virginia
    ## 8  03/09/2022 01/01/2020 03/05/2022 West Virginia
    ## 9  03/09/2022 01/01/2020 03/05/2022       Wyoming
    ## 10 03/09/2022 01/01/2020 03/05/2022       Indiana
    ##                                      Race.Hispanic.origin
    ## 1                                      Non-Hispanic Asian
    ## 2           Non-Hispanic American Indian or Alaska Native
    ## 3                                      Non-Hispanic White
    ## 4           Non-Hispanic American Indian or Alaska Native
    ## 5                                                   Other
    ## 6                                      Non-Hispanic Black
    ## 7                                                Hispanic
    ## 8                                                Hispanic
    ## 9  Non-Hispanic Native Hawaiian or Other Pacific Islander
    ## 10                                     Non-Hispanic White
    ##    Count.of.COVID.19.deaths Distribution.of.COVID.19.deaths....
    ## 1                      7200                                 3.3
    ## 2                        NA                                  NA
    ## 3                      5123                                62.7
    ## 4                        11                                 0.1
    ## 5                         0                                 0.0
    ## 6                      4982                                11.1
    ## 7                        NA                                  NA
    ## 8                        NA                                  NA
    ## 9                         0                                 0.0
    ## 10                     2411                                78.6
    ##    Unweighted.distribution.of.population....
    ## 1                                        4.8
    ## 2                                        0.2
    ## 3                                       71.3
    ## 4                                        0.3
    ## 5                                        2.6
    ## 6                                       10.9
    ## 7                                        0.6
    ## 8                                        2.2
    ## 9                                        0.1
    ## 10                                      85.6
    ##    Weighted.distribution.of.population....
    ## 1                                     10.1
    ## 2                                      0.1
    ## 3                                     68.1
    ## 4                                      0.2
    ## 5                                      2.9
    ## 6                                     18.7
    ## 7                                      0.6
    ## 8                                      2.1
    ## 9                                      0.1
    ## 10                                    72.6
    ##    Difference.between.COVID.19.and.unweighted.population..
    ## 1                                                     -1.5
    ## 2                                                       NA
    ## 3                                                     -8.6
    ## 4                                                     -0.2
    ## 5                                                     -2.6
    ## 6                                                      0.2
    ## 7                                                       NA
    ## 8                                                       NA
    ## 9                                                     -0.1
    ## 10                                                    -7.0
    ##    Difference.between.COVID.19.and.weighted.population..             AgeGroup
    ## 1                                                   -6.8          65-74 years
    ## 2                                                     NA          45-54 years
    ## 3                                                   -5.4          75-84 years
    ## 4                                                   -0.1          75-84 years
    ## 5                                                   -2.9           0-24 years
    ## 6                                                   -7.6 All ages, unadjusted
    ## 7                                                     NA          75-84 years
    ## 8                                                     NA          35-44 years
    ## 9                                                   -0.1           0-24 years
    ## 10                                                   6.0          55-64 years
    ##                Suppression
    ## 1                         
    ## 2  Suppressed (counts <10)
    ## 3                         
    ## 4                         
    ## 5                         
    ## 6                         
    ## 7  Suppressed (counts <10)
    ## 8  Suppressed (counts <10)
    ## 9                         
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

    ##      End.Date         State   Race.Ethnicity Count.of.COVID.19.deaths
    ## 1  03/05/2022 New Hampshire            Other                       11
    ## 2  03/05/2022        Alaska            White                      609
    ## 3  03/05/2022         Texas            White                   41,071
    ## 4  03/05/2022      New York            Black                   13,470
    ## 5  03/05/2022          Ohio Pacific Islander                       NA
    ## 6  03/05/2022    Washington Pacific Islander                      215
    ## 7  03/05/2022       Wyoming            Asian                       NA
    ## 8  03/05/2022       Vermont            Other                        0
    ## 9  03/05/2022   Connecticut            Other                       49
    ## 10 03/05/2022        Kansas       Indigenous                       89

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
    ##  1 Show Zero … <NA>        <NA>             <NA>    <NA>        <NA>            
    ##  2 were prepa… <NA>        <NA>             <NA>    <NA>        <NA>            
    ##  3 <NA>        Not Hispan… 2186-5           Americ… 1002-5      85+ years       
    ##  4 Total       Not Hispan… 2186-5           Native… NHOPI       <NA>            
    ##  5 <NA>        Not Hispan… 2186-5           Black … 2054-5      25-34 years     
    ##  6 <NA>        Not Hispan… 2186-5           Native… NHOPI       5-14 years      
    ##  7 <NA>        Not Hispan… 2186-5           Americ… 1002-5      25-34 years     
    ##  8 ---         <NA>        <NA>             <NA>    <NA>        <NA>            
    ##  9 <NA>        Not Hispan… 2186-5           Asian   A           35-44 years     
    ## 10 single-rac… <NA>        <NA>             <NA>    <NA>        <NA>            
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
    ##    Notes      States  `States Code` `Ten-Year Age G… `Ten-Year Age G… Population
    ##    <chr>      <chr>   <chr>         <chr>            <chr>                 <dbl>
    ##  1 <NA>       Pennsy… 42            5-14 years       5-14                 194772
    ##  2 1. Estima… <NA>    <NA>          <NA>             <NA>                     NA
    ##  3 <NA>       Distri… 11            75-84 years      75-84                  1422
    ##  4 <NA>       Alabama 01            25-34 years      25-34                 31795
    ##  5 <NA>       Wiscon… 55            45-54 years      45-54                 43823
    ##  6 <NA>       Idaho   16            1-4 years        1-4                   18157
    ##  7 <NA>       Hawaii  15            85+ years        85+                     512
    ##  8 <NA>       Michig… 26            75-84 years      75-84                  8972
    ##  9 <NA>       New Yo… 36            55-64 years      55-64                377650
    ## 10 <NA>       Tennes… 47            5-14 years       5-14                  87984

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
    ## 1  03/05/2022       Wyoming            White                     1,319
    ## 2  03/05/2022 Massachusetts            Asian                       588
    ## 3  03/05/2022      Colorado       Indigenous                       166
    ## 4  03/05/2022      Missouri            Black                     2,341
    ## 5  03/05/2022  South Dakota            White                     2,496
    ## 6  03/05/2022      Arkansas Pacific Islander                        72
    ## 7  03/05/2022      New York            Black                    13,470
    ## 8  03/05/2022      Nebraska           Latino                       301
    ## 9  03/05/2022        Alaska            Asian                        96
    ## 10 03/05/2022         Idaho            Asian                        47
    ##    Population Crude Rate age_adjusted_rate_direct age_adjusted_rate_indirect
    ## 1      486788        271                 251.4996                   252.7554
    ## 2      504606        117                       NA                   182.2581
    ## 3       37021        448                       NA                         NA
    ## 4      710312        330                 434.6479                   443.9751
    ## 5      724153        345                       NA                   297.0703
    ## 6       11532        624                       NA                         NA
    ## 7     2786323        483                 536.3347                   539.0855
    ## 8      225592        133                       NA                   389.3747
    ## 9       47145        204                       NA                         NA
    ## 10      27095        173                       NA                         NA
    ##    Direct_Available Age-Adjusted Rate
    ## 1              TRUE               251
    ## 2             FALSE               182
    ## 3             FALSE                NA
    ## 4              TRUE               435
    ## 5             FALSE               297
    ## 6             FALSE                NA
    ## 7              TRUE               536
    ## 8             FALSE               389
    ## 9             FALSE                NA
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

    ##            State Race.Ethnicity Crude Rate Age-Adjusted Rate
    ## 1         Nevada         Latino        247               504
    ## 2        Montana         Latino        207                NA
    ## 3         Oregon         Latino         98               262
    ## 4         Kansas         Latino        191               495
    ## 5     New Jersey         Latino        316               527
    ## 6     California         Latino        261               467
    ## 7     Washington         Latino        112               318
    ## 8       Oklahoma         Latino        201               551
    ## 9  Massachusetts         Latino        166               371
    ## 10     Minnesota         Latino        114               342
    ##    Number of COVID-19 Deaths
    ## 1                      2,285
    ## 2                         93
    ## 3                        569
    ## 4                        693
    ## 5                      5,929
    ## 6                     40,703
    ## 7                      1,146
    ## 8                        910
    ## 9                      1,437
    ## 10                       368

  
