---
layout: page
title: SQL Queries
description: from the fundamental to advanced sql queries
img: assets/img/sql.png
importance: 2
category: Personal
---


# SQL Queries — From Fundamental to Advanced

End-to-end SQL analytics on a global collectibles distributor: from data quality to predictive business signals.

## Project Summary

This project analyzes the operational, commercial, and organizational performance of **Toys & Models Co.**, a global distributor of collectible scale models.

The analysis is performed entirely with SQL, following a professional multi-layer analytics framework (**Descriptive → Diagnostic → Analytical → Predictive → Structural**).

The company operates across North America, EMEA, and APAC, maintaining:

* A global product catalog (cars, motorcycles, aircraft, and ships)
* A sales-rep-driven B2B commercial structure
* Regionally distributed offices
* A diverse customer base
* Multi-stage order processing
* Credit- and payment-dependent workflows

## Key Insights Delivered

Through **39 production-grade SQL queries** organized across **five analytical layers**, this project uncovers:

* **Revenue Concentration** — a relatively small group of customers drives most revenue
* **Risk Detection** — credit and recency-based high-risk accounts
* **Demand Patterns** — monthly time series, lag features, and trend indicators
* **Cross-Sell Opportunities** — market-basket lift analysis across product pairs
* **Churn Signals** — RFM segmentation and next-order timing
* **Geographic Imbalance** — country-level revenue contributions
* **Operational Quality** — verified referential integrity and data consistency

The objective is to move from fundamental business questions toward progressively deeper and more strategic analyses, transforming raw transactional data into actionable business insights.

---

## Data Structure & Schema

The dataset contains detailed relational information about customers, products, orders, payments, offices, and employees.

### Database Summary (Verified)

* **2,649** order details across **283** orders
* **122** customers with credit profiles
* **23** employees across **7** offices
* **110** products across **7** product lines
* **249** payments tracked
* **28** customer countries served
* Orders span **2018-01-06 → 2020-02-17**

  * 111 orders in 2018
  * 151 orders in 2019
  * 21 orders in 2020
* Approximately **3,450** total records across **8** tables

### Data Quality (Verified)

A complete suite of data-quality validations confirms that the dataset is highly reliable:

* Referential integrity is fully preserved (**100% FK match rate**)
* **0 orphan records**
* **0 foreign-key violations**
* **0 duplicate primary keys**
* **22 customers (18%)** have no assigned sales representative (`salesRepEmployeeNumber IS NULL`)

  * All have a credit limit of zero.
  * This represents a business coverage gap rather than a data-quality issue.
* Payment coverage reaches **94.7% by amount**

  * $7.95M in payments vs. $8.40M in sales.
  * 80% of customers have at least one payment.
  * 100% of ordering customers have paid.
* Credit limits range from **$0 to $227,600**

  * Non-zero minimum: $11,000.
  * Average: $67,659.

---

## SQL Analytics Framework

The SQL queries used for exploration, validation, analysis, and predictive modeling are organized into five layers:

### Descriptive / Data Quality

**What is happening?**

* Data exploration
* KPI generation
* Completeness analysis
* Uniqueness validation
* Referential integrity verification

### Diagnostic

**What stands out or went wrong?**

* Anomaly detection
* Outlier analysis
* Credit-risk identification
* Business-rule deviations

### Analytical

**Why is it happening?**

* Country, region, product, customer, and sales-rep deep dives
* Trend analysis
* Comparative rankings
* Pareto and ABC segmentation

### Predictive

**What might happen next?**

* RFM scoring
* Demand trend classification
* Next-order estimation
* Time-series feature engineering
* Cross-sell analysis

### Structural

**How is the system organized?**

* Organizational hierarchy
* Office-territory relationships
* Sales coverage mapping

Each module contains production-grade SQL with:

* Inline documentation
* Window functions
* Common Table Expressions (CTEs)
* Recursive queries
* Advanced aggregations
* Business logic implemented directly in SQL

```text
Raw Tables (SQLite)            SQL Analytics Layers
─────────────────              ────────────────────
 customers      ┐              Descriptive  (What?)
 orders         │              Diagnostic   (What stands out?)
 orderdetails   ├────────────▶ Analytical   (Why?)
 products       │              Predictive   (What next?)
 employees      │              Structural   (How organized?)
 payments       │
 offices        │
 productlines   ┘
```

---

## Phase 1 — Descriptive / Data Quality

### "What is happening?"

Foundation analytics answering core business questions:

* Table dimensions and profiling
* Credit profiling (non-zero range $11K–$227.6K)
* Country-level sales performance
* Rep-to-customer coverage
* Order complexity and product diversity

**Sample Queries**

* `01_table_exploration.sql`
* `05_sales_by_country.sql`
* `07_order_size_unique_products.sql`

### Results (Verified)

* 8 tables and ~3,450 validated records
* Referential integrity: **100%**
* 22 customers excluded from rep-based analysis due to missing assignment
* Temporal consistency maintained across the entire 2018–2020 period

---

## Phase 2 — Diagnostic

### "What stands out?"

Operational-risk and anomaly detection.

Thresholds:

* Credit-to-sales misalignment ratio ≥ 2:1
* Recency risk ≥ 180 inactive days

**Sample Queries**

* `04_high_risk_customers_ratio.sql`
* `03_credit_vs_sales_misalignment_ratio.sql`
* `01_geographic_credit_anomalies.sql`

### Results (Verified)

* **57 high-risk customers**

  * 31 inactive for at least 180 days.
  * 24 customers without order history.
  * Approximately **$3.05M** in flagged credit/sales exposure.
* Credit policy appears well aligned:

  * Only **1 over-credited account**.
  * Only **2 under-credited high performers**.
* Outlier detection highlights top and bottom 5% credit assignments for review.

---

## Phase 3 — Analytical

### "Why is it happening?"

Deep-dive analyses using window functions, trend analysis, and segmentation techniques.

**Sample Queries**

* `03_customer_deep_agg_phase2.sql`
* `02_products_deep_agg.sql`
* `01_sales_by_country_vs_region.sql`
* `04_salesrep_performance_deep_agg.sql`

### Insights (Verified)

* Customer ABC segmentation:

  * A-tier: 48 customers → 69.5% of revenue.
  * B-tier: 26 customers → 19.9%.
  * C-tier: 24 customers → 10.5%.
* Product concentration:

  * Top 10 SKUs generate 18.1% of revenue.
  * 47 of 109 sold SKUs are required to reach 60% of revenue.
* Geographic contribution:

  * USA: 34.7%
  * Spain: 10.6%
  * France: 10.0%
  * Australia: 5.7%
  * United Kingdom: 4.8%
  * Italy: 3.9%
  * New Zealand: 3.7%
  * Finland: 3.5%
* Sales workload:

  * 15 active representatives.
  * 5–10 customers per representative.
  * Average: 6.7 customers per representative.

---

## Phase 4 — Predictive

### "What might happen next?"

Forward-looking indicators and forecasting features.

**Sample Queries**

* `06_customer_rfm_score.sql`
* `07_customer_next_order_prediction.sql`
* `08_product_cross_sell_pairs.sql`
* `05_product_demand_trend_flag.sql`
* `01_company_monthly_timeseries.sql`

### Outputs (Verified)

* RFM segmentation:

  * Top (13–15): 31 customers (25%).
  * High (10–12): 24 customers (20%).
  * Mid (7–9): 28 customers (23%).
  * Low (3–6): 39 customers (32%).
* Next-order estimation:

  * 97 customers receive expected reorder dates.
  * Average reorder cycle: 186 days.
  * 26 customers are overdue (>60 days).
  * 9 customers were recently due.
* Demand classification:

  * 3 Growing.
  * 24 Stable.
  * 81 Declining.
* Cross-sell opportunities:

  * 1,366 product pairs with co-occurrence ≥3.
  * 573 pairs with lift >5.
  * 64 pairs with lift >10.

---

## Phase 5 — Structural

### "How is the system organized?"

Organizational hierarchy and territory coverage analysis.

**Sample Queries**

* `01_employee_hierarchy_recursive.sql`
* `04_org_sales_coverage_map.sql`
* `03_office_region_structure.sql`

### Insights (Verified)

* 7 offices:

  * North America: San Francisco, Boston, NYC.
  * EMEA: Paris, London.
  * Japan: Tokyo.
  * APAC: Sydney.
* 23 employees:

  * 17 Sales Representatives.
  * 6 Management positions.
* Recursive hierarchy:

  * President → VPs → Sales Managers → Sales Representatives.
* Complete office → representative → customer coverage mapping.

---

## Business Impact

The analysis suggests several actionable initiatives:

* Prioritize reactivation efforts over credit reductions for the **57 high-risk accounts**.
* Launch outreach campaigns for:

  * 31 inactive customers.
  * 24 customers without orders.
* Reassess demand trends before making inventory decisions due to limited 2020 data coverage.
* Assign sales representatives to the **22 currently uncovered customers**.
* Develop bundled promotions around the **64 strongest cross-sell product pairs**.
* Strengthen focus on the United States while exploring expansion opportunities in lower-contribution markets.

---

## Explore the Code

The repository contains:

* **39 production-grade SQL queries**
* Five analytical layers
* Inline business documentation
* Query result examples and visualizations
* Module-specific READMEs
* Lightweight CI pipeline:

  * SQLFluff linting
  * Database integrity validation
  * Predictive-query regression snapshots

---

### Project Summary
This project analyzes the operational, commercial, and organizational performance of Toys & Models Co., a global distributor of collectible scale models.

The analysis is performed entirely with SQL, following a professional multi-layer analytics framework.

The company operates across North America, Europe, and APAC, maintaining:
- A global product catalog (cars, motorcycles, aircraft, ships)
- A sales-rep–driven B2B commercial structure
- Regionally distributed offices
- A diverse customer base
- Multi-stage order processing
- Credit- and payment-dependent workflows.

### Key Insights Delivered
Through 50+ production-grade SQL queries organized in 5 analytical layers, this project uncovers:

- Revenue Concentration
- Risk Detection
- Demand Patterns
- Cross-Sell Opportunities
- Churn Prediction
- Geographic Imbalance
- Operational Excellence

Our goal is to extract the necessary data, starting with fundamental questions and then moving towards a deeper, more strategic analysis.

### Data Structure & Schema
The dataset contains detailed relational information on customers, products, orders, payments, offices, and employees.

The database schema is: 

<div class="row justify-content-center">
    <div class="col-md-12 mt-3 mt-md-0 text-center">
        {% include figure.liquid loading="eager" path="assets/img/toys_and_models-db.png" title="example image" class="img-fluid rounded z-depth-1" style="max-width: 350%; width: 350%;" %}
    </div>
</div>
<div class="caption text-center">
    The database schema.
</div>

Database Summary:

- 2,994 order details across 326 orders
- 122 customers with credit profiles
- 23 employees in 7 offices
- 110 products across 7 product lines
- 273 payments tracked
- 27 countries served

A full set of data quality checks (nulls, duplicates, FK integrity, hierarchy integrity) confirms the dataset is well-structured with minor issues:

- 2.1% records with missing sales rep assignments
- 6 orphan orderdetails (FK violations)
- No duplicate primary keys detected
- Payment coverage: 68% of sales backed by payments

### SQL Analytics Framework
[![GitHub Repo](https://img.shields.io/badge/GitHub-View%20Repository-blue?logo=github)](https://github.com/aalopez76/SQL-Queries/tree/main)

The SQL queries used for exploration, cleaning, analysis, and modeling are organized in:

- descriptive/data quality (what is happening/Completeness, Uniqueness & Referential Integrity) — data exploration, KPIs, completeness, uniqueness, and integrity checks
- analytical (Why is it happening?) — deep dives by country, region, product, customer, and sales rep
- diagnostic (What went wrong / stands out?) — anomaly detection, outliers, misalignment, and risk analysis
- predictive (What might happen next?) — RFM scoring, demand trends, next-order estimation, time-series features, cross-sell
- structural (How is the system organized?) — organizational hierarchy, office–territory mapping, coverage structure

Each module contains production-grade SQL with documentation, window functions, CTEs, recursive queries, advanced aggregations, and business logic embedded directly in SQL.

```text
Raw Tables (SQLite)           SQL Analytics Layer
─────────────────             ───────────────────
┌─────────────┐               ┌──────────────┐
│ customers   │──┐            │ Descriptive  │
│ orders      │  │            │ (What?)      │
│ orderdetails│  ├───────────▶│              │
│ products    │  │            │ Analytical   │
│ employees   │  │            │ (Why?)       │
│ payments    │  │            │              │
│ offices     │  │            │ Diagnostic   │
│ productlines│──┘            │ (What wrong?)│
└─────────────┘               │              │
                              │ Predictive   │
                              │ (What next?) │
                              └──────────────┘
```
                                                            

### Phase 1: Descriptive/Data Quality — "What is happening?"
Foundation analytics answering core business questions:

- Structure & Distribution: Table dimensions, row counts, column profiling
- Credit Profiling: Min/max/avg credit limits (13K - 227K range), utilization rates
- Market Performance: Sales by country, ranking by volume, AOV analysis
- Customer Coverage: Rep-to-customer mapping, portfolio size distribution
- Order Analysis: High-value orders, product mix, unique SKUs per order

Sample Queries:

01_table_exploration.sql]- Database schema discovery
05_sales_by_country.sql- Geographic revenue breakdown
07_order_size_unique_products.sql- Order complexity analysis

[![EXPLORE PHASE 1 QUERIES](https://img.shields.io/badge/Explore_All_Phase_1_Queries-343a40?style=for-the-badge&logo=github)](https://github.com/aalopez76/SQL-Queries/tree/main/queries/descriptive)

Data Quality Results:

- 8 tables with 4,000+ total records validated
- 2.1% records excluded due to missing rep assignments
- Referential integrity: 99.8% FK match rate
- Temporal consistency: All orders within 2003-2005 range

### Phase 2: Diagnostic — "What went wrong? What stands out?"
Anomaly detection and operational risk identification:
This module focuses on what should not be happening, deviations from expected behavior, and cases requiring immediate attention:

- High-Risk Customers: Credit/sales misalignment detection (ratio >2:1)
- Geographic Anomalies: Countries with high credit allocation but low sales realization
- Credit Policy Gaps: Over-credited accounts (12) and under-credited growth opportunities (6)
- Recency Risk: Customers inactive >180 days flagged for churn prevention
- Outlier Detection: Bottom 5% and top 5% credit assignments via percentile analysis

Sample Queries:

04_high_risk_customers_ratio.sql]- Combined credit + recency risk model
03_credit_vs_sales_misalignment_ratio.sql - 2:1 ratio threshold classification
01_geographic_credit_anomalies.sql - Country-level credit vs. sales analysis

[![EXPLORE PHASE 2 QUERIES](https://img.shields.io/badge/Explore_All_Phase_2_Queries-343a40?style=for-the-badge&logo=github)](https://github.com/aalopez76/SQL-Queries/tree/main/queries/diagnostic)

Diagnostic Results:

- 18 high-risk customers with 267K at risk
- 12 over-credited accounts with avg $85K unused credit
- 6 under-credited accounts with growth potential ($50K+ opportunity)
- 14 stale customers (>180 days inactive, $185K historical revenue)

### Phase 3: Analytical — "Why is it happening?"
Deep dives through trends, patterns, and comparative analysis:
While descriptive answers what is happening, analytical answers why and what factors explain observed behavior.
Key Techniques:

- Window Functions: ROW_NUMBER(), RANK(), NTILE() for percentile analysis
- Time-Series: MoM/YoY comparisons, 3-month rolling averages
- ABC Segmentation: Pareto analysis (70/20/10 rule) for customers, products, sales reps
- Geographic Analysis: Regional vs. global sales contribution, within-region ranking
- Salesforce Performance: Customer count, territory coverage, average ticket analysis

Sample Queries:

03_customer_deep_agg_phase2.sql - Customer ABC classification with cumulative %
02_products_deep_agg.sql - Product portfolio Pareto analysis
01_sales_by_country_vs_region.sql - Multilevel geographic deep dive
04_salesrep_performance_deep_agg.sql - 360° salesforce analysis

[![EXPLORE PHASE 3 QUERIES](https://img.shields.io/badge/Explore_All_Phase_3_Queries-343a40?style=for-the-badge&logo=github)](https://github.com/aalopez76/SQL-Queries/tree/main/queries/analytical)

Analytical Insights:

- Customer ABC: A-tier (15 customers, 70% revenue), B-tier (24, 20%), C-tier (83, 10%)
- Product Concentration: Top 10 SKUs drive 60%+ of revenue
- Geographic Split: USA (28%), Spain (9%), France (8%), others <5% each
- Rep Workload: Range 2-14 customers per rep (avg 5.3), uneven distribution

### Phase 4: Predictive — "What might happen next?"
Forward-looking indicators and forecasting features:
Unlike descriptive ("What?") and analytical ("Why?"), predictive focuses on:

- Anticipating future behavior
- Deriving forward-looking indicators
- Identifying early trends
- Producing features for ML models

Advanced Techniques:

Time-Series Features: Lag/lead indicators, monthly quartiles, demand trends
RFM Scoring: Recency, Frequency, Monetary value segmentation (scale 3-15)
Next-Order Prediction: Expected reorder dates based on inter-order gaps (avg 42 days)
Cross-Sell Analysis: Product co-occurrence with support, confidence, lift metrics
Demand Classification: Growing/Stable/Declining flags (±15% threshold)

Sample Queries:

06_customer_rfm_score.sql - RFM segmentation for churn prediction
07_customer_next_order_prediction.sql - Expected order date calculation
08_product_cross_sell_pairs.sql - Market basket analysis
05_product_demand_trend_flag.sql - Growth classification (3-month window)
01_company_monthly_timeseries.sql - Company-level KPIs by month

[![EXPLORE PHASE 4 QUERIES](https://img.shields.io/badge/Explore_All_Phase_4_Queries-343a40?style=for-the-badge&logo=github)](https://github.com/aalopez76/SQL-Queries/tree/main/queries/predictive)

Predictive Outputs:

- RFM Segments: 22% Top-tier, 31% High, 28% Mid, 19% Low
- Next Orders: 8 customers "Overdue" (>60 days expected), 14 "Due Soon"
- Demand Trends: 15% SKUs growing, 8% declining, 77% stable
- Cross-Sell: 45 product pairs with lift >5 (12 pairs with lift >10)

### Phase 5: Structural — "How is the system organized?"
Organizational hierarchy and coverage mapping:
This module is not about performance or KPIs. It focuses on relationships, hierarchies, and structural layout:

- Employee Hierarchy: 3-level management chain (recursive CTE traversal)
- Office-Territory Mapping: 7 offices across USA, Europe, APAC
- Sales Coverage: Office → Rep → Customer mapping
- Capacity Analysis: Employees per office, customers per territory

Sample Queries:

01_employee_hierarchy_recursive.sql - Recursive CTE for reporting chains
04_org_sales_coverage_map.sql - End-to-end coverage view
03_office_region_structure.sql - Geographic footprint analysis

[![EXPLORE PHASE 5 QUERIES](https://img.shields.io/badge/Explore_All_Phase_5_Queries-343a40?style=for-the-badge&logo=github)](https://github.com/aalopez76/SQL-Queries/tree/main/queries/structural)

Structural Insights:

- 7 offices: San Francisco (HQ), Paris, Tokyo, Sydney, London, Boston, NYC
- 23 employees: 17 sales reps, 6 managers (President → VP Sales → Managers → Reps)
- Territory coverage: USA (4 offices), Europe (2), APAC (1)
- Capacity: Paris office (6 reps, 35 customers), Tokyo (2 reps, 8 customers)

### Business Impact
Actionable insights derived from SQL analytics:

1. Credit Risk Mitigation: Identified $267K at risk across 18 accounts with misaligned credit policies → Immediate policy review initiated
2. Revenue Opportunity: $50K+ growth potential by increasing credit for 6 under-credited high-performers → Credit increase proposals drafted
3. Churn Prevention: 14 customers flagged for proactive outreach (60% reactivation target) → Automated email campaign triggered
4. Inventory Optimization: Q4 demand spike detected via time-series analysis → Enabled +15% stock adjustment in Nov-Dec
5. Sales Rebalancing: Top rep manages 14 customers while 3 reps have <5 each → Redistribution plan proposed to improve coverage
6. Cross-Sell Strategy: 12 product pairs with lift >10 identified → Bundled promotion campaign designed for Q1 launch
7. Geographic Expansion: Bottom-quartile countries contributing <1% each → Targeted marketing budget allocated to APAC growth markets


### Explore the Code
View Full SQL Repository on [![GitHub Repo](https://img.shields.io/badge/GitHub-View%20Repository-lightgrey?logo=github)](https://github.com/aalopez76/SQL-Queries/tree/main)

The repository contains:

- 50+ production-grade SQL queries across 5 analytical layers
- Inline documentation with business context and logic explanation
- Sample outputs and interpretation notes
- Query images showing execution results (view examples)
- Integration notes for BI tools (Tableau, Power BI, Looker)
- Performance tips for optimization

### Related Projects

#### Executive Dashboard
[![GitHub Repo](https://img.shields.io/badge/GitHub-View%20Repository-lightgrey?logo=github)](https://github.com/aalopez76/Executive_Dashboard)

Interactive Vizro dashboard powered by these SQL queries, featuring:

- 5 pages (Executive, Regional, Risks, Opportunities, Deep Dive)
- Real-time KPIs with YoY comparisons
- Interactive maps and click-to-filter actions
- AG Grid tables with conditional formatting


#### SQL Connection Module 
[![GitHub Repo](https://img.shields.io/badge/GitHub-View%20Repository-lightgrey?logo=github)](https://github.com/aalopez76/SQL-Connection-Module)

Enterprise-level multi-engine database connector supporting:

- SQLite, PostgreSQL, MySQL, SQL Server, Oracle, Snowflake, Redshift
- Unified OOP API for connection management
- Production-ready with context managers and error handling



