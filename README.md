# Marketing Finance Performance Analytics – Power BI Dashboard

## Project Overview

Marketing teams invest heavily in campaigns, but understanding whether those campaigns actually generate profitable results is a major business challenge.
This project analyses marketing campaign performance and financial outcomes to uncover insights related to revenue generation, profitability, and marketing efficiency.

The analysis combines Python-based data cleaning with Power BI dashboards to transform raw marketing and financial data into actionable business insights.

The final solution includes two interactive dashboards:

- Marketing Performance Dashboard – evaluates campaign effectiveness and marketing ROI
- Financial Performance Dashboard – analyzes revenue, costs, and profitability
   
These dashboards help stakeholders understand which campaigns perform well, where money is being spent, and how marketing activities influence overall profitability.

---

## Business Context

Organizations run multiple marketing campaigns across digital channels such as social media, search ads, referrals, and organic traffic. While these campaigns drive customer acquisition, companies must continuously evaluate:

- Which campaigns generate the highest revenue
- Whether marketing investments produce profitable returns
- Which channels drive the most orders
- How discounts and marketing costs affect profitability

By combining marketing and financial data, this project demonstrates how analytics can help businesses optimize campaign strategy, marketing spending, and revenue performance.

---

## Business Objective

The key objectives of this analysis are:

- Evaluate marketing campaign effectiveness
- Analyze revenue generated across marketing channels
- Measure Return on Advertising Spend (ROAS)
- Understand customer purchasing behavior
- Identify profitable products and locations
- Analyze profit trends and financial performance
- Provide actionable recommendations to improve ROI

---

## Dataset Preview

Below is a preview of the dataset used in the analysis.



---

## Dataset Information

The dataset contains marketing campaign, customer, and transaction-level sales data used to evaluate marketing performance and financial profitability.

| Column Name         | Description                                                                                                    |
| ------------------- | -------------------------------------------------------------------------------------------------------------- |
| **OrderID**         | Unique identifier assigned to each customer order                                                              |
| **OrderDate**       | Date when the order was placed                                                                                 |
| **CustomerID**      | Unique identifier for each customer                                                                            |
| **City**            | City from which the order was placed                                                                           |
| **Age**             | Age of the customer                                                                                            |
| **Channel**         | Marketing channel through which the customer was acquired (e.g., Instagram Ads, Google Ads, Organic, Referral) |
| **Campaign**        | Specific marketing campaign responsible for generating the order                                               |
| **ProductCategory** | Category of the product purchased by the customer                                                              |
| **Units**           | Number of product units purchased in the order                                                                 |
| **UnitPrice**       | Selling price per unit of the product                                                                          |
| **DiscountPct**     | Percentage discount applied to the order                                                                       |
| **MarketingCost**   | Marketing expenditure associated with acquiring the order                                                      |
| **COGS_per_unit**   | Cost of goods sold per product unit                                                                            |
| **PaymentStatus**   | Status of the transaction payment (Paid / Pending / Failed)                                                    |
| **PaymentMethod**   | Payment method used by the customer (UPI, Card, Net Banking, etc.)                                             |

### Important Note

Additional financial metrics such as:

- Gross Revenue
- Discount Amount
- Net Revenue
- Total COGS
- Profit

were derived later using Power Query in Microsoft Power BI to support deeper financial analysis in the dashboards.

---

## Data Cleaning & Transformation

Data preparation was performed in two stages.

### Python Data Cleaning

Data cleaning was performed using Python in Google Colab. Key steps included:

-	Removing duplicate records
-	Handling missing values
-	Standardizing column names
-	Correcting data types
-	Exporting a clean dataset for analysis

### Power Query Transformation

After importing the cleaned dataset into Power BI, additional transformations were performed using Power Query.

New calculated columns were created:

-	Gross Revenue
-	Discount Amount
-	Net Revenue
-	Total COGS
-	Profit

These transformations enabled accurate financial analysis in the dashboards.

---

## DAX Calculations

To support marketing and financial analysis, several calculated columns and DAX measures were created in Power BI.

These calculations enabled the creation of KPIs such as revenue, profit, marketing efficiency, and profitability metrics.

### Calculated Columns 

The following calculated columns were created to derive financial metrics from the base dataset.


**Gross Revenue**

Gross Revenue = 

Marketing_Finance_Project_clean[Units] *
Marketing_Finance_Project_clean[UnitPrice]

Calculates the total revenue generated before applying discounts.



**Discount Amount**

Discount Amount =

Marketing_Finance_Project_clean[Gross Revenue] *
Marketing_Finance_Project_clean[DiscountPct]

Calculates the discount applied to each order.



**Net Revenue**

Net Revenue =

Marketing_Finance_Project_clean[Gross Revenue] -
Marketing_Finance_Project_clean[Discount Amount]

Represents the actual revenue earned after discounts.



**Total COGS**

Total COGS =

Marketing_Finance_Project_clean[Units] *
Marketing_Finance_Project_clean[COGS_per_unit]

Calculates the total cost of goods sold for each order.



**Profit**

Profit =

Marketing_Finance_Project_clean[Net Revenue] -
Marketing_Finance_Project_clean[Total COGS] -
Marketing_Finance_Project_clean[MarketingCost]

Represents the final profit after subtracting product costs and marketing expenses.



### DAX Measures (KPIs)

The following DAX measures were created to calculate key performance indicators used across the dashboards.



**Total Net Revenue**

TotalNetRevenue =

SUM(Marketing_Finance_Project_clean[Net Revenue])

Calculates total revenue generated after discounts.



**Total Profit**

TotalProfit =

SUM(Marketing_Finance_Project_clean[Profit])

Calculates total profit across all orders.



**Total Marketing Cost**

TotalMarketingCost =

SUM(Marketing_Finance_Project_clean[MarketingCost])

Represents the total marketing investment.



**Total Orders**

TotalOrders =

DISTINCTCOUNT(Marketing_Finance_Project_clean[OrderID])

Counts the total number of unique customer orders.



**Total Units**

TotalUnits =

SUM(Marketing_Finance_Project_clean[Units])

Represents the total quantity of products sold.



**Total COGS**

TotalCOGS =

SUM(Marketing_Finance_Project_clean[Total COGS])

Calculates the total cost of goods sold.



**Return on Advertising Spend (ROAS)**

ROAS =

DIVIDE([TotalNetRevenue], [TotalMarketingCost])

Measures the revenue generated for every unit of marketing spend.



**Profit Margin %**

ProfitMargin% =

DIVIDE([TotalProfit], [TotalNetRevenue])

Indicates the percentage of revenue retained as profit.



**Average Order Value**

AvgOrderValue =

DIVIDE([TotalNetRevenue], [TotalOrders])

Calculates the average revenue generated per order.


---

# Marketing Campaign Performance Dashboard

## Key Metrics

- Total Net Revenue: 197K
- Total Orders: 60
- Total Units Sold: 180
- Total Marketing Cost: 33K
- ROAS: 6.04

---

## Marketing Dashboard Features

The marketing dashboard analyzes campaign performance through:

- Revenue by marketing channel
- Revenue by campaign
- Revenue trend over time
- Revenue share by channel
- Payment status analysis

---  

## Business Problems Addressed 

Marketing Dashboard

The dashboard answers key marketing questions:

- Which marketing channels generate the highest revenue?
- Which campaigns deliver the best performance?
- How does marketing spending translate into revenue?
- Which channels contribute the largest share of sales?

---

## Key Insights

Marketing Insights

- Instagram Ads generate the highest revenue (~75K), making it the most effective marketing channel.
- Retargeting Push campaign delivers the highest campaign revenue (~60K).
- Marketing channels contribute differently, with social media advertising dominating revenue share.
- Revenue declined significantly in March, indicating potential seasonal demand changes or campaign performance issues.
- 75% of transactions are successfully paid, indicating strong payment completion rates.

--- 

## Business Recommendations

Marketing Recommendations

- Increase investment in Instagram Ads, as it generates the highest revenue.
- Expand retargeting campaigns, which show strong performance.
- Investigate the March revenue decline to identify seasonal patterns or campaign issues.
- Optimize marketing spend by focusing on channels with higher ROAS.

---

# Financial Profitability Analysis Dashboard

## Key Metrics

- Total Net Revenue: 197K
- Profit Margin: 53%
- Total Profit: 104.64K
- Average Order Value: 3.29K

---

## Finance Dashboard Features

The finance dashboard provides financial insights including:

- Profit by product category
- Profit by city
- Profit trend over time
- Profit distribution by payment method
- Net revenue by payment status

---

## Finance Dashboard Features

The finance dashboard provides financial insights including:

- Profit by product category
- Profit by city
- Profit trend over time
- Profit distribution by payment method
- Net revenue by payment status

---

## Key Insights

Financial Insights

- E-books generate the highest profit (~27K) among all product categories.
- Hubli and Pune contribute the highest city-level profits, indicating strong regional demand.
- Profit declined across months, dropping to near zero in March, highlighting a potential demand slowdown.
- UPI and card payments dominate transaction volume, suggesting strong digital payment adoption.
- Profit margins remain relatively strong at 53%, indicating healthy overall profitability.

---

## Business Recommendations

Financial Recommendations

- Focus on promoting high-profit products like E-books and SAP courses.
- Expand marketing efforts in high-performing cities such as Hubli and Pune.
- Maintain strong profit margins by carefully managing discount strategies.
- Encourage digital payment methods to improve transaction efficiency.

---

## Tools Used

**Python** - Data cleaning and preprocessing

**Google Colab** - Python notebook environment

**Microsoft Excel** - Dataset storage and documentation

**Microsoft Power BI** - Dashboard development

**Power Query** - Data transformation in Power BI

**DAX** - KPI and metric calculations 

---

## Skills Demonstrated

- Data Cleaning
- Feature Engineering
- Data Transformation
- Dashboard Development
- DAX Calculations
- Marketing Analytics
- Financial Analysis
- Data Visualization
- Business Insight Generation
- Data Storytelling

---

## Data Workflow

1. Raw Dataset (Excel)
    
2. Data Cleaning (Python – Google Colab)
      
3. Feature Engineering
      
4. Clean Dataset Export
      
5. Power BI Data Modeling
      
6. DAX Measures
    
7. Interactive Dashboards
      
8. Business Insights & Recommendations

---

## How to Use

1. Download or clone the repository.

2. Open the Power BI dashboard file:

   marketing_finance_analytics_dashboard.pbix

3. Explore the two interactive dashboards:

- Marketing Campaign Performance

- Financial Profitability Analysis

4. Review the Python notebook to understand the data cleaning and preprocessing workflow.

---

## Author

**Sarvesh Vernekar**

Aspiring Data Analyst focused on transforming business data into actionable insights through analytics, visualization, and data-driven decision making.
