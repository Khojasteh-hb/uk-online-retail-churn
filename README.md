# UK Online Retail Churn Prediction

## Overview
Customer retention is a key driver of growth in e-commerce businesses. In this project, transactional data is analyzed and machine learning models are built to identify customers at risk of churn.

Since churn is not explicitly defined in retail, it is approximated using a 90-day inactivity window. In addition to prediction, this project focuses on identifying high-value customers, making it a value-driven churn analysis.

---

## Objectives
- Analyze customer purchasing behavior using SQL
- Define churn in a non-subscription setting
- Build and compare multiple machine learning models
- Provide actionable insights for retention strategies

---

## Project Structure
```text
uk-online-retail-churn/
├── 01_sql_exploratory_analysis.ipynb
├── 02_python_rfm_churn_model.ipynb
├── data/
└── README.md
```

---


---

## Dataset
The dataset contains over 500,000 transactions from an online retail store, including:
- Customer ID
- Invoice date
- Quantity and price
- Country

### Data Preprocessing
- Removed missing Customer IDs for customer-level analysis
- Filtered out negative values (returns/cancellations)
- Restricted analysis to UK customers for consistency

---

## Exploratory Data Analysis

Key findings:
- Majority of customers are one-time buyers
- Revenue is concentrated among a small group of high-value users
- Strong seasonality patterns in purchasing behavior

These insights support defining churn using a 90-day inactivity window.

---

## Feature Engineering (RFM)

Customer-level features:
- Recency: Days since last purchase
- Frequency: Number of transactions
- Monetary: Total spend

---

## Churn Definition

A customer is labeled as churned if no purchase is made within 90 days after a reference date.

This approach:
- Reflects real-world retail behavior
- Avoids data leakage
- Accounts for seasonality

---

## Modeling

Two models are trained and compared:

### Logistic Regression
- Class weight: balanced
- Trained on scaled features
- Provides an interpretable baseline model

Performance:
- ROC-AUC: ~0.76
- Recall: ~0.84

---

### Random Forest
- n_estimators = 300
- max_depth = 8
- class_weight = balanced
- Handles non-linear relationships

Performance:
- ROC-AUC: ~0.75
- Recall: ~0.76

---

## Model Evaluation

Evaluation focuses on:
- ROC-AUC (overall discrimination)
- Recall (ability to detect churned customers)

Logistic Regression slightly outperforms Random Forest in both ROC-AUC and recall.

Since the primary business objective is to identify at-risk customers, recall is prioritized.

Therefore, Logistic Regression is selected as the final model.

---

## Visualization

- ROC Curve comparison between models
<img width="386" height="278" alt="image" src="https://github.com/user-attachments/assets/32b3e9de-57e4-4f22-9dca-f5754cecf02c" />

- Feature importance plot (Random Forest)  
<img width="424" height="280" alt="image" src="https://github.com/user-attachments/assets/be51011e-724d-4c36-83fd-11515a917f07" />

---

## Feature Importance

Feature importance analysis shows:

- Monetary is the most influential feature  
- Recency is the second strongest predictor  
- Frequency has the lowest impact among RFM features  

This indicates that customer spending behavior is the strongest signal for churn.

---

## Business Insights

- High-spending customers play a critical role in churn prediction  
- Customer value is more informative than purchase frequency alone  
- Early identification of disengagement among valuable users is crucial  

---

## Recommendations

- Prioritize retention efforts for high-value customers  
- Use personalized offers and loyalty incentives to retain top spenders  
- Monitor inactivity signals (especially among high-monetary users)  

---

## Future Work
- Add Tableau dashboard for business monitoring  
- Test additional models (e.g., XGBoost)  
- Deploy model for real-time prediction  

---

## Tech Stack
- Python (pandas, scikit-learn)  
- SQL  
- Jupyter Notebook  
- Tableau (in progress)  

---

## Author
Hakimeh Khojasteh
