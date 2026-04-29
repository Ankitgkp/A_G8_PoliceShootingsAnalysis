# Data Dictionary

## How To Use This File

1. Add one row for each column used in analysis or dashboarding.
2. Explain what the field means in plain language.
3. Mention any cleaning or standardization applied.
4. Flag nullable columns, derived fields, and known quality issues.

## Dataset Summary

| Item | Details |
|---|---|
| Dataset name | Fatal Police Shootings in the USA (2015-2024) |
| Source | Washington Post Fatal Force database and Police Data Accessibility Project (PDAP) |
| Raw file name | `ShootOut_RawDataset.csv` and `Agency_RawDataset.csv` |
| Last updated | April 2026 |
| Granularity | One row per fatal shooting incident-agency link (after exploding multi-agency incidents) |

## Column Definitions

| Column Name | Data Type | Description | Example Value | Used In | Cleaning Notes |
|---|---|---|---|---|---|
| `date` | datetime | Date of the fatal shooting incident | 2015-01-02 | EDA / KPI / Tableau | Converted from string to datetime. Extracted Year, Month, Day |
| `name` | string | Victim's full name | Tim Elliot | EDA / Tableau | None |
| `age` | float | Victim's age | 53.0 | EDA / KPI / Tableau | Converted to numeric. Unparseable values coerced to NaN. Used to derive `Age_Group` |
| `gender` | string | Victim's gender | m | EDA / Tableau | Lowercased and stripped whitespace |
| `race` | string | Victim's race | White | EDA / Tableau | Mapped abbreviations (W/B/H/A/N/O) to full names. Unmapped values set to "Unknown" |
| `armed_with` | string | Weapon victim was armed with | gun | EDA / KPI / Tableau | Missing values filled with "unknown". Used to create `Is_Unarmed` |
| `flee_status` | string | Whether the victim was fleeing | not | EDA / KPI / Tableau | Missing filled with 'Unknown'. Used to create `Flee_Group` |
| `was_mental_illness_related` | boolean | If victim exhibited signs of mental illness | True | EDA / Tableau | Cast to boolean |
| `body_camera` | boolean | If officer body camera was active | False | EDA / Tableau | Cast to boolean |
| `state` | string | State where incident occurred | WA | EDA / Tableau | None |
| `agency_ids` | float | ID(s) of involved agencies | 73 | EDA / KPI / Tableau | Exploded from semicolon-separated list into individual rows per agency ID. Converted to numeric for joining |
| `id` | int | Unique agency identifier | 73 | Tableau | From Agency dataset. Used as merge key with `agency_ids` |
| `agency_name` | string | Agency name | Shelton Police Department | Tableau | From Agency dataset. |
| `agency_state` | string | State where agency operates | WA | Tableau | From Agency dataset. |
| `type` | string | Agency type | local police | Tableau | From Agency dataset. |
| `total_shootings` | int | Cumulative fatal shootings on record for the agency | 2 | KPI / Tableau | From Agency dataset. Used to calculate `Agency_Shooting_Volume` |

## Derived Columns

| Derived Column | Logic | Business Meaning |
|---|---|---|
| `Age_Group` | Bucketed `age` into 6 bands: <18, 18-24, 25-34, 35-44, 45-54, 55+ | Enables demographic pyramid and age-based trend analysis |
| `Is_Unarmed` | `True` if `armed_with` == 'unarmed' | Key accountability metric — crucial filter for reform debates |
| `Year` | Calendar year extracted from `date` | Temporal trend analysis |
| `Month` | Month name extracted from `date` | Seasonal pattern detection |
| `Day_of_Week` | Day name extracted from `date` | Operational scheduling insights |
| `Flee_Group` | Grouped `flee_status` into 'Fleeing', 'Not Fleeing', 'Unknown' | Reduces granular flee categories to a simpler metric for dashboarding |
| `Agency_Shooting_Volume` | Tiered `total_shootings`: Low (1-5), Medium (6-20), High (>20), Unknown | Identifies high-incident agencies for targeted oversight |

## Data Quality Notes

- **Race Coded as Single Letters**: Required manual mapping to full labels. Unmapped or missing values were set to "Unknown" rather than dropped.
- **Multiple Agency IDs**: Some incidents involved multiple agencies and were stored as semicolon-delimited strings. These were exploded into separate rows, so incidents involving multiple agencies appear multiple times (once per agency).
- **Missing Data Retention**: Incidents with NaN age or unknown armed status were retained rather than dropped to preserve the overall incident count.
- **Irrelevant Columns Dropped**: `race_source`, `location_precision` (shootings), and `oricodes` (agencies) were dropped prior to analysis as they were not required.