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
DateTable = 
ADDCOLUMNS(
    CALENDAR(DATE(2024,1,1), DATE(2024,12,31)),
    "Year", YEAR([Date]),
    "Month", FORMAT([Date], "MMMM"),
    "Month Number", MONTH([Date]),
    "Quarter", "Q" & FORMAT([Date], "Q")
)
```

### 3. 📐 DAX Measures Created
```dax
-- Total Students
Total Students = COUNTROWS(Students)

-- Average Daily Usage Hours
Avg Usage Hours = AVERAGE(Students[Avg_Daily_Usage_Hours])

-- % Affected Academically
% Affected Academically = 
DIVIDE(
    CALCULATE(COUNTROWS(Students), Students[Affects_Academic_Performance] = "Yes"),
    [Total Students]
)

-- Average Sleep Hours
Avg Sleep Hours = AVERAGE(Students[Sleep_Hours_Per_Night])

-- Average Addiction Score
Avg Addiction Score = AVERAGE(Students[Addicted_Score])

-- Average Mental Health Score
Avg Mental Health Score = AVERAGE(Students[Mental_Health_Score])

-- Conflict Level Classification
Conflict Band = 
IF(Students[Conflicts_Over_Social_Media] <= 2, "Low", "Medium")

-- Health Band Classification
Health Band = 
IF(Students[Mental_Health_Score] >= 7, "Good", "Average")
```

---

## 📊 Dashboard Pages

### 📄 Page 1 – Overview
**KPI Cards:**
- 🔢 Total Students → **705**
- ⏱️ Avg Usage Hours → **4.92 hrs/day**
- 📚 % Affected Academically → **64.26%**
- 😴 Avg Sleep Hours → **6.87 hrs/night**

**Visuals:**
- **Addicted Score by Academic Level** – Bar Chart *(Undergraduate: 2292 | Graduate: 2029 | High School: 217)*
- **Avg Usage Hours by Age** – Column Chart *(Age 18–24)*
- **Gender Distribution** – Donut Chart *(Female: 352 | Male: 353)*

---

### 📄 Page 2 – Health & Sleep Analysis
**Visuals:**
- **Country vs Health Band** – Matrix Table *(Average / Good / Total per country)*
- **Addicted Score vs Mental Health Score** – Scatter Plot
- **Sleep Hours vs Age** – Area Line Chart *(Age 18–24)*
- **Gender Slicer** – Female / Male filter

---

### 📄 Page 3 – Platform & Academic Impact
**Visuals:**
- **Avg Daily Usage Hours by Academic Level** – Bar Chart  
  *(Undergraduate: 1766 | Graduate: 1553 | High School: 150)*
- **Academic Performance Impact by Platform** – Bar Chart  
  *(Instagram: 249 | TikTok: 154 | Facebook: 123 | WhatsApp: 54 | Twitter: 30 | LinkedIn: 21 | others)*
- **Age Range Slicer** – 18 to 24

---

### 📄 Page 4 – Gender & Academic Level Platform View
**Visuals:**
- **Avg Usage Hours by Gender** – Bar Chart *(Female: 5.0 | Male: 4.8)*
- **Most Used Platform by Gender** – Stacked Chart with % breakdowns
- **Avg Daily Usage Hours by Academic Level** – Bar Chart *(High School: 5.5 | Undergraduate: 5.0 | Graduate: 4.8)*
- **Most Used Platform by Academic Level** – Chart with % breakdown
- **Toggle:** Gender View ↔ Academic Level View

---

### 📄 Page 5 – Relationship & Conflict Analysis
**Visuals:**
- **Conflict Level by Relationship Status** – Stacked Bar Chart  
  *(Single: Low 111, Medium 273 | In Relationship: Low 136, Medium 153 | Complicated: Low 8, Medium 24)*
- **Relationship Status Distribution** – Pie Chart  
  *(Single: 54.47% | In Relationship: 40.99% | Complicated: 4.54%)*
- **Student-wise Addiction Score** – Detail Table *(Total: 4538)*
- **Country Slicer** & **Academic Level Slicer**

---

### 📄 Page 6 – Student Profile
**Visual:**
- **Full Student Profile Table** – Drillthrough table with all columns:  
  Student ID, Gender, Country, Age, Academic Level, Relationship Status, Sleep Hours, Avg Daily Usage Hours, Addicted Score, Most Used Platform

---

## 💡 Key Insights

| Insight | Finding |
|---------|---------|
| 📚 Academic Impact | **64.26%** of students report social media affects their academics |
| 📱 Top Platform | **Instagram** is the most impactful platform on academic performance (249 students) |
| 😴 Sleep Trend | Sleep hours dip at age 18, peak at age 22, showing a mid-study recovery pattern |
| 🧠 Health vs Addiction | Higher addiction scores consistently correlate with lower mental health scores |
| ⚔️ Conflict Hotspot | **Single** students have the highest medium-level conflicts (273) |
| 🎓 Usage by Level | High School students average the most daily usage hours (5.5 hrs) |
| 👥 Gender Gap | Female students average slightly higher usage (5.0 hrs) than males (4.8 hrs) |

---

## 🚀 How to Open

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free).
2. Clone or download this repository.
3. Place `Students_Social_Media_Addiction.xlsx` in the same folder as `Mini_Project.pbix`.
4. Open `Mini_Project.pbix` in Power BI Desktop.
5. If prompted, update the data source path to point to the Excel file.
6. Click **Refresh** and explore all 6 dashboard pages.

---

## 🧰 Tools & Technologies

| Tool | Usage |
|------|-------|
| Power BI Desktop | Dashboard creation & visualization |
| Power Query | Data cleaning & transformation |
| DAX | Measures, KPIs, calculated columns & date table |
| Microsoft Excel (.xlsx) | Source dataset |

---

## 📁 Repository Structure
```
📦 Student-Social-Media-Addiction-PowerBI
 ┣ 📊 Mini_Project.pbix
 ┣ 📄 Students_Social_Media_Addiction.xlsx
 ┗ 📄 README.md
```

---

## 🙋‍♂️ Author

**Your Name**
- GitHub: https://github.com/r-das-adhikari
- LinkedIn: www.linkedin.com/in/ramkrishna-dasadhikari-7b0021381

---

## 📃 License

This project is open source and available under the [MIT License](LICENSE).
