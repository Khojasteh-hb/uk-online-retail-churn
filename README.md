# UK Online Retail – Customer Churn Analysis

## Project Overview
This project analyzes customer churn using transactional data from a UK-based online retail company.
Since churn is not explicitly defined in non-contractual retail settings, customer inactivity is used
as a proxy to identify churned customers. The project combines SQL-based exploratory analysis with
Python-based feature engineering and machine learning modeling.

## Dataset
The dataset contains transactional records where each row represents a product purchased within
an invoice. It includes information about purchase dates, quantities, prices, and customer IDs.

Data source:
- UCI Machine Learning Repository:
  https://archive.ics.uci.edu/ml/datasets/Online+Retail

## Project Structure

├── 01_sql_exploratory_analysis.ipynb
├── 02_python_rfm_churn_model.ipynb
├── online_retail.csv
├── online_retail.db
└── README.md


## SQL Exploratory Analysis
The initial data exploration was performed using SQL to understand transaction patterns, validate
data quality, and compute basic aggregations. This step was completed in a DataCamp environment and
saved as a standalone notebook.

File:
- `01_sql_exploratory_analysis.ipynb`

## Python Analysis and Modeling
The main analysis was conducted in Python and includes:
- Data cleaning and preprocessing
- RFM (Recency, Frequency, Monetary) feature engineering
- Churn definition based on customer inactivity
- Train-test split and feature scaling
- Random Forest model training
- Model evaluation using classification metrics and ROC-AUC
- Feature importance analysis

File:
- `02_python_rfm_churn_model.ipynb`

## Tools & Technologies
- SQL (SQLite)
- Python
- Pandas, NumPy
- Scikit-learn
- Matplotlib

## Results
The analysis shows that RFM features provide meaningful signals for detecting customer churn.
Recency was identified as the most influential feature, highlighting the importance of recent
customer activity in churn prediction.

## Future Work
Future improvements may include adding additional behavioral features, testing alternative models,
and further optimizing decision thresholds based on business objectives.

## Author
Hakimeh Khojasteh
