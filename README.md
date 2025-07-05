#  Palmora Group HR-Analysis


# 📊 Palmoria Group Employee Insights & Bonus Dashboard

This project analyzes employee data for Palmoria Group to answer critical business questions using Power BI. It includes performance reviews, gender equity, pay band analysis, and bonus allocations.

---

## 🔍 Case Questions Addressed

### ✅ 1. Gender Distribution in the Organization
- Analyzed gender spread across **regions and departments**
- Used pie chart, stacked bar, and matrix visuals
- Insight: Gender representation varies significantly by region

### ✅ 2. Rating Insights Based on Gender
- Compared average ratings by gender using bar charts
- Insight: Identified if there's bias or performance imbalance

### ✅ 3. Salary Structure & Gender Pay Gap
- Created **average salary by gender and region**
- Built a **Gender Pay Gap (%)** measure
- Insight: Certain departments/regions showed notable disparities

### ✅ 4. Salary Band Compliance & Distribution
- Grouped salaries into **$10K bands**
- Checked manufacturing compliance for minimum $90,000
- Visualized pay band spread by region using histogram & matrix

### ✅ 5. Bonus Allocation Based on Performance
- Mapped ratings + department to bonus % via LOOKUPVALUE
- Calculated:
  - Bonus Amount
  - Total Pay (Salary + Bonus)
  - Total Bonus Paid by Region and Company-wide

---

## 📁 File Structure

```
Palmoria-Dashboard/
│
├── data/
│   ├── Palmoria Group emp-data.csv
│   ├── Palmoria Group Bonus Rules.xlsx
│
├── visuals/
│   ├── Palmoria_Bonus_Dashboard_Visual.png
│
├── Palmoria_Bonus_Allocation_Dashboard.xlsx
├── README.md
```

---

## 📊 Power BI Features Used

- Custom DAX: `Bonus %`, `Bonus Amount`, `Gender Pay Gap`
- Relationships between employee data and bonus rules
- Matrix, Card, Column, Pie, and Table visuals
- Slicers: Region, Gender, Department, Rating

---

## ✅ Business Insights

- Bonus costs are highest in [Region]
- Gender pay gap exists in [Department]
- Some manufacturing staff fall below regulatory pay
- Employees with "Very Good" ratings received up to 10% bonuses

---

## 💡 Future Enhancements

- Add Year-over-Year bonus trend analysis
- Incorporate attendance or performance weight
- Automate compliance flag for salaries below threshold

---

## 🛠 Tools

- Power BI Desktop
- Excel (for preprocessing)
- GitHub (for version control & documentation)

---

## 🙋‍♂️ Author

Built by [Your Name] as part of a Power BI case study analysis.
