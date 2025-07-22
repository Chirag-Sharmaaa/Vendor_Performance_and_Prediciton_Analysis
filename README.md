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
├── data/                              # Original raw datasets (hosted on Drive 🔗)
├── CSVs_Created/                      # Processed summary CSVs (from Python EDA)
│
├── db_ingestion.ipynb                 # Python code to ingest CSVs into PostgreSQL
├── sql_eda.ipynb                      # SQL queries for initial exploration
├── python_eda.ipynb                   # Visual and statistical analysis in Python
├── ML_Predictions.ipynb               # Predictive models for vendor performance
│
├── VendorPerformance_Dashboard.pbix   # Interactive Power BI dashboard
├── Project_Summary.docx               # Implementation notes and strategy
└── README.md                          # 📍 You're here!
