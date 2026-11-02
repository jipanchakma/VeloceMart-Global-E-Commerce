# 🛒 VeloceMart: Global E-Commerce Analytics Dashboard

<img width="1586" height="883" alt="products" src="https://github.com/user-attachments/assets/813f2c77-7f67-4b82-a0e8-78251a9df803" />
<img width="1576" height="922" alt="orders" src="https://github.com/user-attachments/assets/0b7ed8fb-9248-4a88-bbd6-33b5888f48ad" />
<img width="1571" height="883" alt="Dashboard" src="https://github.com/user-attachments/assets/52d92a75-1960-4ac9-838a-e3e3ff7cfe17" />
<img width="1570" height="886" alt="customer" src="https://github.com/user-attachments/assets/4aad9475-a841-4bfc-baf4-0b6a6fdd2e36" />


> An end-to-end analytics project: **Excel → SQL → Power BI**, delivered as a fully dynamic, four-page report with slicers and custom navigation.

<img width="1571" height="883" alt="Dashboard" src="https://github.com/user-attachments/assets/6da24e8f-400d-4913-8a70-7be34a3f59fa" />


---

## 📑 Table of Contents

- [Overview](#-overview)
- [Business Questions](#-business-questions)
- [Key Metrics](#-key-metrics)
- [Key Insights](#-key-insights)
- [Report Pages](#-report-pages)
- [Dynamic Features](#-dynamic-features)
- [Tech Stack and Workflow](#-tech-stack-and-workflow)
- [Data Model](#-data-model)
- [Repository Structure](#-repository-structure)
- [How to Reproduce](#-how-to-reproduce)
- [Recommendations](#-recommendations)
- [Skills Demonstrated](#-skills-demonstrated)
- [Author](#-author)

---

## 📌 Overview

VeloceMart is a global e-commerce business. This project converts raw order data into an interactive Power BI report that lets stakeholders explore performance by time, customer, order and product, without writing a single query.

## ❓ Business Questions

1. How fast is revenue growing compared with last year?
2. Which months, channels, regions and segments drive the most revenue?
3. Who are the top customers, and where are they located?
4. Is growth coming from more orders or bigger baskets?
5. Which products, brands and categories perform best?
6. How healthy is order fulfilment (completed vs returned, cancelled, refunded)?

## 📊 Key Metrics

| Metric | Value |
|---|---|
| Total Revenue | **$12.35M** |
| Total Profit | **$5.47M** |
| Profit Margin | **44.28%** |
| Total Orders | **55K** (+34.62% YoY) |
| Revenue YoY | **+34.49%** (prior year: $9.18M) |
| Average Order Value | **$224.48** (flat YoY) |

## 🔍 Key Insights

1. **Seasonality:** November is the peak month ($1.46M revenue, 6.5K orders), followed by December.
2. **Acquisition:** Organic Search is the top channel ($3.71M); Direct is the lowest ($0.81M).
3. **Segments:** Consumer drives 57.7% of revenue, Corporate 28.06%, Home Office 14.24%.
4. **Geography:** North America contributes 52.83% of revenue. The United States leads by orders (23.0K), followed by the UK, Canada, Germany and Australia.
5. **Payments:** Credit Card is the most used method at 42.61%.
6. **Growth driver:** AOV is flat at about $224, so growth comes from **order volume**, not basket size.
7. **Order health:** About 85% of orders are Completed.

## 🧭 Report Pages

| Page | Purpose |
|---|---|
| **Dashboard** | Executive summary: revenue, profit, margin, monthly trends, category and payment mix |
| **Customers** | Top customers, top 5 countries, revenue by segment, region and acquisition channel, loyalty tiers |
| **Orders** | Monthly sales, YoY KPI grid (Revenue, AOV, Margin, Orders), order status, device type, map |
| **Products** | Products by sub-category, brand × category matrix, unit cost by category |

<table>
<tr>
<td><img src="docs/images/02-customers.png" alt="Customers page"></td>
<td><img src="docs/images/03-orders.png" alt="Orders page"></td>
</tr>
<tr>
<td colspan="2"><img src="docs/images/04-products.png" alt="Products page"></td>
</tr>
</table>

## ⚙️ Dynamic Features

- **Custom navigation:** buttons and a page navigator across all four pages, with a back button on each sub-page
- **Slicers:** Month, Year and Country cross-filter every visual
- **Time intelligence (DAX):** Revenue, Orders, AOV and Profit Margin vs prior year, with YoY %
- **Drill-down:** customer → country → segment → region → acquisition channel
- **Last refresh** timestamp on the main dashboard

## 🛠️ Tech Stack and Workflow

| Stage | Tool | What was done |
|---|---|---|
| 1. Clean | **Excel** | Standardised columns, fixed data types, removed duplicates and blanks |
| 2. Transform | **SQL** | Joins, aggregations and analytical views |
| 3. Model | **Power BI** | Star schema, relationships, date table |
| 4. Calculate | **DAX** | KPIs, prior-year and YoY measures |
| 5. Visualise | **Power BI** | Visuals, slicers, navigation and layout |

## 🧩 Data Model

Star schema with `customers`, `products`, `orders` and `order_items`, connected to a `Date` table. Details are in [`docs/data_model.md`](docs/data_model.md).

## 🗂️ Repository Structure

```
velocemart-ecommerce-analytics/
├── README.md
├── LICENSE
├── .gitignore
├── data/
│   ├── raw/                 # original files (not tracked)
│   └── processed/           # cleaned exports (not tracked)
├── excel/                   # Excel cleaning workbook
├── sql/
│   ├── 01_create_tables.sql
│   ├── 02_data_cleaning.sql
│   ├── 03_views.sql
│   └── 04_analysis_queries.sql
├── powerbi/                 # .pbix file (use Git LFS if large)
└── docs/
    ├── data_dictionary.md
    ├── dax_measures.md
    ├── data_model.md
    └── images/              # dashboard screenshots
```

## 🚀 How to Reproduce

1. **Clone** the repo:
   ```bash
   git clone https://github.com/jipanchahkma/velocemart-ecommerce-analytics.git
   ```
2. **Excel:** clean the raw files following [`docs/data_dictionary.md`](docs/data_dictionary.md) and save them to `data/processed/`.
3. **SQL:** run the scripts in `sql/` in order (`01` → `04`) on SQL Server, or adapt them for PostgreSQL or MySQL.
4. **Power BI:** open `powerbi/VeloceMart.pbix`, point the data source to your database views, and click **Refresh**.
5. To rebuild from scratch, add the measures from [`docs/dax_measures.md`](docs/dax_measures.md).

## 💡 Recommendations

- **Lift AOV** with bundles, free-shipping thresholds and cross-sell offers, since growth is currently volume-driven.
- **Prepare for Q4:** build inventory and campaigns ahead of the November peak.
- **Invest in organic channels** (SEO, content) as the top revenue source, and test ways to grow Direct.
- **Reduce returns and cancellations** to protect the 44% margin.

## 🧠 Skills Demonstrated

Data cleaning · SQL joins and aggregations · Star-schema modelling · DAX and time intelligence · Dashboard UX and navigation · Business storytelling

## 👤 Author

**Jipan**, BBA (Finance & Banking) student and aspiring data analyst, Chattogram, Bangladesh.

🔗 (https://www.linkedin.com/in/jipan-chakma/) · 📧

⭐ If you found this project useful, please star the repo.

## 📄 License

Released under the [MIT License](LICENSE).
