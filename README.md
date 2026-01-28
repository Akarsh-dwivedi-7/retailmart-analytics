# Retailmart-SQL-Analytics-Dashboard
________________________________________
### **🎯 Project Overview**
This project showcases an end-to-end, enterprise-style SQL analytics platform that converts raw retail data into structured, decision-ready insights. Developed as a capstone project for the AccioJob SQL Bootcamp, it reflects real-world data engineering and analytics architectures commonly adopted by large-scale organizations such as Flipkart, Amazon, and Swiggy.
The solution emphasizes production-grade design principles including schema isolation, configuration-driven logic, data quality enforcement, performance optimization, automated refresh workflows, and decoupled dashboard consumption.
________________________________________
---
## 🔑 Key Highlights

* **📊 25+ Analytical Views** — Real-time metrics spanning six core business domains
* **⚡ 10 Materialized Views** — Pre-aggregated KPIs optimized for low-latency dashboards
* **🔄 32 JSON Export Functions** — API-friendly data delivery for frontend and integrations
* **📱 Multi-Tab Dashboard** — Responsive, domain-driven business reporting interface
* **🚨 Rule-Based Alerts** — Automated detection of critical business scenarios
* **📈 Automated Analytics Pipeline** — Scheduled refresh, logging, and export orchestration


________________________________________
---

## 📁 Project Structure

| Folder / File                      | Description                                                                      |
| ---------------------------------- | -------------------------------------------------------------------------------- |
| **01_setup/**                      | Analytics foundation and database initialization                                 |
| ├── 01_create_analytics_schema.sql | Creates isolated analytics schema, configuration table, and helper functions     |
| ├── 02_create_metadata_tables.sql  | KPI metadata catalog, execution logs, refresh history, and data quality tracking |
| └── 03_create_indexes.sql          | Performance-optimized indexes for analytics queries                              |
| **02_data_quality/**               | Data validation and governance layer                                             |
| └── data_quality_checks.sql        | Completeness, accuracy, consistency, timeliness, and uniqueness checks           |
| **03_kpi_queries/**                | Domain-wise analytics modules                                                    |
| ├── 01_sales_analytics.sql         | Sales KPIs, trends, payment analysis, and executive metrics                      |
| ├── 02_customer_analytics.sql      | CLV, RFM segmentation, churn risk, and cohort analysis                           |
| ├── 03_product_analytics.sql       | Product performance, inventory health, and ABC analysis                          |
| ├── 04_store_analytics.sql         | Store profitability, regional performance, and workforce metrics                 |
| ├── 05_operations_analytics.sql    | Delivery SLA, returns, courier efficiency, and payment success                   |
| └── 06_marketing_analytics.sql     | Campaign ROI, channel performance, promotions, and email analytics               |
| **04_alerts/**                     | Proactive business monitoring                                                    |
| └── business_alerts.sql            | Stock, churn, revenue anomaly, SLA breach, and return-rate alerts                |
| **05_refresh/**                    | Automation and orchestration                                                     |
| ├── refresh_all_analytics.sql      | Orchestrates refresh of all materialized views with logging                      |
| └── export_all_json.sh             | Exports analytics outputs as JSON for dashboards and APIs                        |
| **06_dashboard/**                  | Frontend visualization layer                                                     |
| ├── index.html                     | Dashboard entry point                                                            |
| ├── css/styles.css                 | Dashboard styling                                                                |
| ├── js/dashboard.js                | Client-side visualization logic                                                  |
| └── data/                          | JSON datasets for all analytics domains                                          |
| **07_documentation/**              | Project documentation                                                            |
| ├── README.md                      | Project overview and setup guide                                                 |
| ├── data_dictionary.md             | Schema and column-level documentation                                            |
| └── kpi_definitions.md             | Business KPI definitions and formulas                                            |

---
________________________________________
### **📁 01_setup — Analytics Platform Initialization**
**Purpose:**
Bootstraps the RetailMart Enterprise Analytics Platform by establishing schema isolation, centralized configuration management, operational metadata tracking, and performance optimization. This layer lays the groundwork for secure, observable, and scalable analytics before any KPI or dashboard logic is executed.
________________________________________
### **📄 01_create_analytics_schema.sql**
Initializes the core analytics foundation by creating a dedicated analytics schema to isolate analytical workloads from transactional systems. Implements a centralized, configuration-driven framework for business rules, alert thresholds, customer segmentation parameters (CLV, RFM), and dashboard behavior, eliminating hard-coded logic across analytics queries.
The script also introduces reusable helper functions to standardize access to configuration values and reference dates, ensuring consistency across KPIs, alerts, and refresh workflows, while applying controlled permissions to support analyst-friendly yet secure access patterns.
________________________________________
### **📄 02_create_metadata_tables.sql**
Establishes the operational intelligence and governance layer of the analytics platform by creating comprehensive metadata and audit tables. This script functions as an internal data catalog, documenting all KPIs with ownership, business definitions, refresh frequency, and source lineage, while simultaneously enabling full auditability of analytics operations.
It captures execution logs, refresh histories, and data quality issues, providing deep visibility into pipeline health, data freshness, performance metrics, and validation failures. Built-in logging helper functions standardize how refresh jobs, KPI updates, and data quality checks are tracked, enabling enterprise-grade observability and troubleshooting.
________________________________________
### **📄 03_create_indexes.sql**
Implements a performance-focused indexing strategy across all core transactional and dimensional schemas to ensure analytics queries, dashboards, and alert evaluations execute efficiently at scale. Indexes are designed around real analytics access patterns, including date-based filtering, high-volume joins, status-driven conditions, and composite query paths.
The script finalizes performance tuning by updating table statistics, allowing the query planner to optimize execution plans. This ensures that complex KPI computations and dashboard refreshes run in seconds rather than minutes, supporting near real-time analytical use cases.
________________________________________
### **📁 02_data_quality**
**Purpose:**
Enforces data reliability and governance by validating source data across multiple quality dimensions before it is consumed by KPIs, alerts, and dashboards. This layer ensures that analytical outputs are trustworthy, explainable, and business-ready.
________________________________________
### **📄 data_quality_checks.sql**
Implements a comprehensive, automated data quality framework that validates transactional and dimensional data across five core dimensions: completeness, accuracy, consistency, timeliness, and uniqueness. The script defines modular validation views to detect missing values, invalid ranges, referential integrity violations, stale records, and potential duplicates across all major business domains.
All individual checks are consolidated into a unified reporting view, providing a single operational snapshot of data health with severity-based prioritization. A dedicated execution function orchestrates the full validation cycle, logs detected issues into governance tables, and records execution metadata for traceability and auditing.
By integrating data quality validation directly into the analytics pipeline, this module prevents corrupted or unreliable data from propagating into KPIs, alerts, and executive dashboards—mirroring enterprise-grade data governance practices used in production analytics platforms.
________________________________________
### **📁 03_kpi_queries**
**Purpose:**
Transforms validated transactional data into structured, decision-ready business KPIs. This layer models core retail metrics using reusable views, materialized views, and API-ready JSON outputs to power dashboards, alerts, and executive reporting.
________________________________________
### **📄 01_sales_analytics.sql**
Implements the core sales intelligence engine of the platform, delivering end-to-end visibility into revenue, orders, customers, and growth trends across daily, monthly, quarterly, and real-time horizons. The module combines granular daily metrics with pre-aggregated materialized views to support both operational monitoring and executive-level reporting.
Advanced analytical constructs such as DoD, MoM, QoQ, and YoY growth, moving averages, weekend vs weekday behavior, payment mode preferences, hourly demand patterns, and returns impact are modeled using window functions and time-series logic. JSON export functions expose curated KPI datasets for seamless dashboard and API consumption, while materialized views ensure high performance for frequently accessed insights.

| KPI                      | Type | Description                                                     |
| ------------------------ | ---- | --------------------------------------------------------------- |
| Monthly Sales Dashboard  | MV   | Month-over-Month and Year-over-Year growth with moving averages |
| Executive Summary        | MV   | High-level KPIs for leadership and executive decision-making    |
| Daily Sales Summary      | View | Day-level sales metrics with Day-over-Day growth                |
| Sales by Day of Week     | View | Performance comparison across weekdays                          |
| Payment Mode Analysis    | View | Revenue contribution by payment method                          |

<img width="1338" height="506" alt="Screenshot 2026-01-11 170102" src="https://github.com/user-attachments/assets/2a14eb7e-cf0b-4e90-88a0-5d46b06fc8c1" />

________________________________________
### **📄 02_customer_analytics.sql** 
Builds a comprehensive customer intelligence layer focused on lifetime value, behavioral segmentation, retention, and churn risk. The module calculates Customer Lifetime Value (CLV) using revenue, frequency, recency, and engagement signals, dynamically assigning value tiers driven by configurable business thresholds.
It applies RFM segmentation to classify customers into actionable behavioral cohorts, tracks cohort-based retention over time, and identifies high-value customers at risk of churn with prioritized intervention recommendations. Demographic, geographic, and acquisition vs retention views provide additional context for strategic marketing and growth planning. JSON exports make customer insights directly consumable by dashboards and downstream systems.

| KPI                     | Type | Description                                                                            |
| ----------------------- | ------------- | -------------------------------------------------------------------------------------- |
| Customer Lifetime Value | MV            | Calculates CLV and categorizes customers into Platinum, Gold, Silver, and Bronze tiers |
| RFM Analysis            | MV            | Segments customers based on Recency, Frequency, and Monetary value                     |
| Cohort Retention        | MV            | Tracks monthly customer retention by acquisition cohort                                |
| Churn Risk              | View          | Identifies high-value customers with elevated churn probability                        |

<img width="1340" height="541" alt="Screenshot 2026-01-11 170216" src="https://github.com/user-attachments/assets/93c68634-181e-4d56-bd54-e58d923ee5f5" />

________________________________________
### **📄 03_product_analytics.sql**
Delivers in-depth product and inventory analytics to identify revenue drivers, demand concentration, and stock efficiency across the catalog. The module ranks products by revenue and volume, performs ABC (Pareto) analysis to highlight top-contributing SKUs, and evaluates category and brand-level performance using market share and ranking logic.
Inventory turnover and velocity metrics translate sales behavior into actionable stock health indicators, flagging low stock, overstocked, dead stock, and out-of-stock scenarios. JSON export functions expose product, category, brand, ABC classification, and inventory status insights, enabling data-driven merchandising, pricing, and supply chain decisions.

| KPI                  | Type | Description                                      |
| -------------------- | ---- | ------------------------------------------------ |
| Top Products         | MV   | Products ranked by revenue and units sold        |
| ABC Analysis         | MV   | Pareto-based product classification (80/20 rule) |
| Category Performance | View | Category-wise sales and profitability metrics    |
| Inventory Turnover   | View | Inventory velocity and stock efficiency          |
| Brand Performance    | View | Revenue and demand by brand                      |
| Inventory Status     | View | Stock availability and risk indicators           |

<img width="1333" height="532" alt="Screenshot 2026-01-11 170258" src="https://github.com/user-attachments/assets/377dd930-cb66-4cd9-b1e2-805d3203dae3" />

________________________________________
### **📄 04_store_analytics.sql** 
Provides a comprehensive store-level performance framework by combining sales, expenses, staffing, and inventory data into a unified profitability and efficiency view. The module computes store-wise revenue, net profit, margin, revenue per employee, and operational rankings, categorizing stores into performance tiers to quickly identify top performers and underperformers.
Regional rollups enable geographic benchmarking across revenue, profit, workforce efficiency, and customer reach, while inventory health analysis highlights stock risks at the store level. Employee distribution metrics add an operational lens, linking payroll and staffing structure to financial outcomes. JSON exports make store, regional, inventory, and workforce insights directly consumable by dashboards and executive scorecards.

| KPI                    | Type | Description                                 |
| ---------------------- | ---- | ------------------------------------------- |
| Store Performance      | MV   | Store-level revenue, profit, and efficiency |
| Regional Performance   | View | Aggregated performance by region            |
| Store Inventory Status | View | Inventory health and stock risk by store    |
| Employee Distribution  | View | Workforce size and payroll by store         |

<img width="1331" height="530" alt="Screenshot 2026-01-11 170328" src="https://github.com/user-attachments/assets/6c1c145f-c0ac-4af2-bde3-61afedf652f9" />

________________________________________
### **📄 05_operations_analytics.sql**
Monitors end-to-end operational health across deliveries, returns, payments, and order fulfillment to ensure service reliability and SLA adherence. The module tracks on-time delivery rates, average delivery durations, courier performance, and delayed shipments to proactively surface logistics bottlenecks.
Return behavior is analyzed by category and reason to quantify refund impact, while payment trends highlight transaction volumes and growth by payment mode. An operations summary materialized view consolidates shipment, return, payment, and order status KPIs into a single operational snapshot. Actionable views and JSON exports enable real-time escalation of pending shipments, courier optimization, and executive-level monitoring of operational efficiency.

| KPI                  | Type | Description                                |
| -------------------- | ---- | ------------------------------------------ |
| Delivery Performance | View | SLA adherence, on-time delivery percentage |
| Courier Comparison   | View | Courier partner benchmarking and rankings  |
| Return Analysis      | View | Return rate and refund impact by category  |
| Payment Success Rate | View | Payment gateway reliability and trends     |
| Pending Shipments    | View | Actionable list of delayed or stuck orders |
| Operations Summary   | MV   | Consolidated operational KPIs snapshot     |

<img width="1342" height="582" alt="Screenshot 2026-01-11 170415" src="https://github.com/user-attachments/assets/45a4e4f3-7be5-49d1-9f05-521ac6960ffb" />

________________________________________
### **📄 06_marketing_analytics.sql** 
Evaluates marketing performance by linking campaign spend, customer engagement, and sales outcomes to quantify true return on investment. The module measures campaign-level ROI, conversion rates, cost efficiency, and revenue attribution across digital channels and promotions.
Channel performance analysis ranks acquisition efficiency by spend, clicks, and conversions, while promotion effectiveness ties discount strategies directly to order volume and revenue impact. Email engagement metrics capture funnel health through open and click-through rates. A centralized marketing ROI materialized view aggregates spend, conversions, and efficiency KPIs, with JSON exports enabling seamless integration into growth dashboards and performance reviews.

| KPI                     | Type | Description                                    |
| ----------------------- | ---- | ---------------------------------------------- |
| Campaign Performance    | View | ROI, CPA, conversion rate per campaign         |
| Channel Performance     | View | Ad spend efficiency by marketing channel       |
| Promotion Effectiveness | View | Revenue impact of discounts and promotions     |
| Email Engagement        | View | Open rate and click-through rate analysis      |
| Marketing ROI Summary   | MV   | Overall marketing spend and conversion metrics |

<img width="1323" height="532" alt="Screenshot 2026-01-11 170446" src="https://github.com/user-attachments/assets/ca12e1ed-d92e-4e60-bc36-1a7f38f30990" />

________________________________________
### **📁 04_alerts** 
Enables real-time business monitoring by continuously evaluating critical risk conditions across inventory, customers, revenue, fulfillment, and returns. This layer transforms analytics into action by surfacing high-impact issues before they escalate into revenue loss or customer churn.
________________________________________
 ## 🚨 Business Alerts

The analytics platform implements **six automated alert mechanisms** designed to proactively surface operational and business risks:

* **Critical Inventory Alert** – Identifies high-impact products where available stock falls below 10 units.
* **High-Value Customer Churn Alert** – Flags Platinum and Gold customers who have remained inactive for more than 60 days.
* **Revenue Anomaly Detection** – Triggers when daily revenue drops below 75% of the rolling 7-day average.
* **Shipment Delay Alert** – Highlights orders that have not been shipped within 3 days of order placement.
* **Elevated Return Rate Alert** – Detects product categories exhibiting return rates exceeding 15%.
* **Payment Mode Concentration Alert** – Warns when a single payment method contributes more than 70% of total transactions.
________________________________________
### **📁 05_refresh**
**Purpose:**
Bridges analytics computation with downstream consumption by automating refresh execution, JSON data exports, and operational logging in a repeatable, production-ready workflow.
________________________________________
### **📂 logs**
Maintains timestamped execution logs for all refresh and export jobs, enabling end-to-end traceability, failure diagnosis, and operational monitoring. Each run records refresh invocations, export outcomes, and database errors, supporting production-grade observability and post-incident analysis.
________________________________________
### **📄 export_all_json.sh**
Automates the final mile of the analytics pipeline by exporting fully refreshed KPIs, dashboards, and alert datasets into structured JSON files for frontend dashboards, APIs, or external reporting systems. The script orchestrates category-wise exports (Sales, Customers, Products, Stores, Operations, Marketing, and Alerts) using database-side JSON functions to ensure consistency and schema control.
The script optionally triggers a full analytics refresh before export, guaranteeing data freshness at the time of delivery. Execution status, failures, and database responses are captured in timestamped log files, providing traceability and auditability for every export run. This mirrors real-world data delivery workflows where analytics outputs are decoupled from visualization layers and served as portable, versioned data assets.
________________________________________
### **📄 refresh_all_analytics.sql — Controlled Materialized View Refresh**
Implements a centralized refresh orchestration mechanism that systematically updates all analytics materialized views in a defined dependency order. The module supports both standard and concurrent refresh modes, enabling low-latency updates without blocking read workloads when required.
Each refresh execution is instrumented with detailed operational logging, capturing batch identifiers, execution duration, row counts, and success or failure status at the individual view level. Refresh metadata is persisted to history and KPI metadata tables, providing visibility into data freshness, refresh performance trends, and operational reliability over time.
Shortcut refresh functions allow selective updates of sales, customer, or product analytics, supporting modular refresh strategies during incidents or partial data loads. This module mirrors real enterprise data pipeline orchestration patterns where observability, fault tolerance, and controlled execution are mandatory.
________________________________________
### **📁 06_dashboard — Analytics Consumption & Visualization Layer**
**Purpose:**
Transforms curated analytics outputs into a lightweight, decoupled dashboard layer by consuming pre-exported JSON datasets generated from the analytics engine. This folder represents the final presentation and consumption tier of the RetailMart Enterprise Analytics Platform.
________________________________________
### **📂 data**
Contains structured, domain-partitioned JSON datasets produced by the automated export pipeline. Each subfolder maps directly to a business domain (Sales, Customers, Products, Stores, Operations, Marketing, Alerts), ensuring clean separation of concerns and predictable data contracts for visualization and frontend logic.
These files act as analytics delivery artifacts, allowing dashboards to load insights without directly querying the database—mirroring real-world architectures where BI layers consume APIs or object storage instead of transactional systems.
Domain Coverage:
•	sales/ — Executive summaries, trends, seasonality, payment behavior, and time-based sales patterns
•	customers/ — CLV tiers, RFM segments, churn risk, demographics, and geographic distribution
•	products/ — Top products, category performance, ABC analysis, brand metrics, inventory health
•	stores/ — Store rankings, regional performance, inventory status, and workforce distribution
•	operations/ — Delivery SLA metrics, courier performance, returns analysis, pending shipments
•	marketing/ — Campaign ROI, channel efficiency, email engagement, overall marketing impact
•	alerts.json — Consolidated, real-time business alerts for proactive monitoring
________________________________________
### **📂 css**
Defines centralized styling rules for the dashboard UI, ensuring consistent layout, typography, and visual hierarchy across all analytical views while keeping presentation logic independent from data and business rules.
________________________________________
### **📂 js**
Houses JavaScript logic responsible for loading JSON datasets, binding analytics to visual components, and driving interactive behavior. This layer focuses purely on data consumption and rendering, keeping all business logic within the database layer.
________________________________________
### **📄 index.html** 
Serves as the primary entry point for the analytics dashboard, assembling domain-specific insights into a unified, browser-based reporting interface. The dashboard operates entirely on exported JSON data, demonstrating a scalable, low-latency alternative to live database connections.
________________________________________
### 🔧 Project Setup & Execution Guide

| Step | Phase                | Description                               | Command / Action                                                               |
| ---- | -------------------- | ----------------------------------------- | ------------------------------------------------------------------------------ |
| 1️⃣  | Database Setup       | Create analytics schema                   | `psql -U postgres -d retailmart -f 01_setup/01_create_analytics_schema.sql`    |
|      |                      | Create metadata & logging tables          | `psql -U postgres -d retailmart -f 01_setup/02_create_metadata_tables.sql`     |
|      |                      | Create performance indexes                | `psql -U postgres -d retailmart -f 01_setup/03_create_indexes.sql`             |
| 2️⃣  | Data Quality         | Run data validation checks                | `psql -U postgres -d retailmart -f 02_data_quality/data_quality_checks.sql`    |
| 3️⃣  | Sales Analytics      | Build sales KPIs & trends                 | `psql -U postgres -d retailmart -f 03_kpi_queries/01_sales_analytics.sql`      |
| 4️⃣  | Customer Analytics   | Generate CLV, RFM, churn insights         | `psql -U postgres -d retailmart -f 03_kpi_queries/02_customer_analytics.sql`   |
| 5️⃣  | Product Analytics    | Analyze products, inventory, ABC          | `psql -U postgres -d retailmart -f 03_kpi_queries/03_product_analytics.sql`    |
| 6️⃣  | Store Analytics      | Store-level revenue & efficiency          | `psql -U postgres -d retailmart -f 03_kpi_queries/04_store_analytics.sql`      |
| 7️⃣  | Operations Analytics | SLA, delivery, returns tracking           | `psql -U postgres -d retailmart -f 03_kpi_queries/05_operations_analytics.sql` |
| 8️⃣  | Marketing Analytics  | Campaign ROI & channel metrics            | `psql -U postgres -d retailmart -f 03_kpi_queries/06_marketing_analytics.sql`  |
| 9️⃣  | Business Alerts      | Enable proactive alerting rules           | `psql -U postgres -d retailmart -f 04_alerts/business_alerts.sql`              |
| 🔄   | Refresh Engine       | Refresh all materialized views            | `psql -U postgres -d retailmart -f 05_refresh/refresh_all_analytics.sql`       |
| 📤   | Data Export          | Grant execute permission to export script | `chmod +x 05_refresh/export_all_json.sh`                                       |
|      |                      | Export refreshed analytics to JSON        | `cd 05_refresh && ./export_all_json.sh --refresh`                              |
| 📊   | Dashboard            | Launch frontend dashboard                 | Open `06_dashboard/index.html` (or use Live Server)                            |

________________________________________
## 🖥️ Dashboard Capabilities

* **Seven Interactive Tabs** — Executive, Sales, Customers, Products, Stores, Operations, and Marketing views
* **Client-Side Caching** — Five-minute data cache to reduce reload latency and API calls
* **Robust Error Handling** — Graceful fallbacks to handle missing or delayed data sources
* **Responsive Layout** — Optimized for both desktop and mobile form factors
* **Auto-Refresh Support** — Optional scheduled data refresh for near real-time insights
________________________________________
## 📈 Performance Engineering

* **53 Optimized Indexes** on high-frequency query columns
* **Materialized Views** to precompute resource-intensive aggregations
* **Composite Index Strategies** for common access patterns
* **ANALYZE-Driven Statistics** to assist the PostgreSQL query planner
________________________________________
## 🎓 Key Learning Outcomes
This project reflects hands-on experience with:

* **Advanced SQL Development** — CTEs, window functions, and nested subqueries
* **Query Performance Optimization** using materialized views and indexing strategies
* **Scalable Schema Design** with normalization and separation of concerns
* **Data Quality Enforcement** through validation and consistency checks
* **End-to-End ETL Pipeline Construction**
* **JSON-Based Data Serving** for frontend and API consumption
* **Interactive Visualization Integration** using Chart.js
* **Production-Ready Deployment Practices** including automation and logging
________________________________________
## ▶️ End-to-End Execution Flow

Once the database setup, analytics modules, and automation scripts are in place, the platform runs as a complete analytics pipeline:

1. **Analytics Refresh**
   All materialized views are refreshed in the correct dependency order using the automated refresh functions.

2. **JSON Data Generation**
   The export script generates domain-wise JSON files (sales, customers, products, stores, operations, marketing, and alerts) from the refreshed analytics layer.

3. **Dashboard Consumption**
   The frontend dashboard loads these JSON files directly, rendering KPIs, trends, charts, and alerts across all tabs.

4. **Live Visualization**
   By opening the dashboard folder in a local server (e.g., VS Code Live Server), users can interact with a fully functional, responsive dashboard reflecting the latest data.

In summary, running the refresh and export scripts ensures that the analytics layer stays up to date, while the dashboard automatically consumes the latest JSON outputs to present real-time, decision-ready insights.













