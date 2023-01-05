## Introduction

A startup company called Sparkify provides music streaming to the users through the application. The songs details and the user activity data from the application are currently available and stored in the format of JSON.

If Sparkify wants to analyze the daily activities, the current state would be though. Hence I recommend a database since it can be efficient for retrieving data.

The STAR schema consists of one fact table referencing any number of dimension tables that helps the Sparkify further analysis.

## ETL
1. Created **songs**, **artist** dimension tables from extracting songs_data by selected columns.
2. Created **users**, **time** dimension tables from extracting log_data by selected columns.
3. Created the most important table fact table from the dimensison tables and log_data called **songplays**. 

## Installation

Install PostgreSQL database drivers by using the below command
```bash
pip install psycopg2
```
## Usage
1. **sql_queries.py**: contains all SQL queries of the project and this file can be used in multiple files.
2. **create_tables.py**: run this file after writing for creating tables for the project.

      #### Libraries used:
     ```python
     import psycopg2
     from sql_queries import create_table_queries, drop_table_queries
     ```
     #### Functions and its importance:
     **create_database**: This function helps in droping existing database, create new database and return the connection.

    **drop_tables**: Used to drop the existing tables.

    **create_tables**: This helps in creating above mentioned fact table and dimension tables.
3. **etl.ipynb**: reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
4. **etl.py**:   read  and process files from song_data and log_data and load them to tables. 
    #### Libraries used:
    ```python
    import os
    import glob
    import psycopg2
    import pandas as pd
    from sql_queries import *
    import json
     ```
    #### Functions and its importance:
   
    **process_song_file**: This function is used to read the song file and insert details with selected columns into song and artist dimension table.

    **process_log_file**: read one by one log file and insert details with selected columns into user, time and songplays tables.
   
    **process_data**: collect all the file paths and call the above two function and show status of files processed.

    **main**: used to call the process_data function.

5. **test.py**: displays the first few rows of each table to let you check your database.

## execute files in the below order each time before pipeline.

   1. create_tables.py
      ```python
         $ python3 create_tables.py
   2. etl.ipynb/et.py
      ```python
         $ python3 etl.py
   3. test.ipynb