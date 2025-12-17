# Uber Trip Analysis Pipeline

## Technical Overview

This project implements an end-to-end data pipeline using NYC Trip Record Data. Raw data is extracted from the source website and ingested into Google Cloud Storage. The data is then transformed and modeled using fact and dimensional modeling techniques in Python (Jupyter Notebook). An ETL pipeline is orchestrated using Mage AI to load the transformed datasets into Google BigQuery, followed by the creation of analytical dashboards in Power BI.


### Business Problem
Business Problem (Realistic)

City transportation authorities and mobility companies lack timely, reliable insights into trip demand, revenue patterns, and operational efficiency due to fragmented, raw trip data.

Raw taxi data is:

High-volume
Messy
Not decision-ready
Hard to analyze without modeling

This prevents stakeholders from:

Identifying peak demand periods
Optimizing pricing and fleet allocation
Monitoring revenue and trip trends
Making data-driven policy decisions


### Business Frame

Aim - Enable data-driven transportation insights by transforming raw trip records into reliable, analytics-ready data.
This project addresses the challenge of converting high-volume transportation data into actionable insights. By building an automated data pipeline, raw NYC taxi trip data is transformed into analytics-ready datasets that support demand analysis, revenue tracking, and operational decision-making through scalable dashboards.


## Dataset Used
Trip Record Data which include fields capturing pick-up and drop-off dates/times, pick-up and drop-off locations, trip distances, itemized fares, rate types, payment types, and driver-reported passenger counts.

RAW CSV : https://github.com/Pharaohleft/Data-engineering-UberTripAnalysisPipeline/blob/main/uber_data.csv

## Data Pipeline Architecture
<img width="1744" height="608" alt="Gemini_Generated_Image_blzdl0blzdl0blzd" src="https://github.com/user-attachments/assets/6719fe2c-2609-4e94-95de-9dd806b11d5d" />


Order of events:
Step 1: Cleaning, transformation & Modeling
Step 2: Storage
Step 3: ETL, Orchestration using Mage: Extract, Transform, Load
Step 4: Analytics with SQL script
Step 5: Dashboard on Power BI



### Ingestion, Cleaning, Transformation & Modeling → Business Need & Usability

1. Data Ingestion
ingest NYC Trip Record data into Google Cloud Storage, creating a centralized, scalable raw data layer.
loaded the CSV file into Jupyter Notebook and carried out data cleaning and transformation activities prior to organizing them into fact and dim tables.

2. Transform and model the data using fact and dimension tables, enabling:

Time-based analysis
Location-based insights
Vendor and trip-level performance tracking

This converts raw data into decision-ready datasets.
Tasks that were performed:

Converted tpep_pickup_datetime and tpep_dropoff_datetime columns into datetime format.
Removed duplicates and reset the index.

3. Data Modeling

<img width="1600" height="1071" alt="236725688-995b6049-26c1-440f-b523-7c6c10d507ba" src="https://github.com/user-attachments/assets/81948de3-f078-4bcc-9268-04880d9972b0" />

### Orchestration → Reliability

This step focuses on orchestrating the ETL workflow using Mage AI. A dedicated compute environment is provisioned and configured with required Python and Google Cloud libraries to ensure reproducible execution. The pipeline is structured into Extract, Transform, and Load stages to enforce separation of concerns and reliability. Secure authentication is handled via configuration files, enabling controlled data loads into BigQuery while maintaining pipeline observability through Mage’s UI.

1. Provisioning an SSH Instance
 
Ensures a stable compute layer
Isolates dependencies
Avoids local-machine inconsistencies
Supports scheduled and repeatable runs
This is about environment reproducibility

Begin by launching the SSH instance and running the following commands below to install the required libraries. 
Python → transformation logic
Pandas → structured data manipulation
Google Cloud libraries → secure interaction with BigQuery

# Install python and pip 

sudo apt-get install update
sudo apt-get install python3-distutils
sudo apt-get install python3-apt
sudo apt-get install wget
wget https://bootstrap.pypa.io/get-pip.py
sudo python3 get-pip.py

# Install Google Cloud Library

sudo pip3 install google-cloud
sudo pip3 install google-cloud-bigquery

# Install Pandas
sudo pip3 install pandas


Problem: Manual processing leads to delays and errors.
Solution:
Orchestrate the ETL pipeline using Mage AI, ensuring:

Repeatable execution
Consistent data refreshes
Reduced operational risk

Using Mage AI for Orchestration

Mage is used to:

Define clear pipeline stages
Manage dependencies between steps
Enable controlled execution order
Make the pipeline observable and debuggable
This replaces fragile one-off scripts with a production-style workflow.

#### Install Mage library
sudo pip3 install mage-ai

#### Create new project
mage start demo_project

### Data Warehouse → Performance

Pipeline Design (Extract → Transform → Load)

Extract (load_uber_data)
Pull raw data from source
No transformations

Transform (transform_uber)
Apply cleaning and modeling logic
Prepare analytics-ready data

Load (load_gbq)
Persist curated data into BigQuery

This separation improves:
Maintainability
Debugging
Reusability

Problem: Large datasets slow down analysis.
Solution:
You load curated tables into BigQuery, enabling:

Fast analytical queries
Scalable reporting
Concurrent access for multiple users


Accessing Mage via External IP

Before executing the Load pipeline, I download credentials from Google API & Credentials and then update them accordingly in the io_config.yaml file within the same pipeline. This step is essential for granting authorization to access and load data into Google BigQuery.

Enables monitoring pipeline execution
Allows validation of each stage
Supports troubleshooting failed runs

Observability is critical for production pipelines.

###  Dashboard → Decision-Making

Additional analysis can be performed using SQL querying before moving to dashboard
for eg: Find the top 10 pickup locations based on the number of trips
Find the total number of trips by passenger count:
Find the average fare amount by hour of the day


Power BI acts as a client that:
Connects to BigQuery
Queries data from BigQuery
Visualizes the results

Problem: Stakeholders need insights, not tables.
Solution:
You build dashboards (Power BI) to surface:

Trip volume trends
Revenue metrics
Peak demand periods
Location-level insights
