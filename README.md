# Project-2
Documentation of my 2nd Project in Data Analysis

### PROJECT TITLE: Customer Segmentation and Trend Analysis for a Subscription Service

### OUTLINE
[PROJECT OVERVIEW](#project-overview)

[DATA SOURCES](#data-sources)

[TOOLS USED](#tools-used)

[DATA CLEANING AND PREPARATIONS](#data-cleaning-and-preparations)

[EXPLORATORY DATA ANALYSIS](#exploratory-data-analysis)

[DATA ANALYSIS](#data-analysis)

[DATA VISUALIZATION](#data-visualization)

### PROJECT OVERVIEW
This project focuses on analyzing customer data for a subscription-based service to gain insights into customer behavior, subscription patterns, and key trends in cancellations and renewals leveraging SQL, Excel, and Power BI. The objective is to segment the customer base, identify the most popular subscription types, patterns in subscriptions and cancellations and evaluate factors influencing customer retention and revenue generation.

Using tools like Excel, SQL and Power BI, the project involves creating detailed reports and dashboards that showcase subscription trends, average subscription durations, and revenue patterns over time. The deliverables include pivot tables and visual representations that help in strategic decision-making to improve customer satisfaction, enhance retention, and optimize marketing strategies. The final Power BI dashboard will present a comprehensive view of the findings, offering actionable insights to inform business strategies for business growth and improved customer engagement.

### KEY STEPS:

#### Data Exploration in Excel:
  -  Used pivot tables to summarize:
        -  Sum of Revenue per Region
        -  Sum of Revenue per Subscription Type
        -  Average Revenue per Subscription Type
        -  Count of Subscription per Region/Subscription Type
        -  
        -  Sales by Month, detailed for the years 2023 and 2024
        -  Calculated metrics such as average sales per product and total revenue by region.
        -  Created additional reports highlighting key sales metrics and trends.

#### SQL Analysis:
  -  Loaded the dataset into SQL Server and wrote queries to extract insights on customer and subscription performance.
  -  Key queries include:

        -  Total Number of Customers by Region
        -  Most Popular Subscription Type by Customer Count
        -  Customers Who Canceled Within 6 Months
        -  Average Subscription Duration for All Customers
        -  Customers with Subscriptions Longer Than 12 Months
        -  Total Revenue by Subscription Type
        -  Top 3 Regions by Subscription Cancellations
        -  Total Number of Active and Canceled Subscriptions

#### Power BI Visualization:
  -  Built an interactive dashboard that showcases the findings from Excel and SQL.
  -  Included visual representations of key metrics such as:
        -  Subscription trends
        -  Revenue by subscription type
        -  Customer segmentation by region
        -  Cancellation and renewal patterns

 ### DATA SOURCES
   -  Customer Subscription Data Excel file
   -  Customer Subscription Data csv file

 ### TOOLS USED
   -   Microsoft Excel [Download Here](https://www.microsoft.com)
          - For Data Cleaning
          - For Analysis
          - For data Visualization
   -   SQL - Structured Query Language for Data Quering
   -   Github for Portfolio building
   -   Microsoft Power BI
          - Data Cleaning
          - Analysis
          - Visualization

### DATA CLEANING AND PREPARATIONS
In the initial phase of Data Cleaning and preparations, i performed the following actions;
  -   **Data loading and Inspection**: Imported the dataset and reviewed the structure, checking for data types and anomalies.
  -   **Handling missing variables**: Identified and addressed missing or inconsistent values to ensure data integrity.
  -   **Data Cleaning and formatting**: Standardized date formats, corrected inconsistent entries, and ensured numerical columns were properly formatted for analysis.

### EXPLORATORY DATA ANALYSIS
This involved exploring of the Data to answer some questions about the Data such as;
  -   **Top 3 Regions by Subscription Cancellations**: Identified regions with the highest cancellation rates to understand geographic trends.
  -   **Popular Subscription Types**: Analyzed which subscription types had the highest adoption rates.
  -   **Average Subscription Duration**: Calculated the typical length of subscriptions to gauge customer retention.
  -   **Revenue Trends by Year**: Examined how revenue evolved over time, particularly focusing on recent years.
  -   **Customers Who Canceled Within 6 Months**: Determined the proportion of early cancellations.
  -   **Subscription Counts by Region and Type**: Assessed regional preferences for different subscription types.
  -   **Total Revenue by Subscription Type**: Evaluated financial contributions from each subscription type.
  -   **Active vs. Canceled Subscriptions**: Compared the total number of ongoing subscriptions to those that were canceled.

### DATA ANALYSIS
This is where I included some basic lines of code or queries and some of the DAX expressions used during the analysis;

#### Data Analysis with Excel

1.  AVERAGE  subscription duration  BY subscription TYPE

   BASIC    =AVERAGEIF(D2:D33788,D2,I2:I33788)
   
   PREMIUM  =AVERAGEIF(D2:D33788,D33773,I2:I33788)
   
   STANDARD =AVERAGEIF(D2:D33788,D5,I2:I33788)

   ![image](https://github.com/user-attachments/assets/3445a5e0-05ac-466e-a687-7fab783ee042)

2.   SUM OF  subscription REVENUE  BY subscription TYPE

     BASIC    =SUMIF(D2:D33788,D2,H2:H33788)
     
     PREMIUM  =SUMIF(D2:D33788,D3,H2:H33788)
     
     STANDARD =SUMIF(D2:D33788,D5,H2:H33788)

![image](https://github.com/user-attachments/assets/ea1c4af6-aac2-4f01-9d54-152687c452a5)

3. SUMMARIES AS FOLLOWS
   
       Sum of Revenue by Region (A)
       Sum of Revenue by Subscription Type (B)
       Average of Revenue by Subscription Type (C)
       Count of Subscription Type per Region/Subscription Type (D)
       Count of Cancelled per SubscriptionType (E)
   
![image](https://github.com/user-attachments/assets/b0fe251c-2bf5-4273-a2d6-0b8748ada70f)




#### Data Analysis with SQL
---
1.  **Total number of customers from each region**:
   ```
SELECT Region, COUNT(CustomerID) AS TotalCustomers
FROM CustomerData
GROUP BY Region;
```
![Screenshot 2024-11-04 235734](https://github.com/user-attachments/assets/bf27f038-6f79-4be5-b7bf-577a3892a5fc)

2.  **Most popular subscription type by the number of customers**:
```
SELECT TOP 1 SubscriptionType, COUNT(CustomerID) AS CustomerCount
FROM CustomerData
GROUP BY SubscriptionType
ORDER BY CustomerCount DESC;
```
![Screenshot 2024-11-05 000140](https://github.com/user-attachments/assets/57e1b626-41fb-4b64-ae2c-27219af3db7c)

3.  **Customers who canceled their subscription within 6 months**.
```
SELECT CustomerID, CustomerName, SubscriptionType, SubscriptionStart, SubscriptionEnd
FROM CustomerData
WHERE Canceled = 0
  AND MONTH (SubscriptionStart) <= 6;
```

4.  **Average subscription duration for all customers**.
```
SELECT AVG([Subscription_Duration]) AS AverageDuration
FROM CustomerData;
```
![image](https://github.com/user-attachments/assets/9f7f5dfb-3419-4142-bd3d-8e6475ef0409)

5.  **Customers with subscriptions longer than 12 months**.
```
SELECT CustomerID, CustomerName, SubscriptionType, SubscriptionStart, SubscriptionEnd
FROM CustomerData
WHERE [Subscription_Duration] > 365;
```

6.  **Total revenue by subscription type**.
```
SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM CustomerData
GROUP BY SubscriptionType;
```
![image](https://github.com/user-attachments/assets/65eda97c-8168-46f4-aecd-9c7d3da15d03)

7.  **Top 3 regions by subscription cancellations**.
```
SELECT TOP 3 Region, COUNT(CustomerID) AS Cancellations
FROM CustomerData
WHERE Canceled = 1
GROUP BY Region
ORDER BY Cancellations DESC;
```
![image](https://github.com/user-attachments/assets/7a9a4c3c-585e-4013-9c79-f7f317e17ed7)

8.  **Total number of active and canceled subscriptions**.
```
SELECT 
    SUM(CASE WHEN Canceled = 0 THEN 1 ELSE 0 END) AS ActiveSubscriptions,
    SUM(CASE WHEN Canceled = 1 THEN 1 ELSE 0 END) AS CanceledSubscriptions
FROM CustomerData;
```
![image](https://github.com/user-attachments/assets/a3309d0a-0769-4557-82ee-0e37c477d54d)


### DATA VISUALIZATION

#### From Excel

![image](https://github.com/user-attachments/assets/ac7714c4-f298-4397-8844-73af368bde70)

![image](https://github.com/user-attachments/assets/83c82676-e115-41ee-9586-ae7bf44d56db)

![image](https://github.com/user-attachments/assets/2e3fff47-129e-4a14-b68f-e2d913566efd)


