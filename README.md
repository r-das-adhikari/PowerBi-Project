# project-PowerBi
# 📱 Student Social Media Addiction – Power BI Dashboard

An end-to-end Power BI project analyzing the impact of social media addiction on student mental health, sleep patterns, platform usage, academic performance, and relationship conflicts across **110 countries**.

---

## 📌 Project Overview

This interactive dashboard explores behavioral and psychological trends among **705 students** worldwide, examining how social media usage relates to mental health scores, academic performance, sleep hours, and relationship conflicts — broken down by gender, academic level, country, and platform.

---

## 📂 Dataset Description

**File:** `Students_Social_Media_Addiction.xlsx`  
**Records:** 705 students | **Columns:** 10

| Column | Type | Description |
|--------|------|-------------|
| `Student_ID` | Integer | Unique student identifier |
| `Age` | Integer | Age of student (18–24) |
| `Gender` | Text | Male / Female |
| `Academic_Level` | Text | Undergraduate / Graduate / High School |
| `Country` | Text | Student's country (110 countries) |
| `Sleep_Hours_Per_Night` | Decimal | Average nightly sleep hours |
| `Avg_Daily_Usage_Hours` | Decimal | Daily social media usage in hours |
| `Mental_Health_Score` | Integer | Mental health score out of 10 |
| `Relationship_Status` | Text | Single / In Relationship / Complicated |
| `Conflicts_Over_Social_Media` | Integer | Conflict level (Low / Medium) |
| `Addicted_Score` | Integer | Social media addiction score out of 10 |
| `Most_Used_Platform` | Text | Primary social media platform used |

---

## 🛠️ Data Preparation Steps

### 1. 🧹 Data Cleaning (Power Query)
- Verified and corrected data types for all columns
- Confirmed zero null values across all fields
- Standardized categorical columns: `Gender`, `Academic_Level`, `Relationship_Status`
- Added and validated `Avg_Daily_Usage_Hours` and `Most_Used_Platform` columns
- Renamed columns for clarity and consistency

### 2. 📅 Date Table (DAX)
Created a custom Date Table and integrated it into the data model:
```dax
