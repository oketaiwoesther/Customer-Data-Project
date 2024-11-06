# Customer-Data-Project
### Project Title: Customer Data Analysis
### Project Overview
This project aims to analyze customer data to uncover insights into buying patterns, preferences, and behavior. By identifying key trends, we seek to inform strategies that enhance customer satisfaction, improve engagement, and support business growth through data-driven decisions.

### Data Sources
The primary dataset for this analysis, Data_sales.csv, is an open-source file exclusively available for download to members of the Ladies in Tech Africa group. It can be accessed through various online platforms and open data repositories.

### Project Objective
This project was designed to address the following Analysis goals;
1. Analyze customer data using pivot tables to find subscription patterns.
2. Calculate the average subscription duration and identify the most populars subscription types.
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

### Inference
Popularity of Subscription Types:

- The Basic subscription type is the most popular, with the highest number of active (non-canceled) subscriptions. This suggests it is the most appealing option for customers, likely due to affordability or meeting essential needs.
Cancellation Rates Across Subscription Types:

- Premium and Standard subscriptions show a higher proportion of cancellations compared to Basic. This could indicate that customers may find less value in these higher-tier plans or that they may be more price-sensitive at these levels.
Retention of Basic Subscribers:

- The Basic subscription type not only has the highest number of subscribers but also appears to have a relatively lower cancellation rate. This suggests that customers in the Basic tier are more likely to continue their subscriptions, possibly due to affordability or meeting minimal requirements.
Potential Focus Areas for Improvement:

Since Premium and Standard plans have a noticeable number of cancellations, there may be an opportunity to improve retention by enhancing features, offering incentives, or adjusting pricing in these tiers.

Preference for Basic Subscription:

The Basic subscription type has the highest count of customers, significantly more than both Premium and Standard. This indicates that most customers prefer the Basic plan, likely due to factors such as affordability, essential features, or meeting their core needs.
Lower Adoption of Premium and Standard Subscriptions:

Premium and Standard subscriptions have similar customer counts, but both are much lower than the Basic subscription. This suggests that higher-tier plans are less appealing to the majority of customers, possibly because they do not see enough additional value to justify the higher cost.
Potential Focus on Basic Plan:

Given the popularity of the Basic subscription, it may be beneficial for the company to continue enhancing this plan or offering slight upgrades to encourage more customer loyalty and retention.
Opportunities for Premium and Standard Plans:

With fewer customers in Premium and Standard plans, there could be opportunities to explore customer feedback and improve these offerings, either by adding more benefits, adjusting pricing, or creating bundled options to make these plans more attractive.

### Conclusion
the data indicates a clear preference among customers for the Basic subscription plan, suggesting that it aligns well with their primary needs, likely due to its affordability or essential feature set. Conversely, the Premium and Standard plans, which have similar but significantly lower customer counts, may benefit from enhancements to boost their appeal. To drive growth in these higher-tier plans, the company could consider adding value, refining pricing strategies, or offering attractive bundles. Focusing on customer feedback could be key to optimizing these plans and ensuring they meet evolving customer expectations.







