# Data Cleaning Log — student_performance_data
**Date:** 18/02/2026  
**Analyst:** MD Noornabi  
**Dataset:** High School Student Performance — Portugal (GP & MS schools)

---

## Issue #1 — Age Column (Potential Data Entry Errors)

- **Column:** age
- **School:** GP (Gabriel Pereira)
- **Issue:** Two students aged 20 with 0 failures recorded. Since this is a high school dataset, students older than 18 with no repeated grades may indicate incorrect age entry.
- **Rows:** 5, 7
- **Action taken:** Flagged for verification. No data deleted; pending confirmation from superintendent.
- **Question asked:** Do these students have a legitimate reason for being 20 years old with no recorded failures?

---

## Issue #2 — Age Column (Rows Deleted)

- **Column:** age
- **Issue:** 9 student records contained ages outside the valid range (20, 21, 22)
- **Superintendent response:** Confirmed valid age range for public high school is **15–19 years**
- **Action taken:** Deleted 9 rows containing ages 20, 21, and 22
- **Rows remaining after deletion:** 639

---

## Issue #3 — Reason Column (Missing Values Filled)

- **Column:** reason
- **Issue:** ~11% of rows (72 out of 648) had blank values in the reason column
- **Decision rationale:** Dropping rows rejected — an 11% loss would risk skewing the analysis. Values cannot be determined without re-surveying students.
- **Action taken:** Blanks initially filled with "N/A", then replaced with "none_given" to match specified convention
- **Note:** The high proportion of missing reason data is a limitation worth flagging in any final analysis report

---

## Issue #4 — Medu & Fedu Columns (Text-to-Numeric Conversion)

- **Columns:** Medu (mother's education), Fedu (father's education)
- **Issue:** Education levels stored as text strings; numeric format required for statistical analysis
- **Action taken:** Used Find & Replace (Match entire cell contents) to convert all text values to numeric codes

| Text Value | Numeric Code |
|---|---|
| none | 0 |
| primary education (4th grade) | 1 |
| 5th to 9th grade | 2 |
| secondary education | 3 |
| higher education | 4 |

- **Note:** Fedu column contained a mix of already-numeric and text values — conversion applied to text values only
