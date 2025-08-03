# Indian_Election_Analysis

## 📌 Overview
This project presents a comprehensive SQL-based analysis of the Indian General Elections 2024 using structured datasets. It explores state-wise, party-wise, and candidate-wise performance using advanced SQL techniques such as window functions, CTEs, aggregation, and joins.

Whether you're an analyst, student, or a curious citizen, this analysis offers insights into:

Party performance across states

Alliance-based comparisons (NDA vs I.N.D.I.A vs Others)

Winning margins, vote distributions, and EVM vs Postal votes

Detailed constituency-level insights


## 🧰 Tech Stack
SQL (Tested on Microsoft SQL Server; easily portable to MySQL/PostgreSQL)

Data Sources: Structured .csv/.xlsx tables for:

Constituency-wise results

State-wise mappings

Party-wise seats

Candidate-wise vote details


## 🔍 Key Analytical Questions & SQL Logic
### ✅ Total Seats Overview
Total number of seats nationally

State-wise distribution of available seats

### 🏛️ Party & Alliance Analysis
Total seats won by NDA, I.N.D.I.A, and Others

Individual party performance within alliances

State-wise alliance win breakdown

Alliance with most seats across all states

### 🎯 Constituency-Level Insights
Winning candidate details per constituency

Victory margin analysis

Runner-up vs winner comparisons using ROW_NUMBER() and CTEs

Highest EVM votes by candidate (Top 10)

### ✉️ Vote Type Breakdown
EVM vs Postal vote distribution by candidate

Total votes breakdown for states like Maharashtra


### 🧠 Advanced SQL Concepts Used
CTEs (Common Table Expressions)

Window Functions like ROW_NUMBER() for ranking

CASE WHEN for conditional aggregation

JOINs for multi-table relational analysis

ALTER/UPDATE statements to add alliance tagging

## 📌 Sample Query – State-wise Alliance Performance
SELECT 
    s.State AS State_Name,
    SUM(CASE WHEN p.party_alliance = 'NDA' THEN 1 ELSE 0 END) AS NDA_Seats_Won,
    SUM(CASE WHEN p.party_alliance = 'I.N.D.I.A' THEN 1 ELSE 0 END) AS INDIA_Seats_Won,
    SUM(CASE WHEN p.party_alliance = 'OTHER' THEN 1 ELSE 0 END) AS OTHER_Seats_Won
FROM 
    constituencywise_results cr
JOIN partywise_results p ON cr.Party_ID = p.Party_ID
JOIN statewise_results sr ON cr.Parliament_Constituency = sr.Parliament_Constituency
JOIN states s ON sr.State_ID = s.State_ID
GROUP BY s.State
ORDER BY s.State;


## 📊 Output Insights
NDA performed strongly in [States A, B, C]

I.N.D.I.A had major victories in [States X, Y]

Some constituencies were won by a margin of <1000 votes

Postal votes played a critical role in close contests


## 📎 Notes
Replace 'Uttar Pradesh' or 'Maharashtra' in queries to analyze other states.

Table creation and data import scripts can be added upon request.

Queries are compatible with slight modification for PostgreSQL or MySQL.

## 🙌 Credits
Project created by Sridhar Guggilla


