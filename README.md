# IPL_-Sports_Magazine
Challenge #10: Analyse historical IPL data and provide insights on IPL 2024 for a Sports Magazine (Codebasics)
## Table of Contents:
1. [Problem Statement](https://github.com/pb319/IPL_Sports_Magazine/edit/main/README.md#problem-statement)
2. [Data Modeling](https://github.com/pb319/IPL_Sports_Magazine?tab=readme-ov-file#data-loading)

## Problem Statement
**"Sports Basics"** is a sports blog company that entered space recently. They
wanted to get more traffic to their website by releasing a special edition magazine
on IPL 2024. This magazine aims to provide interesting insights and facts for
fans, analysts and teams based on the last 3 years' data.
The chief editor Tony Sharma oversees this publication, and he believes in data
analytics. He reached out to Peter Pandey, a journalist in his team who is a data-savvy cricket enthusiast.

## Data Loading
1. MySQL
- First I created a database called "ipl" using the following command

  ```CREATE DATABASE IF NOT EXISTS "ipl";```

- I used Mysql Workbench Table Data Import Wizard to import 
   - [fact_bowling_summary.csv](https://github.com/pb319/IPL_Sports_Magazine/files/14800053/fact_bowling_summary.csv)
   - [dim_match_summary.csv](https://github.com/pb319/IPL_Sports_Magazine/files/14800054/dim_match_summary.csv)
   - [dim_players.csv](https://github.com/pb319/IPL_Sports_Magazine/files/14800055/dim_players.csv)
   - [fact_bating_summary.csv](https://github.com/pb319/IPL_Sports_Magazine/files/14800056/fact_bating_summary.csv)

![01](https://github.com/pb319/IPL_Sports_Magazine/assets/66114329/2f5c505a-73e5-471b-8489-94c8c45a0b34)

Similarly, I added all other dimensions and fact tables into the Mysql Workbench:

  ![02](https://github.com/pb319/IPL_Sports_Magazine/assets/66114329/b3cd8eaf-1955-4840-88a6-707ba121d2f9)

The table names have been changed slightly using Mysql Workbench using the following bunch of code:
```
USE ipl;

ALTER TABLE dim_match_summary
RENAME TO  dim_match;

ALTER TABLE fact_bating_summary
RENAME TO  fact_bating;

ALTER TABLE fact_bowling_summary
RENAME TO  fact_bowling;
```
Connecting Mysql Database with **Power BI**:

  ![04](https://github.com/pb319/IPL_Sports_Magazine/assets/66114329/6b2ba598-1206-431c-b311-87f6a198571e)

## Data Exploration

1. Mysql
  - Top 10 Batsman
    ```SELECT * FROM fact_bating LIMIT 5;
        -- Top 10 batsmen based on past 3 years total runs scored.
        SELECT batsmanName as Name, SUM(runs)as Total_Run 
        FROM fact_bating
        GROUP BY batsmanName
        ORDER BY Total_Run DESC
        LIMIT 10;
    ```

