# UK Online Retail Churn Prediction

## Overview

Customer retention is a key driver of growth in e-commerce businesses. This project analyzes transactional retail data and builds machine learning models to identify customers at risk of churn.

In non-contractual retail settings, churn is not explicitly observed and must be inferred from customer inactivity. In this project, churn is defined using a forward-looking 90-day inactivity window.

Beyond prediction, the analysis focuses on identifying high-value customers and understanding revenue concentration, enabling a value-driven approach to churn management.

Additionally, an interactive Tableau dashboard is developed to communicate key business insights and support decision-making.

---

## Key Highlights

- Built an end-to-end churn prediction pipeline using time-based splitting to prevent data leakage  
- Engineered RFM (Recency, Frequency, Monetary) features to capture customer behavior  
- Compared Logistic Regression and Random Forest models with a recall-focused evaluation strategy  
- Performed SQL-based exploratory analysis for data validation and business insight generation  
- Developed an interactive Tableau dashboard to visualize revenue patterns and customer segments  

---

## Objectives

- Analyze customer purchasing behavior using SQL  
- Define churn in a non-contractual retail setting  
- Build and compare machine learning models for churn prediction  
- Generate actionable insights to support customer retention strategies  

---

## Project Structure

```text
uk-online-retail-churn/
├── 01_sql_exploratory_analysis.ipynb   # SQL-based EDA & business analysis
├── 02_python_rfm_churn_model.ipynb    # Feature engineering & ML modeling
├── data/
└── README.md
```

---

## Dataset

The dataset contains over 500,000 transactional records from a UK-based online retail store, including:

- Customer ID  
- Invoice date  
- Quantity and unit price  
- Country  

### Data Preprocessing

- Removed records with missing Customer IDs to enable customer-level analysis  
- Filtered out transactions with non-positive quantities or prices (returns/cancellations)  
- Restricted the analysis to UK customers to ensure consistency and sufficient data coverage  

---

## Exploratory Data Analysis

Key findings:

- A large proportion of customers are one-time buyers  
- Revenue is highly concentrated among a small group of high-value customers  
- Strong seasonality is observed in purchasing behavior, with peaks during holiday periods  

These insights support defining churn using a 90-day inactivity window to avoid misclassifying seasonal customers as churned.

---

## Interactive Dashboard (Tableau)

An interactive Tableau dashboard was developed to translate analytical findings into actionable business insights.

[View Dashboard on Tableau Public](https://public.tableau.com/app/profile/hakimeh.khojasteh/viz/UK-Online-Retail/UKOnlineRetail)

### Dashboard Highlights

- **Revenue Seasonality**: A clear peak is observed during the holiday season (Nov–Dec)  
- **Customer Segmentation**: Repeat customers (~65%) generate ~93% of total revenue  
- **Revenue Distribution**: Revenue is more broadly distributed across customers, deviating from the classic 80/20 pattern  
- **Pareto Analysis**: Approximately 85% of customers contribute to 80% of total revenue  

### Key Business Insight

Revenue is primarily driven by repeat customers, while overall revenue remains relatively distributed across the broader customer base.

This suggests that improving customer retention can have a significant impact on revenue, particularly by increasing the proportion of repeat buyers.

<img width="1278" height="1050" alt="dashboard" src="https://github.com/user-attachments/assets/b2720c92-45ad-423d-88ff-4cbc01c2f722" />

---

## Feature Engineering (RFM)

Customer-level features are constructed using the RFM framework:

- **Recency**: Number of days since the last purchase  
- **Frequency**: Number of transactions  
- **Monetary**: Total customer spending  

These features provide a compact and interpretable representation of customer behavior and are widely used in churn modeling.

---

## Churn Definition

A customer is labeled as churned if no purchases are made within 90 days following a reference date.

This approach:

- Reflects real-world customer behavior in non-contractual retail settings  
- Prevents data leakage by using a forward-looking observation window  
- Accounts for seasonality in purchasing patterns  

---

## Modeling

Two machine learning models are trained and compared for churn prediction, with a focus on recall due to the business objective of identifying at-risk customers.

### Logistic Regression
- Class weight: balanced  
- Trained on standardized features  
- Provides an interpretable baseline model  

**Performance:**
- ROC-AUC: ~0.76  
- Recall: ~0.84  


### Random Forest
- n_estimators = 300  
- max_depth = 8  
- class_weight = balanced  
- Captures non-linear relationships  

**Performance:**
- ROC-AUC: ~0.75  
- Recall: ~0.76  

---

## Model Evaluation

Model performance is evaluated using:

- **ROC-AUC** (overall discrimination ability)  
- **Recall** (ability to correctly identify churned customers)  

Logistic Regression slightly outperforms Random Forest in both ROC-AUC and recall.

Given that the primary business objective is to identify at-risk customers, recall is prioritized as the key evaluation metric.

Therefore, Logistic Regression is selected as the final model.

- ROC curve comparison between models
<img width="386" height="278" alt="image" src="https://github.com/user-attachments/assets/32b3e9de-57e4-4f22-9dca-f5754cecf02c" />

--- 

## Feature Importance

Feature importance analysis shows:

- Monetary is the most influential feature  
- Recency is the second strongest predictor  
- Frequency has the lowest impact among RFM features  

This indicates that customer spending behavior is the strongest signal for churn.

- Feature importance plot (Random Forest) 
<img width="424" height="280" alt="image" src="https://github.com/user-attachments/assets/be51011e-724d-4c36-83fd-11515a917f07" />

---

## Business Insights

- High-spending customers are the strongest drivers of churn risk and overall revenue  
- Customer value (Monetary) is more informative than purchase frequency alone  
- Early detection of disengagement among high-value customers is critical  

---

## Recommendations

- Prioritize retention strategies for high-value customers  
- Use personalized offers and loyalty incentives to retain top spenders  
- Monitor inactivity signals, particularly among high-monetary customers  

---

## Future Work

- Explore additional models (e.g., XGBoost, LightGBM)  
- Extend the dashboard with real-time or near real-time data integration  
- Incorporate additional features (e.g., customer demographics, time between purchases)  

---

## Tech Stack

- **Python** (pandas, scikit-learn)  
- **SQL**  
- **Jupyter Notebook**  
- **Tableau** (data visualization & dashboarding)  

---

## Author

Hakimeh Khojasteh
