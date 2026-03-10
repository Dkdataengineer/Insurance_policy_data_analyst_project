🚗 Insurance Portfolio Risk & Profitability Analysis

A Business Intelligence project that simulates an insurance company dataset, analyzes policy sales and claim behavior, and builds an interactive Power BI dashboard to measure profitability and risk.

This project demonstrates end-to-end data analytics workflow including:

Data simulation using Python

Database modeling with SQL

Business analysis using analytical queries

Interactive dashboard creation using Power BI



🧠 Business Problem

Insurance companies must monitor risk vs profitability.

If claims exceed premium revenue, the company suffers losses.

This project simulates an auto insurance portfolio and answers key business questions:

How much premium revenue is generated?

What is the total claim cost?

Which policy tenure is the most risky?

What is the loss ratio across policies?

How do claims vary across months and years?

🗂 Project Structure
zopper-insurance-analysis
│
├── data
│   ├── policy_sales.csv
│   └── claims.csv
│
├── notebooks
│   └── data_generation.ipynb
│
├── sql
│   └── analysis_queries.sql
│
├── dashboard
│   └── insurance_dashboard.pbix
│
└── README.md
🛠 Tech Stack
Task	Tool
Data Generation	Python (Pandas, NumPy)
Data Storage	SQL (PostgreSQL / SQL Server)
Data Analysis	SQL
Data Visualization	Power BI
Dataset Size	1,000,000 records
📁 Dataset Overview

Two datasets were generated to simulate real insurance data.

1️⃣ Policy Sales Dataset

Represents car insurance policies sold in 2024.

Each row represents one policy.

Column	Description
Customer_ID	Unique customer identifier
Vehicle_ID	Unique vehicle identifier
Vehicle_Value	Fixed vehicle value (₹100000)
Premium	₹100 × policy tenure
Policy_Purchase_Date	Vehicle purchase date
Policy_Start_Date	Policy starts after 365 days
Policy_End_Date	Policy end date
Policy_Tenure	1,2,3,4 years

Total Records: 1,000,000

2️⃣ Claims Dataset

Represents insurance claims filed by customers.

Column	Description
Claim_ID	Unique claim identifier
Customer_ID	Customer who filed claim
Vehicle_ID	Vehicle associated with claim
Claim_Amount	10% of vehicle value
Claim_Date	Date of claim
Claim_Type	1 = First claim, 2 = Second claim
⚙️ Data Generation (Python)

The dataset was generated using Python Pandas and NumPy to simulate realistic insurance data.

Key features of the simulation:

1 million policies generated

Policy tenure distributed as

20% → 1 year

30% → 2 years

40% → 3 years

10% → 4 years

Claims generated using defined probability rules

Claim Rules

Claims in 2025

Vehicles purchased on

7th

14th

21st

28th

30% of these vehicles file claims

Claims in 2026

Only 4-year policies

10% claim probability

Claim dates between Jan 1 – Feb 28

🗄 SQL Data Model

Two tables were created in the database.

Policy Table
CREATE TABLE policy_sales (
customer_id INT,
vehicle_id INT,
vehicle_value INT,
premium INT,
policy_purchase_date DATE,
policy_start_date DATE,
policy_end_date DATE,
policy_tenure INT
);
Claims Table
CREATE TABLE claims (
claim_id INT,
customer_id INT,
vehicle_id INT,
claim_amount INT,
claim_date DATE,
claim_type INT
);
📊 Analytical Queries
1️⃣ Total Premium Revenue
SELECT SUM(premium) AS total_premium
FROM policy_sales;
2️⃣ Claim Cost by Month
SELECT 
YEAR(claim_date) AS year,
MONTH(claim_date) AS month,
SUM(claim_amount) AS total_claim_cost
FROM claims
GROUP BY YEAR(claim_date), MONTH(claim_date)
ORDER BY year, month;
3️⃣ Claim Ratio by Policy Tenure
SELECT
p.policy_tenure,
SUM(c.claim_amount) / SUM(p.premium) AS claim_ratio
FROM policy_sales p
LEFT JOIN claims c
ON p.vehicle_id = c.vehicle_id
GROUP BY p.policy_tenure;
4️⃣ Claim Ratio by Sales Month
SELECT
MONTH(policy_purchase_date) AS sale_month,
SUM(c.claim_amount) / SUM(premium) AS ratio
FROM policy_sales p
LEFT JOIN claims c
ON p.vehicle_id = c.vehicle_id
GROUP BY MONTH(policy_purchase_date);

📈 Power BI Dashboard

The dashboard provides key business KPIs:

KPI Cards

Total Premium → 240M

Total Claims → 493M

Loss Ratio → 2.06

Total Policies → 1M

Visualizations

Claim Amount by Month

Claim Amount by Year

Claims by Policy Tenure

Claims by Claim Type

Customer Distribution by Policy Tenure

📊 Key Insights

3-year policies generated the highest claims

Claims peaked during early months of the year

Loss ratio indicates claims exceed premium revenue

Policy tenure plays a major role in claim probability

🚀 Skills Demonstrated

This project highlights skills required for Data Analyst / Business Intelligence roles:

✔ Data Simulation
✔ Large Dataset Handling
✔ SQL Analytical Queries
✔ Business KPI Design
✔ Data Visualization
✔ Dashboard Design
✔ Insurance Risk Analysis
