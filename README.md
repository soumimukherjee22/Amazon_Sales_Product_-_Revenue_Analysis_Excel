# 🛒 Amazon Sales Analysis — Data Analyst / MIS Portfolio Project

![Excel](https://img.shields.io/badge/Tool-Microsoft%20Excel-217346?style=flat&logo=microsoft-excel&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat)
![Datasets](https://img.shields.io/badge/Datasets-2-orange?style=flat)
![Records](https://img.shields.io/badge/Records%20Analysed-1%2C601-blue?style=flat)

An end-to-end Data Analyst and MIS project combining two Amazon datasets to deliver
actionable insights on product pricing, customer ratings, discount strategy,
and order performance. Built entirely in **Microsoft Excel** using advanced formulas,
PivotTables, dynamic dashboards, and structured MIS reports.

---

## 📁 Repository Structure

```
amazon-sales-analysis/
│
├── 📊 amazon_revised_table_Final_work.xlsx       ← Part 1: Product Analysis
│     ├── amazon_revised        (raw data — 1,465 rows)
│     ├── Table1                (cleaned data — 1,351 products, 27 columns)
│     ├── Sheet1                (null imputation reference)
│     ├── Report                (MIS Report — Category, Discount, Rating analysis)
│     ├── Pivot                 (4 cross-tab pivot views + charts)
│     └── Dashboard             (interactive dashboard + slicers)
│
├── 📈 amazon_sales_data_2025_Revenue_Report.xlsx  ← Part 2: Revenue & Order Report
│     ├── amazon_sales_data 2025  (raw data — 250 transactions, 19 columns)
│     ├── Data Validation         (6 automated data quality checks)
│     ├── KPI's & Pivot           (8 KPI cards + pivot tables)
│     ├── Key Analysis            (cancellation leakage, payment method, AOV)
│     ├── Dashboard               (Revenue & Order Performance Dashboard)
│     └── Revenue MIS Report      (4 structured management tables)
│
├── 📄 Amazon_Sales_Project_Summary.docx           ← Full project documentation
└── 📖 README.md
```

---

## 🗂️ Part 1 — Product Reviews & Pricing Analysis

### Dataset
| Attribute | Detail |
|-----------|--------|
| **Source** | Amazon India — product listings and customer reviews scrape |
| **Raw Records** | 1,465 rows |
| **After Cleaning** | 1,351 unique products (114 duplicates removed) |
| **Categories** | 9 (Electronics, Home & Kitchen, Computers & Accessories, and 6 others) |
| **Raw Columns** | 16 (product_id, product_name, category, prices, discount, rating, rating_count, reviews, links) |
| **Derived Columns Added** | 11 (Discount_Band, Rating_Band, Price_Bucket, Brand, Category_L1, Category_L2, Discount_Given_₹, Price_Premium_%, Review_Volume, High_Confidence, Star_Category) |

### Data Cleaning Steps
- Removed 114 duplicate product_id entries
- Imputed **2 null rating_count values** using category-level median (Electronics median = 5,179) with an audit flag column
- Standardised `discount_percentage` from text string `"64%"` to numeric decimal `0.64`
- Split `category` hierarchical string into `Category_L1` (top level) and `Category_L2` (sub-category)
- Extracted brand name from product_name using `LEFT()` + `FIND()` formula

### Key Metrics

| KPI | Value |
|-----|-------|
| Total Products Analysed | **1,351** |
| Average Discount % | **46.69%** |
| Average Rating | **4.1 / 5.0** |
| Total Review Volume (sales proxy) | **2,38,12,781** |
| Products with High Confidence Reviews (≥500) | Flagged separately |
| Excellent Rated Products (≥4.5) | **96** (9% of catalogue) |

### Category Breakdown

| Category | Products | Avg Discount | Avg Rating | Insight |
|----------|----------|-------------|------------|---------|
| Electronics | 490 | 50% | 4.1 | Highest ASP (₹10,418); deep discounts needed for volume |
| Home & Kitchen | 448 | 40% | 4.0 | Largest category; quality consistency concern |
| Computers & Accessories | 375 | 53% | 4.2 | Cables dominate; strong value perception |
| OfficeProducts | 31 | 12% | 4.3 | Niche but highest satisfaction; expand assortment |
| Toys & Games | 1 | 0% | 4.3 | 4.3 rating with zero discounting — quality sells itself |

### Discount Band Distribution

| Discount Band | Products | % Share | Avg Rating |
|--------------|----------|---------|------------|
| Moderate (25–49%) | 461 | 34% | 4.1 |
| High (50–69%) | 451 | 33% | 4.1 |
| Minimal (0–24%) | 228 | 17% | **4.2** ← Highest |
| Very High (70–100%) | 211 | 16% | 4.0 |

> 💡 **Key Finding:** Products with the **least discounting (0–24%) achieve the highest average rating (4.2)**. Heavy discounting does not improve customer satisfaction — quality does.

### Rating Band Distribution

| Rating Band | Products | % Share |
|-------------|----------|---------|
| Good (4.0–4.4) | 915 | 68% |
| Average (3.5–3.9) | 299 | 22% |
| Excellent (≥4.5) | 96 | 7% |
| Below Average (<3.5) | 41 | 3% |

### Price Bucket — Sweet Spot Analysis

| Price Tier | Products | Avg Rating | Total Reviews | Avg Discount |
|-----------|----------|------------|---------------|-------------|
| Budget (≤₹200) | 160 | 4.0 | 14,84,010 | 55.85% |
| **Economy (₹201–500)** | **341** | **4.1** | **64,74,111** | **54.50%** |
| Mid-Range (₹501–2000) | 499 | 4.1 | 1,04,91,534 | 45.53% |
| Premium (>₹2000) | 351 | 4.1 | 53,63,126 | 36.55% |

> ⭐ **Sweet Spot: Economy (₹201–500)** — highest review volume with balanced rating. Best tier for assortment investment.

### Top 10 Brands by Review Volume

| Rank | Brand | Products |
|------|-------|----------|
| 1 | boAt | 52 |
| 2 | Samsung | 33 |
| 3 | AmazonBasics | 27 |
| 4 | Bajaj | 26 |
| 5 | Redmi | 25 |
| 6 | Amazon | 23 |
| 7 | Fire-Boltt | 21 |
| 8 | Portronics | 21 |
| 9 | Wayona | 21 |
| 10 | Noise | 20 |

### Dashboards & Reports Built

- **Interactive Dashboard** — 4 pivot charts (Discount Band per Category, Rating Band by Category, Review Volume Band by Category, Product Details by Category) + Top 10 Brands bar chart + slicers (Category L1, Discount Band, Rating Band, Review Volume)
- **MIS Report** — Category-wise Analysis, Discount Band Analysis (% off MRP), Rating Distribution & Analysis — each with insight and recommended action columns

### Excel Formulas Used
```excel
COUNTIF, COUNTIFS, SUMIF, SUMIFS, AVERAGEIF, AVERAGEIFS
CORREL(discount_col, rating_col)          ← discount vs rating correlation
SUMPRODUCT(rating*review_count)/SUM(review_count)  ← weighted avg rating
INDEX(MATCH(MAX(...), ..., 0))            ← top product lookup
LEFT(B2, FIND("|", B2)-1)                ← category L1 extraction
LEFT(B2, FIND(" ", B2)-1)                ← brand extraction
LARGE, PERCENTILE, RANK                  ← ranking and top-N analysis
IFERROR(..., "-")                        ← error handling throughout
```

---

## 📈 Part 2 — Revenue & Order Performance Report (Amazon Sales 2025)

### Dataset
| Attribute | Detail |
|-----------|--------|
| **Source** | Kaggle — Amazon Sales 2025 |
| **Records** | 250 sales transactions (ORD0001–ORD0250) |
| **Date Range** | February 2025 — April 2025 (Q1 2025) |
| **Categories** | 5 (Electronics, Home Appliances, Clothing, Footwear, Books) |
| **Raw Columns** | 11 (Order ID, Date, Product, Category, Price, Quantity, Total Sales, Customer Name, Location, Payment Method, Status) |
| **Derived Columns Added** | 8 (Month, Month_Number, Quarter, Revenue_Bucket, Order_Size, Is_Completed, Is_Cancelled, Revenue_Lost) |

### Data Validation (All 6 Checks Passed ✅)
| Check | Result |
|-------|--------|
| Total rows = 250 | ✅ Confirmed |
| No duplicate Order IDs | ✅ 0 duplicates |
| Date column is proper date format | ✅ Verified |
| Total Sales = Price × Quantity | ✅ TRUE for all 250 rows |
| No blank Status values | ✅ 0 blanks |
| Status only contains valid values | ✅ Only Completed / Pending / Cancelled |

### Key Performance Indicators

| KPI | Value | Interpretation |
|-----|-------|----------------|
| **Total Gross Revenue** | ₹2,43,845 | All 250 orders combined |
| **Completed Revenue** | ₹88,530 | Only **36.3%** of gross revenue realised |
| **Revenue Lost to Cancellations** | **₹65,030** | **26.7% of gross — critical leakage** |
| **Pending Revenue** | ₹90,285 | 85 orders still in limbo |
| **Order Completion Rate** | **35.2%** (88/250) | Only 1 in 3 orders completes |
| **Cancellation Rate** | **30.8%** (77/250) | Above industry benchmark of 10–15% |
| **Avg Order Value (Completed)** | ₹1,006 | Healthy ticket size |
| **Best Month** | March 2025 | 131 orders vs 113 in February |

### Category Performance

| Category | Orders | Cancellation Rate | Revenue Lost (₹) | Action |
|----------|--------|------------------|-----------------|--------|
| Electronics | 118 | 28% | 26,650 | Largest revenue at risk — review delivery SLAs |
| **Home Appliances** | 40 | **40%** ← Highest | **36,000** | 🔴 Urgent audit — damage or installation issues |
| Clothing | 40 | 33% | 1,120 | Fit/size mismatch — improve size guidance |
| Footwear | 27 | 30% | 1,080 | Similar sizing issue as Clothing |
| **Books** | 25 | **0%** ← Best | 180 | ✅ Zero cancellations — scale this category |

### Payment Method Analysis

| Payment Method | Orders | Completion Rate | Cancellation Rate | Insight |
|----------------|--------|-----------------|-------------------|---------|
| **Amazon Pay** | 41 | **23.9%** ← Best | **9%** ← Lowest | ✅ Most reliable — recommend as default checkout |
| Credit Card | 54 | 19.3% | 21% | High AOV (₹1,140) — premium buyer segment |
| PayPal | 60 | 34.1% | 21% | Highest volume and revenue (₹69,645) |
| Debit Card | 53 | 15.9% | 26% | Lowest completion — impulsive buying pattern |
| **Gift Card** | 42 | **6.8%** ← Lowest | 23% | 🔴 Critical — investigate redemption flow |

> 💡 **Quick Win:** Making **Amazon Pay the default checkout option** could immediately reduce the cancellation rate from 30.8% toward the 9% benchmark seen in that segment.

### City / Location Performance

| City | Revenue (₹) | Rank | Cancellation Rate | Insight |
|------|------------|------|------------------|---------|
| Miami | 31,700 | #1 | 39% | Top revenue but high cancellation risk |
| Denver | 29,785 | #2 | 35% | High value; investigate logistics partner |
| Houston | 28,390 | #3 | 22% | Most consistent performer |
| **Seattle** | 26,890 | #5 | **23%** | ✅ Highest AOV (₹1,222) + lowest cancellation among top cities |
| **Los Angeles** | 17,820 | #9 | **53%** | 🔴 Worst city — immediate operational review required |

### Monthly Revenue Trend

| Month | Orders | Total Revenue (₹) | MoM Growth |
|-------|--------|------------------|------------|
| February 2025 | 113 | 1,22,695 | — |
| March 2025 | 131 | 1,17,730 | -4% |
| April 2025 | 6 | 3,420 | Data cut-off |

### Dashboards & Reports Built

- **Revenue & Order Performance Dashboard** — KPI cards, monthly trend chart, category breakdown, order status donut, payment method analysis, city performance, Top 10 customers — with slicers (Category, Status, Payment Method, Quarter)
- **Revenue MIS Report** — 4 structured tables: Category Performance, Monthly Performance (with MoM Growth %), Payment Method Analysis, City/Location Performance — each with conditional formatting and insight columns
- **Key Analysis Sheet** — Cancellation Leakage by category, Payment Method vs Completion Rate, Avg Order Value by Category

### Excel Formulas Used
```excel
COUNTIFS(Category, "Electronics", Status, "Completed")   ← multi-condition counts
SUMIFS(TotalSales, Category, "Electronics", Status, "Cancelled")  ← leakage by category
AVERAGEIF(PaymentMethod, "Amazon Pay", TotalSales)        ← AOV by payment method
=TEXT(Date, "MMM-YYYY")                                   ← month label extraction
=IF(MONTH(Date)<=3,"Q1",IF(MONTH(Date)<=6,"Q2",...))      ← quarter derivation
=(ThisMonth - LastMonth) / LastMonth                      ← MoM growth %
=SUM($Revenue$First : Revenue_This_Row)                   ← running cumulative total
IFERROR(..., "-")                                         ← division-by-zero protection
```

---

## 🔗 Cross-Dataset Insights

These findings are only possible because **both datasets were analysed together**:

| Finding | Implication |
|---------|-------------|
| Electronics is #1 in both datasets — 490 products (36%) in Part 1 AND 118 orders (47%) in Part 2 | Anchor category confirmed. Pricing and quality improvements here have maximum business impact. |
| Part 1 shows 46.69% avg discount. Part 2 shows 30.8% cancellation rate. | Aggressive discounting may attract low-intent buyers who cancel — test reducing discount on high-cancellation categories. |
| Minimal discount = highest rating (4.2) in Part 1. Books (low discount) = 0% cancellation in Part 2. | Consistent cross-dataset signal: quality and reliability improve when discount pressure reduces. |
| boAt is #1 brand by review volume in Part 1 (52 products). Electronics dominates orders in Part 2. | boAt's review strength should translate to conversion — benchmark boAt cancellation rate vs. category average. |

---

## 🛠️ Tools & Skills

| Category | Details |
|----------|---------|
| **Tool** | Microsoft Excel (2019 / 365) |
| **Data Cleaning** | Remove Duplicates, Power Query, SUBSTITUTE, LEFT, FIND, IFERROR |
| **Analysis** | PivotTables, COUNTIFS, SUMIFS, AVERAGEIF, CORREL, SUMPRODUCT, LARGE, INDEX/MATCH |
| **Visualisation** | Clustered Bar, Horizontal Bar, Line, Donut, Combo charts with dual axis |
| **Dashboard Features** | Slicers, Conditional Formatting (Color Scales, Data Bars, Icon Sets), KPI Cards |
| **Reporting** | MIS Report tables with insight columns, Grand Total rows, MoM growth tracking |
| **Statistics** | Weighted average rating, Pareto analysis, Correlation coefficient, Percentile |

---

## 💡 Top 5 Actionable Insights

1. 🔴 **Fix Home Appliances cancellations (40% rate, ₹36,000 lost)** — investigate delivery damage and installation support; this single category accounts for 55% of total revenue lost
2. ✅ **Make Amazon Pay the default checkout** — it has the lowest cancellation rate (9%) vs. the 30.8% overall average; a UX change with immediate revenue impact
3. 📦 **Invest in the Economy price tier (₹201–500)** — sweet spot with 341 products, highest review volume (64 lakh) and 4.1 rating; highest ROI for assortment expansion
4. ⚠️ **Audit Los Angeles operations immediately** — 53% cancellation rate (more than half of all orders cancel); no other city comes close
5. 🌟 **Protect Excellent-rated products from heavy discounting** — only 96 products (9%) are in the Excellent tier; these command price premium and should not be discounted aggressively

---

## 📊 Dashboard Previews

![screenshots/product_dashboard.png](https://github.com/soumimukherjee22/Amazon_Sales_Product_-_Revenue_Analysis_Excel/blob/main/Screenshots/Product_Reviews_%26_Pricing_Analysis_Dashboard.png)
![screenshots/revenue_dashboard.png](https://github.com/soumimukherjee22/Amazon_Sales_Product_-_Revenue_Analysis_Excel/blob/main/Screenshots/Revenue_%26_Order_Performance_Dashboard.png)

## 📊 Report Previews
![screenshots/report.png](https://github.com/soumimukherjee22/Amazon_Sales_Product_-_Revenue_Analysis_Excel/blob/main/Screenshots/Product_Reviews_%26_Pricing_Analysis_Report.png)
![screenshots/report.png](https://github.com/soumimukherjee22/Amazon_Sales_Product_-_Revenue_Analysis_Excel/blob/main/Screenshots/Revenue_%26_Order_Performance_Report.png)

## 📂 How to Use These Files

1. **Download** both `.xlsx` files from this repository
2. Open `amazon_revised_table_Final_work.xlsx` → navigate to the **Dashboard** tab to interact with slicers
3. Open `amazon_sales_data_2025_Revenue_Report.xlsx` → navigate to the **Dashboard** tab for revenue charts
4. Use slicers on the right side of each dashboard to filter by Category, Discount Band, Rating Band, and Review Volume
5. The **Report / Revenue MIS Report** tabs contain the detailed management-ready tables with insights

> ⚠️ Note: Slicer functionality requires Microsoft Excel (not Google Sheets). For view-only, all data and charts are visible in both tools.

---

## 📌 Project Context

This project was built as part of a **Data Analyst / MIS Portfolio** to demonstrate end-to-end analytical capability:

- Sourcing and loading raw data
- Data validation and cleaning
- Deriving meaningful columns from raw fields
- Building PivotTable-based analysis
- Designing management-ready dashboards
- Writing MIS reports with insight and recommended action columns
- Cross-dataset thinking to generate insights neither dataset supports alone

---

** Author

**Soumi Mukherjee**
Data Analyst | Reporting analysis | Excel 

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style-for-the-badge&logo=linkedin&logoColor=white)](www.linkedin.com/in/soumimukherjeeofficial)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/soumimukherjee22)
[![email](https://img.shields.io/badge/Email-D14836?logo=gmail&logoColor=white)](mailto:soumi.mukherjee2003@gmail.com)

---
## 🔖 Tags

`data-analysis` `mis-reporting` `excel` `pivot-tables` `amazon` `sales-analysis`
`dashboard` `data-cleaning` `kpi` `revenue-analysis` `product-analysis` `portfolio`
