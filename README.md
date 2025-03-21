# Data-Preprocessing
## Project overview
This Data Preprocessing project focuses on essential data preprocessing steps, including data cleaning, augmentation, merging, and feature engineering, to enhance dataset quality for machine learning models. 
## What we implemented 
### Part 1: Data Augmentation on CSV Files
1. Data Cleaning & Handling Missing Values: Used median and mode imputation for missing values.
2. Data Augmentation & Transformation:
Applied SMOTE to balance data distribution.
Used log transformation to normalize skewed transaction amounts.
Generated additional synthetic.

### Part 2: Merging Datasets with Transitive Properties
In  part two first of all I integrate customer data from multiple sources and engineering new features to enhance its analytical potential. The primary goal was to combine customer transaction history with their social media profiles using a provided ID mapping file.
First, the customer_transactions_augmented.csv and customer_social_profiles.csv datasets were linked using the id_mapping.csv file, which provided a bridge between legacy and new customer identifiers. Potential conflicts arising from one-to-many mappings in the ID mapping were addressed by retaining the first encountered mapping.
Following the successful integration, several features were engineered to provide richer insights into customer behavior. These included a Customer Engagement Score, calculated by combining normalized transaction counts and social media engagement scores. Additionally, predictive behavioral features such as moving averages of purchase amounts and monthly total spending were created to capture temporal spending patterns. While text processing via TF-IDF was considered, it was not feasible due to the absence of suitable raw text data in the provided datasets.
The resulting integrated and feature-engineered dataset was then prepared for subsequent analysis by handling missing values and ensuring data integrity. This preprocessed data is now ready for further exploration and potential predictive modeling.

### Part 3: Data Consistency and Quality Checks


## Overview
Part 3 focused on validating and preparing the dataset for machine learning by ensuring data consistency, summarizing numerical properties, and selecting features. The process involved integrity checks, statistical analysis, and feature engineering, culminating in a cleaned dataset.

## 1. Data Integrity Checks
* **Duplicates**: Found repeated customer_id_legacy and transaction_id entries across social_media_platform (e.g., customer 101, transaction 1059). Kept as intentional multi-platform records.
* **Categorical Consistency**: Verified product_category (Books, Clothing, etc.), social_media_platform (Twitter, LinkedIn, etc., with NaN), and review_sentiment (Negative, Positive, etc., with NaN). NaNs retained as valid.
* **Social Profile Validation**: Some transactions with platforms lacked engagement data (e.g., engagement_score). Handled via dropna() in preprocessing.

## 2. Statistical Summarization

* **Numerical Summary**: purchase_amount (mean ≈ 300, max ≈ 526), customer_rating (mean ≈ 3.0, 1-5 range), days_since_last_purchase (some negative, indicating errors).
* 
* **Distribution**: purchase_amount histogram showed right-skew, most values < $400, outliers > $500.

## 3. Feature Selection
* **Correlation**: purchase_amount and avg_purchase_amount, transaction_count and normalized_transactions highly correlated (heatmap analysis).
* **Top Features**: Random Forest identified avg_purchase_amount, customer_rating, days_since_last_purchase, etc., as key predictors. Fixed errors (e.g., ValueError from string IDs) by dropping customer_id_new, legacy_id.

## Outcome
* **Export**: Saved cleaned dataset as final_dataset_ready_7.csv.
* **Key Insights**: Retained multi-platform data, flagged negative days for correction, and selected predictive features for modeling.

## Conclusion

After preprocessing we ended up with  the dataset which is consistent and quality-checked, with duplicates preserved, categoricals validated, and top features identified.

## Report Summary
https://docs.google.com/document/d/1KpQXABNp_eZBaxO-0dPRPZRS7eNTSKKnesABlmx-56k/edit?tab=t.0#heading=h.4vdr5y7p2ll5

## Video Presentation

## Setup Instructions
