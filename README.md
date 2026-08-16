# 📊 HR Analytics & Attendance Dashboard

A real-world **HR Data Analytics and Business Intelligence project** built using **Microsoft Power BI, Power Query, Excel, and DAX** to analyze employee attendance, work-from-home behavior, presence trends, and sick leave patterns.

> **Project Type:** Data Analytics / Business Intelligence  
> **Domain:** Human Resources  
> **Tools:** Power BI, Power Query, DAX, Microsoft Excel  
> **Dataset:** Employee Attendance Data  
> **Dashboard:** Interactive Power BI Report  

---

## 📌 Project Overview

The project transforms raw employee attendance data stored across multiple monthly Excel sheets into a clean, analysis-ready dataset using **Power Query**.

The original data follows a wide structure where each date is stored as a separate column:

```text
Employee Code | Employee Name | Apr 1 | Apr 2 | Apr 3 | ...
```

The data is transformed into a normalized structure:

```text
Employee Code | Employee Name | Date | Attendance Status
```

This structure allows Power BI to perform effective time-based, employee-level, and weekday-level analysis.

The final dashboard provides insights into:

- Employee presence
- Work-from-home behavior
- Sick leave patterns
- Attendance trends
- Weekday attendance patterns
- Employee-level attendance metrics

---

## 🎯 Business Problem

HR teams need an effective way to understand attendance patterns and workforce behavior from raw attendance records.

The dashboard addresses questions such as:

- What is the overall employee presence percentage?
- How frequently are employees working from home?
- Which weekdays have higher WFH activity?
- How does attendance change over time?
- Are there noticeable sick-leave spikes?
- Which employees have comparatively high or low attendance?
- How can attendance and WFH patterns support office capacity planning?

---

## 🎯 Project Objectives

1. Combine attendance data from multiple monthly Excel sheets.
2. Clean and transform the data using Power Query.
3. Convert multiple date columns into a single Date column.
4. Create reusable data transformations.
5. Develop DAX measures for key HR KPIs.
6. Analyze presence, WFH, and sick leave patterns.
7. Analyze weekday-level attendance behavior.
8. Build an interactive Power BI dashboard.
9. Validate dashboard calculations against the source data.
10. Generate business insights for workforce planning.

---

## 📁 Dataset

The dataset contains employee attendance records across multiple monthly sheets.

### Original Structure

| Employee Code | Employee Name | Apr 1 | Apr 2 | Apr 3 |
|---|---|---|---|---|
| EMP001 | Employee A | P | WFH | P |
| EMP002 | Employee B | SL | P | WFH |

### Final Structure

| Employee Code | Employee Name | Date | Attendance Status |
|---|---|---|---|
| EMP001 | Employee A | 01-Apr | P |
| EMP001 | Employee A | 02-Apr | WFH |
| EMP001 | Employee A | 03-Apr | P |
| EMP002 | Employee B | 01-Apr | SL |

### Attendance Codes

| Code | Meaning |
|---|---|
| `P` | Present |
| `WFH` | Work From Home |
| `HWFH` | Half Work From Home |
| `SL` | Sick Leave |
| `HSL` | Half Sick Leave |
| `PL` | Paid Leave |
| `WO` | Weekly Off |

> Attendance codes should be verified against the actual source dataset before modifying the DAX logic.

---

## 🔄 Data Transformation

The project uses **Power Query** to convert the raw Excel data into an analysis-ready format.

### Transformation Workflow

```text
Raw Excel Data
      ↓
Power Query
      ↓
Data Cleaning
      ↓
Header & Column Standardization
      ↓
Unpivot Date Columns
      ↓
Date & Data Type Conversion
      ↓
Reusable Transformation
      ↓
Combined Attendance Table
      ↓
Power BI Data Model
```

The transformation uses a reusable approach so that additional monthly attendance sheets can be incorporated without rebuilding the entire data-cleaning process.

---

## 📐 Key DAX Measures

### Presence %

```DAX
Presence % =
DIVIDE(
    [Present Days],
    [Total Working Days],
    0
)
```

### Work From Home %

```DAX
WFH % =
DIVIDE(
    [Work From Home Days],
    [Present Days],
    0
)
```

### Sick Leave %

```DAX
Sick Leave % =
DIVIDE(
    [Sick Leave Days],
    [Total Working Days],
    0
)
```

### Work From Home Count

```DAX
Work From Home Count =
SWITCH(
    'Final Data'[Value],
    "WFH", 1,
    "HWFH", 0.5,
    0
)
```

### Sick Leave Count

```DAX
Sick Leave Count =
SWITCH(
    'Final Data'[Value],
    "SL", 1,
    "HSL", 0.5,
    0
)
```

---

## 🧩 Dashboard

The dashboard provides an interactive view of workforce attendance and behavior.

![HR Attendance Dashboard](Image/Dahboard.png)

### Dashboard Components

- **Presence % KPI**
- **WFH % KPI**
- **Sick Leave % KPI**
- Presence trend by date
- WFH trend by date
- Sick leave trend by date
- WFH by day of week
- Presence by day of week
- Sick leave by day of week
- Employee-level attendance table
- Interactive date/month filters

---

## 💡 Dashboard Insights

Based on the current dashboard:

### Overall Attendance

- **Presence:** 91.83%
- **WFH:** 10.00%
- **Sick Leave:** 1.10%

### Weekday Presence

| Day | Presence % |
|---|---:|
| Monday | 93.21% |
| Tuesday | 93.03% |
| Wednesday | 92.11% |
| Thursday | 90.72% |
| Friday | 90.19% |

Monday shows the highest presence, while Friday shows the lowest presence among the displayed weekdays.

### Weekday WFH

| Day | WFH % |
|---|---:|
| Monday | 8.77% |
| Tuesday | 8.11% |
| Wednesday | 8.43% |
| Thursday | 11.51% |
| Friday | **13.01%** |

Friday has the highest WFH percentage, while Tuesday has the lowest.

### Sick Leave

The sick-leave trend shows fluctuations throughout the analyzed period, including noticeable spikes that can be investigated further by HR.

> The dashboard identifies patterns but does not establish the causes behind attendance or sick-leave changes.

---

## 🔎 Data Validation

Dashboard calculations were validated against the underlying attendance data to ensure consistency between the source Excel records and Power BI.

Example:

```text
Excel
Employee A
10 June
P
```

should correspond to:

```text
Power BI
Employee A
10 June
P
```

The following were checked during validation:

- Employee records
- Attendance status
- Dates
- Monthly data
- Presence %
- WFH %
- Sick Leave %
- Trend calculations

---

## 🛠️ Technology Stack

| Technology | Purpose |
|---|---|
| **Microsoft Power BI** | Dashboard, visualization & data modeling |
| **Power Query** | Data cleaning & transformation |
| **DAX** | KPI calculations & business logic |
| **Microsoft Excel** | Source attendance data |

---

## 📁 Project Structure

```text
HR-Analytics-Attendance-Dashboard/
│
├── 📂 Image/
│   └── Dahboard.png
│
├── 📂 dataset/
│   └── Attendance.xlsx
│
├── 📄 HR Analysis.pbix
│
└── 📄 README.md
```

---

## 🚀 How to Use

### 1. Clone the Repository

```bash
git clone https://github.com/shruti08-31/<repository-name>.git
```

### 2. Open the Power BI File

Open:

```text
HR Analysis.pbix
```

using **Microsoft Power BI Desktop**.

### 3. Check the Data Source

If required, update the Excel source path through:

```text
Transform Data
→ Data Source Settings
→ Change Source
```

Select the attendance dataset from the `dataset/` folder.

### 4. Refresh the Dashboard

In Power BI Desktop:

```text
Home → Refresh
```

---

## 🔮 Future Enhancements

- Automated data refresh using Power BI Service
- Attendance threshold alerts
- Email notifications
- Department-level analysis
- Attendance anomaly detection
- Hybrid-work recommendations
- Row-Level Security (RLS)
- Automated HR data pipeline integration

---

## 📌 Key Skills Demonstrated

```text
Power BI
Power Query
DAX
Excel
Data Cleaning
Data Transformation
Data Modeling
HR Analytics
Business Intelligence
Data Visualization
Dashboard Development
```

---

## 👩‍💻 Author

**Shruti Prasad**

**B.Tech — Artificial Intelligence & Data Science**

**Areas:** Data Analytics • Business Intelligence • Power BI • Data Visualization

---

## 📄 Disclaimer

This project is intended for **educational and portfolio purposes**. Employee identifiers in the underlying dataset are randomized. The dashboard should not be used as the sole basis for sensitive HR decisions without appropriate organizational policies and validation.
