# Scalable Credit Card Fraud Detection & Behavior Analysis


### Project Overview

This project focuses on detecting fraudulent credit card transactions and analyzing user behavior patterns using PySpark on large-scale datasets. The goal is to build an end-to-end Big Data pipeline that ingests raw banking logs, performs feature engineering and exploratory data analysis (EDA), and trains a machine learning model to detect fraud efficiently.

## Datasets

The analysis is based on three relational datasets:

| Dataset | Description |
|---------|-------------|
| Transactions | Logs of user transactions with details such as amount, merchant, location, errors, and card usage. |
| Cards | Information on users’ credit/debit cards including type, brand, credit limit, chip availability, and fraud indicators. |
| Users | Demographic and financial data about users, including age, income, credit score, and debt. |

* Source: Provided ZIP file containing raw CSVs and fraud labels.

### Project Structure


      project_root/

       ├── data/
       │    ├── processed       
       │    ├── raw
       │
       ├── notebooks/
       │        
       ├── results/
       

## Key Steps & Methodology

### 1. Data Ingestion & Cleaning

- Loaded datasets using PySpark.
- Checked for nulls, duplicates, and inconsistent values.
- Cleaned numeric and categorical columns.

### 2. Feature Engineering

- Extracted hour, month, and year from transaction timestamps.
- Detected impossible travel between distant locations within short intervals.
- Identified high-velocity card usage (multiple transactions in 10 minutes).

  
### 3. Exploratory Data Analysis (EDA)

- Analyzed errors by merchant and user.
- Computed distribution of fraud-risk features.
- Determined travel risk levels and high-velocity transaction statistics.

### 4. Machine Learning Model

Created a balanced dataset using all fraud cases and equal non-fraud samples.

**Special Features**: `day_hour`, `chip_indexed`, `is_high_velocity`, `impossible_travel`.

**Model**: Random Forest Classifier.

**Evaluation metrics**:

    - AUC-ROC: 0.9632
    - Precision: 0.9535
    - Recall: 0.9486
    - F1-Score: 0.9485

**Feature Importance**: `impossible_travel` > `is_high_velocity` > `chip_indexed` > `day_hour` > `amount_clean`.


## How to Run

1. Clone the repository.
2. Ensure you have **PySpark 4.1.0** installed and configured.
3. Place the raw datasets in the /data/raw/ folder.
4. Run the notebook CreditCardFraudDetection.ipynb step by step.
5. The processed outputs and model will be saved in /data/processed/ and /models/.

## Project Outcome

Successfully processed 13M+ transactions, 6k cards, and 2k users.

Built a scalable fraud detection pipeline using PySpark.

Identified key fraud patterns such as impossible travel and high-velocity usage.

Trained a high-performing Random Forest model with strong AUC, precision, and recall.
