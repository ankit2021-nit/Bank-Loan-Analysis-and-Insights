# 📊 Bank Loan Analysis – End-to-End Data Analytics Project  

[![Tableau Dashboard](https://img.shields.io/badge/Dashboard-Tableau-blue)](https://public.tableau.com/app/profile/swapnil.mohanty/viz/BankLoanAnalysis_17591253726570/OVERVIEW)  
[![SQL](https://img.shields.io/badge/Database-SQL%20Server-lightgrey)](#-sql-analysis)  
[![Python](https://img.shields.io/badge/EDA-Python-orange)](#-python-eda)  
[![Tableau](https://img.shields.io/badge/Viz-Tableau-green)](#-tableau-visualizations)  

## 📌 Project Overview  
This project demonstrates an **end-to-end analytics pipeline** for **Bank Loan Data**, leveraging **SQL, Python, and Tableau** to extract insights into loan applications, repayments, portfolio health, and customer risk.  

It covers the full lifecycle of analytics:  
- Data ingestion & cleaning  
- SQL-driven KPI computation  
- Exploratory Data Analysis (EDA) in Python  
- Interactive dashboards in Tableau  

---

## 🗂 Dataset  
- **Source:** Financial Loan Dataset (`financial_loan.xlsx`)  
- **Rows:** ~38,500 loan records  
- **Columns:** 24 fields (Loan ID, State, Grade, Loan Amount, Interest Rate, DTI, Purpose, Loan Status, etc.)  
- **Granularity:** Loan-level transactional data  

Refer to [Terminologies.docx](Terminologies.docx) for detailed field descriptions.  

---

## 🏦 Domain Knowledge  
Banks evaluate loan portfolios based on:  
- **Risk assessment** (Good Loans vs. Bad Loans)  
- **Creditworthiness metrics** (Debt-to-Income ratio, Interest Rates)  
- **Cashflow tracking** (Funded Amount vs. Amount Received)  
- **Regulatory compliance & customer insights**  

For in-depth context, see [Domain Knowledge.docx](Domain Knowledge.docx).  

---

## ❓ Problem Statement  
The **Bank Loan Report** was structured into **3 Dashboards**:  

### 1️⃣ Summary Dashboard  
- KPIs:  
  - Total Loan Applications (MTD, MoM)  
  - Total Funded Amount (MTD, MoM)  
  - Total Amount Received (MTD, MoM)  
  - Avg. Interest Rate, Avg. Debt-to-Income (DTI)  
- Loan quality segmentation: **Good Loans vs. Bad Loans**  
- Loan Status Grid view  

### 2️⃣ Overview Dashboard  
- Monthly trends by issue date  
- Regional analysis by state (Map)  
- Loan term distribution (Donut)  
- Employment length impact (Bar)  
- Loan purpose breakdown (Bar)  
- Home ownership analysis (Tree Map)  

### 3️⃣ Details Dashboard  
- Full loan-level detail table for deep-dive analysis  

Refer to [Problem Statement.docx](Problem Statement.docx) or [Project Summary.pptx](Project Summary.pptx) for requirements.  

---

## 🛠 Tech Stack  
- **SQL Server** – Data import, cleaning, KPI calculation ([Query Doc.rtf](Query Doc.rtf), [SQLQuery1.sql](SQLQuery1.sql))  
- **Python (EDA in Jupyter Notebook)** – Trend detection, outlier handling, descriptive stats ([Bank Loan Analysis.ipynb](Bank Loan Analysis.ipynb))  
- **Tableau** – Interactive dashboards ([Bank Loan Analysis.twbx](Bank Loan Analysis.twbx))  

---

## 🔍 SQL Analysis  
Example KPIs implemented:  
```sql
-- Total Loan Applications
SELECT COUNT(id) AS Total_Applications
FROM bank_loan_data;

-- Good Loan Percentage
SELECT 
    (COUNT(CASE WHEN loan_status IN ('Fully Paid','Current') THEN id END) * 100.0) / COUNT(id) 
    AS Good_Loan_Percentage
FROM bank_loan_data;

-- Bad Loan Funded Amount
SELECT SUM(loan_amount) AS Bad_Loan_Funded
FROM bank_loan_data
WHERE loan_status = 'Charged Off';
```  
More queries available in [Query Doc.rtf](Query Doc.rtf).  

---

## 🐍 Python EDA  
Key analysis performed in `Bank Loan Analysis.ipynb`:  
- Descriptive statistics of loan portfolio  
- Distribution of loan purposes, grades, and terms  
- Outlier detection in Interest Rates & DTI  
- Correlation between income, loan amount, repayment  

---

## 📊 Tableau Visualizations  
🔗 **[View Dashboard](https://public.tableau.com/shared/DF9D5PSBR?:display_count=n&:origin=viz_share_link)**  

Dashboards provide interactive insights into:  
- Loan application trends  
- Regional lending activity  
- Loan quality (Good vs. Bad loans)  
- Borrower behavior (employment, income, home ownership)  

---

## 🚀 Key Insights  
- **86% of loans** are classified as *Good Loans*, while ~14% are *Bad Loans*.  
- Average **Interest Rate**: ~12% (higher for lower credit grades).  
- Majority of loans are taken for **Debt Consolidation** and **Credit Card Refinancing**.  
- Borrowers with **10+ years of employment** form the largest loan segment.  
- Regional disparities observed with **CA, NY, FL** leading in loan applications.  

---

## 📥 Repository Structure  
```
├── Dataset.xlsx                # Original dataset
├── financial_loan.xlsx         # Cleaned dataset
├── Bank Loan Analysis.ipynb    # Python EDA notebook
├── Bank Loan Analysis.twbx     # Tableau workbook
├── Query Doc.rtf               # SQL queries & results
├── SQLQuery1.sql               # SQL scripts
├── Domain Knowledge.docx       # Domain context
├── Problem Statement.docx      # Business requirements
├── Project Summary.pptx        # Presentation slides
├── Terminologies.docx          # Field definitions
└── README.md                   # Project documentation
```  

---

## 🏆 Skills Demonstrated  
- **SQL**: Data cleaning, aggregations, KPI calculations, performance validation  
- **Python (Pandas, Matplotlib/Seaborn)**: Exploratory Data Analysis, statistics, visualization  
- **Tableau**: Interactive dashboard design, KPI visualization, drill-down analytics  
- **Finance/Banking Analytics**: Credit risk assessment, portfolio monitoring, customer segmentation  

---

## 📌 Future Enhancements  
- Predictive modeling (Loan Default Prediction using ML)  
- Automated ETL pipeline (SQL → Python → Tableau refresh)  
- Deployment on a cloud-based BI platform  


