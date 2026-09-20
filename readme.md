# Messy Crime Dataset — Data Cleaning & Exploratory Analysis

An end-to-end data cleaning and exploratory data analysis project using Python and Pandas on a synthetic crime dataset.

The project focuses on identifying data-quality issues, applying defensible cleaning transformations, validating the resulting dataset, and exploring patterns across crime type, time, location, severity, age, property loss, and arrests.

## Project Overview

The original dataset contains intentionally messy data with multiple data-quality issues, including:

- Duplicate records
- Missing values
- Inconsistent categorical labels
- Mixed datetime formats
- Invalid numerical values
- Malformed numeric strings
- Invalid geographic coordinates
- Inconsistent text formatting
- Data type inconsistencies

The goal of the project is to produce a cleaner and more reliable analytical dataset while avoiding unsupported assumptions during the cleaning process.

## Objectives

- Inspect and diagnose data-quality issues.
- Clean inconsistent categorical and text values.
- Handle invalid numerical and datetime values.
- Correct recoverable geographic coordinate errors.
- Remove duplicate records.
- Standardize appropriate data types.
- Validate the cleaned dataset using explicit rules.
- Perform exploratory data analysis.
- Document cleaning decisions and dataset limitations.

## Dataset

| Metric                                | Value |
| ------------------------------------- | ----: |
| Original records                      | 5,250 |
| Final records                         | 5,050 |
| Columns                               |    33 |
| Crime types                           |    35 |
| Districts                             |    11 |
| Cities                                |     8 |
| Duplicate rows after cleaning         |     0 |
| Duplicate incident IDs after cleaning |     0 |

The dataset is synthetic and was used for data-cleaning and analytical practice.

## Tools & Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Jupyter Notebook

## Analytical Workflow

```text
Inspect
   ↓
Clean
   ↓
Validate
   ↓
Analyze
   ↓
Visualize
   ↓
Document
```

## Data Cleaning

The cleaning process included:

### Datetime

Standardized mixed datetime formats and converted `incident_datetime` to a consistent datetime representation.

### Numerical Data

Validated and cleaned:

- `badge_number`
- `num_arrests`
- `suspect_age`
- `victim_age`
- `property_loss_usd`

Invalid values were corrected when their intended values could be reasonably determined. Unrecoverable values were converted to missing values.

### Geographic Coordinates

Latitude and longitude values were checked against valid geographic ranges.

Recoverable swapped coordinates were corrected, while unrecoverable coordinate values were converted to missing.

### Categorical Data

Standardized clear spelling, capitalization, abbreviation, and naming variations across fields such as:

- `crime_type`
- `district`
- `severity`
- `case_status`
- `resolution`
- `suspect_gender`
- `suspect_race`
- `victim_gender`
- `weapon_used`

Categories were not merged when doing so would require unsupported assumptions.

### Text Standardization

Selected text fields were normalized by removing unnecessary whitespace, standardizing capitalization, and formatting populated phone-number values consistently.

## Data Validation

The cleaned dataset was validated using predefined rules for:

- Duplicate rows
- Duplicate incident IDs
- Latitude range
- Longitude range
- Suspect age range
- Victim age range
- Number of arrests
- Property loss
- Future incident dates

All defined validation checks passed.

## Exploratory Data Analysis

The EDA examines:

- Crime type distribution
- Annual incident trends
- District distribution
- Severity distribution
- Incident timing
- Suspect age distribution
- Victim age distribution
- Property loss by crime type
- Average arrests by crime type

Relationship analysis also examines:

- Crime type × severity
- District × severity
- Crime type × time of day
- Severity × property loss

## Key Findings

The analysis identified several patterns within the dataset:

- DUI, drug offence, and domestic violence are among the most frequently recorded crime types.
- Annual incident counts remain within a relatively narrow range from 2018 to 2024.
- Incident volume varies across districts, with North and South containing the largest numbers of records.
- Medium and Critical incidents represent substantial portions of the dataset.
- Incident volume varies across different hours of the day.
- Suspect and victim age distributions cover different ranges within the cleaned data.
- Median property loss varies across crime types.
- Average arrests vary across crime types, although the observed differences are relatively modest.

These findings describe patterns within the dataset and should not be interpreted as causal relationships.

## Data Quality Limitations

Although the dataset passes the defined validation checks, some source-data limitations remain.

Certain identifier-to-attribute relationships are inconsistent across records. These relationships were not forcibly reconstructed because the available data did not provide sufficient evidence to determine the intended values.

Some semantically related categories were also intentionally kept separate when merging them would require unsupported assumptions.

Missing values were retained when reliable imputation was not possible.

## Repository Contents

```text
├── messy_crime_data_cleaning_eda.ipynb
├── cleaned_crime_dataset.csv
├── README.md
└── .gitignore
```

## Final Outcome

This project demonstrates a complete practical workflow for:

**Data Cleaning → Data Validation → Exploratory Data Analysis → Documentation**

The emphasis throughout the project is on reproducibility, validation, and defensible analytical decisions.
