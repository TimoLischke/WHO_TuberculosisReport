# WHO_TuberculosisReport
Correlation and prediction of Tuberculosis incidences according to socialeconomic and environmental circumstances

Landing webpage:
https://www.who.int/teams/global-tuberculosis-programme/tb-reports/global-tuberculosis-report-2024

Info:
https://en.wikipedia.org/wiki/Tuberculosis 
https://en.wikipedia.org/wiki/BCG_vaccine 
https://cdn.who.int/media/docs/default-source/global-tuberculosis-report-2024/who_global-tb-report-2024_infographics_full.pdf?sfvrsn=203f6d58_7
https://www.who.int/teams/global-tuberculosis-programme/tb-reports/global-tuberculosis-report-2024/tb-prevention-and-screening
https://www.worlddata.info/countrycodes.php

Tuberculosis Incidence Data Set by WHO:
https://www.who.int/teams/global-tuberculosis-programme/data
https://data.europa.eu/data/datasets/tuberculosis-data

Data Enrichment:
Jupyter Notebook: data_acquisition.ipynb
TB specific factors: multidrug resistance, specifically rifampicin resistance:
https://www.who.int/teams/global-tuberculosis-programme/data 
Healthcare System Factors:
BCG vaccination rate / coverage by WHO:
https://immunizationdata.who.int/global/wiise-detail-page/bacillus-calmette-gu%C3%A9rin-(bcg)-vaccination-coverage?GROUP=Countries&YEAR=&CODE= 
Smoking rates (%) per country for 2022 downloaded here:
https://worldpopulationreview.com/country-rankings/smoking-rates-by-country 
Population Density per Country for 2023 (people/km²) was web scraped from Earth Database:
https://database.earth/population/density/2023 
Poverty Index as Excel File available from United Nations Human Development Report:
https://hdr.undp.org/content/2023-global-multidimensional-poverty-index-mpi 
Country coordinates (not needed, cause OpenMeteo did not give meaningful results):
https://developers.google.com/public-data/docs/canonical/countries_csv
Air pollution data (annual average PM2.5 concentration in μg/m³) for 2023 was web scraped from IQAIR:
https://www.iqair.com/us/world-most-polluted-countries 
Air pollution data (annual average PM2.5 concentration in μg/m³) for 2019 was downloaded from WHO:
https://www.who.int/data/gho/data/themes/air-pollution/who-air-quality-database

Data cleaning & wrangling:
Jupyter Notebook: data_cleaning.ipynb
Dropping all unnecessary column, dropping all rows of years other than 2023
Adding contry iso2 and iso3 codes when missing to all additional data tables
Checking for null values and duplicates 
Filling all missing values with NaN 
Merging selected columns of all additional data tables to the df_TB_burden on "iso3"
Safe the cleaned and enriched data file as: df_TB_burden_enriched

Exploratory Data Analysis:


Project Presentation:
https://www.canva.com/design/DAGgMWLzK3s/rlaceoHXzFSAwmsJoI3y2w/edit 

