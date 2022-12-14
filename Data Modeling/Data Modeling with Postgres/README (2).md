# Data Modeling with Postgres

## Overview 

In this project, I apply data modeling with postgres and build an ETL pipeline using python. A startup wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. Currently, they are collecting data in JSON format and the analytics team is particularly intrested in understanding what songs users are listening to.

## Song Dataset 

Songs dataset is a subset of [Million Song Dataset](http://millionsongdataset.com/)

Sample Record:
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}

## Log Dataset

Log dataset is generated by [Event Simulator](https://github.com/Interana/eventsim)

Sample Record: 
{"artist": null, "auth": "Logged In", "firstName": "Walter", "gender": "M", "itemInSession": 0, "lastName": "Frye", "length": null, "level": "free", "location": "San Francisco-Oakland-Hayward, CA", "method": "GET","page": "Home", "registration": 1540919166796.0, "sessionId": 38, "song": null, "status": 200, "ts": 1541105830796, "userAgent": "\"Mozilla\/5.0 (Macintosh; Intel Mac OS X 10_9_4) AppleWebKit\/537.36 (KHTML, like Gecko) Chrome\/36.0.1985.143 Safari\/537.36\"", "userId": "39"}

## Schema 

### Fact Table

1. **songplays**- records in log data associated with song plays i.e. records with page NextSong
    * songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent

### Dimension Tables 

2. **users** - user in the appp 
    * user_id, first_name, last_name, gender, level
3. **songs** - songs in music database 
    * song_id, title, artist_id, year, duration
4. **artist** - artists in music database 
    * artist_id, name, location, latitude, longitude
5. **time** timestamps of records in songplays broken down into specific units
    * start_time, hour, day, week, month, year, weekday
    
## Project Files 

test.ipynb displays the first few rows of each table to let you check your database.
create_tables.py drops and creates your tables. You run this file to reset your tables before each time you run your ETL scripts.
etl.ipynb reads and processes a single file from song_data and log_data and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables.
etl.py reads and processes files from song_data and log_data and loads them into your tables. You can fill this out based on your work in the ETL notebook.
sql_queries.py contains all your sql queries, and is imported into the last three files above.