#  Palmora Group HR-Analysis


# 📊 Palmoria Group Employee Insights & Bonus Dashboard

This project analyzes employee data for Palmoria Group to answer critical business questions using Power BI. It includes performance reviews, gender equity, pay band analysis, and bonus allocations.

---
![Screenshot 2025-07-05 160355](https://github.com/user-attachments/assets/c78ab6af-3eec-4506-9822-ffbf03f6d92d)


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
![Screenshot 2025-07-05 160255](https://github.com/user-attachments/assets/34a405ec-c11a-403e-a213-99243133b023)


---

## 🧮 DAX Expressions Used

```dax
Gender Pay Gap = 
VAR MaleAvg = CALCULATE(AVERAGE('Palmoria Group emp-data'[Salary]), 'Palmoria Group emp-data'[Gender] = "Male")
VAR FemaleAvg = CALCULATE(AVERAGE('Palmoria Group emp-data'[Salary]), 'Palmoria Group emp-data'[Gender] = "Female")
RETURN DIVIDE(MaleAvg - FemaleAvg, MaleAvg, 0)

Salary Band = 
VAR band = FLOOR('Palmoria Group emp-data'[Salary], 10000)
RETURN FORMAT(band, "$#,##0") & " - " & FORMAT(band + 9999, "$#,##0")

Manufacturing Below Threshold = 
CALCULATE(
    COUNTROWS('Palmoria Group emp-data'),
    FILTER(
        'Palmoria Group emp-data',
        'Palmoria Group emp-data'[Department] = "Manufacturing" &&
        'Palmoria Group emp-data'[Salary] < 90000
    )
)

Bonus % (Based on Rating & Department) = 
SWITCH(
    TRUE(),
    'Palmoria Group emp-data'[Rating] = "Very Poor", LOOKUPVALUE('Bonus Rules'[Very Poor], 'Bonus Rules'[Department], 'Palmoria Group emp-data'[Department]),
    'Palmoria Group emp-data'[Rating] = "Poor", LOOKUPVALUE('Bonus Rules'[Poor], 'Bonus Rules'[Department], 'Palmoria Group emp-data'[Department]),
    'Palmoria Group emp-data'[Rating] = "Average", LOOKUPVALUE('Bonus Rules'[Average], 'Bonus Rules'[Department], 'Palmoria Group emp-data'[Department]),
    'Palmoria Group emp-data'[Rating] = "Good", LOOKUPVALUE('Bonus Rules'[Good], 'Bonus Rules'[Department], 'Palmoria Group emp-data'[Department]),
    'Palmoria Group emp-data'[Rating] = "Very Good", LOOKUPVALUE('Bonus Rules'[Very Good], 'Bonus Rules'[Department], 'Palmoria Group emp-data'[Department])
)

Bonus Amount = 
'Palmoria Group emp-data'[Salary] * 'Palmoria Group emp-data'[Bonus %]

Total Pay = 
'Palmoria Group emp-data'[Salary] + 'Palmoria Group emp-data'[Bonus Amount]

Bonus Paid (Measure) = 
SUM('Palmoria Group emp-data'[Bonus Amount])

Total Pay Paid = 
SUM('Palmoria Group emp-data'[Total Pay])

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

- Integrate time-based data for trend analysis.
   - Include job roles or seniority levels for a deeper look into compensation structure.
   - Develop automated flags for regulatory compliance and pay equity violations.
---

## 🛠 Tools

- Power BI Desktop
- Excel (for preprocessing)
- GitHub (for version control & documentation)

---
## ⚠️ Project Limitations

1. **No Historical Data**  
   The analysis is based on a single snapshot of employee data, limiting trend or time-based insights.

2. **No Job Title or Level**  
   The dataset lacks role or seniority information, which restricts fair comparisons of salaries across employees.

3. **Simplified Bonus Logic**  
   Bonus percentages are applied uniformly based on department and rating, without adjustments for tenure or manager input.

4. **Assumed Data Accuracy**  
   All insights assume that the provided data is complete, clean, and correctly categorized (e.g., ratings, departments).

5. **Missing Cost of Living Adjustments**  
   Salaries are compared across regions without accounting for location-based differences in living expenses or local market rates.

---
## 📚 References

- **Dataset Source** – Provided by DSA as part of the Palmoria Group case study, containing employee records and department-based bonus rules.

- **Power BI Documentation** – [https://learn.microsoft.com/power-bi](https://learn.microsoft.com/power-bi)  
  Official documentation used to understand data modeling, DAX functions, and visualization techniques.

- **DAX Guide** – [https://dax.guide](https://dax.guide)  
  Used for writing and validating DAX expressions such as `LOOKUPVALUE`, `CALCULATE`, and `SWITCH`.

- **Microsoft Excel Functions** – [https://support.microsoft.com/excel](https://support.microsoft.com/excel)  
  For data preprocessing and formatting before importing into Power BI.



