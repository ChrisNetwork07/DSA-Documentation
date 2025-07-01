# DSA-Final Project

**I applied my SQL skills from the DSA Data Analysis class and to solve 11 different Exploratory Data Analysis (EDA) divided under 2 case scenarios.**

## Case Study 2: Kultra Mega Stores Inventory
## Company Overview
Kultra Mega Stores (KMS), headquartered in Lagos, specialises in office supplies a
furniture. Its customer base includes individual consumers, small businesses (retail), and
large corporate clients (wholesale) across Lagos, Nigeria.
You have been engaged as a Business Intelligence Analyst to support the Abuja division of
KMS. The Business Manager has shared an Excel file containing order data from 2009 
2012 and has requested that you analyze the data and present your key insights and
findings.

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
I analyzed this using the query below to know that the product category with the highest sales was Technology

```select Product_category, SUM(sales) as [Total Sales]
from [dbo].[KMS Sql Case Study]
group by Product_category
order by SUM(sales) desc
```

#### 2.	What are the Top 3 and Bottom 3 regions in terms of sales?
The top 3 regions in terms of sales are: West (3597549.41), Ontario (3063212.60) and Prarie (2837304.60)

```select top 3 Region, SUM(sales) as [Total Sales]
from [dbo].[KMS Sql Case Study]
group by Region
order by SUM(sales) desc
```

The bottom 3 regions in terms of sales are: Yukon (975867.39), Northwest Territories (800847.35), and Nunavut (116376.47)

```select top 3 Region, SUM(sales) as [Total Sales]
from [dbo].[KMS Sql Case Study]
group by Region
order by SUM(sales) asc
```

#### 3.	What were the total sales of appliances in Ontario?
The total sales of appliances in Ontario = 3063212.60

```select Region, SUM(sales) as [Total Sales]
from [dbo].[KMS Sql Case Study]
where Region = 'Ontario'
group by Region
```

#### 4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
In order to advise the management meaningfully, I firstly identified the bottom 10 customers by total sales using the query below:

```select top 10 Order_ID, customer_name, Region, Order_Priority, Ship_Mode,Shipping_Cost, Profit, customer_segment, SUM(sales) as [Total Sales]
from [dbo].[KMS Sql Case Study]
group by Order_ID, customer_name, Region, Order_Priority,Ship_Mode, Shipping_Cost, Profit, customer_segment
order by SUM(sales) asc
```

My advice to the management is that they should cross-sell and up-sell complementary or premium products to these customers through targeted email with limited-time discounts and loyalty points attach to the products recommendation. That at a certain loyalty point they will be eligible for free shipping of their products.

#### 5.	KMS incurred the most shipping cost using which shipping method?
KMS incurred the most shipping cost using Delivery trunk.

```select top 1 Ship_Mode,SUM(Shipping_Cost) as [Total shipping cost]
from [dbo].[KMS Sql Case Study]
group by Ship_Mode
```

### Case Scenario II
### 6.	Who are the most valuable customers, and what products or services do they typically purchase?
They are the customers that the company made highest profits from their transactions and they typically purchased products in Technology and Office supplies categories.
I got these customers using the query below:
```select top 30 Order_ID, customer_name, Order_Quantity,Product_Category, Product_Name, Profit, SUM(sales) as [Total Sales]
from [dbo].[KMS Sql Case Study]
group by Order_ID, customer_name, Order_Quantity,Product_Category, Product_Name, Profit
order by Profit desc
```

### 7.	Which small business customer had the highest sales?
Small business owned by Dennis Kane had the highest sales (75967.59)
```select top 1 Customer_Name, Customer_Segment, SUM(Sales) as [Highest Sale]
from [KMS Sql Case Study]
where Customer_Segment = 'Small business'
group by Customer_Name, Customer_Segment
order by [Highest Sale] desc
```

### 8.	Which Corporate Customer placed the most number of orders in 2009 – 2012?
Laurel Elliston was the corporate customer with the highest number of orders in 2009-2012 with 148 orders.
```select top 1 Customer_Name, Customer_Segment, Order_Date ,sum(Order_Quantity) as [Highest No of orders]
from [KMS Sql Case Study]
where Customer_Segment = 'corporate' and Order_Date between '2009-01-01' and '2012-12-31'
group by Customer_Name, Customer_Segment, Order_Date
order by [Highest No of orders] desc
```
or
```select top 1 Customer_Name, Customer_Segment, Order_Date ,sum(Order_Quantity) as [Highest No of orders]
from [KMS Sql Case Study]
where Customer_Segment = 'corporate' and year(Order_Date) between 2009 and 2012
group by Customer_Name, Customer_Segment, Order_Date
order by [Highest No of orders] desc
```

### 9.	Which consumer customer was the most profitable one?
The most profitable consumer customer was Emily Phan with total profits = 34005.44
```select top 1 Customer_Name, Customer_Segment,sum(Profit) as [Highest Profits]
from [KMS Sql Case Study]
where Customer_Segment = 'consumer'
group by Customer_Name, Customer_Segment
order by [Highest Profits] desc
``` 
alternatively
```select top 1 Customer_Name, Customer_Segment,sum(Profit) as [Highest Profits]
from [KMS Sql Case Study]
group by Customer_Name, Customer_Segment
having Customer_Segment = 'consumer'
order by [Highest Profits] desc
```

### 10.	Which customer returned items, and what segment do they belong to?
I got the list of customers that returned items, and the segment they belong by Joining the two (2) tables given; KMS Sql Case Study and Order_Status
```
[dbo].[KMS Sql Case Study] k
[dbo].[Order_Status] s

select k.Customer_Name,k.Customer_Segment, s.[Status]
from [dbo].[KMS Sql Case Study] k
join [dbo].[Order_Status] s
on k.Order_ID=s.Order_ID
group by Customer_Name, Customer_Segment, [Status]
order by Customer_Segment
```

### 11.	If the delivery truck is the most economical but the slowest shipping method and Express Air is the fastest but the most expensive one, do you think the company appropriately spent shipping costs based on the Order Priority? Explain your answer

