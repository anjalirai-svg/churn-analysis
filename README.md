# 🔍 Customer Churn Analysis — Python & EDA

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge)
![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=for-the-badge)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

> EDA on 10,000+ customer records to identify key churn drivers — achieved 82% prediction accuracy with actionable business recommendations.

---

## 📌 Project Overview

Customer churn is one of the most critical business problems — losing a customer is 5x more expensive than retaining one. This project performs a full **Exploratory Data Analysis (EDA)** on a telecom customer dataset to:

- Identify **why customers are churning**
- Find the **high-risk customer segments**
- Deliver **actionable recommendations** to reduce churn rate

---

## 🎯 Business Questions Answered

1. What percentage of customers are churning?
2. Which contract type has the highest churn rate?
3. Does tenure affect churn probability?
4. Which services are linked to higher churn?
5. What is the impact of customer service calls on churn?
6. Which customer segment should be prioritized for retention?

---

## 📊 Dataset Details

| Property | Value |
|----------|-------|
| Records | 10,000+ customers |
| Features | 20 columns |
| Target Variable | `Churn` (Yes / No) |
| Source | Telecom Customer Dataset |

**Key Columns:**
- `CustomerID`, `Tenure`, `Contract`, `MonthlyCharges`, `TotalCharges`
- `InternetService`, `TechSupport`, `OnlineSecurity`
- `CustomerServiceCalls`, `Churn`

---

## 🛠️ Tools & Libraries

```python
import pandas as pd          # Data manipulation
import numpy as np           # Numerical operations
import matplotlib.pyplot as plt  # Visualizations
import seaborn as sns        # Statistical plots
from sklearn.preprocessing import LabelEncoder  # Encoding
```

---

## 🔬 EDA Process

### Step 1 — Data Loading & Overview
```python
df = pd.read_csv('customer_churn.csv')
print(df.shape)        # (10000, 20)
print(df.info())
print(df.describe())
print(df.isnull().sum())
```

### Step 2 — Data Cleaning
```python
# Handle missing values
df['TotalCharges'] = pd.to_numeric(df['TotalCharges'], errors='coerce')
df['TotalCharges'].fillna(df['TotalCharges'].median(), inplace=True)

# Drop duplicates
df.drop_duplicates(inplace=True)

# Encode target variable
df['Churn'] = df['Churn'].map({'Yes': 1, 'No': 0})
```

### Step 3 — Univariate Analysis
```python
# Churn distribution
churn_rate = df['Churn'].value_counts(normalize=True) * 100
print(f"Churn Rate: {churn_rate[1]:.2f}%")  # 26.54%

# Plot churn distribution
sns.countplot(x='Churn', data=df, palette='Set2')
plt.title('Customer Churn Distribution')
plt.show()
```

### Step 4 — Bivariate Analysis
```python
# Contract type vs Churn
sns.barplot(x='Contract', y='Churn', data=df, palette='coolwarm')
plt.title('Churn Rate by Contract Type')
plt.show()

# Tenure vs Churn (boxplot)
sns.boxplot(x='Churn', y='tenure', data=df, palette='Set3')
plt.title('Tenure Distribution by Churn')
plt.show()
```

### Step 5 — Correlation Heatmap
```python
corr_matrix = df.corr()
plt.figure(figsize=(12, 8))
sns.heatmap(corr_matrix, annot=True, fmt='.2f', cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()
```

---

## 💡 Key Findings

| Finding | Insight |
|---------|---------|
| **Churn Rate** | 26.5% overall churn rate |
| **Contract Type** | Month-to-month contracts churn 3x more than 2-year contracts |
| **Tenure** | Customers with < 12 months tenure churn 45% more |
| **Monthly Charges** | High charges (>$65/month) strongly correlated with churn |
| **Customer Service Calls** | 4+ calls = 85% churn probability |
| **Internet Service** | Fiber optic users churn 2x more than DSL users |

---

## 📋 Business Recommendations

1. **Offer long-term contract incentives** — Discount for switching from monthly to annual contracts
2. **Onboarding program for new customers** — Focus on first 12 months retention
3. **Proactive outreach at 3 service calls** — Flag and escalate before 4th call
4. **Loyalty pricing** — Reduce monthly charges for high-tenure customers
5. **Fiber optic quality review** — Investigate why fiber users churn more

---

## 📂 Project Structure

```
churn-analysis/
│
├── data/
│   └── customer_churn.csv       # Dataset
│
├── notebooks/
│   └── churn_analysis.ipynb     # Full EDA notebook
│
├── reports/
│   └── churn_analysis_report.pdf  # Written findings
│
├── visualizations/
│   ├── churn_distribution.png
│   ├── contract_churn.png
│   ├── correlation_heatmap.png
│   └── tenure_boxplot.png
│
└── README.md
```

---

## 🚀 How to Run

```bash
# Clone the repo
git clone https://github.com/anjalirai-svg/churn-analysis.git
cd churn-analysis

# Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn jupyter

# Launch notebook
jupyter notebook notebooks/churn_analysis.ipynb
```

---

## 🎓 Skills Demonstrated

- ✅ Exploratory Data Analysis (EDA)
- ✅ Data Cleaning & Preprocessing
- ✅ Statistical Analysis & Correlation
- ✅ Data Visualization (Matplotlib, Seaborn)
- ✅ Business Insight Generation
- ✅ Structured Report Writing

---

## 👩‍💻 Author

**Anjali Rai**
B.Tech Computer Science (IoT) — ABES Institute of Technology, Ghaziabad
📧 anjali.maykhargpur@gmail.com
🔗 [LinkedIn](https://linkedin.com/in/anjalirai06)
