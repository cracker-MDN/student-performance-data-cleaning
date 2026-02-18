# 🎓 Student Performance Data Cleaning — Excel Project

**Author:** MD Noornabi  
**LinkedIn:** [md-noornabi25](https://www.linkedin.com/in/md-noornabi25/)  
**Tools Used:** Microsoft Excel (Sorting, Filtering, Find & Replace, Data Validation)  
**Dataset:** High School Student Achievement — Portugal (Gabriel Pereira & Mouzinho da Silveira)  
**Course Context:** Google Data Analytics Certificate Track  

---

## 📌 Business Context

The superintendent of a large public school district in Portugal wants to understand **what factors drive student performance** in core subjects across two public high schools — Gabriel Pereira (GP) and Mouzinho da Silveira (MS). The dataset was collected via academic reports and student surveys.

Before any analysis could begin, the data required thorough cleaning. Analyzing dirty data risks leading the superintendent to wrong conclusions and ineffective policy decisions.

---

## ❓ Business Questions

1. What factors influence student grades in core subjects?
2. Does parental education level correlate with student performance?
3. Does a student's reason for choosing a school affect their academic outcomes?
4. What is the valid age range of students across both schools?
5. Are there data quality issues that could skew the analysis?

---

## 📊 Dataset Overview

| Property | Details |
|---|---|
| Source | Portuguese public school district (academic reports + surveys) |
| Schools | Gabriel Pereira (GP), Mouzinho da Silveira (MS) |
| Original Rows | 648 student records |
| Cleaned Rows | 639 student records |
| Columns | 33 (grades, demographics, study habits, family background) |

**Key columns analyzed:**
- `school` — GP or MS
- `age` — student age
- `reason` — reason for choosing the school
- `Medu` — mother's education level
- `Fedu` — father's education level

---

## 🔍 Executive Summary

The dataset contained several data quality issues that required resolution before analysis. Missing values were found in the `reason` column (~11% of records), education level columns (`Medu`, `Fedu`) stored numeric data as text strings, and 9 student records contained age values outside the district's confirmed valid range of 15–19 years. All issues were identified, documented, and resolved systematically using Excel's sorting, filtering, and Find & Replace tools.

---

## 🧹 Data Cleaning Steps

### 1. Column Audit — school, age, reason, Medu, Fedu

Applied filters to each priority column to inspect unique values and identify anomalies.

| Column | Issue Found | Action Taken |
|---|---|---|
| `school` | None | No changes needed ✓ |
| `age` | 9 records with ages 20–22 outside valid range | Flagged → deleted after superintendent confirmation |
| `reason` | ~11% blank values (72 rows) | Filled with `none_given` |
| `Medu` | Text strings instead of numeric values | Converted to numeric scale 0–4 |
| `Fedu` | Mixed text and numeric values | Converted to numeric scale 0–4 |

### 2. Age Range Investigation

- Sorted data by **school A→Z**, then **age largest to smallest**
- Discovered GP students ranged 15–22; MS students ranged 15–20
- Identified 2 suspicious records: age 20 with 0 failures — flagged for verification
- Superintendent confirmed valid range is **15–19 years**
- **Deleted 9 rows** containing ages 20, 21, and 22

### 3. Missing Values — reason column

- Filtered for blanks: **72 of 648 rows** (~11%) had no reason recorded
- Dropping rows rejected — 11% loss would risk skewing analysis
- Decision: filled all blanks with `none_given` to honestly represent missing data without fabricating values

### 4. Text-to-Numeric Conversion — Medu & Fedu

Education levels converted using Find & Replace (Match entire cell contents):

| Text Value | Numeric Code |
|---|---|
| none | 0 |
| primary education (4th grade) | 1 |
| 5th to 9th grade | 2 |
| secondary education | 3 |
| higher education | 4 |

This conversion enables statistical calculations such as average parental education level per student.

---

## 💡 Key Insights from Cleaning

- **Age anomalies:** 9 students (1.4% of dataset) fell outside the valid 15–19 range and were removed. 2 of these had 0 recorded failures, suggesting potential data entry errors rather than grade repetition.
- **Missing reason data:** Over 1 in 10 students did not provide a reason for school selection. This limits the reliability of any analysis linking school choice reason to performance — a limitation worth flagging to the superintendent.
- **Parental education:** Both Medu and Fedu required full text-to-numeric conversion before any statistical analysis on parental influence is possible.

---

## 📁 Repository Structure

```
student-performance-data-cleaning/
│
├── README.md                          ← Project overview (this file)
├── data/
│   └── student-performance-data.xlsx  ← Cleaned dataset
└── docs/
    └── Data-Cleaning-Log.docx         ← Full issue log with flagged records
```

---

## 🛠 Skills Demonstrated

- Data auditing and column inspection using filters
- Sorting on multiple columns for pattern discovery
- Handling missing data — reasoning between deletion vs. imputation
- Text-to-numeric data type conversion
- Documenting data cleaning decisions in a professional issue log
- Communicating data quality findings to a non-technical stakeholder (superintendent)

---

*This project was completed as part of the Google Data Analytics Certificate track.*
