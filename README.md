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
## Report Summary
https://docs.google.com/document/d/1KpQXABNp_eZBaxO-0dPRPZRS7eNTSKKnesABlmx-56k/edit?tab=t.0#heading=h.4vdr5y7p2ll5

## Video Presentation

## Setup Instructions
