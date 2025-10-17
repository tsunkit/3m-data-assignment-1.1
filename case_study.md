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
select
	genre,
	round(sum(global_sales), 2) as total_global_sales
from
	vgsales
group by
	genre
order by
	total_global_sales desc --top sales ordered in first row
limit 1;
-- limit to first row only

```
Findings:
```findings
Genre Action contribute the most to global sales(1,751.18)
```
Which platforms generate the highest global sales?

SQL:
```sql
--in shorter form
select platform, round(sum(global_sales), 2) as total_global_sales from vgsales group by 1 order by total_global_sales desc limit 1; --group by 1st column limited by 1 row
```
Findings:
```findings
Platform PS2 generate the highest global sales(1,255.64)
```
Which publishers are the most successful in terms of global sales?

SQL:
```sql
--in even shorter form
select publisher, round(sum(global_sales), 2) from vgsales group by 1 order by 2 desc limit 1; --group by 1st column ordered by 2nd column limited by 1 row
```
Findings:
```findings
Publisher Nintendo is the most successful in term of global saless(1,786,56)
```
How does success vary across regions (North America, Europe, Japan, Others)?

SQL:
```sql
with sales as (
 select 
 	round(sum(NA_Sales),2) as NA_Sales_Sum, 
 	round(sum(EU_Sales),2) as EU_Sales_Sum, 
 	round( sum(JP_Sales),2) as JP_Sales_Sum, 
 	round(sum(Other_Sales),2) as Other_Sales_Sum, 
 	round(sum(global_sales), 2) as Global_Sales_Sum 
 from  vgsales
)
select 
	NA_Sales_Sum, 
	round(NA_Sales_Sum/Global_Sales_Sum * 100, 2 )||'%' as NA_Sales_Percentage,
	EU_Sales_Sum, 
	round(EU_Sales_Sum/Global_Sales_Sum * 100, 2 )||'%' as NA_Sales_Percentage,
	JP_Sales_Sum,
	round(JP_Sales_Sum/Global_Sales_Sum * 100, 2 )||'%' as NA_Sales_Percentage,
	Other_Sales_Sum, 
	round(Other_Sales_Sum/Global_Sales_Sum * 100, 2 )||'%' as NA_Sales_Percentage,
	Global_Sales_Sum 
from sales
```
Findings:
```findings
https://github.com/user-attachments/assets/13597b27-a2b6-420d-b07e-a1b11628457c

```
What are the trends over time in game sales by genre and platform?

SQL:
```sql
select genre, platform, formatted_year, 
sum(NA_Sales) as NA_Sales_Sum, sum(EU_Sales) as EU_Sales_Sum, sum(JP_Sales) as JP_Sales_Sum, sum(Other_Sales) as Other_Sales_Sum , sum(Global_Sales) as Global_Sales_Sum 
FROM (
	select vgs.*, 
	(case when year = 'N/A' then '0' else year end)::INT as formatted_year --convert N/A to 0 and format the year to integer
	from vgsales vgs 
)
group by genre, platform, formatted_year
order by genre, platform, formatted_year
```
Findings:
```findings
https://github.com/user-attachments/assets/76a206b7-9864-4710-ae98-226c6264ac5b

```
Which platforms are most successful for specific genres?

SQL:
```sql
select genre, platform, total_sales from 
(
	select  genre, platform, total_sales, 
		row_number() over (partition by genre order by total_sales desc) as myrank -- set a rank that group by genre generate row number based on descending order of max sales of the group(genre)
	from 
	(
		select genre, platform, sum(Global_Sales) as total_sales 
		from vgsales group by genre, platform  
	)  order by 1, 3 desc -- order by genre and max sales
) where myrank=1 -- show only the top sales of the platform for each genre
```
Findings:
```findings
https://github.com/user-attachments/assets/cdec2511-bf82-4ba6-b17f-9917564e8dc0

```
## Deliverables:
- SQL Queries: Provide all the SQL queries you used to answer the business questions.
- Summary of Findings: For each question, summarise your key findings and recommendations based on your analysis.

## Submission

- Submit the GitHub URL of your assignment to NTU black board.
- Should you reference the work of your classmate(s) or online resources, give them credit by adding either the name of your classmate or URL.
