# 🚗 Insurance Portfolio Risk & Profitability Analysis

A **Business Intelligence project** that simulates an **insurance company dataset**, analyzes **policy sales and claim behavior**, and builds an **interactive Power BI dashboard** to measure profitability and risk.

This project demonstrates **end-to-end data analytics workflow** including:

-   Data simulation using Python
    
-   Database modeling with SQL
    
-   Business analysis using analytical queries
    
-   Interactive dashboard creation using Power BI

# 🧠 Business Problem

Insurance companies must monitor **risk vs profitability**.

If claims exceed premium revenue, the company suffers losses.

This project simulates an **auto insurance portfolio** and answers key business questions:

-   How much premium revenue is generated?
    
-   What is the total claim cost?
    
-   Which policy tenure is the most risky?
    
-   What is the loss ratio across policies?
    
-   How do claims vary across months and years?

# 🛠 Tech Stack
![Power BI Dashboard](Tech_stack.jpg)

# ⚙️ Data Generation Logic (Python)

```
import pandas as pd
import numpy as np

# number of customers
n = 1_000_000

# customer ids
customer_ids = np.arange(1, n+1)

vehicle_ids = np.arange(1, n+1)

vehicle_value = 100000

# purchase dates evenly distributed
dates = pd.date_range("2024-01-01", "2024-12-31")
purchase_dates = np.tile(dates, int(np.ceil(n/len(dates))))[:n]

# tenure distribution
tenure_choices = [1,2,3,4]
tenure_prob = [0.2,0.3,0.4,0.1]

tenure = np.random.choice(tenure_choices, size=n, p=tenure_prob)

premium = tenure * 100

start_date = purchase_dates + pd.Timedelta(days=365)

end_date = start_date + pd.to_timedelta(tenure*365, unit="D")

df = pd.DataFrame({
    "Customer_ID":customer_ids,
    "Vehicle_ID":vehicle_ids,
    "Vehicle_Value":vehicle_value,
    "Premium":premium,
    "Policy_Purchase_Date":purchase_dates,
    "Policy_Start_Date":start_date,
    "Policy_End_Date":end_date,
    "Policy_Tenure":tenure
})

df.to_csv("policy_sales.csv",index=False)

```
