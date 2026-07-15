# Analyzing Factors Associated with Area Burned by Wildfires in the United States
 
A statistical analysis of ~55,000 U.S. wildfires (1992–2015) using multiple linear and logistic regression to identify the environmental, geographic, and fire-related factors associated with how much area a wildfire burns.
 
*Team project by Info Innovators: Kevin Mao, Arnav Meduri, Ben Trokenheim, and Ricardo Urena. Duke University, STA 221 (Spring 2025).*
 
## Overview
 
Wildfires occur regularly across the United States and carry serious economic, environmental, and health consequences. This project asks which factors are associated with the extent of area a fire burns, with the goal of informing early wildfire response decisions. We frame the work as two questions:
 
1. Using only information available *before or at* a fire's discovery, what factors are most associated with the likelihood that a fire burns a greater-than-typical area? (a predictive question)
2. Using *all* available information, including post-containment variables, what factors help explain variability in the continuous size of the burned area? (an explanatory question)
## Data
 
The analysis draws on an integrated dataset of over 55,000 U.S. wildfire records (1992–2015) compiled from the Fire Program Analysis system, supplemented with weather data (NOAA), vegetation and land-cover data, and geographic proximity data. Predictors include fire cause, temperature, wind speed, humidity, precipitation, vegetation type, remoteness, containment time, and region. To focus on fires realistically addressable during early containment, the analysis is restricted to the interquartile range of fire sizes.
 
## Methods
 
- **Exploratory data analysis** and cleaning: filtering the response to a practical range, transforming skewed variables, and consolidating states, vegetation types, and fire causes into interpretable groups.
- **Multiple linear regression** (explanatory model) on log-transformed burned area, with forward selection, mean-centered predictors, diagnostic checks, and a variance-stabilizing transformation.
- **Logistic regression** (predictive model) on whether a fire exceeds the median burned area, using only pre-discovery predictors, evaluated with AUC and a drop-in-deviance test for interaction terms.
## Key Findings
 
- Region, cause category, vegetation type, remoteness, wind speed, temperature, containment time, and a shrubland–precipitation interaction were significantly associated with log-transformed burned area. Relative humidity and precipitation alone were not.
- Fires in shrubland and grassland, with higher wind speed and temperature and lower remoteness, had greater odds of exceeding the median burned area. Fires in the Northeast were less likely to.
- Model performance was modest by design given the noisiness of wildfire behavior and the limited predictor set (linear model R² ≈ 0.05; logistic model AUC ≈ 0.57). The value of the project is in identifying and interpreting associations, not in high predictive accuracy.
## Repository Structure
 
- `written-report.qmd` / `written-report.pdf` — the full analysis, methods, results, and discussion
- `proposal.qmd` / `proposal.pdf` — initial project proposal
- `presentation/` — project presentation materials
- `data/` — the wildfire dataset used in the analysis
- `project.Rproj` — RStudio project file
## Tools
 
Built in **R** and **Quarto**, using `tidyverse`, `tidymodels`, `rms`, `GGally`, `patchwork`, and `kableExtra`.
