# Credit_Card_Financial_Dashboard
Power BI Dashboard
📊 Credit Card Financial Dashboard – Power BI Project

This project presents an interactive Credit Card Financial Dashboard built using Power BI, with data extracted and processed from SQL and advanced modeling done using DAX. The dashboard provides weekly and YTD insights into revenue, customer behavior, transaction trends, and credit card performance across regions and customer segments.

🚀 Project Overview

The goal of this project was to build a comprehensive weekly credit card analytics dashboard that enables stakeholders to monitor financial performance, customer engagement, and operational trends in real time.

🔍 Key Insights
Week-over-Week (WoW)

Revenue increased by 28.8%

Total transaction amount & count showed strong positive growth

Customer count increased (XX%)

Year-to-Date (YTD) Overview

Total Revenue: ₹55M

Total Interest Earned: ₹8M

Total Transaction Amount: ₹46M

Gender Contribution:

Male: ₹31M

Female: ₹26M

Card Performance: Blue & Silver cards contributed 93% of transactions

Top Regions: TX, NY & CA contributed 68%

Activation Rate: 57.5%

Delinquency Rate: 6.06%

🛠️ Tech Stack & Tools

SQL – Data extraction & cleaning

Power BI – Data modeling, visualization & dashboarding

DAX – Custom measures, WoW calculations, segmentation, KPIs

🧮 DAX Measures Used
Age Group Segmentation
AgeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[customer_age] < 30, "20-30",
 'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
 'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
 'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
 'public cust_detail'[customer_age] >= 60, "60+",
 "unknown"
)

Income Group Segmentation
IncomeGroup = SWITCH(
 TRUE(),
 'public cust_detail'[income] < 35000, "Low",
 'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
 'public cust_detail'[income] >= 70000, "High",
 "unknown"
)

Week Number
week_num2 = WEEKNUM('public cc_detail'[week_start_date])

Revenue Calculation
Revenue = 
'public cc_detail'[annual_fees] +
'public cc_detail'[total_trans_amt] +
'public cc_detail'[interest_earned]

Current Week Revenue
Current_week_Reveneue =
CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
  ALL('public cc_detail'),
  'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])
 )
)

Previous Week Revenue
Previous_week_Reveneue =
CALCULATE(
 SUM('public cc_detail'[Revenue]),
 FILTER(
  ALL('public cc_detail'),
  'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) - 1
 )
)

📈 Dashboard Features

KPI Cards (Revenue, Transactions, Customer Count)

WoW comparison metrics

YTD financial overview

Customer demographics (Age, Income, Gender)

Card category performance (Blue, Silver, Gold, etc.)

Regional breakdown

Delinquency & activation rates

Interactive slicers for deeper analysis

📂 Folder Structure
📁 Credit-Card-Financial-Dashboard
│── 📄 README.md
│── 📊 Dashboard.pbix
│── 🗃️ SQL Queries.sql
│── 📁 Datasets/
│── 📁 Screenshots/

📬 Contact

If you’d like to discuss this project or collaborate:
Ujjwal Modgill
📧 Email: [your email]
🔗 LinkedIn: [your profile link]
