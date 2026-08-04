# DAX Measures

This dashboard uses custom DAX measures to calculate key Human Resources metrics and support interactive reporting.

---

## Total Employees

Counts the total number of unique employees.

```DAX
Total Employees =
DISTINCTCOUNT(HR_Analytics[EmpID])
```

---

## Employee Count

Counts employees while respecting the current filter context.

```DAX
Employee Count =
DISTINCTCOUNT(HR_Analytics[EmpID])
```

This measure is used in visuals where employee counts need to respond dynamically to slicers and chart filters.

---

## Attrition Count

Calculates the total number of employees who have left the company.

```DAX
Attrition Count =
CALCULATE(
    [Total Employees],
    HR_Analytics[Attrition] = "Yes"
)
```

---

## Attrition Rate

Calculates the percentage of employees who left the company.

```DAX
Attrition Rate =
DIVIDE(
    [Attrition Count],
    [Total Employees]
)
```

---

## Average Salary

Calculates the average monthly income of employees.

```DAX
Average Salary =
AVERAGE(HR_Analytics[MonthlyIncome])
```

---

## Average Age

Calculates the average age of employees.

```DAX
Average Age =
AVERAGE(HR_Analytics[Age])
```

---

## Average Years at Company

Calculates the average number of years employees have worked at the company.

```DAX
Average Years at Company =
AVERAGE(HR_Analytics[YearsAtCompany])
```

---

# Summary

| Measure | Purpose |
|----------|---------|
| Total Employees | Counts all employees |
| Employee Count | Dynamic employee count respecting filters |
| Attrition Count | Counts employees who left |
| Attrition Rate | Calculates employee turnover percentage |
| Average Salary | Calculates average monthly salary |
| Average Age | Calculates average employee age |
| Average Years at Company | Calculates average employee tenure |

---

# Notes

These measures were developed using DAX best practices by separating reusable business calculations into a dedicated `_Measures` table. This approach improves model organization, simplifies maintenance, and encourages measure reuse across multiple report visuals.
