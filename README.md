Data Modeling with Postgres

Project Overview

This project focuses on leveraging Data Modeling with Postgres to construct an ETL pipeline using Python. The objective is to assist a startup in analyzing the data collected from their new music streaming app, with a specific interest in understanding user song preferences. The existing data is in JSON format, and the analytics team aims to gain insights into the songs users are actively listening to.

Song Dataset
The songs dataset is a subset of the Million Song Dataset.

Sample Record:

sql
#code
{"artist": null, "auth": "Logged In", "firstName": "Walter", "gender": "M", "itemInSession": 0, "lastName": "Frye", "length": null, "level": "free", "location": "San Francisco-Oakland-Hayward, CA", "method": "GET","page": "Home", "registration": 1540919166796.0, "sessionId": 38, "song": null, "status": 200, "ts": 1541105830796, "userAgent": "\"Mozilla\/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/36.0.1985.143 Safari\/537.36\"", "userId": "39"}


Schema

Fact Table

songplays - Records in log data associated with song plays, identified by the page NextSong.

#code
songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent
Dimension Tables
users - Users in the app.

#code
user_id, first_name, last_name, gender, level
songs - Songs in the music database.

sql
#code
song_id, title, artist_id, year, duration
artists - Artists in the music database.

#code
artist_id, name, location, latitude, longitude
time - Timestamps of records in songplays, broken down into specific units.

sql
#code
start_time, hour, day, week, month, year, weekday


Project Files:

- sql_queries.py: Contains SQL queries for dropping and creating fact and dimension tables, along with insertion query templates.
- create_tables.py: Sets up the database. Running this file creates the sparkifydb and the fact and dimension tables.
- etl.ipynb: Jupyter notebook for dataset analysis before loading.
- etl.py: Reads and processes song_data and log_data.
- test.ipynb: Notebook to connect to the PostgreSQL database and validate the loaded data.


Environment:

Python 3.6 or above
PostgreSQL 9.5 or above
psycopg2: PostgreSQL database adapter for Python


References:

Psycopg Documentation
PostgreSQL Documentation
Pandas Documentation