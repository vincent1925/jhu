# Causal Inference Analysis on Water Contaminants and Mortality in California

All the files in the california folders + stdpop.18ages.txt are files with the given data. The "cleaned_data" contains files that have been cleaned. Notes on the cleaned dataset are explained below.

Files too large for GitHub are found in [this](https://drive.google.com/drive/folders/1CFRAB6wdipsDzCsJT3llI_BiKUcJ36by?usp=sharing) Google Drive folder. Additionally, the folder has a copy of the cleaned water quality data set water.csv and the mortality data, mortality.csv

The setup for the regressions is done in Python in waterquality.qmd and the regressions are done in waterquality_r.qmd. 

The significant results of the regressions are shown in significant_results. significant_results_pop contains the same regressions but includes population as a covariate instead of an offset.

For water.csv:
- SDWIS1 through SDWIS4 were concatenated.
- Added a column called 'Sample Year' that contains the year that the sample was taken.
- Samples taken in the years 2023 and 2024 were dropped.
- Trailing whitespace in the columns "Water System Number", "Analyte Name", "Units of Measure", and "Result" were removed.
- Samples with NAN under "Result" were imputed with "Reporting Level" divided by sqrt(2)
- Samples with NAN under 'Less Than Reporting Level' were imputed with the correct value.
- Samples with "LEAD", "COPPER, FREE", "NITRITE", "NITRATE-NITRITE", and "AGGRESSIVE INDEX" as their "Analyte Name" had multiple units of measures which were then converted to the unit that was the most common.
- Note that for future use, the values for your relevant analytes that were originally NaN and thus imputed should be checked as these are common, depending on the analyte.

For mortality.csv:
- dropped the columns 'Annotation_Code','Annotation_Desc','Data_Revision_Date','ICD_Revision', and 'Geography_Type'.
- dropped rows in the years 2009 and 2010.
- only kept rows that contained all causes.
- note that there an NaN values that haven't been imputed yet.

For mortality_age.csv:
- a subset of mortality.csv that only contains mortality data by age.

For mortality_total.csv:
- a subset of mortality.csv that only contains total mortality.

For mortality_gender.csv:
- a subset of mortality.csv that only contains mortality data by gender.

For std2000:
- contains 2000 US Standard Population by age group.

For population.csv:
- data obtained through the ACS API [here](https://www.census.gov/data/developers/data-sets/acs-1year.html).
- contains data on the population in California for each zip code by age by year.

For questions, email vzheng@uchicago.edu.
