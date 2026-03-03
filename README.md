# Telco Customer Churn Segmentation & Retention Strategy Dashboard

## Overview
This project analyzes customer churn behavior for a telecom company and translates the analysis into a retention-focused business dashboard. Using PostgreSQL for data preparation and Power BI for visualization, the project identifies churn drivers, builds customer segments, defines risk cohorts, and recommends business actions to reduce churn and protect revenue.

## Problem Statement
Telecom businesses face revenue loss when customers discontinue service. The goal of this project was to:
- identify the key factors associated with churn,
- segment customers based on value and behavior,
- prioritize high-risk customer cohorts,
- estimate revenue at risk,
- and recommend retention actions to improve customer retention.

## Tools & Technologies
- **PostgreSQL**
- **pgAdmin 4**
- **Power BI**
- **DAX**
- **SQL**

## Dataset
- **Dataset:** IBM Telco Customer Churn
- **Records:** 7,043 customers
- **Domain:** Telecommunications / Customer Retention

## Project Workflow

### 1. Data Preparation (PostgreSQL)
- Imported raw telco churn data into PostgreSQL
- Created a staging table for initial CSV ingestion
- Cleaned and typed the dataset into a fact table
- Handled missing values in `TotalCharges`
- Created customer-level features such as:
  - tenure bands
  - value bands
  - add-on count
  - churn flag
  - age group proxy (Senior vs Non-senior)

### 2. Customer Segmentation
Developed rule-based customer segments such as:
- Loyal High-Value
- High-Value At-Risk
- New & Unsure
- Price-Sensitive
- Bundled & Stable
- Mainstream

### 3. Risk Cohort Creation
Built risk cohorts to identify the most vulnerable customer combinations:
- Fiber + Month-to-month + Electronic check
- Fiber + Month-to-month
- Month-to-month + Electronic check
- Month-to-month (other)
- Term contract

### 4. Targeting Logic
Created a targeting view using:
- segment churn rate
- monthly charges
- risk multiplier
- incentive cost
- priority score

This enabled prioritization of customers and cohorts for retention outreach.

### 5. Dashboard Development (Power BI)
Built a 3-page Power BI dashboard:

#### Page 1 — Executive Summary
- Total Customers
- Total Churned
- Churn Rate
- Revenue at Risk
- Churn by Contract
- Churn by Internet Service
- Churn by Payment Method
- Churn by Age Group

#### Page 2 — Segmentation & Targeting
- Segment performance overview
- Churn rate by segment
- Average monthly charges by segment
- Tenure band × value band heatmap
- Revenue-at-risk analysis

#### Page 3 — Retention Action Center
- Revenue at risk by risk cohort
- Churn composition by contract and payment method
- Revenue at risk by service and contract
- Key churn influencers

## Key Insights
- **Month-to-month customers** had the highest churn rate.
- **Electronic check** customers churned significantly more than customers using auto-pay methods.
- **Fiber optic** customers showed the highest churn among internet service groups.
- The highest-risk cohort was **Fiber + Month-to-month + Electronic check**.
- Revenue at risk was concentrated in a small number of high-risk customer cohorts.

## Business Recommendations
- Prioritize outreach to customers in the **Fiber + Month-to-month + Electronic check** cohort.
- Increase **autopay adoption** to reduce payment-related churn.
- Promote **12/24-month contract upgrades** for month-to-month customers.
- Use targeted incentives only for high priority-score cohorts to optimize retention spend.
- Provide service assurance and proactive support for high-value fiber customers.

## Repository Structure
```text
telco-churn-segmentation-powerbi/
│
├── README.md
├── Telco.pbix
├── data/
│   └── WA_Fn-UseC_-Telco-Customer-Churn.csv
│
├── sql/
│   ├── 01_create_staging_table
│   ├── 02_create_fact_telco
│   ├── 03_create_customer_360
│   ├── 04_create_segments
│   ├── 05_create_risk_cohorts
│   ├── 06_create_targeting_view
│   ├── 07_create_analysis_ready_view
│   └── 08_validation_queries
│
├── screenshots/
│   ├── page1_executive_summary.png
│   ├── page2_segmentation_targeting.png
│   └── page3_retention_action_center.png
