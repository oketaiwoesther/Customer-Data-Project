# Customer-Data-Project
### Project Title: Customer Data Analysis
### Project Overview
This project aims to analyze customer data to uncover insights into buying patterns, preferences, and behavior. By identifying key trends, we seek to inform strategies that enhance customer satisfaction, improve engagement, and support business growth through data-driven decisions.

### Data Sources
The primary dataset for this analysis, Data_sales.csv, is an open-source file exclusively available for download to members of the Ladies in Tech Africa group. It can be accessed through various online platforms and open data repositories.

### Project Objective
This project was designed to address the following Analysis goals;
1. Analyze customer data using pivot tables to find subscription patterns.
2. Calculate the average subscription duration and identify the most populars ubscription types.
3. Create any other interesting reports.
4. Retrieve the total number of customers from each region.
5. Find the most popular subscription type by the number of customers.
6. Find customers who canceled their subscription within 6 months.
7. Calculate the average subscription duration for all customers.
8. Find customers with subscriptions longer than 12 months.
9. Calculate total revenue by subscription type.
10. Find the top 3 regions by subscription cancellations.
11. Find the total number of active and canceled subscriptions.
12. Build a Power BI dashboard that visualizes key customer segments, cancellations, and subscription trends. Include slicers for interactive analysis.

### Key Metrics
- Average Revenue Per User (ARPU) - Indicates the average income generated per user or customer.
- Customer Satisfaction Score (CSAT) - Assesses how satisfied customers are with specific interactions or the overall experience.
- Purchase Frequency - Measures how often customers make purchases, helping identify highly engaged customers.

### How To Used The Data
- Total Revenue by SubscriptionType: Segment total revenue by each subscription type (e.g., monthly, quarterly, yearly) to identify which subscriptions are most profitable
- Total No of Customer: Monitor the total customer count over time to gauge growth, stagnation, or decline in customer acquisition.
- Average Subscription Duration: Segment average subscription duration by factors like subscription type, customer demographics, or geographic location.

### Data Cleaning and Preparation
At the beginning of data cleaning and preparation, we carry out the following steps:
1. Data loading and Inspection
2. Handling missing variables
3. Data Cleaning and formatting

### Formular Used
```
SELECT * FROM [dbo].[lita capstone_CustomersData]

--- The total number of customers from each region.
SELECT Region, 
       COUNT(DISTINCT CustomerID) AS TotalCustomers
FROM dbo.[lita capstone_CustomersData]
GROUP BY Region;

--- The most popular subscription type by the number of customers.
SELECT TOP 1 SubscriptionType, 
       COUNT(DISTINCT CustomerID) AS CustomerCount
FROM dbo.[lita capstone_CustomersData]
GROUP BY SubscriptionType
ORDER BY CustomerCount DESC;

--- customers who canceled their subscription within 6 months.
SELECT CustomerID, 
       SubscriptionStart, 
       SubscriptionEnd
FROM [dbo].[lita capstone_CustomersData]
WHERE Canceled = 'True' 
	AND DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) <= 6;
	
 --- The average subscription duration for all customers.
SELECT AVG(DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd)) AS AverageSubscriptionDurationDays
FROM dbo.[lita capstone_CustomersData]
WHERE SubscriptionEnd IS NOT NULL;

---  customers with subscriptions longer than 12 months.
SELECT CustomerID, 
       SubscriptionStart, 
       SubscriptionEnd
FROM [dbo].[lita capstone_CustomersData]
WHERE DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd) > 12;

--- calculate total revenue by subscription type. 
SELECT SubscriptionType, 
       SUM(Revenue) AS TotalRevenue
FROM [dbo].[lita capstone_CustomersData]
GROUP BY SubscriptionType;

--- Top 3 regions by subscription cancellations
SELECT TOP 3 Region, 
       COUNT(*) AS CancellationCount
FROM [dbo].[lita capstone_CustomersData]
WHERE Canceled = 'True'  -- Only count canceled subscriptions
GROUP BY Region
ORDER BY CancellationCount DESC;

--- The total number of active and canceled subscriptions.
SELECT 
    Canceled, 
    COUNT(*) AS TotalSubscriptions
FROM 
    [dbo].[lita capstone_CustomersData]
GROUP BY 
    Canceled;

SELECT COUNT(DISTINCT CustomerID) AS TotalUniqueCustomers
FROM [dbo].[lita capstone_CustomersData];
```

### Tools and Method Used
- Microsoft Excel  The Data was analysis using Microsoft Excel, utilizing pivot table to organize, summarize , and filter the Data for easier interpretation [Download Here](https://canvas.instructure.com/courses/10186984/files/folder/Capstone%20Project)
- SQL - Structured Query Language for Querying of Data
- Power BI - For Visualization
- GitHub for Portfolio Building


### Visual Analysis and Inference

![image](https://github.com/user-attachments/assets/79135e89-1db4-4398-bf0c-aed02bf0bc0c)

![image](https://github.com/user-attachments/assets/dad4416b-e7ff-4a79-b25c-1c247bff0949)

![customerData short](https://github.com/user-attachments/assets/cee8bdda-c0f2-45b2-b41d-6287c6f77fde)

![CustomerData short2](https://github.com/user-attachments/assets/a9b40e14-67be-403e-a3d0-36d883a51369)

![customerData power bi short](https://github.com/user-attachments/assets/755becfc-baf4-4171-a8c7-71d0de6779ec)

### Conclusion
