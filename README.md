# HR Attrition Analytics Dashboard

[![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com/)
[![DAX](https://img.shields.io/badge/DAX-005571?style=for-the-badge&logo=microsoft&logoColor=white)](https://docs.microsoft.com/en-us/dax/)
[![Kaggle](https://img.shields.io/badge/Kaggle-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)](https://www.kaggle.com/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-FF6600?style=for-the-badge&logo=xgboost&logoColor=white)](https://xgboost.ai/)

---

## Project Overview

This project is a comprehensive **HR Analytics solution** that combines:

1. **Interactive Power BI Dashboard** - Visualizes attrition patterns and KPIs
2. **Machine Learning Models** - Predicts which employees are at risk of leaving
3. **Actionable Recommendations** - Data-driven strategies for HR leaders

The dashboard and models work together to help organizations understand why employees leave and take proactive action to retain talent.

### Key Questions Answered

- Which departments have the highest attrition?
- What job roles are most at risk?
- Which age groups are leaving the company?
- Does overtime drive attrition?
- What is the salary gap between leavers and stayers?
- **Can we predict which employees will leave before they quit?**

---

## Dashboard Preview

### Page 1: KPI Overview
*Key metrics and high-level performance indicators at a glance.*

![KPI Overview](Screenshots/KPI_Overview.png)

---

### Page 2: Attrition Analysis
*Detailed breakdown of attrition by department, job role, age group, and overtime.*

![Attrition Analysis](Screenshots/Attrition_Analysis.png)

---

### Page 3: Executive Summary - Key Findings
*Visual summary of the most critical insights discovered from the data.*

![Executive Summary - Key Findings](Screenshots/Executive_Summary_Key_Findings.png)

---

### Page 4: Executive Summary - Recommendations
*Data-driven recommendations for HR leadership.*

![Executive Summary - Recommendations](Screenshots/Executive_Summary_Recommendations.png)

---

### Page 5: Key Takeaways
*Concise summary of the most important metrics and strategic actions.*

![Key Takeaways](Screenshots/Key_Takeaways.png)

---

## Key Insights

| Metric | Value |
|--------|-------|
| **Total Employees** | 1,470 |
| **Attrition Count** | 237 |
| **Attrition Rate** | 16.1% |
| **Avg Monthly Income** | $6,500 |
| **Avg Age** | 36.9 years |
| **Avg Tenure** | 7 years |

### Top Findings

| # | Insight | Severity |
|---|---------|----------|
| 1 | R&D Department has the highest attrition (133 employees) | High |
| 2 | Lab Technicians leave the most (62 employees) | High |
| 3 | 26-35 age group accounts for 120 leavers | Medium |
| 4 | 46% of leavers worked overtime | High |
| 5 | Leavers earn $2,000 less than stayers | High |
| 6 | Leavers have only 2.5 years average tenure | Medium |

---

## Recommendations

| Priority | Action | Expected Impact |
|----------|--------|-----------------|
| 1 | Increase salaries for entry-level roles | 15-20% reduction |
| 2 | Reduce overtime in high-turnover departments | 10-15% reduction |
| 3 | Improve engagement for 26-35 age group | 15-20% reduction |
| 4 | Fix onboarding process for new hires | 25% reduction |
| 5 | Conduct exit interviews for R&D | Identify root causes |

---

## Machine Learning Models

### Model Overview

I trained **7 different machine learning models** to predict employee attrition and selected the 2 best performers:

| # | Model | Purpose |
|---|-------|---------|
| 1 | Random Forest | Baseline ensemble model |
| 2 | Random Forest + SMOTE | Handled class imbalance |
| 3 | XGBoost | Advanced boosting model |
| 4 | Logistic Regression | Simple and interpretable |
| 5 | Decision Tree | Easy to visualize |
| 6 | Gradient Boosting | Alternative boosting |
| 7 | Tuned XGBoost | Optimized hyperparameters |

### Winning Models (Two-Model Strategy)

| Model | Role | Key Metric |
|-------|------|------------|
| **Logistic Regression** | Primary (Screening) | **Recall: 78.7%** - Catches most leavers |
| **XGBoost** | Secondary (Validation) | **Accuracy: 85%** - Confirms predictions |

### How the Two Models Work Together

```
1,470 Employees
    │
    ▼
Logistic Regression (Screens everyone)
    │
    ▼
Flags employees at risk
    │
    ▼
XGBoost (Validates flagged employees)
    │
    ▼
Confirms high-risk employees
    │
    ▼
HR focuses on confirmed cases
```

### Model Performance Comparison

| Model | Accuracy | Precision | Recall | F1 Score | ROC AUC |
|-------|----------|-----------|--------|----------|---------|
| Random Forest (Default) | 82.0% | 28.6% | 8.5% | 13.1% | 77.3% |
| Random Forest + SMOTE | 81.0% | 39.5% | 36.2% | 37.8% | 73.5% |
| XGBoost | 84.7% | 53.1% | 36.2% | 43.0% | 79.8% |
| **Logistic Regression** | 68.0% | 30.6% | **78.7%** | 44.1% | 81.4% |
| Decision Tree | 72.8% | 21.1% | 25.5% | 23.1% | 53.2% |
| Gradient Boosting | 85.0% | 57.1% | 25.5% | 35.3% | 78.7% |
| Tuned XGBoost | ~84% | 55.2% | 34.0% | 42.1% | 78.2% |

### Top 5 Features Driving Attrition

| Rank | Feature | Why It Matters |
|------|---------|----------------|
| 1 | **Overtime** | Employees who work overtime are 2x more likely to leave |
| 2 | **Monthly Income** | Low salary is a major driver of attrition |
| 3 | **Job Satisfaction** | Unhappy employees leave |
| 4 | **Years at Company** | New hires (2-3 years) are most at risk |
| 5 | **Work-Life Balance** | Poor balance drives employees away |

### Model Files

The `Predictive_Models/` folder contains:

| File | Description |
|------|-------------|
| `HR_Attrition_Prediction.ipynb` | Complete Jupyter Notebook with all code |
| `lr_model.pkl` | Logistic Regression model |
| `xgb_model.pkl` | XGBoost model |
| `label_encoders.pkl` | Categorical variable encoders |
| `feature_names.pkl` | Feature names used in models |
| `lr_model_joblib.pkl` | LR model for Power BI integration |
| `xgb_model_joblib.pkl` | XGBoost model for Power BI integration |
| `attrition_predictions.xlsx` | Risk predictions for all 1,470 employees |

---

## Tools & Technologies

### Power BI
- **Power BI Desktop** - Dashboard development and visualization
- **DAX** - Measures and calculations
- **Power Query** - Data cleaning and transformation
- **Power BI Service** - Publishing and sharing

### Machine Learning
- **Python** - Data preprocessing and modeling
- **Pandas/Numpy** - Data manipulation
- **Scikit-Learn** - Machine learning models
- **XGBoost** - Advanced gradient boosting
- **SMOTE** - Handling class imbalance
- **SHAP** - Model explainability
- **Matplotlib/Seaborn** - Data visualization
- **Pickle/Joblib** - Model serialization

---

## Dataset

**Source:** IBM HR Analytics - Attrition Dataset (Kaggle)

**Link:** https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset

**Size:** 1,470 rows x 35 columns

**Key Columns:**
- Attrition (Target Variable - Yes/No)
- Age, Gender, MaritalStatus
- Department, JobRole, JobLevel
- MonthlyIncome, OverTime
- YearsAtCompany, YearsInCurrentRole
- JobSatisfaction, WorkLifeBalance

---

## DAX Measures

All 9 measures are documented in [Measures.txt](Measures.txt)

```dax
Total Employees = COUNTROWS('data')

Attrition Count = 
CALCULATE(
    COUNTROWS('data'),
    'data'[Attrition] = "Yes"
)

Attrition Rate = 
DIVIDE([Attrition Count], [Total Employees], 0)
```

View all measures in [Measures.txt](Measures.txt)

---

## How to View the Dashboard

### Option 1: Power BI Desktop (Recommended)
1. Download `HR_Attrition_Dashboard.pbix`
2. Open in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (Free)
3. Explore all 5 pages interactively

### Option 2: Power BI Service (Online)
Live Dashboard: [View Online](https://app.powerbi.com/your-link-here)

---

## How to Use the Machine Learning Models

### Option 1: Run the Jupyter Notebook
1. Navigate to `Predictive_Models/` folder
2. Open `HR_Attrition_Prediction.ipynb` in Jupyter Notebook or VS Code
3. Run all cells to train models and generate predictions

### Option 2: Use the Pre-trained Models
1. Load `lr_model.pkl` or `xgb_model.pkl` in Python
2. Use `label_encoders.pkl` to encode categorical data
3. Make predictions on new employee data

### Option 3: Use the Predictions File
1. Open `attrition_predictions.xlsx`
2. Review risk scores for all employees
3. Filter by "High Risk" or "Very High Risk" for HR action

---

## Project Structure

```
HR-Workforce-Analytics-Attrition-Prediction/
│
├── HR_Attrition_Dashboard.pbix          # Power BI dashboard file
├── README.md                             # Project documentation
├── Measures.txt                          # All DAX formulas
├── Insights.txt                          # Key findings & recommendations
├── attrition_predictions.xlsx            # ML predictions for all employees
│
├── Data/
│   └── WA_Fn-UseC_-HR-Employee-Attrition.csv
│
├── Predictive_Models/                    # Machine Learning models
│   ├── HR_Attrition_Prediction.ipynb    # Complete Jupyter Notebook
│   ├── lr_model.pkl                      # Logistic Regression model
│   ├── xgb_model.pkl                     # XGBoost model
│   ├── label_encoders.pkl                # Categorical encoders
│   ├── feature_names.pkl                 # Feature names
│   ├── lr_model_joblib.pkl               # LR model for Power BI
│   └── xgb_model_joblib.pkl              # XGBoost model for Power BI
│
└── Screenshots/                          # Dashboard page images
    ├── KPI_Overview.png
    ├── Attrition_Analysis.png
    ├── Executive_Summary_Key_Findings.png
    ├── Executive_Summary_Recommendations.png
    └── Key_Takeaways.png
```

---

## Business Impact

| Area | Improvement |
|------|-------------|
| Retention | 15-20% reduction in attrition |
| Hiring Costs | Significant cost savings |
| Targeting | Focus on high-risk departments |
| Decision Making | Data-driven HR strategies |
| Proactive Action | Identify at-risk employees before they leave |

---

## Connect With Me

**LinkedIn:** [Your LinkedIn URL]

**GitHub:** https://github.com/George-tech-svg

**Portfolio:** [Your Portfolio URL]

---

## License

This project is for portfolio purposes only.

---

## Show Your Support

If you found this project helpful, please give it a star on GitHub.

---

**Built with Power BI, DAX, Python, and Machine Learning**
