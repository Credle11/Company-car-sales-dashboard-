# Company-car-sales-dashboard-
# Performance Analysis 

## Project Overview 

The primary goal of this project is to analyze the vehicle sales data to identify trends and insights that can inform future business decisions. The analysis focuses on key metrics such as the number of vehicles sold, CAP values, metal margins, and the relationship between various dates in the sales process.

### Data Sources

The data is sourced from the vehicle sales records and includes the following columns:

* Deal Agreed Date:The date when the potential purchase of a vehicle was agreed upon.
* Purchase Date: The date when the payment was made to the customer for the vehicle.
* Sold Date: The date when the vehicle was sold at auction.
* Affiliate: The source from which the vehicle was purchased.
* CAP Value: The industry guide to the resale value of the vehicle.
* Metal Margin: The profit or loss made on the vehicle.
* Vehicle ID: Unique identifier for each vehicle.

## Tools Used
* Excel : Data clleaning 
* Microsoft Power BI: For data visualization and analysis.
* DAX (Data Analysis Expressions): For calculating complex metrics and aggregations.

## Data Preparation
* Data Cleaning: The dataset was reviewed for missing values, especially in crucial columns such as sales dates and prices. Missing values were addressed appropriately, either by imputation or exclusion.
* Data Formatting: We ensured that all numerical values, especially those stored as text, were correctly formatted. This included converting date fields to proper date formats and numeric fields to appropriate data types.

## Key Metrics and Calculations
* Number of Vehicles Sold Per Month: Using the 'Sold Date' to count the number of vehicles sold each month.
* Total CAP Value: Calculating the total CAP value for all vehicles.
* Year-to-Date (YTD) and Month-to-Date (MTD) Calculations:
     1. YTD Total Vehicles Sold
     2. MTD Total Vehicles Sold
     3. YTD CAP Value
* Previous YTD and MTD calculations for comparison

## Data analysis 

```Dax
TOTALYTD(SUM(Sheet1[Sold Price]),&#39;CA sold date&#39;[Date],&quot;30,4,2024&quot;)
TOTALYTD(SUM(Sheet1[Sold Price]),&#39;CA sold date&#39;[Date],&#39;CA sold date&#39;,&quot;01,05,2023&quot;)
[YTD Total sold]-[Previous YTD Total sold]
IF([Sale difference]&gt;0, &quot;Green&quot;, &quot;Red&quot;)
[Sale difference] / [Previous YTD Total sold]
TOTALYTD(SUM(Sheet1[Purchase Price]),&#39;CA purchase date&#39;[Date],&quot;30,4,2024&quot;)
TOTALMTD(SUM(Sheet1[Sold Price]), &#39;CA sold date&#39;[Date])
CONCATENATE(&quot;MTD Total Sale : &quot;,FORMAT([MTD Total sale]/1000000,&quot;£0.00m&quot;))
TOTALMTD(SUM(Sheet1[Purchase Price]),&#39;CA purchase date&#39;[Date])
CONCATENATE(&quot;MTD Total Purchase : &quot;,FORMAT([MTD Total sale]/1000000,&quot;£0.00m&quot;))
[YTD Total purchase] + [YTD Total Sold] + [YTD Total Sold Agreed]
TOTALYTD(COUNT(Sheet1[Vehicle ID]), &#39;CA sold date&#39;[Date])
SUM(Sheet1[CAP Value])
SUM(Sheet1[Purchase Price])
SUM(Sheet1[Metal Margin])
IF(MAXX(ALLSELECTED(&#39;CA sold date&#39;[Month]),[Total Sales])= [Total Sales],MAXX(ALLSELECTED(&#39;CA sold
date&#39;[Month]),[Total Sales]),BLANK())
![image](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/c080c996-ed2b-4884-9260-565ebb931e62)
