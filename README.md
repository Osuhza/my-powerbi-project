# 🩺 Student Health Analytics Dashboard

[![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)](https://powerbi.microsoft.com/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge)]()
[![Dataset](https://img.shields.io/badge/Dataset-50k%20records-blue?style=for-the-badge)]()
[![PDF](https://img.shields.io/badge/Download-PDF%20Report-red?style=for-the-badge&logo=adobe-acrobat-reader)](./Student%20Health_Dashboard.pdf)

> **A comprehensive student health analytics dashboard developed using Microsoft Power BI Desktop to analyze behavioral, physical, mental, and academic health indicators from 50,000 student health records.**

---

## 📋 Table of Contents
- [Project Overview](#project-overview)
- [Dataset](#dataset)
- [Key Findings](#key-findings)
- [Data Processing](#data-processing)
- [Data Modeling](#data-modeling)
- [DAX Measures](#dax-measures)
- [Dashboard Pages](#dashboard-pages)
- [Insights & Recommendations](#insights--recommendations)
- [Technologies Used](#technologies-used)
- [Team](#team)
- [Future Enhancements](#future-enhancements)

---

## 📌 Project Overview

This project analyzes student wellness data to identify major health risk factors affecting students and provides data-driven recommendations for school administrators and health counselors.

### 🎯 Objectives
- Preprocess and clean student health data using the CLEAN framework
- Design a star schema data model suitable for analytical reporting
- Create DAX measures for KPI monitoring and behavioral analysis
- Develop interactive dashboards for administrators and counselors
- Generate actionable insights based on student health trends

### 📊 Key Metrics Monitored
| Category | Metrics |
|----------|---------|
| **Physical** | Sleep duration, BMI, heart rate, step count |
| **Lifestyle** | Exercise duration, water intake, screen time |
| **Mental** | Stress level, mental health status |
| **Academic** | Academic pressure level |

---

## 📁 Dataset

### Source Information
| Attribute | Details |
|-----------|---------|
| **File Name** | `enhanced_student_health_dataset_50k.csv` |
| **Total Records** | 50,000 |
| **Total Columns** | 22 |
| **File Type** | CSV |
| **Target Variable** | `health_condition` |

### Health Condition Distribution
| Condition | Count | Percentage |
|-----------|-------|------------|
| 🟢 Fit | 25,481 | 50.96% |
| 🟡 At-Risk | 21,539 | 43.08% |
| 🔴 Unhealthy | 2,980 | 5.96% |

> ⚠️ **Key Insight:** Nearly half of students are classified as "at-risk," highlighting the need for wellness monitoring and preventive interventions.

---

## 🔍 Key Findings

| Metric | Average | Range |
|--------|---------|-------|
| Sleep Duration | 7.0 hrs | 3–10 hrs |
| Heart Rate | 75 BPM | 50–117 BPM |
| BMI | 23.0 | 16–35 |
| Step Count | 7,985 | 1,000–14,999 |
| Exercise Duration | 40 min | 0–120 min |
| Water Intake | 2.2 L | 0.5–5 L |
| Screen Time | 5.0 hrs | 0–12 hrs |

### Cross-Analysis Highlights
- **83%** of unhealthy students exhibit high stress levels (vs. 11% of fit students)
- **60%** of unhealthy students are sedentary (vs. 22% of fit students)
- Fit students average **7.41 hrs** sleep vs. **5.69 hrs** for unhealthy students
- Higher screen time correlates with reduced sleep and physical activity

---

## 🧹 Data Processing (CLEAN Framework)

| Step | Action | Result |
|------|--------|--------|
| **Completeness** | Verified no null values | 100% valid data |
| **Legitimacy** | Removed duplicates, validated ranges | Clean, valid records |
| **Efficiency** | Assigned proper data types | Optimized for performance |
| **Accuracy** | Encoded ordinal categories (Low=1, Medium=2, High=3) | Analytics-ready |
| **Normalization** | Standardized values | Ready for predictive modeling |

---

## 📐 Data Modeling (Star Schema)

### Fact Table
- **FactStudentHealth** - Transactional health observations

### Dimension Tables
| Table | Purpose |
|-------|---------|
| DimStudent | Student demographics |
| DimHealth | Health indicators |
| DimLifestyle | Lifestyle behaviors |
| DimAcademic | Academic-related factors |
| DimDate | Time analysis |

### Relationship Type
**Many-to-One** between fact table and all dimension tables

---

## 📊 DAX Measures

### Core KPIs
```dax
Total Students = COUNTROWS(FactStudentHealth)

% Fit Students = DIVIDE([Fit Count], [Total Students])

% At-Risk Students = DIVIDE([At-Risk Count], [Total Students])

High Stress Count = CALCULATE([Total Students], stress_level = "High")
