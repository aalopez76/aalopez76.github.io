---
layout: page
title: SQL Queries
description: from the fundamental to Advanced
img: assets/img/sql.png
importance: 2
category: Personal
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
The SQL queries used for exploration, cleaning, analysis, and modeling are organized in:

- descriptive/data quality (what is happening/Completeness, Uniqueness & Referential Integrity) — data exploration, KPIs, completeness, uniqueness, and integrity checks
- analytical (Why is it happening?) — deep dives by country, region, product, customer, and sales rep
- diagnostic (What went wrong / stands out?) — anomaly detection, outliers, misalignment, and risk analysis
- predictive (What might happen next?) — RFM scoring, demand trends, next-order estimation, time-series features, cross-sell
- structural (How is the system organized?) — organizational hierarchy, office–territory mapping, coverage structure

Each module contains production-grade SQL with documentation, window functions, CTEs, recursive queries, advanced aggregations, and business logic embedded directly in SQL.

[![GitHub Repo](https://img.shields.io/badge/GitHub-View%20Repository-blue?logo=github)](https://github.com/aalopez76/SQL-Queries/tree/main)

Phase 1: Descriptive/Data Quality — "What is happening?"
Foundation analytics answering core business questions:

- Structure & Distribution: Table dimensions, row counts, column profiling
- Credit Profiling: Min/max/avg credit limits ($13K - $227K range), utilization rates
- Market Performance: Sales by country, ranking by volume, AOV analysis
- Customer Coverage: Rep-to-customer mapping, portfolio size distribution
- Order Analysis: High-value orders, product mix, unique SKUs per order

Sample Queries:

[![01_table_exploration.sql](https://github.com/aalopez76/SQL-Queries/blob/main/queries/descriptive/.sql/01_table_exploration.sql)- Database schema discovery
05_sales_by_country.sql - Geographic revenue breakdown
07_order_size_unique_products.sql - Order complexity analysis

Data Quality Results:

- 8 tables with 4,000+ total records validated
- 2.1% records excluded due to missing rep assignments
- Referential integrity: 99.8% FK match rate
- Temporal consistency: All orders within 2003-2005 range

### Phase 1: Descriptive/Data Quality Schema 
This module contains a set of SQL queries designed to explore, profile, and understand the *Toys & Models (Classic Models)* commercial database , helps answer key business questions:

- What is the structure and distribution of the dataset?
- How large are the tables, and how are they related?
- What is the credit profile of customers?
- Which markets generate the highest sales volume?
- How many customers does each representative manage, and how are they distributed?
- Which orders stand out due to size or value, and what products do they include?
- How do orders contribute to the organization’s overall performance?

### Phase 2: Diagnostic Schema

This module contains diagnostic SQL queries designed to identify anomalies, outliers, and operational misalignments within the business. Its goal is to highlight patterns that may require:

- credit policy review
- risk assessment
- commercial intervention
- financial oversight.

While the descriptive and analytical modules explain what is happening and why, this diagnostic module focuses on what should not be happening, what deviates from expected behavior, and which cases warrant immediate attention.

### Phase 3: Analytical Schema

This module contains queries designed to deepen business understanding through trends, patterns, comparative analysis, and performance metrics.

While *descriptive schema* answers **what is happening**, this module answers **why it is happening** and what factors explain the behavior observed.

The queries leverage:

- Window functions
- Hierarchical CTEs
- Rolling averages
- MoM and YoY comparisons
- ABC segmentation
- Multidimensional KPIs
- Geographic, portfolio, customer, and salesforce analytics


### Phase 4: Predictive Schema
 Unlike the descriptive (“What is happening?”) and analytical (“Why is it happening?”) modules, the predictive layer focuses on:

anticipating future behavior
deriving forward-looking indicators
identifying early trends
producing features useful for forecasting and recommendation systems.

### Phase 5: Structural Schema
This module focuses on the organizational and structural layout of the Classic Models dataset. The Structural module answers:

“How is the system (organization + geography + coverage) structured?”

The queries in this folder are not about performance or KPIs. They are about relationships, hierarchies, and coverage mapping across:

-employees and managers
-organizational hierarchy
-offices and territories
-sales representatives and their customers.



