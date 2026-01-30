# ❤️ Heart Disease Analysis Dashboard

## 📌 Project Overview
This project is a **Power BI Dashboard** created to analyze heart disease patient data.  
The dashboard helps in understanding **survival rate, death rate, age impact, gender distribution, and medical factors** affecting heart patients.

The dataset was first prepared in **Microsoft Excel** and then visualized in **Power BI** using calculated columns, DAX measures, and interactive visuals.

---

## 🛠 Tools & Technologies Used
- Power BI
- Microsoft Excel
- DAX (Data Analysis Expressions)

---

## 📂 Dataset
- Dataset Name: Heart Disease Clinical Records  
- Format: Excel (.xlsx)  
- Attributes Included:
  - Age
  - Gender
  - Diabetes
  - High Blood Pressure
  - Serum Creatinine
  - Ejection Fraction
  - Platelets
  - Smoking
  - Death Event

---

## 🧮 Calculated Columns

### 1. Age Group
Patients are divided into age categories:
- 40–50  
- 51–60  
- 61–70  
- 71+  
- Below 40  

**DAX Logic Used:**
```
AGE_GROUP = 
SWITCH(
    TRUE(),
    'heart_Disease_clinical_records_'[age] >= 40 && 'heart_Disease_clinical_records_'[age] <= 50, "40-50",
    'heart_Disease_clinical_records_'[age] >= 51 && 'heart_Disease_clinical_records_'[age] <= 60, "51-60",
    'heart_Disease_clinical_records_'[age] >= 61 && 'heart_Disease_clinical_records_'[age] <= 70, "61-70",
    'heart_Disease_clinical_records_'[age] >= 70, "71+",
    "Below 40"
)
```

---

### 2. Gender
Numeric gender converted into text.

**DAX Logic:**
```
Gender = IF('heart_Disease_clinical_records_'[sex] = 0, "Female", "Male")
```

---

## 📊 Measures (DAX)

### 1. Survival Rate
```
Survival Rate =
1 - DIVIDE(
    SUM('heart_Disease_clinical_records_'[DEATH_EVENT]),
    COUNT('heart_Disease_clinical_records_'[count])
)
```

---

### 2. Total Survival
```
Total_Survivor =
CALCULATE(
    COUNT('heart_Disease_clinical_records_'[count]),
    'heart_Disease_clinical_records_'[DEATH_EVENT] = 0
)
```

---

### 3. Total Death
```
Total_Death =
CALCULATE(
    COUNT('heart_Disease_clinical_records_'[count]),
    'heart_Disease_clinical_records_'[DEATH_EVENT] = 1
)
```

---

### 4. Average Age of Survival
```
AVG_Age_Survival =
CALCULATE(
    AVERAGE('heart_Disease_clinical_records_'[age]),
    'heart_Disease_clinical_records_'[DEATH_EVENT] = 0
)
```

---

## 📈 Dashboard Features
- Survival Rate KPI
- Average Age of Survival KPI
- Total Survivors & Total Death Count
- Survival Count by Age Group
- Serum Creatinine Analysis
- Ejection Fraction Analysis
- Impact of Smoking, Diabetes, High Blood Pressure & Anemia
- Gender Filter (Male / Female)
- Interactive and Clean UI

---

## 🎯 Key Insights
- Survival rate decreases as age increases.
- Medical attributes like **serum creatinine** and **ejection fraction** strongly impact survival.
- Lifestyle factors such as **smoking and diabetes** also influence death rate.
- Gender comparison helps in better demographic analysis.

---

## 🚀 How to Use
1. Open Power BI Desktop.
2. Load the Excel dataset.
3. Create calculated columns.
4. Add DAX measures.
5. Build visuals and KPIs.
6. Use filters to explore insights.

---

## 📌 Conclusion
This dashboard provides a clear and interactive analysis of heart disease data.  
It helps understand survival trends, medical impacts, and demographic distribution, improving data analysis and visualization skills.

---

**Author:** Jyoti Yadav  
**Role:** Power BI Learner / Data Analyst  
