# 📦 Vendor Performance and Prediction Analysis

This end-to-end data analytics project investigates vendor sales, purchases, and inventory performance using SQL, Python, and Power BI. It aims to provide actionable insights to the business by solving five core business problems based on real-world transactional data. The project also includes predictive modeling using machine learning for deeper decision-making.

---

## 🚀 Problem Statement

Effective inventory and sales management are critical for optimizing profitability in the retail and wholesale industry. Companies need to ensure that they are not incurring losses due to inefficient pricing, poor inventory turnover or vendor dependency. The goal of this analysis is to:

- Identify underperforming brands that require promotional or pricing adjustments.
- Determine top vendors contributing to sales and gross profit.
- Analyze the impact of bulk purchasing on unit cost.
- Assess inventory turnover to reduce holding costs and improve efficiency.
- Investigate profitability variance between high- and low-performing vendors.

---

## 📁 Project Structure

```plaintext
Vendor_Performance_Analysis/
│
├── Raw_Datasets/                      # Original raw datasets (hosted on Drive 🔗)
├── All_CSVs/                          # Processed summary CSVs (from Python EDA)
│
├── db_ingestion.ipynb                 # Python code to ingest CSVs into PostgreSQL
├── sql_eda.ipynb                      # SQL queries for initial exploration
├── python_eda.ipynb                   # Visual and statistical analysis in Python
├── ML_Predictions.ipynb               # Predictive models for vendor performance
│
├── VendorPerformance_Dashboard.pbix   # Interactive Power BI dashboard
├── Project_Summary.docx               # Implementation notes and strategy
└── README.md                          # 📍 You're here!
```

## 🧪 Step-by-Step Pipeline

### 1️⃣ Data Ingestion

- All raw CSV files were loaded using **Python** into a **PostgreSQL** database.
- Due to dataset sizes (up to **1 crore rows**), large files were ingested in **100,000-row chunks** using a custom function.
- Data was stored in normalized tables like: `purchases`, `sales`, `freight`, `purchase_prices`, etc.

---

### 2️⃣ SQL Analysis & Aggregation

- Multiple **joins and aggregations** were performed to summarize vendor performance.
- A final summary table called `vendor_sales_summary` was created using **CTEs and JOINS**.
- This summary table was stored back into the database to avoid redundant computations.

---

### 3️⃣ Python EDA

- **Outlier detection** using boxplots and histograms.
- **Feature exploration** through correlation heatmaps.
- **Data cleaning and derived features**, including:
  - `StockTurnover`
  - `UnitPurchasePrice`
  - `UnsoldInventoryValue`


## 💼 Business Problem Solving

### 🧩 Problem 1: Identify Underperforming Brands
- Quantile-based thresholds were set on `TotalSalesDollar` and `ProfitMargin`.
- Brands with **low sales but high margins** were flagged.
- 📈 A **scatter plot** visualized underperforming brands clearly.

---

### 🧩 Problem 2: Top Vendors & Brands by Sales
- Ranked **top 10 vendors and brands** by `TotalSalesDollar` and `GrossProfit`.
- 📊 Used **horizontal bar charts** and a **Pareto chart** to visualize their contribution to total sales and profit.

---

### 🧩 Problem 3: Bulk Purchase vs Unit Cost
- Introduced a new derived feature: `OrderSize` categorized into Small, Medium, and Large.
- 📉 Found that **bulk buyers received ~72% cheaper prices** on average.
- Insight supports designing **pricing discounts** for high-volume vendors.

---

### 🧩 Problem 4: Low Inventory Turnover
- Identified vendors with `StockTurnover < 1`, indicating poor inventory movement.
- 📌 **Top 10 vendors** with lowest turnover were highlighted for further inventory optimization.

---

### 🧩 Problem 5: Locked Capital in Unsold Inventory
- Derived feature: `UnsoldInventoryValue = (PurchaseQty - SalesQty) × PurchasePrice`
- Ranked vendors by **capital locked in unsold stock**.
- 📉 Used a **donut chart** to visualize top contributors to inventory-based capital blockage.

---

### 🧪 Bonus Insight: Profit Margin Confidence Intervals
- Compared **95% Confidence Intervals** of margins for top-performing vs underperforming vendors.
- Surprisingly, **low-performing vendors had higher average margins**, suggesting potential pricing or volume misalignment.
