---
layout: page
title: Executive KPI Dashboard
description: Strategic bridge between raw data processing and high-level decision-making.
img: assets/img/kpi-dashboard.png
importance: 1
category: Personal
---

## Project Summary

End-to-end analytics product that transforms transactional sales data into **executive-grade insights** across **performance, operational risk, and growth opportunities**. I designed and implemented a **multi-layer SQL analytics framework** (descriptive → analytical → diagnostic → predictive) and delivered an interactive dashboard supporting **C-level decision-making**, sales operations, and commercial strategy.

**Scope:** 326 orders across multiple years · 27 countries · 122 customers · 110 products · 23 sales representatives (NA, EU, APAC)

<p align="center">
  <img src="/assets/img/kpi-dashboard.gif" alt="Dashboard Preview" width="1300">
</p>

---

## Business Problem

Transactional systems provide raw records but rarely enable strategic decision-making. The objective was to build an **analytics layer + dashboard** that:

- consolidates business-critical KPIs into a single executive view,
- detects revenue, credit, and operational risks early,
- identifies cross-sell and growth opportunities using association metrics,
- enables fast drill-down exploration without ad-hoc manual reporting cycles.

---

## Analytics Architecture

The solution follows a **three-layer data product architecture**:

1) **Raw Data Layer (SQLite)**  
Customers, orders, order details, products, employees, payments, offices, product lines.

2) **SQL Analytics Layer (Production-style SQL modules)**  
- **Descriptive** — KPIs and core reporting (What happened?)  
- **Analytical** — drivers, segmentation, and portfolio insights (Why?)  
- **Diagnostic** — anomalies, misalignment, and risk detection (What went wrong?)  
- **Predictive** — reorder cadence, seasonality, churn indicators, cross-sell (What’s next?)

3) **Dashboard Layer**  
Executive KPIs, regional insights, risks & diagnostics, opportunities, and deep dives.

````Markdown
```
Raw Tables (SQLite)          SQL Analytics Layer              Dashboard Layer
─────────────────            ───────────────────              ───────────────
┌─────────────┐              ┌──────────────┐               ┌──────────────┐
│ customers   │──┐           │ Descriptive  │──┐            │ Executive    │
│ orders      │  │           │ (What?)      │  │            │ View         │
│ orderdetails│  ├─────────▶│              │  │            ├──────────────┤
│ products    │  │           │ Analytical   │  │            │ Regional     │
│ employees   │  │           │ (Why?)       │  ├──────────▶│ View         │
│ payments    │  │           │              │  │            ├──────────────┤
│ offices     │  │           │ Diagnostic   │  │            │ Risks &      │
│ productlines│──┘           │ (What wrong?)│  │            │ Diagnostics  │
└─────────────┘              │              │  │            ├──────────────┤
                             │ Predictive   │  │            │ Opportunities│
                             │ (What next?) │──┘            ├──────────────┤
                             └──────────────┘               │ Deep Dive    │
                                                            └──────────────┘
```
````

## Data Model & Dataset Quality
<div class="row justify-content-center"> <div class="col-md-12 mt-3 mt-md-0 text-center"> {% include figure.liquid loading="eager" path="assets/img/toys_and_models-db.png" title="Database Schema" class="img-fluid rounded z-depth-1" style="max-width: 125%; height: auto;" %} </div> </div> <div class="caption text-center"> Database schema (Classic Models / Toys & Models Co.). </div>

### Dataset Summary

- 2,994 order details across 326 orders
-  customers with credit profiles
- 23 employees in 7 offices
- 110 products across 7 product lines
- 273 payments tracked
- 27 countries served

### Data Quality Checks (nulls, duplicates, FK integrity, hierarchy integrity)

- 2.1% records with missing sales rep assignment
- 6 orphan orderdetails (FK violations)
- No duplicate primary keys detected
- Payment coverage: 68% of sales backed by payments

### Key Product Capabilities

- Executive KPIs: revenue, orders, AOV, on-time delivery, and product concentration metrics (YoY deltas)
- Interactive exploration: filtering and drilldowns by region, customer, product, and sales rep
- Risk & diagnostics: credit-to-sales misalignment flags and exception monitoring
- Opportunity mining: cross-sell lift metrics + customer targeting signals

### Engineering design: modular SQL + reusable connectors via Git submodules

## Highlights & Results (Selected)

1. Revenue concentration: top 20% of customers contribute 70%+ of revenue (ABC / Pareto).
2. Risk exposure: credit policy misalignment impacting $250K+ in revenue exposure.
3. Operational improvement: +14pp YoY increase in on-time delivery.
4. Cross-sell opportunities: lift >10x for strategic product pairs.
5. Churn/recency risk: customers inactive >180 days represent $185K historical revenue at risk.

### SQL Analytics Framework (Production SQL)

The analytical layer is organized into five modules:

- Descriptive/Data Quality — completeness, uniqueness, referential integrity, KPIs
- Analytical — segmentation and drivers by region, product, and customer
- Diagnostic — anomalies, outliers, credit misalignment, risk flags
- Predictive — RFM scoring, seasonality, next-order estimation, cross-sell
- Structural — hierarchy, office–territory mapping, sales coverage

Each module contains production-grade SQL featuring CTEs, window functions, recursive queries, and business logic embedded directly in SQL.


## Links

Executive Dashboard: **[Executive_Dashboard](https://github.com/aalopez76/Executive_Dashboard/tree/main)**

SQL Analytics Layer: **[SQL-Queries](https://github.com/aalopez76/SQL-Queries)**

Connection Module: **[SQL-Connection-Module](https://github.com/aalopez76/SQL-Connection-Module)**

