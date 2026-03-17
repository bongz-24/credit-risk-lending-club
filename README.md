# Credit Risk Modeling Using Lending Club Data

## Project Overview

This project aims to build a machine learning model that predicts the probability that a borrower will default on a loan. The model will be trained using historical lending data from the Lending Club platform.

Credit risk modeling is a critical task in financial institutions. Banks and lending platforms use these models to estimate the likelihood of borrower default and make informed lending decisions.

The final goal of this project is to develop an end-to-end credit risk system that includes:

- Data cleaning and preprocessing
- Exploratory data analysis (EDA)
- Feature engineering
- Machine learning model training
- Model evaluation
- A deployed prediction interface using Streamlit

---

# Dataset Description

The dataset used in this project is the **Lending Club Loan Dataset**, which contains historical records of loans issued through the Lending Club peer-to-peer lending platform.

Dataset characteristics:

- Number of observations: **2,260,668 loans**
- Number of variables: **145 columns**
- Dataset size: **~2.4 GB**

The dataset contains information about:

- Borrower characteristics
- Loan characteristics
- Credit history variables
- Loan repayment outcomes

Examples of features include:

- `loan_amnt`
- `int_rate`
- `annual_inc`
- `dti`
- `emp_length`
- `home_ownership`
- `revol_util`
- `loan_status`

---

# Project Objective

The main objective is to build a **binary classification model** that predicts whether a borrower will default on a loan.

The target variable will be defined as:

| Loan Status | Target |
|-------------|-------|
| Fully Paid | 0 |
| Charged Off | 1 |

Meaning:

- **0 = loan successfully repaid**
- **1 = borrower defaulted**

Loans that are still active (e.g., `Current`, `Late`, `In Grace Period`) will be excluded from the training dataset because their final outcome is unknown.

---
Explanation:

- **data/raw** → original dataset
- **notebooks** → exploratory analysis and experiments
- **src** → reusable Python scripts (feature engineering, modeling, etc.)
- **models** → saved trained models
- **app** → Streamlit web application for predictions

---

# Work Completed So Far

## Project Setup

The following steps have been completed:

- Created GitHub repository
- Initialized Git version control
- Connected project to GitHub remote repository
- Created project folder structure
- Downloaded Lending Club dataset
- Excluded dataset from Git tracking due to large file size

---

## Dataset Loading

The dataset was successfully loaded using **pandas**.

Key results:

- Number of rows: **2,260,668**
- Number of columns: **145**
- Memory usage: **~2.4 GB**

This confirms that the dataset is large and requires efficient preprocessing.

---

## Initial Data Audit

Initial inspection of the dataset was performed to understand:

- dataset dimensions
- column types
- dataset structure

The dataset contains:

- **105 numeric columns**
- **4 integer columns**
- **36 categorical/string columns**

---

## Missing Value Analysis

A missing value audit was conducted.

Several columns contain extremely high levels of missing data.

Examples include:

- `hardship_amount`
- `hardship_status`
- `hardship_reason`
- `settlement_amount`
- `settlement_term`

These columns are mostly related to rare financial hardship situations and will be evaluated during feature cleaning.

---

## Target Variable Exploration

The distribution of the loan outcome variable (`loan_status`) was analyzed.

| Loan Status | Count |
|-------------|------|
| Fully Paid | 1,041,952 |
| Current | 919,695 |
| Charged Off | 261,655 |
| Late (31-120 days) | 21,897 |
| In Grace Period | 8,952 |
| Late (16-30 days) | 3,737 |
| Other | small counts |

Because **Current and Late loans are still active**, they will not be used for training.

Only completed loans will be kept:

- **Fully Paid**
- **Charged Off**

---

# Key Challenges in the Dataset

## Data Leakage

Some variables contain information that becomes available **after the loan outcome is known**.

Examples include:

- `total_pymnt`
- `recoveries`
- `collection_recovery_fee`
- `last_pymnt_amnt`

These variables must be removed because they would allow the model to “cheat”.

---

## Missing Data

Many variables contain high proportions of missing values. Decisions must be made regarding whether to:

- drop these columns
- encode missingness
- impute missing values

---

## Class Imbalance

The dataset contains more non-default loans than default loans.

Estimated distribution after filtering:

- ~80% Fully Paid
- ~20% Charged Off

Model training will need to account for this imbalance.

---

# Current Stage of the Project

We are currently in the **Data Cleaning phase**.

Completed stages:

- Data loading
- Dataset inspection
- Missing value analysis
- Target variable exploration

Current step:

- Filter dataset to completed loans
- Create binary target variable
- Remove data leakage features

---

# Next Steps

The upcoming stages of the project include:

1. Filter dataset to only completed loans
2. Create the binary target variable
3. Remove leakage variables
4. Perform exploratory data analysis (EDA)
5. Engineer predictive features
6. Train machine learning models
7. Evaluate model performance
8. Build a Streamlit application for credit risk prediction

---

# Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Streamlit
- Git / GitHub

