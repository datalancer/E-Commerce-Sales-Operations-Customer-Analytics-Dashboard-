# E-Commerce Sales, Operations & Customer Analytics Dashboard (Power BI)

An end-to-end Business Intelligence and Customer Segmentation project built in **Microsoft Power BI**. This 5-page interactive report transforms raw multi-table e-commerce transaction records into executive, sales, customer, product, and store-level insights[cite: 10, 11, 12, 13, 14].

---

## 📌 Business Problem Statement
Raw operational data was distributed across 6 separate relational files covering **1 million orders**, **9,000+ active customers**, **264 products**, and **726 stores** spanning **2014 to 2021**[cite: 1, 10, 11, 13, 14]. Without a centralized analytics solution, stakeholders lacked visibility into:
* Regional revenue concentration across divisions, districts, and upazilas[cite: 10, 12, 14].
* Peak shopping hours, weekly fulfillment spikes, and payment method preferences[cite: 10, 11, 14].
* Product category performance, supplier contributions, and manufacturing country share[cite: 13].
* Customer purchasing behavior and retention tiers[cite: 12].

---

## 🏗️ Data Architecture & Modeling
Instead of flattening all files into a single wide table, the 6 raw datasets (`customer_dim`, `fact_table`, `item_dim`, `store_dim`, `time_dim`, `Trans_dim`) were cleaned in **Power Query** and modeled into a **Star Schema**[cite: 1, 2, 3]:
* **Central Fact Table:** `Orders` (transaction quantities, unit prices, total prices, and foreign keys)[cite: 2, 3].
* **Dimension Tables (5):** `Customers`, `Products`, `Stores`, `Calendar`, and `Transaction` connected via single-direction `1:*` relationships[cite: 2, 3].
* **Dedicated Measures Table:** `_Measures` housing all core KPI, time-intelligence, product, and store throughput calculations.

---

## 📊 Dashboard Pages & Key Insights

### 1. Executive Summary
* **KPIs Tracked:** Total Revenue (**₹105.40M**), Total Orders (**1M**), Active Customers (**9K**), Average Order Value (**₹105.40**), and Total Units Sold (**6M**)[cite: 10].
* **Key Findings:** **Dhaka** leads all regional divisions with over **₹40M** in revenue, and **card payments** dominate transactions at **89.74% (₹94.58M)** followed by **mobile payments** at **7.69% (₹8.11M)**[cite: 10].

### 2. Sales Performance
* **Visuals:** Quarterly revenue comparison, monthly revenue vs. order volume dual-axis seasonality chart, top 10 banking partners, and a day-by-hour order heatmap[cite: 11].
* **Key Findings:** Customers purchase an average of **6.00 units per order**, with steady multi-quarter demand across major banking partners such as Bangladesh Commerce Bank, AB Bank, and Dhaka Bank[cite: 11].

### 3. Customer Insights & RFM Segmentation
* **Methodology:** Implemented percentile-based **RFM (Recency, Frequency, Monetary)** scoring (`1–4` scale) to classify customers into 5 actionable segments: **Champions**, **Loyal Customers**, **Recent / Promising**, **Needs Attention**, and **At-Risk / Hibernating**[cite: 12].
* **Visuals:** Segment revenue & headcount combo chart, segment share treemap, top districts bar chart, and an individual customer spend table (`customer_key`, name, segment, orders, total spend, and recency)[cite: 12].

### 4. Product & Supplier Analytics
* **KPIs Tracked:** **264** total products, **10** active suppliers, **₹17.56** average unit price, and **6M** units sold[cite: 13].
* **Key Findings:** **Beverage - Energy/Protein**, **Food - Healthy**, and **Coffee K-Cups** lead category sales, while **Bangladesh** and **India** serve as the top manufacturing countries by revenue[cite: 10, 13].

### 5. Operations & Store Fulfillment
* **KPIs Tracked:** **726** active stores across **540** upazilas, averaging **₹145.18K** in revenue and **1.38K** orders per store[cite: 14].
* **Key Findings:** Order fulfillment load spikes sharply during the **4th week** of the month, and packaging volume is led by `ct`, `cans`, and `bottles`[cite: 14]. Includes a 4-level regional drill-down matrix (`Division → District → Upazila → Store`)[cite: 14].

---

## 🛠️ Technical Challenges & Solutions
1. **Hourly Timestamps in `Calendar`:** Because `time_dim` tracked individual hours alongside dates, Power BI could not mark it as a standard unique date table, and records ended in 2021[cite: 4, 10, 11]. Resolved by anchoring customer recency (`DATEDIFF`) to the dataset's maximum order date (`MAXX`) and using `REMOVEFILTERS('Calendar')` for period comparisons.
2. **Duplicate Customer Names:** Multiple distinct customers shared identical first names[cite: 12]. Adding `customer_key` alongside customer names in detail visuals prevented profiles from aggregating together[cite: 12].
3. **High-Cardinality Visual Clutter:** Applied **Top-N** filtering across categories, banks, districts, and stores, and added a unified **Page Navigator** bar across all 5 pages for seamless navigation[cite: 10, 11, 12, 13, 14].

---

## 🧰 Tools & Skills Used
* **Power BI Desktop** (Power Query M, Star Schema Data Modeling, DAX, Conditional Formatting, Drill-Down Matrices, Page Navigator)[cite: 2, 3, 11, 14]
* **Analytics Techniques:** RFM Customer Segmentation, Cohort/Recency Scoring, Time-Intelligence, Pareto / Top-N Analysis[cite: 12, 13]

---

## 🚀 How to Use This Repository
1. Download the `.pbix` file from this repository.
2. Open it in **Power BI Desktop** (latest version recommended).
3. Use the top **Page Navigator** buttons (`Ctrl + Click` in Desktop) to switch across the 5 report pages and filter by Year, Division, District, Payment Type, or RFM Customer Segment[cite: 10, 11, 12, 14].
