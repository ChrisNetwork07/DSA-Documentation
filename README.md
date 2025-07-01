# DSA-Final Project (My first business analysis Project)
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
