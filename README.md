# Full-Stack Business Intelligence (BI) - Retail Sales Analytics

## Executive Summary

This project simulates a real-world Business Intelligence (BI) initiative for a mid-sized retail organization struggling with fragmented reporting across ERP and CRM systems. Due to siloed data and inconsistent KPI definitions, leadership lacked a reliable, unified view of sales performance, customer behavior, and product profitability.
The solution delivers an end-to-end BI framework that integrates disparate data sources into a centralized data warehouse (Medallion Architecture in SQL Server), enables consistent KPI measurement, and supports decision-making through structured SQL-based analysis and role-focused Power BI reporting. The project demonstrates how sound BI architecture, combined with business-oriented analytics, can transform raw operational data into actionable insights for executives, marketing teams, and product stakeholders.

---

## Table of Contents

- [Problem Statement and Strategic Context](#problem-statement-and-strategic-context)
- [Business Objectives and Success Criteria](#business-objectives-and-success-criteria)
- [Solution Approach](#solution-approach)
- [Phase 1: Data Foundation and Integration](#phase-1-data-foundation-and-integration)
- [Phase 2: Business Analysis and Analytical Insights (SQL-Based)](#phase-2-business-analysis-and-analytical-insights-sql-based)
- [Phase 3: Reporting, Insights and Decision Enablement (Power BI)](#phase-3-reporting-insights-and-decision-enablement-power-bi)
- [KPIs and Business Value Alignment](#kpis-and-business-value-alignment)
- [Estimated Benefits and Expected Outcomes](#estimated-benefits-and-expected-outcomes)
- [Limitations, Constraints and Design Trade-offs](#limitations-constraints-and-design-tradeoffs)
- [Repository Structure](#repository-structure)
- [Future Enhancements Opportunities](#future-enhancements-opportunities)
- [Key Deliverables and Repository Navigation](#key-deliverables-and-repository-structure)

---

## Problem Statement and Strategic Context

The organization operates with multiple transactional systems—ERP for product and order data and CRM for customer information—resulting in fragmented reporting and inconsistent KPI calculations across departments. Teams relied heavily on manual data extraction and spreadsheet-based reporting, increasing the risk of errors and misaligned interpretations.
Leadership lacked timely visibility into critical questions such as revenue drivers, customer retention trends, and product-level profitability. Different teams interpreted metrics differently, which slowed decision-making and increased the risk of acting on incomplete or conflicting information.
From a strategic standpoint, the organization needed a centralized, trusted data foundation that could support consistent reporting, reduce manual effort, and enable stakeholders to focus on insights rather than data reconciliation.

---

## Business Objectives and Success Criteria

**Business Objectives**
- Establish a single, trusted analytical foundation for sales, customer, and product data.
- Enable consistent KPI definitions across leadership, marketing, and product teams.
- Improve decision-making speed and confidence by reducing reliance on manual reporting.
- Support analysis of revenue quality, customer retention, and pricing effectiveness.

**Success Criteria**
- KPIs such as Revenue, AOV, Orders, and Profit are calculated consistently from a centralized data layer.
- Business questions can be answered through SQL-based analysis without ad-hoc data preparation.
- Executives and analysts can explore insights independently using governed Power BI reports.
- Reporting processes are repeatable, auditable, and refreshable without manual intervention.

---

## Solution Approach (High-Level)

To address the fragmented reporting landscape, the solution followed an end-to-end Business Intelligence approach that aligned business needs with a scalable technical design.
The project was structured into three logical phases to mirror how enterprise BI initiatives are typically delivered. First, a centralized data foundation was established to integrate ERP and CRM data into a consistent, business-ready structure. Next, analytical exploration was performed to uncover performance drivers and validate key business hypotheses. Finally, insights were operationalized through dashboards designed for different stakeholder groups. Throughout the solution, emphasis was placed on:

- Translating business questions into measurable KPIs
- Designing data structures that reflect how the business operates
- Ensuring repeatability through automated data refreshes
- Delivering insights in a format that supports decision-making, not just reporting

This phased approach ensured that technical implementation remained directly tied to business outcomes, while also allowing each stage to build logically on the previous one.

---

## Phase 1: Data Foundation and Integration

The first phase focused on establishing a reliable data foundation to eliminate reporting inconsistencies caused by siloed ERP and CRM systems. From a business perspective, the primary challenge was the absence of a single source of truth. Sales, customer, and product data existed across multiple systems with varying definitions, formats, and levels of quality. This made it difficult for stakeholders to trust KPIs such as revenue, AOV, and customer performance.

To address this, a centralized data warehouse was designed in SQL Server using a Medallion Architecture (Bronze, Silver, Gold). Raw ERP and CRM data was ingested into the Bronze layer, standardized and enriched in the Silver layer, and modeled into business-ready fact and dimension views in the Gold layer. This ensured consistent definitions for customers, products, and transactions across all downstream reporting. Business rules such as customer segmentation, product categorization, and date handling were applied during transformation to reflect how the organization actually operates. Data quality issues like duplicates, missing values, and inconsistent codes were resolved early to prevent flawed insights later in the reporting lifecycle.

To support operational reporting needs, data refresh processes were automated using stored procedures and scheduling logic, ensuring that updated data could be delivered without manual intervention.

![Data Warehouse Architecture Diagram](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/blob/main/docs/data_architecture.drawio.png)

*This diagram illustrates the full Medallion Architecture (Bronze → Silver → Gold) and how data flows across layers in SQL Server. The architecture shows how fragmented ERP and CRM data was transformed into a single, business-ready source of truth powering analytics and executive reporting.*

### Outcome of Phase 1
A trusted, reusable data foundation that supports consistent KPI reporting, reduces manual reconciliation, and enables faster analysis across teams.

---

## Phase 2: Business Analysis and Analytical Insights (SQL-Based)

With a trusted data foundation in place, the second phase focused on converting integrated data into actionable business insights. Using the Gold layer as the analytical source, SQL was used to perform exploratory and diagnostic analysis across sales, customers, and products. The objective was not only to report what happened, but to understand why performance shifted and where intervention was required. Key analyses included revenue and order trends over time, customer contribution analysis, retention behavior, and product-level profitability. Metrics such as Average Order Value (AOV), revenue per customer, order frequency, and category-level performance were evaluated to assess both growth quality and sustainability.

One of the most critical insights uncovered was that while order volume increased significantly year-over-year, AOV declined sharply. Further analysis showed that new customers accounted for most transactions but contributed disproportionately less revenue, indicating a retention and pricing challenge rather than healthy growth. Throughout this phase, emphasis was placed on interpreting metrics in business context. High volume metrics were deliberately evaluated alongside revenue contribution to avoid misleading conclusions. This approach mirrors how business analysts validate insights before presenting them to leadership.

### Outcome of Phase 2

Clear identification of revenue quality issues, customer retention risks, and pricing inefficiencies, forming a solid analytical basis for targeted business actions and strategic discussions.

---

## Phase 3: Reporting, Insights and Decision Enablement (Power BI)

### Objective

Translate business-ready data from the Gold layer into intuitive, self-service dashboards that enable leadership and functional teams to monitor performance, identify risks, and make informed decisions without relying on ad-hoc SQL queries.

### Approach

Power BI was connected directly to the Gold layer of the SQL data warehouse, ensuring that all reports were driven by a single, governed source of truth. The reporting layer was designed around user personas, not charts, so that each dashboard answered a specific set of business questions relevant to its audience. To simulate a production-like BI environment, scheduled refresh was enabled using Power BI Service and an On-Premises Gateway, ensuring dashboards stayed aligned with upstream data updates.

Three report pages were designed, each aligned to a specific business persona and decision context.

### Executive Overview

![Executive Overview](https://github.com/nitinskunigal/Full-Stack-Business-Intelligence-Project-for-Retail-Sales/blob/main/docs/PBI%20-%20Executive%20Overview.png)

**Purpose:**
Provide leadership with a consolidated view of business performance and early warning signals.

**What it enables:**
- Monitor core KPIs such as Revenue, Orders, and Average Order Value over time
- Identify value-driven vs volume-driven growth patterns
- Compare performance across product categories and time periods

**Business interpretation:**
While overall revenue and order volumes showed strong growth, declining AOV highlighted a potential erosion in order quality. This insight helps leadership balance growth initiatives with profitability considerations.

**Decision support:**
- Evaluate pricing and bundling strategies
- Prioritize high-margin product segments
- Align growth targets with value realization

### Customer View

![Customer View](https://github.com/nitinskunigal/Full-Stack-Business-Intelligence-Project-for-Retail-Sales/blob/main/docs/PBI%20-%20Customer%20View.png)

**Purpose:**
Enable marketing and customer teams to understand customer behavior, retention dynamics, and value contribution.

**What it enables:**
- Segment customers by contribution and engagement
- Track new vs repeat customer behavior
- Identify early indicators of retention risk

**Business interpretation:**
A large share of orders came from new customers, but repeat customers contributed disproportionately higher revenue. This pointed toward retention as a key lever for sustainable growth.

**Decision support:**
- Design targeted retention and loyalty initiatives
- Allocate marketing spend more effectively
- Shift focus from acquisition-only to lifecycle value optimization

### Product Drillthrough View

![Product Drillthrough View](https://github.com/nitinskunigal/Full-Stack-Business-Intelligence-Project-for-Retail-Sales/blob/main/docs/PBI%20-%20Product%20Drillthrough%20View.png)

**Purpose:**
Support product and merchandising teams with deeper SKU-level performance insights.

**What it enables:**
- Analyze product-level revenue and profitability
- Simulate pricing changes using What-If scenarios
- Detect underperforming products and margin risks

**Business interpretation:**
Some high-volume products underperformed on profitability, while select SKUs showed strong margin potential with minor pricing adjustments.

**Decision support:**
- Optimize pricing without sacrificing volume
- Rationalize product assortment
- Support data-backed merchandising decisions

### Outcome of Phase 3

This phase demonstrated how a well-designed BI layer can scale insights across the organization, reduce dependency on manual reporting, and empower non-technical stakeholders to make data-informed decisions independently. [Access Live Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNDdlNTViNmItZDZkNC00N2FkLWE2N2EtYzdjOWZkOGIwNTRiIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9)

---

## KPIs and Business Value Alignment

The KPIs used in this project were defined based on stakeholder needs and validated through SQL-based analysis before being surfaced in dashboards, ensuring analytical consistency and governance.
Key KPIs included:

- Revenue & YoY Growth – Assess overall business performance and growth sustainability.
- Average Order Value (AOV) – Evaluate revenue quality beyond transaction volume.
- Orders & Customer Count – Understand demand drivers and customer acquisition patterns.
- Product-Level Profitability – Identify high- and low-margin products for pricing decisions.

Each KPI directly supports business decisions related to pricing strategy, customer retention, and product portfolio optimization.

---

## Estimated Benefits and Expected Outcomes

Although this project was executed in a simulated environment, the solution reflects outcomes that organizations typically expect from a well-designed business intelligence initiative.

**Operational Benefits**
- Reduced manual reporting effort through centralized, automated data preparation.
- Improved consistency in KPI reporting across departments.

**Analytical Benefits**
- Faster identification of revenue trends, retention gaps, and pricing inefficiencies.
- Improved confidence in insights through standardized data modeling and validation.

**Strategic Benefits**
- Enhanced visibility into growth quality, not just growth volume.
- Better-informed pricing and retention strategies driven by data-backed insights.
- Stronger alignment between leadership decisions and underlying business performance.

---

## Limitations, Constraints & Design Trade-offs

This project was designed to balance realism, technical feasibility, and business value within practical constraints. The following limitations and trade-offs reflect conscious design decisions rather than oversights.

- **ETL Orchestration**: SQL Server Express does not support SQL Server Agent, so Windows Task Scheduler was used to simulate automated ETL execution. This approach reflects a realistic workaround often used in proof-of-concept or local BI environments.
- **Tooling Choices**: SSIS was not used since the data sources were flat files and SQL-based transformations provided sufficient transparency and control.
- **Platform Constraints**: Microsoft Fabric was not implemented due to environment access limitations; however, the architectural principles applied are directly transferable to cloud-based BI platforms.
- **Security & Governance Scope**: Row-Level Security (RLS) and advanced access control were not implemented, as the project focused on analytics design rather than enterprise governance. While not in scope, the project acknowledges where RLS would be required in multi-team or role-based reporting environments.
- **Historical Dataset Constraints**: The dataset spans historical periods and does not include real-time or streaming data. This limits operational use cases but remains sufficient for strategic, trend-based, and performance analysis scenarios.

These trade-offs do not weaken the solution’s design. Instead, they demonstrate that strong BI principles i.e., data modeling, governance, and business alignment, remain effective regardless of tooling constraints.

---

## Repository Structure

```
📁 data-warehouse-and-analytics-project/
├── 📁 datasets/                            # Raw datasets used for the project (ERP and CRM data)

├── 📁 docs/                                # Project documentation and architecture details
│   ├── 📄 data_architecture.drawio           # High-level project architecture (Bronze, Silver, Gold)
│   ├── 📄 data_catalog_source_system.md      # Captures essential metadata of source systems
│   ├── 📄 data_catalog_source_system.xlx     # Data Catalog in Excel sheet format
│   ├── 📄 data_cleaning_transformation.md    # Outlines the key data cleaning and transformation techniques
│   ├── 📄 data_dictionary.md                 # Provides detailed metadata for each column in the business-ready tables
│   ├── 📄 data_flow.drawio                   # Visual representation of data flow across layers
│   ├── 📄 data_flow_tasks.drawio             # Flow of tasks in each layer — analyzing, coding, validating, documenting
│   ├── 📄 data_integration.drawio            # Visual representation that depicts how Source Tables are connected
│   ├── 📄 data_layer_specifications.drawio   # Summarizes the objectives, transformations, and targets of each layer
│   ├── 📄 data_model.drawio                  # Data model design (e.g., star schema)
│   ├── 📄 etl_methods.md                     # Brief explanation of ETL strategy and methods used in this project
│   ├── 📄 etl_mind_map.png                   # Mind map showing the holistic understanding of ETL
│   └── 📄 naming_conventions.md              # Consistent naming guidelines for tables, columns, and files
│   ├── 📄 project_presentation.pdf           # Presentation deck related to this project

├── 📁 scripts/                             # All SQL-based work divided into two main tracks
│
│   ├── 📁 data_warehouse/                  # Scripts for building the data warehouse
│   │   ├── 📁 bronze/                        # Scripts for extracting and loading (full load) raw data
│   │   ├── 📁 silver/                        # Scripts for cleaning and transforming data
│   │   └── 📁 gold/                          # Scipts for creating analytical models (views and data models)
│
│   └── 📁 eda_analytics/                   # Scripts for EDA and advanced data (business) analytics

├── 📁 tests/                               # QA scripts for verifying integrity and logic of gold and silver layers

├── 📄 README.md                            # Project overview and instructions
```

---

> **Note on Historical Data**:  
> While the dataset used in this project spans from 2011 to 2014, it was selected for its realistic structure and complexity. This allowed for a robust simulation of real-world business scenarios including data modeling, segmentation, and KPI analysis.  
> 
> The **recommendations provided** are not intended for tactical execution but to demonstrate how an analyst would draw insights and inform strategy in a production environment.

---

## Future Enhancements Opportunities

In a scaled enterprise or cloud-based environment, this solution could be extended through:

- Migration to Microsoft Fabric or a cloud-native data platform for managed orchestration and scalability.
- Implementation of incremental loading or Change Data Capture (CDC) to improve refresh efficiency.
- Introduction of Row-Level Security (RLS) to support role-based data access across departments.
- Expansion of analytical use cases such as cohort analysis, forecasting, or customer lifetime value modeling.

---

## Key Deliverables and Repository Navigation

- A fully functional, SQL Server-based **full-stack BI solution** following industry-standard **layered Medallion Architecture**

- Clean and reusable **[SQL scripts](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/tree/main/scripts)** for analytics

- **[QA Scripts](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/tree/main/tests)** for Silver and Gold Layers

- **[Documentation](https://github.com/nitinskunigal/SQL-Data-Warehouse-and-Analytics-Project/tree/main/docs)** for data architecture diagrams, ETL flow, data model, data catalog, data layer specifications, etc.

- **[Power BI Dashboards](https://app.powerbi.com/view?r=eyJrIjoiNDdlNTViNmItZDZkNC00N2FkLWE2N2EtYzdjOWZkOGIwNTRiIiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9)**, shared online through Power BI Service

- **[Video Walkthrough](https://www.youtube.com/watch?v=Kspob_lGIaA&t=429s)** of this Project

- **[Presentation Deck](https://github.com/nitinskunigal/Full-Stack-Business-Intelligence-Project-for-Retail-Sales/blob/main/docs/project_presentation.pdf)**
