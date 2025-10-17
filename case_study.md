# Video Game Sales Analysis

## Dataset

You will be working with the following dataset: [Video Game Sales](https://www.kaggle.com/datasets/gregorut/videogamesales?resource=download)

📦 **Dataset Download Instructions**
1. Download the dataset ZIP file from the above link.
2. After downloading: Unzip the file to access vgsales.csv. Note the full file path to vgsales.csv — you'll need it in the next step.

🔍 **Challenge: Load the Data into DuckDB**
Using DBeaver and your DuckDB connection, how would you load the vgsales.csv file into a table so you can begin querying it?

## Business Question
How can game developers and publishers optimize their strategy to maximize global sales by understanding the performance of different game genres, platforms, and publishers?

*To answer the above question, use the following SQL queries to explore the dataset and address the following questions:*

Which genres contribute the most to global sales?

SQL:
```sql
SELECT Genre, sum(Global_Sales) as Sales
FROM  vgmain.vgsales
GROUP BY Genre 
Order by Sales DESC


```
Findings:
```findings
Action
```
Which platforms generate the highest global sales?

SQL:
```sql
SELECT  Platform, sum(Global_Sales) as Sales
FROM  vgmain.vgsales
GROUP BY  Platform 
Order by Sales DESC

```
Findings:
```findings
PS2
```
Which publishers are the most successful in terms of global sales?

SQL:
```sql
SELECT  Publisher, sum(Global_Sales) as Sales
FROM  vgmain.vgsales
GROUP BY  Publisher 
Order by Sales DESC
```
Findings:
```findings
Nintendo
```
How does success vary across regions (North America, Europe, Japan, Others)?

SQL:
```sql
SELECT 
round(sum(NA_Sales)/sum(Global_Sales),2) as NA,
round(sum(EU_Sales)/sum(Global_Sales),2) as EU,
round(sum(JP_Sales)/sum(Global_Sales),2) as JP, 
round(sum(Other_Sales)/sum(Global_Sales),2) as Other
FROM  vgmain.vgsales
```
Findings:
```findings
NA:49%, EU:27%, JP:14%, Other:9% 
```
What are the trends over time in game sales by genre and platform?

SQL:
```sql
SELECT  Year, Genre, platform, sum(Global_Sales)
FROM  vgmain.vgsales
GROUP BY  Year, Genre, Platform 
Order by year
```
Findings:
```findings
Larg data, may use graphs
```
Which platforms are most successful for specific genres?

SQL:
```sql
SELECT  Platform, Genre, sum(Global_Sales) as Sales
FROM  vgmain.vgsales
where Genre  = 'Sports'
GROUP BY  Platform,Genre
```
Findings:
```findings
Larg data, may use graphs
```
## Deliverables:
- SQL Queries: Provide all the SQL queries you used to answer the business questions.
- Summary of Findings: For each question, summarise your key findings and recommendations based on your analysis.

## Submission

- Submit the GitHub URL of your assignment to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
