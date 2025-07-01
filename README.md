# DSA-Final Project
I was given the task of using the knowledge gained so far in the analysis journey to solve 2 different real-life business problems Using Either Excel, SQL or Power BI.
## Case Study 2: Kultra Mega Stores Inventory
## Company Overview
Kultra Mega Stores (KMS), headquartered in Lagos, specialises in office supplies a
furniture. Its customer base includes individual consumers, small businesses (retail), and
large corporate clients (wholesale) across Lagos, Nigeria.
You have been engaged as a Business Intelligence Analyst to support the Abuja division of
KMS. The Business Manager has shared an Excel file containing order data from 2009 
2012 and has requested that you analyze the data and present your key insights and
findings.

**I applied my SQL skills from the DSA Data Analysis class and to solve 11 different analytical and critical thinking questions divided under 2 case scenarios.**

## DATA SOURCES, IMPORTING AND TRANSFORMATION.
1. I imported the csv file named “KMS Sql Case Study” as a flat file and I performed some transformation to the data variables datatype:
  -	I changed the following columns to decimal (10,2) datatype:
    -	Sales,
    -	Discount,
    -	Profit,
    -	Unit Price,
    -	Shipping Cost, and
    -	Product Base Margin.
  -	Order ID was changed to Int from smallint because some values don’t fit in to smallint datatype. Order ID can’t be made primary key because it contains duplicate values.
  -	Order Quantity was changed to Int too from tinyint.
  -	I made Row_ID the primary key (pk).
2. I Imported the second csv file named “Order status” too which contains information about returned products without any transformation.

## EXPLORATORY DATA ANALYSIS
### Case Scenario I 
1. Which product category had the highest sales? 
2. What are the Top 3 and Bottom 3 regions in terms of sales? 
3. What were the total sales of appliances in Ontario? 
4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
5. KMS incurred the most shipping cost using which shipping method? 
### Case Scenario II 
6. Who are the most valuable customers, and what products or services do they typically purchase? 
7. Which small business customer had the highest sales? 
8. Which Corporate Customer placed the most number of orders in 2009 – 2012? 
9. Which consumer customer was the most profitable on 
10. Which customer returned items, and what segment do they belong to? 
11. If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority? Explain your answer


## ANALYSIS
### Case Scenario I
#### 1.	Which product category had the highest sales?
