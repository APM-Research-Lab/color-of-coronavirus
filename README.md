# Color of Coronavirus 
**Analyses of COVID-19 mortality by race and ethnicity in the US**

This repository contains data, methods and code for APM Research Lab's [Color of Coronavirus project](https://www.apmresearchlab.org/covid/deaths-by-race). 

View our methods [here](https://apm-research-lab.github.io/color-of-coronavirus/Methods_Overview.html).

Our full code is in [Notebook_1](Notebook_1.Rmd) and [Notebook_2](Notebook_2.Rmd). 

Datasets as used for the graphics are in [data_from_charts](data_from_charts).

Datasets as downloaded from CDC are in [raw_data](raw_data). 
*To allow for a smaller sized dataset, the CDC file beginning with AH_Quarterly is filtered such that `(Sex == "All Sexes" & Year %in% c(2020:2022) & AgeGroup == "All Ages")` and then uploaded here as 'raw' data. 

[![DOI](https://zenodo.org/badge/470160713.svg)](https://zenodo.org/badge/latestdoi/470160713)
