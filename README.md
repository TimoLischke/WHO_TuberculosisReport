WHO_TuberculosisReport_2024 --> reporting the TB incidence numbers for 2023
Correlation and prediction of Tuberculosis incidences and severity level according to health, socialeconomic and environmental factors

Objective:
Use the WHO dataset on tuberculosis (TB) incidences per country for 2023.
Enrich the dataset with further health, socialeconomic and environmental data.
Make predictions using supervised machine learning models about TB incidences and severity level.

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
Jupyter Notebook: exploratory_data_analysis.ipynb
Some more data polishing: reduce length of country names for the longest 12 country names
Remove duplicated "Congo" rows. (Only Democratic Republic of Congo kept. Congo dropped.)
Replace iso2 code for Namibia: NaN --> NA.
Add calculated value: TB incidence rate in percent "e_tb_inc_prct":
df_TB_burden_enriched["e_tb_inc_prct"] = (df_TB_burden_enriched["e_inc_num"] / df_TB_burden_enriched["e_pop_num"]) * 100
Add categorical value: Categorization of the tuberculosis incidence rate (%)
in the column "e_tb_inc_prct" into tuberculosis severity levels "tb_severity":
Based on SD intervals: 0.1 (Mean), 0.244 (Mean to Mean + 1 SD), & 0.388 (Mean + 1 SD to Mean + 2 SD) --> 5 Levels
"Very Low <= 0.05; "Low" <= 0.1, "Moderate" <= 0.244, "High" <= 0.388, "Critical" >= 0.388
Create histograms of all columns.
Visualization: Display top 5 countries per world region according to: 
TB incidences, treatment resistance, BCG vaccination rate, population density, poverty index, smoking rates, air pollution
Create Pie Charts of Tuberculosis severity per world region

Supervised machine learning models to predict TB incidence and severity level:
Jupyter Notebook: machine_learning.ipynb
Translation of categorical string values in the column "TB_severity" into integers stored in "TB_severity_level":
Very Low = 1, Low = 2, Moderate = 3, High = 4, Critical = 5
Feature engineering: Draw a correlation map for features with target column
Select 3 + 6 feature columns.
Select target column: TB_severity_level 
Train/Test data splitting: 80% + 20%
Normlization: MinMax Scaler for standardization
Checking balance of target data (TB severity level)
Supervised machine learning models to predict Tuberculosis severity level
Feature columns contain NaN values. This limits the number of models that can be used.
Running Ensemble ML Modelling Methods: HistGradientBoostingClassifier & RandomForestClassifier
Evaluation of both models according to accuracy & F1-score.
Visualization of the Feature Importance in the Random Forest Classifier Model.
Visualization of the Decision Tree nodes of the first tree in the Random Forest.
Target Data Balancing & Class Weight Balancing to improve Random Forest Classifier model prediction.
Hyperparameter Tuning using GridSearch to improve HistGradientBoosting Classifier model prediction.



Project Presentation:
https://www.canva.com/design/DAGgMWLzK3s/rlaceoHXzFSAwmsJoI3y2w/edit 

