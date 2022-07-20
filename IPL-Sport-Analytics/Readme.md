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

	    CREATE TABLE matches(
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
		);
		
2. Create a table named ‘deliveries’ with appropriate data types for columns

```
CREATE TABLE deliveries (
    id INT,
    inning INT,
    `over` INT,
    ball INT,
    batsman VARCHAR(40),
    non_striker VARCHAR(40),
    bowler VARCHAR(40),
    batsman_runs INT,
    extra_runs INT,
    total_runs INT,
    is_wicket INT,
    dismissal_kind VARCHAR(40),
    player_dismissed VARCHAR(40),
    fielder VARCHAR(40),
    extras_type VARCHAR(40),
    batting_team VARCHAR(40),
    bowling_team VARCHAR(40),
    FOREIGN KEY(id) REFERENCES matches(id)
);
 ```
3. Import data from CSV file ’IPL_matches.csv’ attached in resources to ‘matches’

Here, data cleaning should be performed first. The date format should be similar and I prefer it to be in yyyy-mm-dd format. 
To change the date format to yyyy-mm-dd: right cick > Format cells > Number > Date > selecting 'yyyy-mm-dd' format > Ok. And save te file.
Since the file is too large to load into mysql, its better to use "load data infile" command
loading 'IPL_matches.csv'.

```
LOAD DATA INFILE 'D:/!. Azub learning/1. Start tech internship/Task 2/IPL_matches.csv' INTO TABLE matches
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
ESCAPED BY '\\'
LINES TERMINATED BY '\n'
IGNORE 1 LINES
(id,city,date,player_of_match,venue,neutral_venue,team1,team2,toss_winner,toss_decision,winner,result,result_margin,eliminator,method,umpire1,umpire2)
;
```

The variable `secure_file_priv` is used to limit the effect of data import and export operations. 
To see the current folder for upload, Just execute the below command after login in to your MySQL command line.
` SHOW VARIABLES LIKE "secure_file_priv";`
