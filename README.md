# LITA_CAPSTONE_PROJECT-Customerdata

## Project Title: Customer Data
## Project Content
- [Project Title](#project-title)
- [Project Content](#project_content)
- [Project Overview](#project_overview)
- [Project Aim & Objectives](#project_aim_and_objective)
- [Data Source and Methodology](#data_sources_and_methodology)
- [Analytical Result](#analytical_result)
- [Conclusion](#conclusion)

## Project Overview
This project involves analyzing customer data for a subscription service to identify segments and trends.
## Project Aim & Objectives
 The primary aim of this project is to understand customer behaviour.

Project Objectives
- Track Subscription types.
- Identify key trends in cancellation and renewals 

## Data Source and Methodology
Dataset was provided by Incubator hub instructors. 
-  The variables includes:
     - Customer ID: distinct code given to each customers used for each subscription
     - Customer Name: Name unique to each customers used for multiple subsccription
     - Region: Location of Subscription (East, West, South and North)
     - Subscription Type: Specific subscription choice
     - Subscription Start: Date when subscription begins
     - Subscription End: Date when subscriptin finishes
     - Cancellation: No longer subscribes
     - Renewal: Continues subscription
     - Duration: Period length of subscription
     
   - Data Info
      - Data Format: Excel.
      - Data Quality: Check for inconsistents
        
   - Analytical tools: Download link on other repository
       - Microsoft Excel (Ms Excel)
         - Data cleaning
          -Duration column was added and calculated using this function
 
                = (Subscription end - Subscription start)
       - Pivot table was used analyze customer data to find subscription patterns: 
       - Determine Average subscription duration
       - Determine most popular subscription type
       - Total revenue generated.              

      - Structured Query Language (SQL)
          - The dataset was converted to Comma seperated values to load into the SQL server
          - The following queries were written to analyse the sales performance
              - 1. Retrieve the total number of customers from each region.

                       select Region, count(CustomerId) AS TOTAL_CUSTOMERS FROM [dbo].[LITA CAPSTONE_PROJECT_CUSTOMERDATA] GROUP BY REGION
                2. Find the most popular subscription type by number of customers.

                        SELECT TOP 1 Subscriptiontype, count(CustomerID) as Popular_Subscription from [dbo].[LITA CAPSTONE_PROJECT_CUSTOMERDATA] group by SubscriptionType
                3. Find customers who cancelled their subscription within 6 months 
               
                         select customername, Subscriptiontype, subscriptionstart, subscriptionend, canceled from [dbo].[LITA CAPSTONE_PROJECT_CUSTOMERDATA] where canceled = 1  and DATEDIFF(DAY, SubscriptionEnd, SubscriptionStart) <= 180
                4. Calculate the average subscription duration for all customers 
            
                       select AVG(duration) as Average_Subscription_Duration from [dbo].[LITA CAPSTONE_PROJECT_CUSTOMERDATA]
                5. Find customers with subscriptions longer than 12 months

                        select customername, Subscriptiontype, subscriptionstart, subscriptionend, Duration from [dbo].[LITA CAPSTONE_PROJECT_CUSTOMERDATA] where DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd) > 365
                6. Calculate total revenue by subscription type

                        select Subscriptiontype, sum(Revenue) as Total_Revenue from [dbo].[LITA CAPSTONE_PROJECT_CUSTOMERDATA] group by SubscriptionType
                7. Find the top 3 regions by subscription cancellations 

                         select top 3 Region, count(canceled) as Canceled_Subscription from [dbo].[LITA CAPSTONE_PROJECT_CUSTOMERDATA] where canceled = 1 Group by Region Order by Canceled_Subscription desc
                8. Find the total number of active and cancelled subscription
 
                              select sum(case when canceled = 0 then 1 else 0 end) as Active_subscription, sum(case when canceled = 1 then 1 else 0 end) as Canceled_subscription from [dbo].[LITA CAPSTONE_PROJECT_CUSTOMERDATA]
 
      - Power Business intelligence (Power Bi).
           - For creation of dashboard that visualizes the insights found in excel and SQL
           - The dashboard visualizes key customer segments, cancellations and subscription trends.
## Analytical Result
   - Data Visualization
     




 