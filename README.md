# PoliceCrimeProject

# UK Police Street-Level Crime Data Project

This project shows how I prepared the UK Police street-level crime dataset for monthly reporting, using **Snowflake**, **Python**, and **SQL**.


## Dataset Overview

The dataset contains street-level crime reports across the UK with columns such as:
- `crime_type`
- `month`
- `street_name`
- `lsoa_name`
- `location`
- and others

Key considerations:
- Some rows have missing or null `lsoa_name` or `street_name`, which were filtered or flagged.
- Same applies for locationn longitude and latitiude
- Data is updated monthly and needs to be reprocessed regularly.


## Tools Used

- **Python** – Data cleaning and transformation
- **Snowflake SQL** – Data loading and aggregation
- **GitHub** – Code sharing and documentation


## Project Contents

| File | Description |
|------|-------------|
| `Clean Crime Dataset.ipynb` | Python script for cleaning the data |
| `Upload Data.ipynb` | Python script for creating the Staging/Main table and loading the data to Snowflake |
| `Crime Query.sql` | SQL script for aggregating monthly crime counts |
| `Crime Data` | Folder with all the raw data |
| `UK_Crime_Data.csv` | The dataset that was loaded to the Snowflake enevironment. The contains all data combined into one dataset. |
| `README.md` | Project documentation |


## Sample Aggregation Query

```sql
select month AS report_month, lsoa_name as location, crime_type, COUNT(*) AS crime_count 
from UK_POLICE_DATA.STREET_LEVEL_CRIME.CRIME_DATA
WHERE lsoa_name IS NOT NULL
GROUP BY month, lsoa_name, crime_type
ORDER BY month, lsoa_name, crime_type desc;
```

## Accessing the UK Crime Dataset in Snowflake

The full crime dataset is in Snowflake as the CSV is too big to upload to GitHub

### To access:
1. Email me or raise an issue in this repo
2. You will be given login credentials for a read-only user

### Login URL
Copy and Paste this link into the browser
https://zrdegrg-jk37645.snowflakecomputing.com/console/login#/

Username - Interview_User

Password - Interviewuser1!

### You’ll get access to:
- **Database:** `uk_police_data`
- **Schema:** `street_level_crime`
- **Example table:** CRIME_DATA (Main Table), STAGING_CRIME_DATA (Staging Table)

