# KULTRA-MEGA-STORE-SQL-ANALYSIS
Comprehensive SQL case study analysis for Kultra Mega Stores inventory and sales data. Includes data cleaning, business insight queries, shipping cost evaluation, customer segmentation, and performance breakdowns.
# 📝INTRODUCTION
Kultra Mega Stores (KMS) is a rapidly expanding retail chain in Nigeria, with its headquarters in Lagos and a strong operational focus in Abuja and Lagos. The company specializes in office supplies and furniture, catering to a diverse customer base that includes individual consumers, small retail businesses, and large corporate clients.

This SQL case study analyzes KMS’s historical inventory and sales data from 2009 to 2012 to uncover performance drivers such as product demand, regional sales trends, shipping cost efficiency, and customer profitability. The project simulates a real-world business intelligence scenario, where data-driven insights are vital for making decisions around business growth, inventory management, and customer satisfaction.
# 📖 BACKGROUND
As a Business Intelligence Analyst, I was tasked with analyzing operational and customer data for Kultra Mega Stores (KMS) using SQL. The goal was to uncover actionable insights that could inform strategic decisions in areas such as sales performance, customer profitability, and shipping efficiency.

With branches across Nigeria, KMS maintains a rich dataset of customer orders, shipping methods, product categories, pricing, and profit margins. Analyzing this data allows stakeholders to understand regional trends, optimize inventory and logistics, and improve overall business performance.

This project showcases how SQL can be applied to extract meaningful insights from large datasets by answering key questions like:

Which product categories generate the most sales?

Which regions or customer segments are the most profitable?

What shipping methods incur the highest costs?

How do discounts affect overall profitability
# 🎯 OBJECTIVE
1. Which product category had the highest sales?

2. What are the top and bottom 3 performing regions by sales?

3. What were the total sales of appliances in Ontario?

4. What actions can management take to increase revenue from the bottom 10 customers?

5. Which shipping method incurred the highest shipping cost?

6. Who are the most valuable customers, and what do they typically purchase?

7. Which small business customer had the highest sales?

8. Which corporate customer placed the most orders (2009–2012)?

9. Which consumer customer was the most profitable?

10. Which customers returned items and what segments do they belong to?

11. Did the company appropriately spend shipping costs based on order priority?
# 📂 SOURCES

- **Dataset Origin:** Provided by **Digital Skills Africa / Incubator Hub** as part of the final SQL case study project.

- **Primary Table Used:** `KMS SQL Case Study`

- **Data Columns Included:**
  - `RowID`
  - `OrderID`
  - `OrderDates`
  - `OrderPriority`
  - `OrderQuantity`
  - `Sales`
  - `Discount`
  - `ShipMode`
  - `Profits`
  - `ShippingCost`
  - `UnitPrice`
  - `ProductSubCategory`
  - `ProductContainer`
  - `CustomerName`
  - `CustomerSegment`
  - `Region`
  - `Province`
  - `ProductName`
  - `ProductCategory`
  - `ProductBaseMargin`
  - `ShipDate`

## 🛠️ Tools Used for the Analysis

- **SQL Server Management Studio (SSMS)** – For writing and executing SQL queries.
-  **Relational Database Concepts** – Understanding normalization, joins, and aggregation.
-  **Business Intelligence (BI)** Mindset – Applied for interpreting data meaningfully.
-  **GitHub** – For project documentation and portfolio presentation.
-  **Data Visualization Tools** *(optional)* – For presenting SQL insights using charts and graphs.

# 📊 ANALYSIS
This section outlines the core business questions explored through SQL and presents data-driven insights derived from Kultra Mega Stores' historical sales and operations data. Each question is followed by a breakdown of the SQL logic used and a brief business interpretation.

---
### **1. Which product category had the highest sales?**

This query aims to identify which product category generated the highest revenue over the period analyzed. This insight can guide KMS in prioritizing inventory planning, promotional efforts, and supplier negotiations around top-performing products.

**SQL Query Used:**

#### Analysis: Which Product Had the Highest Sales?

```sql
SELECT Product_Name, SUM(Sales) AS [Total Sales]
FROM [KMS Sql Case Study]
GROUP BY Product_Name
ORDER BY [Total Sales] DESC;
```
#### Insight:
According to my analysis, the product Global Troy™ Executive Leather Low-Back Tilter generated the highest total sales of ₦275,941.520. This makes it the top-performing product in the entire dataset and a key contributor to revenue.

### **2. What Are the Top Three and Bottom Three Regions in Terms of Sales?**
This analysis investigates regional performance by comparing total sales across all regions. Identifying the highest and lowest-performing regions allows KMS to evaluate what drives strong sales in top regions and what may be hindering sales in underperforming ones. These insights can support better allocation of marketing resources, stock distribution, and regional sales strategies.

**SQL Query Used:**

#### Analysis: Top 3 Regions by Sales

```sql
SELECT TOP 3 Region, SUM(Sales) AS [Total Sales]
FROM [KMS Sql Case Study]
GROUP BY Region
ORDER BY [Total Sales] ASC;
```
#### Analysis: Top 3 Regions by Sale
```sql
SELECT TOP 3 Region, SUM(Sales) AS [Total Sales]
FROM [KMS Sql Case Study]
GROUP BY Region
ORDER BY [Total Sales] ASC;
```
#### Insight:

Based on the analysis, the **top three regions** with the highest total sales are **West** (₦**3,597,549.33**), **Ontario** (₦**3,063,212.55**), and **Prairie** (₦**2,837,304.59**). These regions likely contribute significantly to the company’s revenue due to higher population density, purchasing power, and well-established supply chains.

Conversely, the **bottom three regions** in terms of total sales are **Atlantic** (₦**1,167,627.86**), **Quebec** (₦**1,359,364.33**), and **Northwest Territories** (₦**1,447,390.01**). These low figures may indicate limited customer reach, operational constraints, or lower demand. KMS may consider targeted marketing, local partnerships, or revised distribution strategies to improve performance in these areas.

### **3. What were the total sales of appliances in the Ontario region?**
This query was designed to calculate the total sales value of appliances within a specific geographic area — Ontario. The objective here is to help the company understand how a particular product sub-category (Appliances) performs in a given region, which is vital for regional marketing strategies, supply chain allocation, and inventory decisions.

**SQL Query Used:**

#### Analysis: Total sales of appliances in the Ontario region?
```sql
SELECT Region, SUM(Sales) AS [Appliance Sales]
FROM [KMS Sql Case Study]
WHERE Product_Sub_Category = 'Appliances' AND Region = 'Ontario'
GROUP BY Region;
```
#### Insight:
According to the analysis, the total sales of appliances in the **Ontario** region amounted to (₦**202,346.840**). This figure gives management a clear view of how this sub-category is performing in Ontario. The sales volume indicates that appliances are in moderate demand in this region. To further boost revenue, KMS might explore promotions, bundling strategies, or customer feedback to understand how to grow sales in this category.

### **4. How Can KMS Increase Revenue from the Bottom 10 Customers?

This analysis aims to help management understand why certain customers generate the lowest revenue and how to potentially increase their spending. By analyzing sales, frequency of orders, average order value, and customer segments, we can better tailor engagement strategies.

**SQL Query Used:**

#### Analysis: Identification of Bottom 10 Customers
```sql



















