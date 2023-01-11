# YouTube_ETL_Pipeline_AWS

![image](https://user-images.githubusercontent.com/54287482/211855659-ee6c2bfd-c368-4bde-8771-913727b41b47.png)

Using AWS's ETL for YouTube Trends Analysis

This project's objective is to extract, transform, and load (ETL) information about popular YouTube videos using the Kaggle dataset. For additional research and visualisation, the data will be kept in AWS.


Data extraction from the Kaggle dataset and storage in an S3 bucket on AWS will be the initial stage in this project. The data will then be changed in order to guarantee that it is in the right format for analysis. This will entail data cleansing, addressing missing values, and data type conversion.

A relational database (like RDS) or a data warehousing service (like Redshift) on AWS will receive the converted data before being loaded into those services. It will then be simple to access for analysis and visualisation.

After the data has been saved on AWS, the project will concentrate on data analysis to discover patterns in YouTube video views, likes, and comments. This can entail spotting trends in the data, such as which kinds of movies are popular or which nations receive the most views. Furthermore, interactive visualisations displaying these trends can be produced using data visualisation tools like QuickSight.

For the most part, this project will show how to use AWS for ETL and storing sizable datasets for further analysis. It can also offer fascinating trends and insights on the kinds of videos and content that are most and less popular on YouTube.

Project Steps

1 -utilising AWS CLI commands to upload data from a local computer to an S3 bucket while striving to maintain file organisation. The JSON and CSV files each have their own folder.
local_S3_cli_commands.sh

2 - Data from raw bucket JSON and CSV files will be crawled and stored in a separate database using AWS Glue Catalog..
3 - If JSON-formatted data causes issues, you should develop a Python function using AWS Lambda to clean them up and convert them to parquet format.
lambda_function.py

4 -The result was saved in a new database in Athena, and this Lambda function now has a trigger that will execute each time fresh data is added to the S3 bucket.
The CSV files were also transformed to parquet format using AWS Glue ETL.
ETL_clean_data.py

![image](https://user-images.githubusercontent.com/54287482/211887017-efcb23a0-a392-4d2a-bc6c-891fd1328225.png)

The CSV files were also transformed to parquet format using AWS Glue ETL,the workflow is find below,this is done by using the jobs function found in AWS Glue,the AWS Glue is usually used to perform ETL jobs,one can create the target folder to be in any format i.e csv,databases,tables etc and the source can be from the S3 bucket in any format.

![image](https://user-images.githubusercontent.com/54287482/211889920-80872ddb-c6b7-4d27-bb2b-a20d76185573.png)

The ETL flow generates a pyspark programme to which adjustments can be made/added as desired:ETL_data.py


6 - generated a new Glue Crawler to enter the database with the clean data. The Crawler is found in AWS Glue it is used to convert dataset to database/tables which can then be queried in AWS Athens.
7 - Once the database has all of the clean data from the parquet files (converted from CSV and JSON files), run an ETL task in AWS Glue Studio to combine the two tables and store the data in a different S3 bucket for business intelligence (BI) needs. The cleaned json and cleaned csv files are joined together using the ETL under jobs(AWS Glue) to create a final dataset in S3 bucket which is then visualized by Quicksight.


![image](https://user-images.githubusercontent.com/54287482/211892455-3c51c961-6aaf-4935-a9db-a13cc309f4de.png)

The pyspark for the process is found here :ETL_joining_data.py



8 - The Quicksight will establish connection with S3 bucket to retrieve the final dataset which can now be used for building dashboards out of it.

![image](https://user-images.githubusercontent.com/54287482/211897286-a7da7fe8-52ad-4d07-a566-04eb31d6d478.png)


![image](https://user-images.githubusercontent.com/54287482/211897649-9cde1405-b4a2-4a37-8f31-360072277a43.png)


![image](https://user-images.githubusercontent.com/54287482/211898638-358181f5-dff9-4493-a9e3-db976b012064.png)





