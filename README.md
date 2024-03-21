
# AWS Data Pipeline Project

## Overview
This project involves the development of an AWS-based data pipeline using Airflow, Python, Spark, and AWS services. The aim is to extract Weather Data from OpenWeather, store it in S3, and load it into Redshift using Airflow.


https://github.com/SiddharthUchil/data-engineering-airflow-aws/assets/36127139/0e7f1faa-03eb-4c49-9f0c-15060b3c939d


![alt text](https://github.com/SiddharthUchil/data-engineering-airflow-aws/blob/main/High%20Level%20Infra.drawio.png)


## Architecture
The project's architecture is constructed using Infrastructure as Code (IAC) methodologies, with two main Airflow DAGs configured for the workflow.

### First Airflow DAG: Data Acquisition and Storage
This DAG handles the extraction of weather data from the OpenWeather API and its storage in an S3 bucket.

#### Tasks
- **Extract Data from OpenWeather API**: Utilizes a Python operator to retrieve weather data using the "requests" library.
- **Store Data in S3**: Structures the extracted data into a dataframe and stores it in an S3 bucket using the S3CreateObjectOperator.

### Second Airflow DAG: Data Transformation and Loading
This DAG is responsible for extracting data from S3, transforming it, and loading it into Redshift.

#### Tasks
- **Sync Check**: Ensures the completion of the first DAG's tasks before proceeding.
- **ETL to Redshift**: Employs GlueContext and Spark context for ETL processes, loading the transformed data into Redshift.

## Conclusion
The pipeline facilitates the automated extraction, storage, and loading of weather data into Redshift, leveraging the integration of Apache Airflow and Glue operators for routine updates.

We've established the entire architecture through infrastructure as code (IAC) methodologies. Following that, we've configured two separate Airflow DAGs.

**Setting Up the First Airflow DAG:**
This DAG encompasses tasks for data extraction via the weather API and subsequent loading into an S3 bucket.

**Task 1: Extracting Data from OpenWeather API:** Utilizing a Python operator, we retrieve weather data from the OpenWeather API. This involves leveraging libraries such as "requests" to initiate API requests and obtain the required data.

**Task 2: Storing Data in S3:** After successfully extracting the data, we structure it within a data frame and then store it within an S3 bucket. This operation is executed using the S3CreateObjectOperator.

**Setting Up the Second Airflow DAG:**
This DAG includes tasks for extracting data from S3, applying transformations, and finally loading the processed data into Redshift.

**Task 1: Waiting for Completion of the First DAG:** Before proceeding, this task ensures that the first DAG has successfully completed its operations.

**Task 2: ETL Processing to Redshift using Glue Operator:** This step involves employing the GlueContext and Spark context for Extract, Transform, Load (ETL) operations. The data, once transformed, is loaded into the Redshift database.

**Conclusion:**
By adhering to these outlined steps, a comprehensive ETL pipeline is established within AWS. This pipeline facilitates the extraction of weather data from OpenWeather, its storage within S3, and its subsequent loading into Redshift. The integration of Apache Airflow and Glue operators guarantees the automation of routine updates to the weather data in the Redshift database.
