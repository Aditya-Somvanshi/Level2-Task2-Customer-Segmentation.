# Level 2 – Task 2: Customer Segmentation Analysis
**RaushByte Technologies – Data Analytics Internship**

---

## 📌 Objective
Segment 8,000 customers into meaningful groups, compare New vs Returning vs Premium customers, study spending behavior and membership duration, and present everything in an interactive dashboard.

---

## ✅ Requirements Completed

| # | Requirement | Status |
|---|-------------|--------|
| 1 | Segment customers into different categories | ✅ Done (6 value segments) |
| 2 | Analyze New vs Returning vs Premium customers | ✅ Done |
| 3 | Study spending behavior | ✅ Done (segments, tiers, age groups) |
| 4 | Analyze membership duration | ✅ Done (1–10 years, 3 tenure bands) |
| 5 | Build visual dashboards | ✅ Done (interactive HTML) |

---

## 📊 Dataset
- **File:** `customer_analytics_dataset`
- **Rows:** 8,000 customers | **Missing values:** 0 | **Duplicates:** 0
- **Columns used:** Customer_Type, Age, Purchase_Count, Total_Spending, Satisfaction_Score, Membership_Years

---

## 🧩 Segmentation Method

Segments are rule-based (evaluated top-down) using spending, satisfaction and membership years.

| Segment | Rule | Customers | % Customers | % Revenue |
|---------|------|-----------|-------------|-----------|
| 🏆 Champions | Spend ≥ ₹2.5L, satisfaction ≥ 7, member 6+ yrs | 784 | 9.8% | 14.7% |
| 📈 Rising Value | Spend ≥ ₹2.5L, satisfaction 5–10, not yet Champion | 1,608 | 20.1% | 29.9% |
| ⚠️ At-Risk High Spenders | Spend ≥ ₹2.5L, satisfaction ≤ 4 | 1,611 | 20.1% | 30.0% |
| 🤝 Loyal Mid-Spenders | Spend ₹1L–2.5L, member 6+ yrs | 1,265 | 15.8% | 11.0% |
| 🌱 Casual Mid-Spenders | Spend ₹1L–2.5L, member < 6 yrs | 1,203 | 15.0% | 10.4% |
| 💤 Low Value | Spend < ₹1L | 1,529 | 19.1% | 4.0% |

**Why rule-based?** K-Means clustering on age, purchases, spending, satisfaction and tenure gave silhouette scores of only ~0.15 (clear clusters need 0.5+), so the data has no natural clusters. Business rules give groups that are easy to explain and act on.

---

## 📈 Key Findings

### 1. Customer type does not separate customers
| Type | Customers | Avg Spending | Avg Satisfaction | Avg Membership | Avg Purchases |
|------|-----------|--------------|------------------|----------------|---------------|
| New | 2,624 | ₹2,51,725 | 5.55 | 5.45 yrs | 25.2 |
| Returning | 2,665 | ₹2,47,561 | 5.48 | 5.44 yrs | 25.9 |
| Premium | 2,711 | ₹2,53,878 | 5.51 | 5.58 yrs | 25.1 |

The gap between highest and lowest is about 2.5% for spending. ANOVA p-values: spending 0.26, purchases 0.07, satisfaction 0.68, membership 0.15, so **none are statistically significant**. Premium customers are not meaningfully higher-value than New or Returning ones.

### 2. Spending behavior
- Average spending is ₹2,51,068; total revenue is ₹200.9 Cr.
- Spending tiers: Budget 19.1%, Mid-Range 30.9%, High 30.2%, Top Tier 19.9%.
- Age groups are nearly flat (₹2.48L–2.55L average spending).

### 3. Membership duration
- Average spending stays around ₹2.5L for every membership year (correlation r = +0.004, p = 0.73).
- Satisfaction does not change with tenure (r = −0.015, p = 0.18).
- Premium share is about 30–35% in every tenure year.

### 4. Business takeaway
**At-Risk High Spenders (1,611 customers) hold 30% of revenue but score 4/10 or lower on satisfaction.** Contacting them first protects the most revenue. Champions (9.8% of customers) are the group to reward and learn from.

### ⚠️ Data quality notes
- 1,570 customers labelled **New** have 5 or more membership years.
- **Feedback** does not follow **Satisfaction_Score** (e.g. 590 customers have "Excellent" feedback with a score of 3 or lower).

These should be confirmed with the data owner before relying on tenure or sentiment findings.

---

## 🖥️ Dashboard Features

- **6 KPI cards:** Customers, Total Revenue, Avg Spending, Avg Membership, Avg Satisfaction, At-Risk Revenue
- **Filters:** Customer type, Segment, Age group, Membership tenure, Spending tier (all charts update live)
- **Click a segment bar** to isolate that segment
- **"What this view says"** panel that rewrites itself for the current filters
- **8 visuals:** Segment bars, revenue donut, type comparison table, spending by membership year, customers + Premium share by tenure, segment-by-type heatmap, spending tiers, spending by age group
- Works offline, no install, light and dark mode

---

## 📁 Project Structure

```
Level2-Task2-Customer-Segmentation/
│
├── dashboard.html      ← Interactive dashboard (data embedded)
├── README.md           ← This file
└── requirements.txt    ← Python dependencies (optional)
```

---

## 🚀 How to Open

1. Download `dashboard.html`
2. Double-click it → opens in your browser (Chrome, Edge, Firefox)
3. Use the filters on the left, or click a segment bar

---

## 🛠️ Tools Used

- **Python 3** (pandas, SciPy, scikit-learn): data checks, ANOVA / chi-square tests, K-Means validation
- **HTML + CSS + JavaScript:** interactive dashboard with hand-built SVG charts (no external libraries)

---

*Level 2 – Task 2 | RaushByte Technologies Data Analytics Internship*
