# Project: HCAHPS Patient Survey Analysis
<img width="725" height="420" alt="HCAHPS Cover" src="https://github.com/user-attachments/assets/18f5f2a9-2dbf-4775-9bda-cae9873cac4e" />

## Overview

This project analyzes real HCAHPS (Hospital Consumer Assessment of Healthcare Providers and Systems) patient survey data using Power BI and Excel.

The project focuses on survey analysis, data cleaning, data modeling, visualization, and Net Promoter Score (NPS) analysis to evaluate patient satisfaction trends across U.S. hospitals, states, and regions.

This project was completed as part of the Maven Analytics Healthcare Challenge and emphasizes several core analytical skills relevant to survey and research focused business tasks, including:
* Survey data analysis
* Data cleaning and verification
* Multi-source data modeling
* KPI development
* Trend analysis
* Data visualization
* Communicating analytical findings through dashboards

## Data Source

The data source for this project was real HCAHPS patient survey data from the Centers for Medicare & Medicaid Services (CMS). Its a national, standardized survey data of hospital patients regarding their experiences during a recent inpatient hospital stay between 2013 and 2022.

The dataset included survey response metrics and hospital performance indicators across multiple reporting periods.

Survey categories included:
* Communication with doctors
* Communication with nurses
* Responsiveness of hospital staff
* Discharge information
* Care transition
* Hospital cleanliness
* Overall hospital rating
* Willingness to recommend the hospital

From this, the project analyzed:
* National survey results
* State-level survey results
* Hospital response rates
* Regional performance trends
* Positive vs. negative response behavior
* Net Promoter Score (NPS) trends over time

## Tools Breakdown:
* Microsoft Power BI
* Microsoft Excel
* DAX
* Data Modeling
* Data Visualization

## Project Objectives

The goal of the project was to:
* Analyze patient satisfaction trends across U.S. hospitals
* Evaluate positive and negative survey response behavior
* Compare hospital performance across states and regions
* Track changes in patient sentiment over time
* Develop KPIs from survey response data
* Present findings through interactive dashboards and visual storytelling

## Planning and Research

The project began with reviewing the HCAHPS data dictionary and understanding the structure of the survey data. Research was conducted to define the analytical focus and determine which dimensions and measures would provide the most meaningful insight into patient satisfaction and hospital performance.

Important fields and measures were identified early to support:
* Time-series analysis
* Regional comparisons
* State-level analysis
* NPS calculations
* Response trend analysis

## Data Cleaning and Transformation

A major part of the project involved preparing and validating the survey data before analysis.

### Cleaning and Transformation Tasks
* Removed or corrected missing values
* Imputed missing numeric values using averages in the Response Rate
* Corrected inconsistent data types such as State Name
* Converted mixed-type identifiers into text fields where necessary such as Facility ID
* Standardized reporting periods
* Built a reporting/date structure for time-series analysis
* Combined multiple related datasets into a relational data model

The project emphasized working with survey data from varying sources and varying quality levels.

## Data Modeling
<img width="797" height="739" alt="HCAHPS Survey Data Model" src="https://github.com/user-attachments/assets/a4f5cfbd-8827-4cae-91aa-62c58e489462" />

The project used a star-schema style data model to support filtering, aggregation, and cross-table analysis.

### Dimension Tables
* Reports (date/reporting dimension)
* States
* Measures
* Questions

### Fact Tables
* State Results
* National Results
* Cleaned Responses

### Key Relationships

* reports[Release Period] > state_results[Release Period]
* reports[Release Period] > national_results[Release Period]
* reports[Release Period] > cleaned_responses[Release Period]

* states[State] > state_results[State]
* states[State] > cleaned_responses[State]

* measures[Measure ID] > state_results[Measure ID]
* measures[Measure ID] > national_results[Measure ID]
/ measures[Measure ID] > questions[Measure ID]


The reporting table functioned as the project’s date/reporting dimension and standardized filtering across all dashboard pages.

## DAX Measures

Several DAX measures were created to support KPI analysis and trend evaluation.

Core Measures:
```Hospital Count =
DISTINCTCOUNT(cleaned_responses[Facility ID])
```
```Total Completed Surveys =
SUM(cleaned_responses[Completed Surveys])
````
```Average Response Rate =
AVERAGE(cleaned_responses[cleaned Response Rate])
```
```Average NPS =
[Average Top-box %] - [Average Bottom-box %]
```

The DAX calculations supported several analyses such as: Survey response analysis, Positive vs. negative response tracking, Regional comparisons, State rankings, and so on.

## Dashboard Pages

### National & Regional Overview
<img width="804" height="458" alt="HCAHPS  page 1" src="https://github.com/user-attachments/assets/b39da12d-1892-44dc-b388-801814e33994" />

Focused on Overall patient satisfaction, National NPS, Positive vs. negative survey responses, and Regional healthcare performance

## State Level Analysis
<img width="803" height="458" alt="HCAHPS  page 2" src="https://github.com/user-attachments/assets/9931bd2e-f370-4276-b416-6f15076ae98d" />

Focused on State rankings, Regional comparisons, Geographic analysis,and  State level positive and negative response trends

## Recommendations & Trend Insights
<img width="800" height="455" alt="HCAHPS  page 3" src="https://github.com/user-attachments/assets/ff619041-c9b7-4a8b-a864-560f6fa67cbc" />

Focused on Declining satisfaction trends since 2019, NPS changes over time, Quality-of-care improvement areas, and Operational recommendations

## Key Findings

### Highest Positive Response Regions

The following regions showed the strongest positive survey responses:
* West North Central
* West South Central
* East South Central

### Strongest Performing Survey Categories

Patients responded most positively to:
* Communication with doctors
* Communication with nurses
* Discharge information

### Negative Trends Identified

The analysis found several concerning trends:
* Negative responses increased since 2019
* Positive responses declined over time
* NPS declined at nearly the same rate as positive responses

## Net Promoter Score (NPS)

Overall NPS was approximately 63. While not poor, it did not reach the benchmark threshold of 70, which is generally considered excellent.

## Recommendations

Based on the analysis, several operational recommendations were identified.

### Staffing & Operational Support

Increasing staff or volunteer support may improve:
1. Hospital cleanliness
2. Patient movement efficiency
3. Responsiveness to patient needs
4. Communication Improvements

Additional training and technology adoption may improve:
1. Nurse communication
2. Doctor communication
3. Care transition clarity
4. Patient discharge experience
5. Regional Focus Areas

The following regions may require additional quality improvement focus:
* Mid-Atlantic
* South Atlantic

These regions showed some of the lowest NPS and patient satisfaction scores in the analysis.












