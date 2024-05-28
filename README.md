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

YTD TOTAL Sold
```Dax  
TOTALYTD(SUM(Sheet1[Sold Price]),'CA sold date'[Date],"30,4,2024")
```
Previous YTD Total sold
``` dax 
TOTALYTD(SUM(Sheet1[Sold Price]),'CA sold date'[Date],'CA sold date',"01,05,2023")
```
Sale difference
```dax
[YTD Total sold]-[Previous YTD Total sold]
```
sale Difference in colour to show when sales is low 
```dax
IF([Sale difference]>0, "Green", "Red")
```
YOY Sale Growth
```dax
[Sale difference] / [Previous YTD Total sold]
```
YTD Total purchase
```dax
TOTALYTD(SUM(Sheet1[Purchase Price]),'CA purchase date'[Date],"30,4,2024")
```
MTD Total sale
```dax
TOTALMTD(SUM(Sheet1[Sold Price]), 'CA sold date'[Date])
```
MTD KPI
```dax
CONCATENATE("MTD Total Sale : ",FORMAT([MTD Total sale]/1000000,"£0.00m"))
```
MTD Total purchase
```dax
TOTALMTD(SUM(Sheet1[Purchase Price]),'CA purchase date'[Date])
```
MTD KPI Purchase
```dax
CONCATENATE("MTD Total Purchase : ",FORMAT([MTD Total sale]/1000000,"£0.00m"))
```
Combined YTD Total Sold
```dax
[YTD Total purchase] + [YTD Total Sold] + [YTD Total Sold Agreed]
````
YTD Total Sold Agreed
```dax
TOTALYTD(COUNT(Sheet1[Vehicle ID]), 'CA sold date'[Date])
```

Total CAP Value
```dax
SUM(Sheet1[CAP Value])
```
Total Sales
```dax
SUM(Sheet1[Purchase Price])
```
Total Metal Margin
```dax
SUM(Sheet1[Metal Margin])
```
Max Point
```dax
IF(MAXX(ALLSELECTED('CA sold date'[Month]),[Total Sales])= [Total Sales],MAXX(ALLSELECTED('CA sold date'[Month]),[Total Sales]),BLANK())![image]
```
## Dashboard 
![power bi screen ](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/a74dd5dd-9dcd-4a81-a9a4-8e53fb308d83)
![Screenshot 2024-05-28 015058](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/b26da192-192c-4f9b-941a-c52ad0111612)
![Screenshot 2024-05-28 014419](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/da64f55c-5949-45c5-8c91-a21b49fcb87e)
![Screenshot 2024-05-28 014612](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/6ec2e81c-7c9a-4516-a875-db65e8fc46ec)
![Screenshot 2024-05-28 014824](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/3b1cbef7-960a-487e-a27a-71db32b02d16)
![Screenshot 2024-05-28 014919](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/ea727018-c8e2-44b7-9fe7-2890219ddbee)
![Screenshot 2024-05-28 014919](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/c06ea093-55a3-4c7e-99cd-48db7e234b7d)
![Screenshot 2024-05-28 015001](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/7e48a1b7-3b2b-4f4c-a97b-e3e2c63a0cf4)
![Screenshot 2024-05-28 015058](https://github.com/Credle11/Company-car-sales-dashboard-/assets/170504844/8fe31fc3-88a2-405c-80f9-502529f9e64e)


