---
layout: page
title: D&G_project
description: Digitalization & Data Governance
img: /assets/img/D&G.png
importance: 3
category: Stakeholder
---

Project Background
Background about the company

La Ferme is a Mexican company dedicated to the artisanal pasteurization of cow cream, operating continuously since 1980. Its business model has historically relied on manual production processes to deliver high-quality pasteurized cream to various local retailers. For over four decades, inventory management, quality control, production logs, and sales records have been handled manually and in a non-standardized manner.

In 2020, the company made a strategic decision to initiate a comprehensive digital transformation and establish a data governance framework aimed at improving operational efficiency, ensuring product traceability, and enabling more informed decision-making. However, the organization is still in the early stages of this transformation, and the existing information is currently limited, inconsistent, and often duplicated.

As a data analyst supporting this transition, my role involves collaborating in the design of the data model, assessing the quality of existing records, defining standardization and data cleaning rules, and building a solid foundation for the systems that will manage, analyze, and leverage data reliably in the future.

Key business metrics to be monitored once the digital system is in place include:

Production volume (liters of pasteurized cream)

Quality rejection rate

Average distribution time

Monthly sales volume by channel

Net monthly income

Cost per liter produced

Insights and recommendations are provided on the following key areas:
Category 1: Traceability and data governance
Current data is scattered, incomplete, and affected by multiple inconsistencies. A top priority is the design of a relational data model that incorporates master data domains such as suppliers, batches, products, and customers. In the short term, a controlled manual digitization and normalization process is recommended, accompanied by the definition of SQL-based validation and cleaning rules. In the medium term, the development of a centralized and accessible data catalog for operational teams is advised.

Category 2: Production and product quality
At present, there are no detailed records of temperature or processing times. The next phase involves installing IoT sensors to capture critical real-time data. This will enable the detection of correlations between environmental conditions, raw material sources, and final product quality. Such insights will be essential to building a predictive quality control system.

Category 3: Sales and distribution channel analysis
The first step is to digitize historical and current sales records. Once the data is structured, it will be possible to quantify the impact of each sales channel (direct-to-store, by order, bulk). It is recommended to develop a weekly demand forecasting model, based on seasonality and customer type, to optimize production and minimize waste.

Category 4: Operational efficiency and cost optimization
Currently, it is difficult to estimate production and distribution costs due to the lack of integration in logistics data. It is recommended to build a system that combines production, sales, and delivery route data. In later stages, this will support the implementation of a weather-based forecasting model and a route optimization tool to reduce delivery times and operational costs.

Technical Resources
The SQL queries for inspection, cleaning, and data standardization will be developed as part of the database implementation process and will be documented here: [link]

Targeted SQL queries addressing key business questions will be consolidated in this section: [link]

An interactive Tableau dashboard for exploring sales trends will be built once a reliable data structure is in place. It will be hosted here: [link]
