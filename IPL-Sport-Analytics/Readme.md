## Project Introduction 
As a data analysis intern, you have to analyze sports data for a client. You are given two datasets
related to IPL (Indian Premier League) cricket matches. One dataset contains ball-by-ball data
and the other contains match-wise data. You have to import the datasets into an SQL database
and perform the tasks given in this assignment to find important insights from this dataset

Datasets

[IPL_Ball.csv](https://drive.google.com/file/d/1It3JnQPpNHCHoZyB6xLyTCP6prrzE3p-/view)


[IPL_matches.csv](https://drive.google.com/file/d/18GFAORe6kWU6UQxNXSgoOofR9h8dZ7wU/view)

### About the Data

The first CSV file ("IPL_Ball.csv")  is for ball-by-ball data and it has information of all the 193468 balls bowled
between the years 2008 and 2020. It has 17 columns. The second file ("IPL_matches.csv") contains match-wise data and has data of 816 IPL matches. This table has also 17 columns. 

### Required tasks
The first step before solving the problem is to create a database in MySQL workbench

`CREATE DATABASE ipldb;`

Then start using the database created to perform the SQL queries:

+ Using the database

`use ipldb; `

1. Create a table named ‘matches’ with appropriate data types for columns

```CREATE TABLE matches(
    id INT PRIMARY KEY,
    city VARCHAR(40),
    date DATE,
    player_of_match VARCHAR(40),
    venue VARCHAR(80),
    neutral_venue INT,
    team1 VARCHAR(80),
    team2 VARCHAR(80),
    toss_winner VARCHAR(80),
    toss_decision VARCHAR(20),
    winner VARCHAR(80),
    result VARCHAR(40),
    result_margin INT,
    eliminator VARCHAR(10),
    method VARCHAR(10),
    umpire1 VARCHAR(40),
    umpire2 VARCHAR(40)
);```


2. Create a table named ‘deliveries’ with appropriate data types for columns
```CREATE TABLE deliveries (
    `id` INT,
    `inning` INT,
    `over` INT,
    `ball` INT,
    `batsman` VARCHAR(40),
    `non_striker` VARCHAR(40),
    `bowler` VARCHAR(40),
    `batsman_runs` INT,
    `extra_runs` INT,
    `total_runs` INT,
    `is_wicket` INT,
    `dismissal_kind` VARCHAR(40),
    `player_dismissed` VARCHAR(40),
    `fielder` VARCHAR(40),
    `extras_type` VARCHAR(40),
    `batting_team` VARCHAR(40),
    `bowling_team` VARCHAR(40),
     FOREIGN KEY(id) REFERENCES matches(id)
); ```

3. Import data from CSV file ’IPL_matches.csv’ attached in resources to ‘matches’

4. Import data from CSV file ’IPL_Ball.csv’ attached in resources to ‘deliveries’

5. Select the top 20 rows of the deliveries table.

6. Select the top 20 rows of the matches table.

7. Fetch data of all the matches played on 2nd May 2013.

8. Fetch data of all the matches where the margin of victory is more than 100 runs.

9. Fetch data of all the matches where the final scores of both teams tied and order it in

descending order of the date.

10. Get the count of cities that have hosted an IPL match.
