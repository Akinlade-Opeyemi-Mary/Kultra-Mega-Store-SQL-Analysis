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

- **Dataset Origin:** Provided by **Digital Skills Africa / Incubator Hub** as part of the final SQL case study project.https://canvas.instructure.com/files/folder/courses_11955369/DSA%20Capstone%20Project%20Files

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
-  **Data Visualization Tools** *(POWER BI)* – For presenting SQL insights using charts and graphs.

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

### 📊 Total Sales by Region

This chart visualizes the total sales across various regions, helping identify the top-performing areas for Kultra Mega Stores.

![Alt text](https://github.com/Akinlade-Opeyemi-Mary/Kultra-Mega-Store-SQL-Analysis/blob/5a4eac6c75d8c054e8490c717158fcb1a35e5a45/total_sales_by_region_chart.png)


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
SELECT TOP 10 Customer_Name, SUM(Sales) AS [Total Sales]
FROM [KMS Sql Case Study]
GROUP BY Customer_Name
ORDER BY [Total Sales] ASC;
```
#### Analysis:Order Frequency of Bottom 10 Customers
```sql
SELECT Customer_Name, COUNT(Order_ID) AS [Order Count]
FROM [KMS Sql Case Study]
WHERE Customer_Name IN ('Jeremy Farry','Natalie DeCherney','Nicole Fjeld','Katrina Edelman',
'Dorothy Dickinson','Christine Kargatis','Eric Murdock','Chris McAfee','Rick Huthwaite','Mark Hamilton')
GROUP BY Customer_Name
ORDER BY [Order Count] DESC;
```
#### Analysis:Average Sales per Order
```sql
SELECT Customer_Name, AVG(Sales) AS [Average Order Values]
FROM [KMS Sql Case Study]
WHERE Customer_Name IN ('Jeremy Farry','Natalie DeCherney','Nicole Fjeld','Katrina Edelman',
'Dorothy Dickinson','Christine Kargatis','Eric Murdock','Chris McAfee','Rick Huthwaite','Mark Hamilton')
GROUP BY Customer_Name
ORDER BY [Average Order Values] ASC;
```
#### Analysis: Customer Segment Distribution of Bottom 10 Customers
```sql
SELECT Customer_Name, Customer_Segment, COUNT(DISTINCT Customer_Name) AS [Customer Count]
FROM [KMS Sql Case Study]
WHERE Customer_Name IN ('Jeremy Farry','Natalie DeCherney','Nicole Fjeld','Katrina Edelman',
'Dorothy Dickinson','Christine Kargatis','Eric Murdock','Chris McAfee','Rick Huthwaite','Mark Hamilton')
GROUP BY Customer_Name, Customer_Segment
ORDER BY [Customer Count];
```
#### Analysis:Segment Distribution Summary
```sql
SELECT Customer_Segment, COUNT(DISTINCT Customer_Name) AS [Customer Count]
FROM [KMS Sql Case Study]
WHERE Customer_Name IN ('Jeremy Farry','Natalie DeCherney','Nicole Fjeld','Katrina Edelman',
'Dorothy Dickinson','Christine Kargatis','Eric Murdock','Chris McAfee','Rick Huthwaite','Mark Hamilton')
GROUP BY Customer_Segment
ORDER BY [Customer Count] DESC;
```
#### Analysis:Purchase Behaviour Summary
```sql
SELECT Customer_Name, AVG(Sales) AS [Average Order Value],
       SUM(Sales) AS [Total Sales],
       COUNT(Order_ID) AS [Order Count]
FROM [KMS Sql Case Study]
WHERE Customer_Name IN ('Jeremy Farry','Natalie DeCherney','Nicole Fjeld','Katrina Edelman',
'Dorothy Dickinson','Christine Kargatis','Eric Murdock','Chris McAfee','Rick Huthwaite','Mark Hamilton')
GROUP BY Customer_Name
ORDER BY [Average Order Value];
```

#### Insight:The bottom 10 customers by sales include Jeremy Farry (₦**85.72**), Natalie DeCherney (₦125.90), and Nicole Fjeld (₦**153.03**), among others. Many of them place orders infrequently, and several have only placed 1–2 orders in total.

The majority belong to the Small Business and Corporate segments, with fewer from Home Office and Consumer groups. Their average order values vary significantly, with Mark Hamilton having the highest average of  (₦**225.49**) and Jeremy Farry the lowest at  (₦**42.86**).

### Recommendation: KMS should consider:

 - `Offering targeted promotions or loyalty programs for these customers`.

- `Engaging them with personalized product recommendations`.

- `Investigating any operational or satisfaction issues causing low engagement`.

- `This strategy can help uplift overall sales from underperforming segments without acquiring new customers`.

### **5. Which Shipping Method Incurred the Highest Total Shipping Cost?**
This analysis aims to determine which shipping method generated the highest total shipping expenses over the period. Understanding this can help KMS optimize logistics and cut unnecessary costs by evaluating the cost-effectiveness of each shipping option.

**SQL Query Used:**

#### Analysis:Most Profitable Customers and What They Buy

```sql
SELECT Ship_Mode, SUM(Shipping_Cost) AS [Total Shipping Spend]
FROM [KMS Sql Case Study]
GROUP BY Ship_Mode;
```

#### Insight:
According to the analysis, the Delivery Truck shipping method incurred the highest total shipping cost at  (₦**51,971.94**), followed by Regular Air at  (₦**48,008.19**) and Express Air at  (₦**7,850.91**).
This suggests that while Delivery Truck may be economical per order, its frequent usage or volume results in the highest cumulative spend. Management may want to evaluate delivery frequency or explore optimizing routes.

### **6. Who Are the Most Valuable Customers, and What Products or Services Do They Typically Purchase?**

This analysis identifies the most profitable customers for Kultra Mega Stores and highlights the product sub-categories from which the company earns the highest profit. This insight helps the business understand its high-value clients and focus marketing or loyalty efforts on sustaining and expanding those relationships.

**SQL Query Used:**

#### Analysis: Products or Services Valuable Customers Purchase
```sql
SELECT TOP 5 Customer_Name, Product_Sub_Category, SUM(Profit) AS [Total Profit]
FROM [KMS Sql Case Study]
GROUP BY Customer_Name, Product_Sub_Category
ORDER BY [Total Profit] DESC;
```
### 🧾 Top 5 Customers by Profit and Sub-Category

| Customer Name     | Product Sub-Category             | Total Profit ($) |
|-------------------|----------------------------------|------------------|
| Emily Phan        | Office Machines                  | 32,696.49        |
| Grant Carroll     | Binders and Binder Accessories   | 20,316.20        |
| Raymond Book      | Copiers and Fax                  | 18,477.07        |
| Alejandro Grove   | Binders and Binder Accessories   | 17,445.23        |
| Clytie Kelty      | Copiers and Fax                  | 15,886.93        |


#### Insight:
According to the analysis, the most valuable customers and their most profitable product sub-categories include:

- **Emily Phan** – *Office Machines* (**₦32,696.49**)  
- **Grant Carroll** – *Binders and Binder Accessories* (**₦20,316.20**)  
- **Raymond Book** – *Copiers and Fax* (**₦18,477.07**)  
- **Alejandro Grove** – *Binders and Binder Accessories* (**₦17,445.23**)  
- **Clytie Kelty** – *Copiers and Fax* (**₦15,886.93**)

### **7. Which small business customer had the highest sales?**
This query identifies the top-performing customer within the Small Business segment. Understanding which customer brings in the most sales within this segment allows Kultra Mega Stores (KMS) to tailor strategic decisions such as targeted promotions, loyalty programs, and personalized customer service.

SQL Query Used:

#### Analysis: Small Business Customer with the Highest Sales
```sql
SELECT TOP 1 Customer_Name, SUM(Sales) AS [Highest Sales]
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Small Business'
GROUP BY Customer_Name
ORDER BY [Highest Sales] DESC;
```

#### Insight:
According to the analysis, **Dennis Kane** is the most valuable customer in the Small Business segment with a total sales value of **₦75,967.59**. This highlights Dennis Kane as a key account within this segment and a potential model for understanding successful customer engagement.

### **8. Which Corporate Customer Placed the Most Number of Orders in 2009–2012?**
This analysis focuses on identifying the most active corporate customer in terms of the number of orders placed during the period between 2009 and 2012. Understanding which clients consistently generate high order volumes helps inform decisions about client retention strategies, loyalty programs, and service prioritization.

SQL Query Used:

#### Analysis: Corporate Customer with the Most Orders (2009–2012)
```sql
SELECT Customer_Name, Customer_Segment, COUNT(Order_ID) AS [Numbers of Orders]
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Corporate'
  AND Ship_Date BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY Customer_Name, Customer_Segment
ORDER BY [Numbers of Orders] DESC;
```
#### Analysis: Top Corporate Customer with the Most Orders (2009–2012)
```sql
SELECT TOP 1 Customer_Name, Customer_Segment, COUNT(Order_ID) AS [Numbers of Orders]
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Corporate'
  AND Ship_Date BETWEEN '2009-01-01' AND '2012-12-31'
GROUP BY Customer_Name, Customer_Segment
ORDER BY [Numbers of Orders] DESC;
```

#### Insight:
According to the analysis, the corporate customer Adam Hart placed the highest number of orders (27 orders) between 2009 and 2012. This indicates a strong and consistent relationship with KMS and shows Adam Hart as a loyal client who likely contributes significantly to recurring revenue.

### **9. Which Consumer Customer Was the Most Profitable One?**
This analysis seeks to identify the top-performing consumer customer in terms of profit generated. Understanding which individual consumers drive the most profit can help Kultra Mega Stores (KMS) tailor retention strategies and targeted offers to maintain loyalty and encourage repeat business.

SQL Query Used

#### Analysis: Most Profitable Consumer Customer
```sql
SELECT TOP 1 Customer_Name, Customer_Segment, SUM(Profit) AS [Total Profit]
FROM [KMS Sql Case Study]
WHERE Customer_Segment = 'Consumer'
GROUP BY Customer_Name, Customer_Segment
ORDER BY [Total Profit] DESC;
```

#### Insight:
According to the analysis, the most profitable consumer customer is **Emily Phan**, from the Consumer segment, with a total profit contribution of **₦34,005.44**. This highlights her importance to the business and suggests that personalized engagement or loyalty initiatives could help sustain her continued patronage.

### **10. Which Customer Returned Items, and What Segment Do They Belong To?**
This analysis identifies customers who returned items by filtering records with negative profit values. It also shows the customer segments these individuals belong to. Understanding patterns of returns can help Kultra Mega Stores (KMS) investigate product or service issues, assess customer satisfaction, and revise policies to reduce future returns.

SQL Query Used:

#### Analysis:Customers Who Returned Items and Their Segment
```sql
SELECT DISTINCT Customer_Name, Customer_Segment
FROM [KMS Sql Case Study]
WHERE Profit < 0;
```

#### Insight:

According to the analysis, numerous customers across all four segments—**Consumer**, **Corporate**, **Home Office**, and **Small Business**—returned items during the period under review. This suggests returns are not limited to a specific customer category and may warrant:

- **Reviewing top returned products.**
- **Investigating reasons for negative profit** (e.g., high discounts or damaged goods).
- **Offering better product descriptions, warranties, or quality control checks.**

Due to the large volume of customers involved, a **summarized view or visual chart** (like a donut chart of customer segments with returns) is recommended in the dashboard or final presentation for clearer insight.

### **11. Was Shipping Cost Appropriately Spent Based on Order Priority?**

This analysis evaluates if **Kultra Mega Stores (KMS)** allocated shipping costs effectively by matching shipping methods to order priorities. Since **Delivery Truck** is the most economical but slowest, and **Express Air** is the fastest but most expensive, high-priority orders should ideally favor Express Air, while low-priority ones should use Delivery Truck to optimize costs.

SQL Queries Used:

#### Analysis: Alignment Between Order Priority and Shipping Method
```sql
SELECT Order_Priority, Ship_Mode, COUNT(Order_ID) AS [Total Orders]
FROM [KMS Sql Case Study]
GROUP BY Order_Priority, Ship_Mode
ORDER BY [Total Orders] DESC;
```
#### Analysis: Average Shipping Cost per Priority
```sql
SELECT Order_Priority, 
       CAST(ROUND(AVG(Shipping_Cost), 3) AS DECIMAL(10,3)) AS [Average Shipping Cost]
FROM [KMS Sql Case Study]
GROUP BY Order_Priority
ORDER BY [Average Shipping Cost] DESC;
```
#### Analysis: . Orders by Priority and Shipping Method (with % Distribution)
```sql
WITH TotalPerPriority AS (
    SELECT Order_Priority, COUNT(Order_ID) AS [Total Orders]
    FROM [KMS Sql Case Study]
    GROUP BY Order_Priority
)
SELECT k.Order_Priority, k.Ship_Mode, COUNT(k.Order_ID) AS [Order Count],
       CAST(COUNT(k.Order_ID) * 100.0 / tp.[Total Orders] AS DECIMAL(10,2)) AS [Percentage of Order]
FROM [KMS Sql Case Study] k
JOIN TotalPerPriority tp 
  ON k.Order_Priority = tp.Order_Priority
GROUP BY k.Order_Priority, k.Ship_Mode, tp.[Total Orders]
ORDER BY k.Order_Priority, [Percentage of Order] DESC;
```

#### Insight:
### Shipping Misalignment Analysis

Despite having clearly defined order priorities (**Critical**, **High**, **Medium**, **Low**, **Not Specified**), **KMS** does not appear to align its shipping mode choices appropriately with the urgency of orders.

####  Shipping Distribution by Priority (%)

| Order Priority   | Regular Air (%) | Delivery Truck (%) | Express Air (%) |
|------------------|------------------|---------------------|------------------|
| **Critical**      | 73.38%           | 14.18%              | 12.44%           |
| **High**          | 73.98%           | 14.03%              | 11.99%           |
| **Medium**        | 75.11%           | 12.57%              | 12.32%           |
| **Low**           | 74.42%           | 14.53%              | 11.05%           |
| **Not Specified** | 76.38%           | 12.86%              | 10.77%           |

#### Average Shipping Cost per Priority

| Order Priority     | Avg. Shipping Cost (₦) |
|--------------------|------------------------|
| **Low**            | ₦13.34                 |
| **Critical**       | ₦13.13                 |
| **High**           | ₦12.82                 |
| **Medium**         | ₦12.58                 |
| **Not Specified**  | ₦12.32                 |

>  **Conclusion:** Low-priority orders are incurring **higher average shipping costs** than even critical ones — a **major operational inefficiency**.

---

####  Business Problem:

This suggests a **misalignment between operational cost management and business logic**, leading to:

- **Increased logistics cost** for non-urgent orders.  
-  **Potential customer dissatisfaction** for delayed critical deliveries.  
-  **Missed cost-saving opportunities** on high-volume, low-priority orders.

---

#### Recommendations:

##### 1. Redesign the Shipping Logic Flow
Create a **rule-based system** that matches:

- `Critical & High Priority → Express Air or Regular Air (based on SLA deadlines)`
- `Medium Priority → Regular Air`
- `Low & Not Specified → Delivery Truck by default`

##### 2. Implement a Shipping Audit Tracker
- Add a **validation layer** before final shipment to check if:
  - `Shipping Mode ≠ Order Priority`, flag the order for review.
- Generate **weekly reports** on "**Priority vs Shipping Mismatch**".

##### 3. Automate Shipping Assignment
- Use **SQL-based triggers or workflow automation** in your ERP to auto-assign:
  - **Express Air only for Critical** or time-sensitive deliveries.

##### 4. Reallocate Budget & Reduce Wastage
- Redirect saved shipping costs from **Low-priority** orders to:
  - Offer **free Express Air upgrades** for **VIP customers**.
  - Fund **marketing loyalty campaigns** or discounts.

##### 5. Monitor & Measure with KPIs
Track monthly:
- % of **Critical orders delivered via Express Air** *(target: >70%)*
-  % of **Low-priority orders using Delivery Truck** *(target: >80%)*
-  **Shipping cost variance vs monthly logistics budget**

---

### Conclusion

KMS currently **overspends on low-priority deliveries** and **underutilizes Express Air for critical orders**. These mismatches raise costs, reduce efficiency, and risk customer trust.

> By **realigning shipping modes to match order urgency**, KMS can unlock:
-  **Smarter logistics**
-  **Cost optimization**
-  **Faster fulfillment**
-  **Data-driven automation for scalability**

---
# FINAL CONCLUSION
The Kultra Mega Stores Inventory Analysis conducted using SQL has unveiled actionable insights that can significantly enhance business performance across logistics, customer management, and sales optimization.

Key findings such as the misalignment between order priority and shipping mode, regional sales distribution, and the identification of high-value customers offer a strategic roadmap for KMS to refine its operations. Furthermore, the discovery of unnecessary shipping expenses on low-priority orders and the identification of repeat item returns across all customer segments highlight opportunities to minimize cost and improve service delivery.

From evaluating shipping cost inefficiencies, to understanding product performance by category, and recognizing top-performing customer segments, this analysis demonstrates the power of data-driven decisions in optimizing profitability and customer satisfaction.

✅ By leveraging these insights:

- KMS can implement smart logistics rules to reduce wastage.

- Focus marketing efforts on high-profit customers.

- Improve quality control and return prevention strategies.

- Tailor sales strategies by region, product category, and segment.

This project not only showcases SQL capabilities in solving real-world problems, but also sets the foundation for integrating Power BI visualizations and automated reporting systems in future phases.

📊 **Data isn't just for analysis — it's a decision-making engine.**
This case study reflects how structured SQL logic can uncover inefficiencies, solve core business issues, and shape intelligent strategy in a retail environment.

































