# **Data-Preprocessing**
## **Project Overview**
This project focuses on essential data preprocessing steps, including **data cleaning, augmentation, merging, and feature engineering**, to enhance dataset quality for machine learning models.

The assignment is divided into three parts:

1. **Data Augmentation on CSV Files** (Handling missing values & generating synthetic data)
2. **Merging Datasets with Transitive Properties** (Linking datasets)
3. **Data Consistency & Quality Checks** (Ensuring the dataset is ML-ready)

---

## Project Structure

- 📂 **Data-Preprocessing/**
  - 📜 `README.md`
  - 📜 `Report.pdf`
  - 📂 **derived_datasets/**
    - 📜 `customer_transactions_augmented.csv` *(Output of Part 1)*
    - 📜 `final_customer_data_7.csv` *(Output of Part 2)*
    - 📜 `final_dataset_ready_7.csv` *(Output of Part 3)*
  - 📂 **notebooks/**
    - 📜 `Part_1_Data_Augmentation.ipynb`
    - 📜 `Part_2_Merging_Datasets_with_Transitive_Properties.ipynb`
    - 📜 `Part_3_Data_Consistency_and_Quality_Checks.ipynb`
    - 📜 `customer_spending_model.pkl`
  - 📜 `final_data_processing_steps_combined.ipynb`
  - 📜 `machine_learning_model.ipynb`



---

## **What We Implemented**
### **Part 1: Data Augmentation on CSV Files**
#### **1. Data Cleaning & Handling Missing Values**
- Used **median and mode imputation** to handle missing values.
- Checked and removed inconsistencies in the dataset.

#### **2. Data Augmentation & Transformation**
- **SMOTE (Synthetic Minority Over-sampling Technique)** was applied to balance data distribution.
- **Log transformation** was used to normalize skewed transaction amounts.
- **Synthetic data generation** was applied to create additional transactions.

---

### **Part 2: Merging Datasets with Transitive Properties**
#### **Objective:**  
Integrating customer transaction history with social media profiles using **ID mapping**.

#### **Steps Taken:**
1. **Data Integration**
   - Used **id_mapping.csv** to link `customer_id_legacy` and `customer_id_new`.
   - Addressed **one-to-many conflicts** by retaining the first encountered mapping.

2. **Feature Engineering**
   - **Customer Engagement Score:** Combined **normalized transaction counts** and **social media engagement scores**.
   - **Predictive Features:** Created **moving averages of purchase amounts** and **monthly total spending**.
   - Considered **TF-IDF for text processing**, but it was infeasible due to a lack of raw text data.

3. **Final Output**
   - Preprocessed and merged dataset saved as **final_customer_data_7.csv**.

---

### **Part 3: Data Consistency and Quality Checks**
#### **Objective:**  
Validating and preparing the dataset for machine learning by ensuring **data integrity, statistical summarization, and feature selection**.

#### **1. Data Integrity Checks**
- **Duplicates:**  
  - Found repeated `customer_id_legacy` and `transaction_id` across social media platforms.  
  - Retained **intentional multi-platform records** (e.g., customer 101, transaction 1059).
- **Categorical Consistency:**  
  - Verified `product_category`, `social_media_platform`, and `review_sentiment`.  
  - Retained **valid NaN values** where applicable.
- **Social Profile Validation:**  
  - Addressed missing engagement data by applying `dropna()`.

#### **2. Statistical Summarization**
- **Numerical Summary:**  
  - **purchase_amount** (mean ≈ 300, max ≈ 526).  
  - **customer_rating** (mean ≈ 3.0, range: 1-5).  
  - Found **negative values** in `days_since_last_purchase`, indicating possible errors.
- **Data Distribution:**  
  - **purchase_amount histogram** showed a **right-skewed** distribution.  
  - Outliers **above $500** were identified.

#### **3. Feature Selection**
- **Correlation Analysis:**  
  - Found strong relationships between:
    - `purchase_amount` and `avg_purchase_amount`
    - `transaction_count` and `normalized_transactions`
- **Top Feature Selection:**  
  - **Random Forest identified the most important features**, including:
    - `avg_purchase_amount`
    - `customer_rating`
    - `days_since_last_purchase`
  - Resolved **ValueErrors** from string ID columns by dropping `customer_id_new` and `legacy_id`.

#### **4. Final Output**
- **Exported cleaned dataset:** `final_dataset_ready_7.csv`
- **Key insights:**
  - Retained multi-platform data.
  - Flagged **negative values** in `days_since_last_purchase` for correction.
  - Selected **top features** for predictive modeling.


---

## **Report Summary**
 **Report:** [Google Doc Link](https://docs.google.com/document/d/1KpQXABNp_eZBaxO-0dPRPZRS7eNTSKKnesABlmx-56k/edit?tab=t.0#heading=h.4vdr5y7p2ll5)

## **Video Presentation**
 **Video:** [Vimeo Link](https://vimeo.com/1068311978/0313d0d289?ts=0&share=copy)

---

## **How to Run the Project**
### **Requirements**
- **Python 3.8+**
- Required libraries: `pandas`, `numpy`, `scikit-learn`, `matplotlib`, `seaborn`
- **Jupyter Notebook** (for running the `.ipynb` files)

### **Steps to Run**
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo-link.git
   cd Data_Preprocessing_Project

2. Run each notebook sequentially:

   Step 1: notebooks/Part_1_Data_Augmentation.ipynb

   Step 2: notebooks/Part_2_Merging_Datasets_with_Transitive_Properties.ipynb

   Step 3: notebooks/Part_3_Data_Consistency_and_Quality_Checks.ipynb

3. Check processed files in the derived_datasets/ folder.

## Team Contributions

| **Team Member**   | **Contribution**                                      |
|------------------|------------------------------------------------------|
| **Josiane Ishimwe**  | Part 1: Data Augmentation                            |
| **Ines Ikirezi**     | Part 2: Merging Datasets with Transitive Properties  |
| **Liliane Kayitesi**     | Part 3: Data Consistency & Quality Checks and Bonus Challenge           |
