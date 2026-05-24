# Customer Churn Analysis | MySQL + Power BI

> **End-to-end customer churn analysis using SQL querying and interactive Power BI dashboards — identifying churn drivers across contract types, payment methods, internet services, and customer tenure for a telecom dataset of 7,000+ records.**

---

## Project Overview

Built a full-cycle **Customer Churn Analytics solution** using **MySQL** for data extraction and business reporting, and **Power BI** for KPI dashboard development. Analyzed a telecom dataset of **7,000+ customers** to surface churn drivers, retention patterns, and monthly revenue loss.

The project answers three core business questions:
- Which customer segments are at highest risk of churning?
- How do contract type, payment method, and internet service affect churn rate?
- What tenure threshold separates high-risk customers from loyal ones?

---

## Tools & Technologies

| Category | Stack |
|---|---|
| Database & Querying | MySQL, SQL |
| Visualization & BI | Power BI Desktop |
| Analysis Techniques | Tenure Segmentation, KPI Reporting, Churn Segmentation |
| Skills Applied | Data Cleaning, Business Intelligence, Dashboard Development |

---

## Dataset

- **Source:** Telecom Customer Churn Dataset (IBM Sample / Kaggle)
- **Size:** 7,043 customer records, 21 columns
- **Key Columns:** `CustomerID`, `Contract`, `PaymentMethod`, `InternetService`, `tenure`, `MonthlyCharges`, `TotalCharges`, `Churn`

---

## Key Insights & Findings

| Dimension | Finding |
|---|---|
| **Contract Type** | Month-to-month customers churned at **~42%** vs. **~11%** for 2-year contracts |
| **Payment Method** | Electronic check users had the **highest churn rate (~45%)** across all payment types |
| **Internet Service** | Fiber optic customers churned significantly more than DSL customers |
| **Customer Tenure** | Customers with **< 12 months tenure** accounted for the majority of total churn |
| **Revenue Loss** | Churned customers had an average monthly charge of **$74.44** — SQL-calculated from actual dataset |

---

## SQL Analysis Performed

All queries are available in the `/SQL` folder. Core analyses include:

- **Overall Churn Rate** — total churned vs. retained customers with percentage
- **Contract Type Distribution** — churn rate across month-to-month, one-year, two-year contracts
- **Payment Method Analysis** — churn comparison across 4 payment methods
- **Internet Service Segmentation** — DSL vs. Fiber Optic vs. No Service churn behavior
- **Tenure Segmentation Analysis** — churn rate grouped by 0–12, 12–24, 24+ months tenure bands
- **Monthly Revenue Loss** — total `MonthlyCharges` sum for churned customers

**Sample Query — Churn Rate by Contract Type:**
```sql
SELECT 
    Contract,
    COUNT(*) AS total_customers,
    SUM(CASE WHEN Churn = 'Yes' THEN 1 ELSE 0 END) AS churned_customers,
    ROUND(
        SUM(CASE WHEN Churn = 'Yes' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 2
    ) AS churn_rate_pct
FROM customer_churn
GROUP BY Contract
ORDER BY churn_rate_pct DESC;
```

**Sample Query — Monthly Revenue Lost to Churn:**
```sql
SELECT 
    ROUND(AVG(MonthlyCharges), 2) AS avg_monthly_charge_churned,
    ROUND(SUM(MonthlyCharges), 2) AS total_monthly_revenue_lost
FROM customer_churn
WHERE Churn = 'Yes';
```

---

## Power BI Dashboard

### Dashboard Features
- **KPI Cards** — Total Customers, Overall Churn Rate %, Churned Count, Retained Count
- **Churn by Contract Type** — Clustered bar chart comparing churn across contract lengths
- **Churn by Payment Method** — Donut chart with percentage labels per method
- **Churn by Internet Service** — Stacked bar showing DSL vs. Fiber Optic vs. None
- **Tenure vs. Churn Trend** — Line chart showing how churn decreases as tenure increases
- **Interactive Slicers** — Filter entire dashboard by Contract Type, Internet Service, Senior Citizen status

### Dashboard Preview

![Power BI Dashboard](https://github.com/pravalikagunaganti/customer-churn-analysis-sql-powerbi/blob/main/customer-churn-dashboard.png?raw=true)

*KPI dashboard showing churn rate by contract type, payment method, and tenure built using Power BI.*

### SQL Analysis Preview

![SQL Query](https://github.com/pravalikagunaganti/customer-churn-analysis-sql-powerbi/blob/main/sql-churn-analysis-query.png?raw=true)

*MySQL Workbench showing churn analysis query output.*

---

## Project Structure

```
Customer-Churn-Analysis/
│
├── Dashboard/
│   └── customer-churn-dashboard.png        # Power BI dashboard screenshot
│
├── SQL/
│   ├── 01_overall_churn_rate.sql
│   ├── 02_contract_type_analysis.sql
│   ├── 03_payment_method_analysis.sql
│   ├── 04_internet_service_analysis.sql
│   ├── 05_tenure_segmentation_analysis.sql
│   └── 06_revenue_loss_analysis.sql
│
├── PowerBI/
│   └── customer_churn_dashboard.pbix       # Power BI report file
│
├── Screenshots/
│   └── sql-churn-analysis-query.png
│
└── README.md
```

---

## Business Impact

This analysis gives a telecom business clear, actionable direction:

1. **Target month-to-month customers** with upgrade offers to annual contracts — directly reduces the highest-churn segment
2. **Investigate electronic check friction** — nearly half of these users churn; switching them to auto-pay could improve retention
3. **Launch early-tenure onboarding programs** — customers in their first 12 months are the most vulnerable
4. **Quantify churn in revenue terms** — monthly revenue loss figure enables finance teams to justify retention spend

---

## How to Run

1. Download the dataset from [Kaggle — Telco Customer Churn](https://www.kaggle.com/datasets/blastchar/telco-customer-churn)
2. Import into MySQL and run scripts from `/SQL` in numbered order
3. Open `customer_churn_dashboard.pbix` in Power BI Desktop
4. Connect to your MySQL instance via Get Data → MySQL Database
5. Refresh and explore the interactive dashboard

---

## Skills Demonstrated

`SQL` `MySQL` `Power BI` `Data Analytics` `Data Visualization` `KPI Dashboard` `Business Intelligence` `Customer Churn Analysis` `Customer Retention` `Tenure Segmentation` `Data Cleaning` `Dashboard Development` `Analytical Thinking` `Storytelling with Data` `Revenue Analysis` `MIS Reporting`

---

## Connect With Me

📧 Email: [pravalikagunaganti16@gmail.com](mailto:pravalikagunaganti16@gmail.com)

💼 LinkedIn: [https://www.linkedin.com/in/pravalika-gunagantiti-5a333a304](https://www.linkedin.com/in/pravalika-gunagantiti-5a333a304)

💻 GitHub: [https://github.com/pravalikagunaganti](https://github.com/pravalikagunaganti)

---

## Tags

`#SQL` `#MySQL` `#PowerBI` `#DataAnalytics` `#BusinessIntelligence` `#CustomerChurnAnalysis` `#DataVisualization` `#OpenToWork`

---

*Built by [Pravalika Gunaganti](https://github.com/pravalikagunaganti) — Data Analytics Portfolio Project focused on practical SQL querying, business insight generation, and Power BI dashboard development.*
