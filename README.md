
# 📊 Adventure Works Sales Analytics Dashboard in Power BI

## End-to-End Data Modeling & Analytics Project

---
## 📌 Project Overview

This project presents an end-to-end Business Intelligence solution using Power BI, analysing 2020-2022 sales data from the Adventure Works dataset, which is  a sample database created by Microsoft

The objective is to transform raw sales data into a structured data model and then deliver actionable insights through an interactive dashboard to support data-driven decision-making.

This project demonstrates:

* Data modeling (Star schema)
* Data transformation using Power Query
* Advanced DAX calculations
* Business-driven KPI development
* Analytical storytelling & dashboard design

---

## 🌐 Live Dashboard
You can explore the interactive Power BI dashboard here:

🔗 View Live Dashboard on Power BI Service

---

## 🎯 Problem Statement
The business needs to understand:
* What are the main drivers of revenue and sales performance?
* Which products and categories contribute the most?
* How does profitability vary across products, categories, and regions?
* How does sales performance vary over a time period?
* Which regions and customer segments perform best?
* Which regions and customer segments perform worst?
* How does return rate trend over time (improving or worsening)?

---

## 🛠️ Technical Stack
* Power BI Desktop
* Power Query (M)
* DAX Measures

---

## 📊 Dataset Information
* **Source:** a sample database created by Microsoft 
* **Year Covered:** 2020 to 2022
* **Number of datasets:** 10

The dataset consists of multiple related tables representing different aspects of the business. 

### 📁 Source Files
1. AdventureWorks Calendar Lookup - Date information 
2. AdventureWorks Customer Lookup  – Customer information 
3. AdventureWorks Product Categories Lookup  – Categories information 
4. AdventureWorks Product Lookup  – Product details 
5. AdventureWorks Product Subcategories Lookup  – Subcategory information 
6. AdventureWorks Returns Data   – Returns information
7. AdventureWorks Territory Lookup  – Territory information 
8. AdventureWorks Sales Data 2020  – Sales information from Jan 2020 to December 2020
9. AdventureWorks Sales Data 2021   – Sales information from January 2021 to December 2021
10. AdventureWorks Sales Data 2022   – Sales information from January 2022 to June 2022

### Data Preparation and Cleaning

* Change the data type of id from text to int for all datasets.
* Created Fact Sales 2020-2022 by combining *AdventureWorks Sales Data 2020*, *AdventureWorks Sales Data 2021*, and *AdventureWorks Sales Data 2022*.
* Created Dim Date by generating the Date table according to the *order date* column from the Fact Sales 2020-2022 table and not using the *AdventureWorks Calendar Lookup* table.
* Created Dim Customer by renaming the AdventureWorks Customer Lookup table. Data types were standardised, invalid records were removed to remain unique customers, and a *Full Name* column was generated using Power Query (M) to improve customer analysis.
* Created Dim Product by renaming the *AdventureWorks Product Lookup* table after combining the *AdventureWorks Product Categories Lookup* and *AdventureWorks Product Subcategories Lookup* tables into a single dimension. This transformed the original snowflake structure into a star schema, reducing relationship complexity, improving query performance, simplifying DAX calculations, and providing a more intuitive hierarchy (Category → Subcategory → Product) for report users.
* Created Dim Territory by renaming the *AdventureWorks Territory Lookup* table
* Created Fact Returns by renaming the *AdventureWorks Returns Data* table

---

## 🏗️ Data Modeling
Below is the star schema model used in this project: Data Model

![Dashboard](https://github.com/MaddyL28/Adventure-Works-Sales-Analytics-Dashboard/blob/main/images/Data%20Model.png) 

### Fact Table
1. Fact Sales 2020-2022
* One row per customer per order
* Contains Order Date, Stock Date, Order Number, Product Key, Customer Key, Territory Key, OrderLineItem, and Order Quantity attributes.

2. Fact Returns
* One row per product return event aggregated at the product and territory level per return date
* Contains return date,  Product Key,  Territory Key, and Return Date attributes


### Dimension Tables
1. Dim Date 
2. Dim Customer 
3. Dim Product
4. Dim Territory 


### 🔗 Data Relationships
* Fact table connects to all dimension tables via keys
* One-to-many relationships used for efficient filtering
* Designed to support a star schema model

---

## 📈 Dashboard Features

### 🧭 Navigation Guide 

This page provides an overview of the project’s navigation structure.

* Top Section: Displays the project name along with the names of all available pages, giving a clear understanding of the overall layout.
* Bottom Section: Contains navigation icons representing each page.

![Dashboard](https://github.com/MaddyL28/Adventure-Works-Sales-Analytics-Dashboard/blob/main/images/Page%201%20-%20Navigation%20Guide%20Page.png) 

---

### 🏠 Executive Overview

- **Slicers:**
  - **Category, Year, Country**  – Enables interactive filtering for multi-dimensional analysis.
- **KPI Cards:**
  - **Total Revenue** – Displays the overall revenue performance from Jan 2020 to Jun 2022.
  - **Total Profit** – Indicates the total profit earned after costs, helping assess business profitability.
  - **Total Cost** – Represents the total of operational and product-related costs.
  - **Total Quantity Sold** – Shows the total number of units sold, helping measure product demand.
  - **Total Orders** – Represents the total number of customer orders placed from Jan 2020 to Jun 2022.
  - **Profit Margin %** – Measures the percentage of revenue retained as profit, indicating overall business efficiency.
  - **Return Rate %** – Measures the proportion of products returned by customers, helping monitor product quality and customer satisfaction.

- **Charts:**
  - **Total Orders by Category and Country Visual Analysis**  – *Clustered Column Chart*  –   Compares order volume across product categories and countries, helping identify key markets and product demand patterns.
  - **Revenue and Profit by Year**  –  *Multiple Line Chart*  –  Displays changes in revenue and profit over time, helping monitor business growth and profitability trends.
  - **Product Categories by Revenue and Profit Margin**  – *Matrix Table* – Displays category-level rankings by volume and revenue to support performance benchmarking.

![Dashboard](https://github.com/MaddyL28/Adventure-Works-Sales-Analytics-Dashboard/blob/main/images/Page%202%20-%20Overview%20Page.png) 

---

### 🌍 Country Analysis

- **Slicers:**
  - **Continent, Year** – Enables multi-dimensional analysis of business performance across geographic regions and reporting periods.

- **KPI Cards:**
  - **Total Revenue** – Displays total revenue generated from Jan 2020 to Jun 2022.
  - **Total Orders** – Represents the total number of customer orders placed from Jan 2020 to Jun 2022.
  - **Return Rate** – Measures the proportion of products returned by customers, helping monitor product quality and customer satisfaction.

- **Interactive Chart with Selector**
  - **KPI Selector** – *Dynamic Parameter* – Allows users to switch between  Total Cost, Total Orders, Total Profit, Total Quantity Sold, and Total Revenue.
  - **Map Visualisation** – *Filled Map* – Displays KPI performance selector across countries and regions.

- **Interactive Chart with Selector**
  - **KPI Selector** – *Dynamic Parameter* – Allows users to switch between Total Revenue and Total Orders.
  - *Line chart*  –   Displays KPI performance selector over time using monthly and yearly views, helping identify changes in total orders or total revenue.

- **Interactive Chart with Selector**
  - **Product / Customer Option** - *Selector* – Enables users to drill into product or customer performance.
  - **Most Popular by Product or Customer**  –  *Matrix Table* – Identifies top-performing products or customers based on revenue contribution.

![Dashboard](https://github.com/MaddyL28/Adventure-Works-Sales-Analytics-Dashboard/blob/main/images/Page%203%20-%20Country%20Page.png)

---

### 👥 Customer Analysis

- **Slicers**
  - **Category, Year, Country** – Enables interactive filtering for multi-dimensional analysis.

- **KPI Cards**
  - **Total Customer** – Used to display the total number of customers within the selected period, helping monitor customer growth and engagement.
  - **Turnover per Customer** – Indicates the average revenue generated per customer, helping assess customer spending behaviour and overall customer value.

- **Charts:**
  - **Occupation by Orders per Customer and Revenue**  –  *Clustered Column Chart*  –  Compares purchasing behaviour across occupation groups to identify customer segments with volume and revenue.
  - **Education Level Revenue and Profit Margin**  –  *Line and Column Charts*  –  Evaluates revenue and profitability across education levels, helping identify demographic groups with the largest business value.
  - **Revenue and Orders by Customer**  – *Matrix Table*  – Displays customer-level revenue and order information, helping identify top-performing customers as well as customers with low purchasing activity.

- **Interactive Chart with Selector**
  - **KPI Selector**  –  *Dynamic Parameter*  –  Allows users to switch between Orders, Turnover per Customer, and Total Customers.
  - *Line chart*  –  Displays KPI performance selector over time using monthly and yearly views, helping identify changes in customer activity and purchasing behaviour.

![Dashboard](https://github.com/MaddyL28/Adventure-Works-Sales-Analytics-Dashboard/blob/main/images/Page%204%20-%20Customer%20Page.png) 

---

### 📦 Product Performance

- **Slicers:**
  - **Category, Year, Country** – Enable interactive filtering for multi-dimensional analysis.

- **Chart:**
  - **Revenue, Cost, Profit by Time**  –  *Line and Clustered Column Chart* – Displays product financial performance over time to monitor growth and profitability trends.

- **Interactive Charts with Multiple Selectors**
  - **Subcategory / Product Breakdown** – *Selector* – Enables users to drill into product performance at different levels of granularity.
  - **Top / Bottom Value** – *Selector* – Enables users to drill into top or bottom value.
  - **Ranking by Revenue** – *Bar chart*  – Identifies top and bottom-performing products or product subcategories based on revenue contribution.
  - **Ranking by Return Rate** – *Bar chart* – Identifies products with the highest and lowest return rates to support product or product subcategories performance evaluation

![Dashboard](https://github.com/MaddyL28/Adventure-Works-Sales-Analytics-Dashboard/blob/main/images/Page%205%20-%20Product%20Performance%20Page.png) 

--- 

### 📄 Product Details

- **Slicers:**
  - **Selected Card** –  Displays the currently selected product for detailed analysis on this page.

- **Chart:**
  - **Monthly Orders vs Order Target** – *Gauge Chart* – Evaluates whether monthly order volume is on track to achieve sales targets and supports monitoring of product demand performance.
  - **Monthly Revenue vs Revenue Target** – *Gauge Chart* – Evaluates revenue achievement against monthly targets, helping assess the effectiveness of sales and marketing activities.
  - **Monthly Profit vs Profit Target** – *Gauge Chart* – Measures profitability performance against planned targets, enabling users to monitor financial efficiency and business outcomes.
  - **Monthly Return Rate vs Return Rate Target** – *Gauge Chart* – Evaluates return rate performance against established targets, helping identify products that may require further investigation to reduce returns.
  - **Profit and Orders by Product** – *Matrix Table* – Compares selected products against the wider product portfolio with total profit and total order values.

- **Interactive Chart with Selector**
  - **Metrics (KPI Selector)** – *Dynamic Parameter* – Allows users to switch between Total Revenue, Total Profit, Total Cost, Total Orders, Total Quantity Sold, Return Rate %, Profit Margin %.
  - *Line chart* – Tracks changes in product performance over time across multiple KPIs.

![Dashboard](https://github.com/MaddyL28/Adventure-Works-Sales-Analytics-Dashboard/blob/main/images/Page%206%20-%20Product%20Details%20Page.png)

---

## 📌 Key Insights

### Revenue vs Profitability Imbalance 
- Revenue is heavily focused on Bikes, but higher profit margins come from Accessories.
- Some lower-revenue categories (e.g., Clothing) show untapped growth potential.

👉 The business is currently volume-driven rather than profit-optimised.

### Customer Growth vs Customer Value
- Customer numbers are increasing, but average spend per customer is declining.
- Revenue is concentrated among a small group of high-value customers in the professional occupation group.

👉 Growth is driven by acquisition, not customer value maximisation.

### Geographic Performance Variability
- North America dominates revenue, confirming it as the core market.
- Markets like Canada show high volume but low revenue, indicating lower basket size.
- Regional performance shifts over time suggest changing market dynamics.

👉 There is a need for market-specific strategies rather than a one-size-fits-all approach.

### Product Performance vs Return Risk
- High-performing products (e.g., Bikes) also show higher return rates.
- Certain subcategories (e.g., Shorts) consistently underperform in quality metrics.

👉 Revenue growth may be offset by return-related costs and customer dissatisfaction.

### Seasonal Demand Patterns
- Sales and customer activity peak in August and December.

👉 Business performance is influenced by seasonality and promotional cycles.

---

## 🚀 Business Recommendations

### Demand Optimisation
- Concentrate marketing campaigns and promotional efforts during peak periods.
- Introduce targeted promotions during low-performing months to stimulate demand.
### Product & Category Performance
- Expand and bundle high-performing products to increase average order value.
- Review underperforming products for repositioning, redesign, or removal.
### Customer Performance
- Introduce personalised promotions and targeted marketing campaigns.
- Develop premium offerings for high-value customer segments.
- Improve alignment between products and customer expectations.
### Profitability Improvement
Recommendation:
- Shift focus from revenue-driven to profit-driven decision-making.
- Reassess pricing strategies and cost structures for low-margin products.
### Returns & Customer Experience Improvement
- Improve product targeting and recommendation systems.
- Track and analyse return reasons (e.g., quality, sizing, expectations).
- Focus on net revenue (after returns) as a key performance metric.

---

## ▶️ How to Use

* Use slicers to filter data by year, country, category, continent, and key metrics
* Navigate between report pages to explore different levels of analysis
* Hover over charts and visuals to see more detailed information

---

## 💡 Skills Demonstrated

* Designed a Star Schema data model
* Performed data cleaning and transformation to ensure data accuracy and consistency
* Developed DAX measures and KPIs to support business performance tracking
* Built interactive dashboards and data visualisations in Power BI
* Generated actionable insights to support business decision-making

---

## 📎 Repository Contents
* `Adventure Works Bike Sales DashBoard.pbix` - Power BI Dashboard file 
* `README.md` – Project documentation

---

## 👩‍💻 Author

**Maddy Le**

Data Analytics


