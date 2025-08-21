---
layout: page
title: SQL Queries
description: Extracting data for a business dashboard
img: assets/img/sql.png
importance: 2
category: Personal
---

### Project Summary
This project focuses on building a dashboard to gain a comprehensive overview of the "Toys and Models" business. The main objective is to identify trends, areas of opportunity, and operational issues. The database contains detailed information about employees, products, orders, customers, and their payments.

The database schema is as follows: 

<div class="row justify-content-center"> <div class="col-md-12 mt-3 mt-md-0 text-center"> {% include figure.liquid loading="eager" path="assets/img/toys_and_models-db.png" title="example image" class="img-fluid rounded z-depth-1" %}
</div>
</div>
<div class="caption text-center"> The database schema.
</div>

Our goal is to extract the necessary data, starting with fundamental questions and then moving towards a deeper, more strategic analysis.

### Phase 1: Descriptive Schema (Fundamental Queries)
- **Table Exploration**: Identify the available tables and the variables they contain.
- **Business Overview**: Quantify the total number of customers, products, and employees.
- **Customer Financial Profile**: Analyze the average, maximum, and minimum credit limit of customers.

### Phase 2: Relational Analysis (JOINs and Aggregations)
- **Sales Performance by Country**: Determine the sales volume generated in each country.
- **Customer Distribution**: Map customers to their corresponding sales representatives to understand the workload of the sales force.
- **Order Size**: Analyze the number of products per order to identify the average size and high-volume orders.
- **Types of JOINs and Relationships**: Explore the connections between tables to understand relationships between customers and employees, as well as the internal staff hierarchy.

### Phase 3: Strategic Analysis (Subqueries and Window Functions)
- **Product Classification**: Identify the top-selling products to highlight the "star products".
- **Product Trends**: Analyze the monthly sales of a key product to detect seasonality and growth.
- **Employee Performance**: Classify salespeople based on their sales to recognize top performers.
- **Detailed Product Analysis**: Conduct a deep evaluation of a specific product's performance using advanced metrics.
- **Organizational Mapping**: Visualize the company's hierarchy to understand the command structure.

### Phase 4: Consolidation and Visualization (Dashboard)
With the extracted data, a dashboard will be built to visualize the findings. The queries will be grouped into thematic panels:

**Sales**:
* Product trends and sales by country.

**Finances**:
* Analysis of credit limits and sales volume.

**Logistics**:
* Identification of top-selling products for inventory management.

**Human Resources**:
* Classification of performance and organizational structure.
