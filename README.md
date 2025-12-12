# Data-engineering-UberTripAnalysisPipeline

##Overview
This project implements an end-to-end data pipeline using NYC Trip Record Data. Raw data is extracted from the source website and ingested into Google Cloud Storage. The data is then transformed and modeled using fact and dimensional modeling techniques in Python (Jupyter Notebook). An ETL pipeline is orchestrated using Mage AI to load the transformed datasets into Google BigQuery, followed by the creation of analytical dashboards in Power BI.


##Dataset Used
TLC Trip Record Data which include fields capturing pick-up and drop-off dates/times, pick-up and drop-off locations, trip distances, itemized fares, rate types, payment types, and driver-reported passenger counts.

CSV : 
