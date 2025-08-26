# Bank Loan Analysis Dashboard

This project provides a comprehensive analysis of a bank's loan portfolio. It features a detailed dashboard that visualizes key lending metrics, risk assessment, and financial performance. The analysis is based on a dataset of loan records, and the insights are derived using SQL queries to calculate various Key Performance Indicators (KPIs).

## 📊 Dashboard Overview
The interactive dashboard provides a summary and detailed overview of the bank's lending activities. It is designed to help stakeholders understand portfolio health, identify trends, and make data-driven decisions. The dashboard is divided into two main sections:

- **Summary View**: Displays high-level KPIs such as total loan applications, total funded amount, total amount received, and average interest rates. It also includes month-to-date (MTD) and previous month-to-date (PMTD) comparisons to track recent performance.

- **Detailed Overview**: Offers deeper insights into the loan portfolio, with breakdowns by:
  - **Loan Status**: Analysis of 'Good Loans' (Current or Fully Paid) versus 'Bad Loans' (Charged Off).
  - **Monthly Trends**: Visualization of loan applications, funding, and payments over time.
  - **Geographical Distribution**: Loan data segmented by state.
  - **Borrower Characteristics**: Analysis based on loan term, employment length, home ownership, and loan purpose.

## 📈 Summary Dashboard
<img width="1842" height="795" alt="image" src="https://github.com/user-attachments/assets/c1498d05-fbc1-4d18-9ef4-409ebde13a57" />


## 📈 Overview Dashboard
<img width="1860" height="792" alt="image" src="https://github.com/user-attachments/assets/c2da219b-13e7-40ca-af0f-073fcdc0dd95" />



## 💾 Dataset
The analysis is based on the **bank_loan_data.csv** dataset. This file contains detailed information for each loan, including:

- `id`: A unique identifier for each loan application.
- `loan_amount`: The total amount of the loan funded.
- `term`: The duration of the loan (e.g., 36 months, 60 months).
- `int_rate`: The interest rate of the loan.
- `grade`, `sub_grade`: The assigned loan grade and sub-grade.
- `emp_length`: The employment length of the borrower.
- `home_ownership`: The home ownership status of the borrower (e.g., RENT, MORTGAGE, OWN).
- `annual_inc`: The annual income of the borrower.
- `verification_status`: The verification status of the borrower's income.
- `issue_d`: The date the loan was issued.
- `loan_status`: The current status of the loan (e.g., Fully Paid, Charged Off, Current).
- `purpose`: The stated purpose of the loan.
- `addr_state`: The state where the borrower resides.
- `dti`: The debt-to-income ratio of the borrower.

## 🛠️ Analysis & Methodology
The core of the analysis was performed using SQL queries to extract meaningful insights from the dataset. The key metrics and their corresponding queries are detailed below.

### Key Performance Indicators (KPIs)
**Total Loan Applications:**
```sql
SELECT COUNT(id) AS Total_Applications FROM bank_loan_data;
```

**Total Funded Amount:**
```sql
SELECT SUM(loan_amount) AS Total_Funded_Amount FROM bank_loan_data;
```

**Total Amount Received:**
```sql
SELECT SUM(total_payment) AS Total_Amount_Collected FROM bank_loan_data;
```

**Average Interest Rate:**
```sql
SELECT AVG(int_rate) * 100 AS Avg_Int_Rate FROM bank_loan_data;
```

**Average Debt-to-Income (DTI):**
```sql
SELECT AVG(dti) * 100 AS Avg_DTI FROM bank_loan_data;
```

### Loan Portfolio Health
**Good Loan vs. Bad Loan Analysis**: Loans were segmented based on their `loan_status`. 'Fully Paid' and 'Current' loans were classified as 'Good Loans', while 'Charged Off' loans were classified as 'Bad Loans'.

```sql
-- Good Loan Percentage
SELECT (COUNT(CASE WHEN loan_status IN ('Fully Paid', 'Current') THEN id END) * 100.0) / COUNT(id) AS Good_Loan_Percentage 
FROM bank_loan_data;

-- Bad Loan Percentage
SELECT (COUNT(CASE WHEN loan_status = 'Charged Off' THEN id END) * 100.0) / COUNT(id) AS Bad_Loan_Percentage 
FROM bank_loan_data;
```

### Detailed Breakdowns
The dashboard provides further analysis by segmenting the data based on various dimensions such as `loan_status`, `MONTH(issue_date)`, `addr_state`, `term`, `emp_length`, `purpose`, and `home_ownership`.

## 🚀 How to Use
1. Clone the repository:
```bash
git clone https://github.com/your-username/bank-loan-analysis.git
```

2. Explore the data: The **bank_loan_data.csv** file is available for your own analysis.

3. Review the queries: The **query_document.pdf** contains all the SQL queries used for the dashboard's KPIs.

4. View the dashboard: The project includes a **Power BI** or **Tableau** file (**DATA_ANALYSIS_DASHBOARD.xlsx**) that you can open to view the interactive dashboard.

## 🤝 Contributing
Contributions are welcome! If you have suggestions for improving the analysis or adding new features to the dashboard, please feel free to fork the repository and submit a pull request.
