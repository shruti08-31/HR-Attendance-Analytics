Here is the clean, professional `README.md` code formatted exactly to your requested structure.

```markdown
# 📊 HR Analytics & Attendance Dashboard


## 📌 Project Overview

The **HR Analytics & Attendance Dashboard** is a business intelligence project built with **Microsoft Power BI** to transform raw employee attendance records into actionable HR insights.

The source data contains attendance information across multiple monthly Excel sheets. Using **Power Query**, the data is cleaned, transformed, and converted into an analysis-ready format. **DAX measures** are then used to calculate key HR metrics, which are presented through an interactive Power BI dashboard.

The dashboard enables HR teams and management to monitor:
- Employee presence
- Work-from-home behavior
- Sick leave patterns
- Attendance trends
- Weekday-level attendance behavior
- Employee-level attendance metrics

---

## 🎯 Business Problem

HR teams often have attendance data but lack an efficient way to identify meaningful patterns from it. This project addresses questions such as:
- What is the overall employee presence percentage?
- How frequently are employees working from home?
- Is WFH increasing or decreasing over time?
- Which weekdays have higher WFH activity?
- What percentage of working days are affected by sick leave?
- Which employees have comparatively low or high attendance?

### Business Objectives
| Objective | Business Value |
|---|---|
| **Track employee presence** | Monitor overall workforce availability |
| **Analyze WFH behavior** | Understand hybrid-work patterns |
| **Monitor sick leave** | Identify unusual attendance patterns |
| **Analyze weekday trends** | Support workforce and office planning |
| **Track monthly trends** | Identify changes over time |
| **Analyze employees individually** | Enable detailed HR investigation |

---

## 📊 Dashboard

![HR Analytics Dashboard](screenshots/dashboard.png)

The Power BI dashboard provides both high-level KPIs and detailed employee-level analysis. 

**Interactive Features & Components:**
*   **KPI Cards:** Quick views of Presence %, WFH %, and Sick Leave %.
*   **Trend Analysis:** Line charts tracking Presence, WFH, and Sick leave trends over time.
*   **Weekday Analysis:** Patterns of WFH and presence across different days of the week.
*   **Employee Table:** A detailed matrix containing individual employee metrics.
*   **Filters/Slicers:** Slice the data by Employee, Date, Month, or Day of Week.

---

## 📐 Key Metrics

The dashboard focuses on three primary HR KPIs. *(Note: Complete measure definitions and calculations can be found in `docs/DAX-Measures.md`)*

**1. Presence %**
Measures the percentage of working days on which employees were present.
```dax
Presence % = DIVIDE([Present Days], [Total Working Days], 0)

```

**2. Work From Home %**
Measures WFH days relative to total present days.

```dax
WFH % = DIVIDE([Work From Home Days], [Present Days], 0)

```

**3. Sick Leave %**
Measures sick-leave days relative to total working days.

```dax
Sick Leave % = DIVIDE([Sick Leave Days], [Total Working Days], 0)

```

---

## 🏗️ Data Pipeline

The source dataset contains employee attendance records maintained across multiple monthly Excel sheets. To perform time-based analysis, the original wide structure is transformed into a normalized, long format.

### Project Workflow

```text
Raw Excel Data ➔ Power Query (ETL) ➔ Normalized Data ➔ DAX Measures ➔ Power BI Model ➔ Dashboard

```

### Data Transformation (Power Query)

The data preparation pipeline ensures the model is optimized for dynamic filtering:

1. **Import & Combine:** Load and merge multiple monthly sheets.
2. **Clean:** Remove unnecessary rows, promote headers, and drop invalid records.
3. **Unpivot:** Convert cross-tabular date columns into standardized `Date` and `Attendance Status` columns.
4. **Format:** Standardize data types for DAX calculations.

**Final Normalized Table Structure:**

| Employee ID | Employee Name | Date | Attendance Status |
| --- | --- | --- | --- |
| EMP001 | Employee A | 01-Apr | P |
| EMP001 | Employee A | 02-Apr | WFH |
| EMP002 | Employee B | 01-Apr | SL |

---

## ⚙️ DAX & Core Concepts

This project demonstrates practical business intelligence techniques:

* **Data Modeling:** Connecting raw HR data to an analytical structure.
* **Power Query:** Unpivoting, reusable transformations, and data type handling.
* **DAX Logic:** Using `CALCULATE()`, `DIVIDE()`, `COUNTROWS()`, `SWITCH()`, and conditional aggregation.
* **Validation:** Ensuring transformed records match the original Excel totals prior to dashboard deployment.

---

## 🔍 Business Insights

The dashboard is designed to identify patterns such as:

* 📈 **Presence Trends:** Track whether employee presence is increasing or decreasing over time.
* 🏠 **WFH Behavior:** Identify if WFH adoption is growing and which weekdays show peak remote work.
* 🤒 **Sick Leave Patterns:** Spot dates or periods with unusually high sick leave for further HR investigation.
* 🏢 **Workforce Planning:** Use attendance and WFH trends to support office capacity planning and hybrid-work resource allocation.

---

## 🛠️ Tech Stack

| Technology | Purpose |
| --- | --- |
| **Microsoft Power BI** | Dashboard, Data Modeling, & Visualization |
| **Power Query** | Data cleaning & transformation (ETL) |
| **DAX** | KPI calculations & business logic |
| **Microsoft Excel** | Source data format |

---

## 🚀 Setup & Installation

**1. Clone the repository**

```bash
git clone [https://github.com/](https://github.com/)<username>/<repository-name>.git

```

**2. Open the Power BI file**
Open `powerbi/HR_Analytics_Dashboard.pbix` using Power BI Desktop.

**3. Verify the data source**
If required, update the Excel file path:
`Transform Data` → `Data Source Settings` → Point to `data/Attendance.xlsx`

**4. Refresh the data**
Click `Home` → `Refresh` to load the latest data into the model.

---

## 🔮 Future Scope

Potential enhancements for future iterations:

* Automated data refresh via Power BI Service deployment.
* Row-Level Security (RLS) for department managers.
* Attendance threshold alerts and email notifications.
* Automated HR data pipeline integrations.

---

### 👩‍💻 Author

**Shruti Prasad**

*B.Tech — Artificial Intelligence & Data Science*

Areas: Data Analytics • Business Intelligence • Power BI • Data Visualization

📄 **Disclaimer:** *This project is intended for educational and portfolio purposes. Employee identifiers in the underlying dataset are randomized. The dashboard should not be used as the sole basis for sensitive HR decisions without appropriate organizational policies and validation.*

```

```
