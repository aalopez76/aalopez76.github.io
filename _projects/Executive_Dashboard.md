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

[![Hugging Face Space](https://img.shields.io/badge/HuggingFace-Live%20Dashboard-yellow?logo=huggingface)](https://aalpzp-executive-kpi-dashboard.hf.space/deep-dive)

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

----
----
-----
------
# Executive KPI Dashboard
### Turning transactional data into board-ready decisions.

[![Live demo](https://img.shields.io/badge/Live-Hugging%20Face%20Space-yellow?logo=huggingface)](https://huggingface.co/spaces/aalpzp/Executive_KPI_Dashboard)
[![Dashboard repo](https://img.shields.io/badge/Code-Executive__Dashboard-181717?logo=github)](https://github.com/aalopez76/Executive_Dashboard)
[![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![CI](https://img.shields.io/badge/CI-GitHub%20Actions-2088FF?logo=githubactions&logoColor=white)](https://github.com/aalopez76/Executive_Dashboard/actions)

> **A deployed analytics product** — not a notebook — that consolidates sales performance, operational
> risk, and growth opportunities into a single executive view, backed by a production SQL layer,
> automated tests, and CI/CD.

<p align="center">
  <img src="assets/images/kpi-dashboard.png" alt="Executive KPI Dashboard — Executive View" width="720">
  <br><em>Executive view: real-time KPIs with year-over-year deltas, risk flags, and drill-downs.</em>
</p>

---

## Executive Summary

Leadership teams sit on transactional systems that record *what happened* but rarely answer *what to do
next*. I built an end-to-end analytics product that closes that gap: a five-layer SQL framework feeds an
interactive dashboard that lets executives, sales managers, and commercial teams **see performance,
catch risk early, and act on opportunities** — without waiting on manual reporting cycles.

The work spans the full stack of a modern data product: **production SQL**, a **reusable data connector**,
**automated testing & CI**, and a **reproducible cloud deployment** — engineered so the numbers can be
trusted and the product can be maintained.

### Key metrics at a glance *(all verified against the database)*

| Metric | Value | Note |
|---|---:|---|
| Orders analyzed | **283** | 2018 → Feb 2020 |
| Customers | **122** (98 active) | 18% without an assigned rep |
| Products / lines | **110 / 7** | catalog breadth |
| Countries with sales | **22** | NA · EU · APAC |
| Referential integrity | **100%** | 0 orphan rows, 0 duplicate PKs |
| Payment coverage | **94.7%** | of revenue, by amount |
| Credit risk flagged | **58 customers / ~$3.05M** | exposure surfaced for review |
| On-time delivery | **~100%** | 1 late of 278 shipped |
| Cross-sell pairs | **1,367** | market-basket (support/confidence) |
| Production SQL queries | **39** | across 5 analytical layers |

> **Rigor note:** the database is a curated **subset** of *Classic Models*. Every figure on this page is
> reproduced from a SQL query against the actual data — **not** the canonical reference totals.

---

## Business Problem

Transactional systems store records but rarely enable strategy. The objective was an analytics layer +
dashboard that:

- **consolidates** business-critical KPIs into one executive view,
- **detects** revenue, credit, and operational risk early,
- **surfaces** cross-sell and growth opportunities via association metrics,
- **enables** fast, self-service drill-down — no ad-hoc reporting cycles.

---

## Analytics Architecture

A three-layer data-product architecture, from raw tables to decisions:

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
└─────────────┘              │ Predictive   │  │            ├──────────────┤
                             │ (What next?) │──┘            │ Opportunities│
                             └──────────────┘               │ Deep Dive    │
                                                            └──────────────┘
```

<p align="center">
  <img src="assets/images/toys_and_models-db.png" alt="Database schema (Classic Models / Toys & Models Co.)" width="640">
  <br><em>Relational schema — the single source of truth behind every metric.</em>
</p>

---

## Data Model & Dataset Quality

**Dataset summary (verified):** 283 orders · 2,649 order details · 249 payments · 122 customers
(98 with orders) · 110 products / 7 lines · 23 employees / 7 offices · 22 countries · dates **2018 → Feb 2020**.

**Quality checks** (nulls, duplicates, FK & hierarchy integrity):

| Check | Result |
|---|---|
| Referential integrity (all FKs) | ✅ **0 orphan rows** (100% match) |
| Duplicate primary keys | ✅ **0** |
| Customers without sales rep | ⚠️ **18%** (valid optional gap, 0 credit limit) |
| Rows with invalid dates (excluded from KPIs) | ⚠️ **2.9%** |
| Payment coverage (by amount) | ✅ **94.7%** |

---

## Key Findings *(verified)*

- **Revenue is diversified, not concentrated.** The top 10 products drive only ~**18%** of revenue
  (it takes ~47 SKUs to reach 60%) — low single-SKU dependency, a portfolio strength.
- **Moderate customer concentration.** Top 20% of customers ≈ **39%** of revenue (ABC/Pareto).
- **Geographic concentration risk.** USA, Spain, and France ≈ **55%** of sales (USA alone 34.7%).
- **Product mix.** Classic Cars **40.5%**, Vintage Cars **18.9%**, Motorcycles **11.2%**.
- **Credit exposure surfaced.** **58 high-risk customers**, ~**$3.05M** flagged for credit review.
- **Strong operations.** On-time delivery ≈ **100%**; payment coverage **94.7%**.
- **Retention signals.** RFM segmentation (Top 25% / High 20% / Mid 23% / Low 32%); avg reorder ≈ **204 days**.
- **Cross-sell upside.** Market-basket analysis across **1,367 product pairs**.

---

## SQL Analytics Framework — 39 production queries, 5 modules

| Layer | Question | Examples |
|---|---|---|
| **Descriptive / DQ** | What happened? | KPIs, completeness, uniqueness, FK integrity |
| **Analytical** | Why? | country/region/product/customer/rep deep-dives |
| **Diagnostic** | What went wrong? | credit anomalies, outliers, risk flags |
| **Predictive** | What's next? | RFM, seasonality, next-order, cross-sell |
| **Structural** | How is it organized? | recursive org hierarchy, office–territory coverage |

Each query is production-grade SQL with CTEs, window functions, and recursive logic. Two samples:

**RFM scoring** *(customer engagement / churn proxy)*

```sql
WITH CustomerRFM AS (
    SELECT  c.customerNumber, c.customerName,
            COUNT(DISTINCT o.orderNumber)                     AS freq_orders,
            COALESCE(SUM(od.quantityOrdered * od.priceEach),0) AS monetary,
            MAX(o.orderDate)                                  AS last_order_date
    FROM customers c
    LEFT JOIN orders       o  ON c.customerNumber = o.customerNumber
    LEFT JOIN orderdetails od ON o.orderNumber    = od.orderNumber
    GROUP BY c.customerNumber, c.customerName
)
-- Recency/Frequency/Monetary bucketed with NTILE() and combined into an RFM score.
```

**Recursive organizational hierarchy** *(reporting chain, any employee → CEO)*

```sql
WITH RECURSIVE EmployeeHierarchy AS (
    SELECT employeeNumber, reportsTo,
           firstName || ' ' || lastName AS employeeName, 1 AS level
    FROM employees
    WHERE employeeNumber = 1370          -- start node
    UNION ALL
    SELECT e.employeeNumber, e.reportsTo,
           e.firstName || ' ' || e.lastName, h.level + 1
    FROM employees e
    JOIN EmployeeHierarchy h ON e.employeeNumber = h.reportsTo   -- climb up
)
SELECT * FROM EmployeeHierarchy;
```

---

## Engineering & Reliability

What turns this analysis into a **maintainable product** — and demonstrates senior, full-lifecycle ownership:

| Area | Implementation |
|---|---|
| **Data engine** | Reads through my own multi-engine SQL connector (`SQL-Connection-Module`) — *dogfooding* a reusable component instead of ad-hoc `sqlite3`. |
| **Reproducibility** | Pinned dependency lockfile · Python 3.12 · deterministic builds. |
| **Testing** | Integration (data contract, query resolution, dashboard build) · unit (KPI math) · **end-to-end browser tests (Playwright)** · **data-regression snapshots** that catch silent metric drift. |
| **CI/CD** | **GitHub Actions** runs lint + tests + headless e2e on every push/PR. |
| **Deployment** | One-command bundle generator → self-contained Docker image, **live on Hugging Face Spaces** (gunicorn/WSGI) with a `/health` endpoint. |
| **Data trust** | Every published figure is query-backed; FK/integrity checks run in CI to prevent regressions. |
| **System design** | Three coordinated repos (dashboard + SQL layer + connector) wired via Git submodules. |

**Tech stack:** SQL (SQLite) · Python 3.12 · pandas · Vizro / Dash / Plotly · gunicorn · Docker ·
GitHub Actions · Playwright · pytest · ruff · Hugging Face Spaces.

---

## Links

- 🚀 **Live dashboard** — [Hugging Face Space](https://huggingface.co/spaces/aalpzp/Executive_KPI_Dashboard)
- 📊 **Dashboard** — [Executive_Dashboard](https://github.com/aalopez76/Executive_Dashboard)
- 🧮 **SQL analytics layer** — [SQL-Queries](https://github.com/aalopez76/SQL-Queries)
- 🔌 **Connection module** — [SQL-Connection-Module](https://github.com/aalopez76/SQL-Connection-Module)

<sub>Figures verified against the database on 2026-06-04. QA assisted by AI tooling.</sub>


