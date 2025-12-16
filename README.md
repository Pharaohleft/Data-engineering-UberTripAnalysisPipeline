# Uber Trip Analysis Pipeline

## Technical Overview

This project implements an end-to-end data pipeline using NYC Trip Record Data. Raw data is extracted from the source website and ingested into Google Cloud Storage. The data is then transformed and modeled using fact and dimensional modeling techniques in Python (Jupyter Notebook). An ETL pipeline is orchestrated using Mage AI to load the transformed datasets into Google BigQuery, followed by the creation of analytical dashboards in Power BI.

### Business Frame

Aim - Enable data-driven transportation insights by transforming raw trip records into reliable, analytics-ready data.
This project addresses the challenge of converting high-volume transportation data into actionable insights. By building an automated data pipeline, raw NYC taxi trip data is transformed into analytics-ready datasets that support demand analysis, revenue tracking, and operational decision-making through scalable dashboards.


## Dataset Used
Trip Record Data which include fields capturing pick-up and drop-off dates/times, pick-up and drop-off locations, trip distances, itemized fares, rate types, payment types, and driver-reported passenger counts.

RAW CSV : https://github.com/Pharaohleft/Data-engineering-UberTripAnalysisPipeline/blob/main/uber_data.csv

## Data Pipeline Architecture
<img width="1744" height="608" alt="Gemini_Generated_Image_blzdl0blzdl0blzd" src="https://github.com/user-attachments/assets/6719fe2c-2609-4e94-95de-9dd806b11d5d" />
