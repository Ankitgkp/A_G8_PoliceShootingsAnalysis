## Fatal Police Shootings in the USA (2015–2024)

Data Analytics Capstone Project | Team G8


## Project Overview

This project is an end-to-end data analytics case study on fatal police shootings in the United States from 2015 to 2024.

The objective is to analyze long-term patterns in police shootings and understand:

* Demographic disparities (age, race, gender)
* Situational contexts (mental health, fleeing status, armed/unarmed)
* Geographic and temporal trends
* Impact of body camera usage on accountability

Using real-world datasets (Washington Post + PDAP), we built a complete pipeline involving data cleaning, feature engineering, statistical analysis, and visualization dashboards.


## Problem Statement

Despite increasing public awareness and reforms, there is limited clarity on:

* Whether fatal police shootings are increasing or decreasing
* Which groups are disproportionately affected
* How situational factors influence outcomes

This project aims to answer these questions using data-driven insights.


## Tech Stack

Programming & Analysis

* Python (Pandas, NumPy)
* Jupyter Notebook

Visualization

* Tableau (Interactive Dashboards)
* Matplotlib / Seaborn (EDA)

Data Processing

* Data Cleaning & Preprocessing
* Feature Engineering
* ETL Pipeline Design

⸻

## Methodology

1. Data Collection
    * Washington Post Fatal Force Database
    * PDAP (Police Data Accessibility Project)
2. Data Cleaning
    * Handling missing values
    * Standardizing categorical fields
    * Removing inconsistencies
3. Feature Engineering
    * Age group segmentation
    * Time-based features (year, month, day)
    * Armed vs unarmed classification
    * Agency-level shooting volume tiers
4. Exploratory Data Analysis (EDA)
    * Trend analysis over 10 years
    * Demographic comparisons
    * Correlation studies
5. Visualization
    * Interactive Tableau dashboards
    * KPI-based storytelling


## Key Insights

1. No Significant Improvement Over Time

Despite reforms and increased scrutiny, fatal police shootings have remained relatively stable over the decade.

2. Gender Disparity

More than 95% of victims are male, indicating a strong gender imbalance in incidents.

3. Racial Disparities

Black and Hispanic individuals are disproportionately affected compared to their population share.

4. Mental Health Factor

A significant proportion of cases involve individuals experiencing mental health crises.

5. Body Camera Usage Gaps

Body camera usage remains inconsistent, limiting transparency and accountability.


## Key KPIs Created

* Age Group Distribution (18–24, 25–34, etc.)
* Armed vs Unarmed Classification
* Fleeing Status (Yes/No)
* Agency Risk Tier (Low / Medium / High incident volume)
* Temporal Trends (Yearly / Monthly patterns)


## Recommendations

R1. Mandatory Body Cameras

Ensure all law enforcement encounters are recorded for transparency.

R2. Mental Health Response Teams

Introduce co-response teams with trained mental health professionals.

R3. High-Risk Agency Monitoring

Flag agencies with consistently high incident rates for audits.

R4. Better Data Standardization

Improve reporting consistency across states and departments.

##  Team Contribution Matrix

| Team Member | Primary Contribution Area | Key Deliverables |
| :--- | :--- | :--- |
| **Adithya & Ranvendra** | ETL / Data Engineering | 01_extraction.py, 02_cleaning.py, raw-to-clean pipeline |
| **Ranvendra & Ankit** | Exploratory Data Analysis (EDA)  | 03_eda.py, exploratory charts and visual summaries  |
| **Harshita & Vriha** | Statistical Analysis  | 04_statistical_analysis.py, regression and group comparison outputs  |
| **Aryan & Chinmay** | KPI Design & Final Load  | 05_Final_Load.py, KPI column definitions, final_data.csv  |
| **Chinmay & Harshita** | Dashboarding & Reporting | Tableau dashboard, final project report |

 Key Learnings

* Real-world messy data handling
* End-to-end analytics pipeline design
* Importance of bias and fairness in data
* Translating data into policy-level insights

