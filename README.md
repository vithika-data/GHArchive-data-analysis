# GHArchive-data-analysis
Analyzing GHArchive KPIs using Pyspark 

I had an amazing opportunity to work on GHArchive data (https://www.gharchive.org/) where I analyzed one day raw data of Github. The analysis is for 13th July 2020 using PySpark. The codes to analyse this data has been written in DataBricks Community Edition and the GHArchive_Data_Analysis.py file attached to this repository can be used to run those codes there.

**Created ETL pipeline for this project

Extracted data from GHarchive ------> Transformed the data in PySpark -------> Load the target data in AWS-S3 bucket for day-to-day pipeline

I followed the following steps to get the analysis done:
- Extracting data files from GHarchive
- Processing the Data
- Understanding the data
- Analysing the data with a problem statement
- Data Visualisation
- Exported dataframe with relevant fields into S3 bucket(where business can create a trigger using AWS lambda) for day-to-day pipeline analysis

## Extracting the data files from GHArchive
- Used wget command to download the data for a day
- The data was a compressed .gz file for each hour
- I initially decompressed the data in my system, however the data size was more than 23GB and therefore, I decided to work on the compressed file online and decided on using online Databricks to understand and manipulate the data.

## Processing the Data
- I created a Spark.Session and I read all the json data in one single data frame
- This process, though fairly straightforward, actually took some time since the file I downloaded at first( for Date: 17th July 2020), contained a corrupt hourly file which was not readable. I then decided to get data for another date(Date: 13th July 2020) to proceed with the analysis
- I changed a string data containing dates into datetime column to analyse the results on hourly level
- Then, I cached my data for faster code execution

## Understanding the Data
- This took most of my time since the schema of the json data is fairly large and nested. 
- I printed schemas and started understanding various informations from nested jsons. 
- Upon understanding, Payload column actually provided a lot of information on - issues, commit, forks, description, comments etc

## Analysing the data
- Upon looking up the data and deciding on important information that can be presented to the CEO, I decided on presenting my analysis for the following questions:
  - What are the different type of events that took place in a day?
  - How many issues were raised per hour in a day?
  - How many issues were opened and closed per hour in a day?
  
 ## Data Visualisation and Presentation
  - Created charts based on the filtered data from each visualizations
  - Created a google presentation : https://docs.google.com/presentation/d/1JAAPCznVMUEttWROyrISgTXyGieDKmN5FsDsNSmMzDI/edit?usp=sharing 
  
  ## Loaded the data to S3 bucket
  - Exported dataframe with relevant fields into S3 bucket(where business can create a trigger using AWS lambda) for day-to-day pipeline analysis
  
