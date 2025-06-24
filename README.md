# 📊 HDFC Financial Dashboard – Power BI Project

This project presents an interactive and insightful **Power BI dashboard** to analyze the **financial performance of HDFC**, based on a sample dataset. It covers key metrics such as **Income**, **Expenses**, **Expense Types**, and **Net Profitability**, along with comparisons between **Actuals vs Budget vs Forecast** scenarios.

---

## 📁 Files in this Repository

| File Name                               | Description                                      |
|----------------------------------------|--------------------------------------------------|
| `Financials Sample Data _ Randomized.xlsx` | Sample monthly financial dataset (raw input)    |
| `HDFC.pbix`                             | Final Power BI dashboard file                   |
| `Documentation.pdf` / `Documentation.md`| Step-by-step documentation of the entire project |
| `README.md`                             | Project summary and GitHub overview             |

---

## 🧠 Key Features of the Dashboard

- ✅ Dynamic KPIs: **Total Income**, **Total Expenses**, **Net Profit**, **Profit Margin %**
- 📊 Visuals:
  - Year-wise Profitability Trends
  - Actual vs Forecast vs Budget (Clustered Column)
  - Top Expense Types
  - Decomposition Tree (Interactive Drilldowns)
- 🧩 DAX Measures for contextual percentage metrics (Year/Month/BU)
- 🔍 Insight into Business Unit and Seasonal Trends

---

## 🧹 Data Cleaning & Transformation

1. **Unpivoted** Jan–Dec columns to create a normalized structure
2. **Categorized** months (Jan–Dec) for sorting
3. **Validated** column types (Amount → Numeric, Year → String)
4. Created a **long-format table** with `Month` and `Amount` columns

---

## 📐 DAX Measures Used

```dax
Net Profit = SUM(Financials[Amount])
Total Income = CALCULATE(SUM(Financials[Amount]), FILTER(Financials, Financials[Account] = "Revenue"))
Total Expenses = CALCULATE(SUM(Financials[Amount]), FILTER(Financials, Financials[Account] = "Expense"))
Profit Margin % = DIVIDE([Net Profit], [Total Income])
% of Net Profit by Year = DIVIDE([Net Profit], CALCULATE([Net Profit], ALLEXCEPT(Financials, Financials[Year])))
% of Net Profit by Month = DIVIDE([Net Profit], CALCULATE([Net Profit], ALLEXCEPT(Financials, Financials[Year], Financials[Month])))
% of Net Profit by BU = DIVIDE([Net Profit], CALCULATE([Net Profit], ALLEXCEPT(Financials, Financials[Year], Financials[Month], Financials[Businees Unit])))


Author
Aditya Mishra
PGPM – Business Analytics & Marketing
Great Lakes Institute of Management, Chennai
