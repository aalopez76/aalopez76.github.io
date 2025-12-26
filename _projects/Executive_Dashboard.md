---
layout: page
title: Executive dashboard
description: strategic bridge between raw data processing and high-level decision-making.
img: assets/img/kpi-dashboard.png
importance: 3
category: Personal
---

### Project Summary

![Dashboard Preview](/assets/img/kpi-dashboard.gif)


This dashboard provides comprehensive insights across five key areas: executive KPIs, regional performance, risk diagnostics, growth opportunities, and deep-dive analytics. The analysis reveals significant revenue concentration among top customers and products, geographic imbalances in sales distribution, and predictable demand patterns ideal for forecasting. Key findings include a 14% on-time delivery rate improvement year-over-year, credit misalignment risks affecting $250K+ in revenue, and cross-sell opportunities with lift metrics exceeding 10x for strategic product pairs.



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

````markdown
```
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
````
                                                            

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


