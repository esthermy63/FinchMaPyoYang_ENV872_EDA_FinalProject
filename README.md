# EDE_Fall2025CP
ENV 872 course project for E. Yang, Y. Ma, J. Pyo, M. Finch.

## Summary

This repository contains the data, scripts, and outputs for our ENV 872 course project. The goal of this project is to examine federal energy and environment investment in the United States from 2021 to 2024 and to explore the social and environmental factors that may influence federal spending patterns.

We analyze investment trends over time and investigate how natural disasters, state demographic characteristics, and public awareness of climate change relate to federal allocation decisions. The project uses publicly available datasets, including federal investment records, U.S. Census population and household characteristics, FEMA disaster summaries, and state-level climate opinion data.

All data cleaning, analysis, and visualization scripts are included in this repository, and the project is fully reproducible through the R Markdown file.

## Investigators

Esther Yang, Yike Ma, Jiyeong Pyo, Morgan Finch

## Keywords

Energy
Environment
Federal spending
Natural disasters
Demographics
Climate opinion
Investment patterns

## Database Information

1. DisasterDeclarationSummaries (https://www.fema.gov/openfema-data-page/disaster-declarations-summaries-v2)

2. Federal energy and environment spending by COUNTY (https://www.pdx.edu/policy-consensus-center/sites/policyconsensuscenter.web.wdt.pdx.edu/files/2025-06/Energy%20Enviro%20Spending%20Report_FINAL060225_reduced.pdf)

3. Census data

4. All spatial data comes from us census data (retrieved from Assignment)

5. Bureau of economic analysis (https://apps.bea.gov/regional/downloadzip.htm?_gl=1*4m94vr*_ga*MTI0MDQyMTU0NS4xNzY0Mjc4MTU2*_ga_J4698JNNFT*czE3NjQyNzgxNTUkbzEkZzEkdDE3NjQyNzgyNzIkajkkbDAkaDA.)

6. State Population Totals and Components of Change: 2020-2024
(https://www.census.gov/data/tables/time-series/demo/popest/2020s-state-total.html)

7. Regulate C02 percentage data
(https://climatecommunication.yale.edu/visualizations-data/ycom-us/)
Marlon, J. R., Wang, X., Bergquist, P., Howe, P., Leiserowitz, A., Maibach, E., Mildenberger, M., and Rosenthal, S. “Change in US state-level public opinion about climate change: 2008–2020.” Environmental Research Letters 17, no. 12 (2022). 124046.



## Folder structure, file formats, and naming conventions 

FinchMaPyoYang_ENV872_EDA_FinalProject/
│
├── Data/
│   ├── Raw/              # Original datasets downloaded from external sources
│   ├── Spatial/          # Shapefiles for mapping and GIS work
│   └── Processed/        # Cleaned and merged datasets created during analysis
│
├── Scripts/              # R scripts for cleaning, wrangling, and analysis
│
├── Outputs/              # Figures, tables, and model results
│
├── Project_Template.Rmd  # Main reproducible research document (analysis + report)
│
└── README.md             # Project overview and documentation 


## Metadata

<For each data file in the repository, describe the data contained in each column. Include the column name, a description of the information, the class of data, and any units associated with the data. Create a list or table for each data file.> 

1. Federal Energy and Environment Spending by State (2010–2025)

File: Federal energy and environment spending by STATE (2010-2025).csv

This dataset contains federal spending amounts by state, by year, including both total federal spending and spending specifically in energy and environmental programs.

| Column Name                   | Description                                           | Class               | Unit               |
| ----------------------------- | ----------------------------------------------------- | ------------------- | ------------------ |
| OBJECTID                      | Internal row ID                                       | Integer             | None               |
| STATEFP                       | State FIPS code                                       | Integer             | None               |
| FIP_JOIN                      | Join field combining FIPS with prefix                 | Character           | None               |
| stname                        | State name                                            | Character           | None               |
| stusps                        | Two-letter postal abbreviation                        | Character           | None               |
| Population_2020               | State population in 2020                              | Numeric             | Persons            |
| State_UPPER                   | Uppercase state name                                  | Character           | None               |
| performancestate_cleaned      | Cleaned state name                                    | Character           | None               |
| TotalFedAction_EnergyEnv_YYYY | Federal energy and environment spending for year YYYY | Character → Numeric | Dollars            |
| TotalFedAction_YYYY           | Total federal spending for year YYYY                  | Character → Numeric | Dollars            |
| Total_PerCap_YYYY             | Per-capita total federal spending                     | Character → Numeric | Dollars per person |
| EnergyEnv_PerCap_YYYY         | Per-capita E&E spending                               | Character → Numeric | Dollars per person |
| Total_PerCap_YYYY_YYYY$       | Change in per-capita spending between years           | Character → Numeric | Dollars            |
| EnergyEnv_PerCap_YYYY_YYYY$   | Change in per-capita E&E spending between years       | Character → Numeric | Dollars            |

2. Census ACS Data (2021–2024)

Files:

ACSSPP1Y2021.S0201-2025-11-29T154845.csv

ACSSPP1Y2022.S0201-2025-11-29T154817.csv

ACSSPP1Y2023.S0201-2025-11-29T154759.csv

ACSSPP1Y2024.S0201-2025-11-29T154742.csv

Each file contains demographic and housing characteristics for U.S. states.
The structure is:

Each row is a demographic variable (example: Total population, Male, Female, Under 5 years).

Each column after the first is a state value (example: Alabama!!Total population!!Estimate).

Values include counts, percentages, or medians depending on the variable.
| Column Name                                          | Description                      | Class     | Unit       |
| ---------------------------------------------------- | -------------------------------- | --------- | ---------- |
| Label (Grouping)                                     | Name of ACS demographic variable | Character | None       |
| <state>!!Total population!!Estimate                  | Total population estimate        | Numeric   | Persons    |
| <state>!!Male!!Estimate                              | Percent male                     | Numeric   | Proportion |
| <state>!!Female!!Estimate                            | Percent female                   | Numeric   | Proportion |
| <state>!!Under 5 years!!Estimate                     | Percent under age 5              | Numeric   | Percent    |
| <state>!!5 to 17 years!!Estimate                     | Percent ages 5–17                | Numeric   | Percent    |
| <state>!!Median age (years)!!Estimate                | Median age                       | Numeric   | Years      |
| <state>!!Median household income (dollars)!!Estimate | Median household income          | Numeric   | Dollars    |
| <state>!!Gas!!Estimate                               | Percent households using gas     | Numeric   | Percent    |
| <state>!!Electricity!!Estimate                       | Percent using electricity        | Numeric   | Percent    |
| <state>!!All other fuels!!Estimate                   | Percent using other fuels        | Numeric   | Percent    |
| <state>!!No fuel used!!Estimate                      | Percent using no heating fuel    | Numeric   | Percent    |

3. FEMA DisasterDeclarationsSummaries.csv

File: DisasterDeclarationsSummaries.csv

This dataset includes all FEMA disaster declarations across U.S. states.
| Column Name           | Description                                 | Class     | Unit      |
| --------------------- | ------------------------------------------- | --------- | --------- |
| femaDeclarationString | FEMA declaration identifier                 | Character | None      |
| disasterNumber        | Numeric disaster ID                         | Integer   | None      |
| state                 | Two-letter state code                       | Character | None      |
| declarationType       | FEMA declaration type (DR, EM, FM)          | Character | None      |
| declarationDate       | Date declared                               | Character | Date      |
| fyDeclared            | Fiscal year declared                        | Integer   | Year      |
| incidentType          | Type of disaster (Fire, Flood, Storm, etc.) | Character | None      |
| incidentBeginDate     | Start date of incident                      | Character | Date      |
| incidentEndDate       | End date of incident                        | Character | Date      |
| fipsStateCode         | Numeric state code                          | Integer   | None      |
| placeCode             | County or place FIPS code                   | Integer   | None      |
| lastRefresh           | Timestamp of latest update                  | Character | Timestamp |
| id                    | Unique FEMA record identifier (UUID)        | Character | None      |

4. Regulate_percentage(2021~2024).xlsx

This dataset includes state-level climate opinion data from the Yale Program on Climate Change Communication. Specifically, it reports the percentage of adults who believe CO₂ should be regulated.

| Column Name | Description                       | Class     | Unit    |
| ----------- | --------------------------------- | --------- | ------- |
| GeoID       | Numeric state ID                  | Integer   | None    |
| GeoName     | State name                        | Character | None    |
| GeoType     | Geography type (state)            | Character | None    |
| variable    | Variable measured (“regulate”)    | Character | None    |
| 2021        | Percent supporting CO₂ regulation | Numeric   | Percent |
| 2022        | Same measure for 2022             | Numeric   | Percent |
| 2023        | Same measure for 2023             | Numeric   | Percent |
| 2024        | Same measure for 2024             | Numeric   | Percent |

## Scripts and code

| File                      | Description                                                                                                                     |
| ------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| Project_Template.Rmd      | Full reproducible analysis, including data cleaning, exploratory analysis, mapping, time series analysis, and regression models |
| Data cleaning scripts     | Located in the Rmd. These prepare Census, FEMA, and investment data for analysis                                                |
| Mapping code              | Generates spatial visualizations of investments and disasters                                                                   |
| Statistical analysis code | Runs regression models and Mann-Kendall trend tests                                                                             |

