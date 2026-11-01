# Task 02 – Data Cleaning & Feature Engineering

## Project Overview
This project focuses on cleaning and preparing a Retail-Store Sales Dataset using Python. The objective is to improve data quality, handle missing values, investigate potential outliers, encode categorical variables, scale numerical features, and create new features for further analysis.

## Dataset Information
- **Dataset Name:** Retail-Store Sales Dataset
- **Original Dataset Shape:** 12,575 rows × 11 columns
- **Transaction Date Range:** January 1, 2022 – January 18, 2025

### Dataset Columns
1. Transaction ID
2. Customer ID
3. Category
4. Item
5. Price Per Unit
6. Quantity
7. Total Spent
8. Payment Method
9. Location
10. Transaction Date
11. Discount Applied

## Tools and Technologies
- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Google Colab
- Jupyter Notebook

## Tasks Performed

### 1. Initial Data Inspection
- Checked dataset dimensions and column names.
- Examined data types and statistical information.
- Checked missing values and duplicate records.
- Inspected the first five rows.

### 2. Missing Value Analysis
Identified missing values in the following columns:

| Column | Missing Values |
|---|---:|
| Item | 1,213 |
| Price Per Unit | 609 |
| Quantity | 604 |
| Total Spent | 604 |
| Discount Applied | 4,199 |

### 3. Missing Value Treatment
- Replaced missing Item values with `Unknown`.
- Filled missing Price Per Unit and Quantity values using their median.
- Calculated missing Total Spent values using Price Per Unit × Quantity where possible.
- Filled remaining missing Total Spent values using the median.
- Replaced missing Discount Applied values with `Unknown`.

### 4. Duplicate Record Check
- Checked the dataset for exact duplicate rows.
- No duplicate records were found.
- Dataset dimensions remained unchanged.

### 5. Outlier Detection and Investigation
Used the Interquartile Range (IQR) method to identify potential outliers.

| Numerical Feature | Potential Outliers |
|---|---:|
| Price Per Unit | 0 |
| Quantity | 0 |
| Total Spent | 60 |

- Investigated all 60 potential outliers in Total Spent.
- Found that 56 records matched Price Per Unit × Quantity.
- Identified 4 records that did not match the calculation after imputation.
- Retained the records rather than automatically deleting them.

### 6. Data Type Conversion
- Converted Transaction Date into datetime format.
- Converted Transaction ID and Customer ID into string data types.
- Checked the updated data types.

### 7. Categorical Variable Encoding
- Converted Discount Applied into numerical values:
  - True = 1
  - False = 0
  - Unknown = -1
- Applied one-hot encoding to Category, Payment Method, and Location.
- Encoded dataset shape: **12,575 × 21**.

### 8. Feature Scaling
Applied `MinMaxScaler` to:
- Price Per Unit
- Quantity
- Total Spent

The scaled values ranged from 0 to 1.

### 9. Feature Engineering
Created five new features:
- Transaction Year
- Transaction Month
- Day of Week
- Price Category
- Quantity Category

Price categories: Low, Medium, High.

Quantity categories: Small, Medium, Large.

The feature-engineered dataset shape was **12,575 × 16**.

### 10. Descriptive Statistics Before and After Cleaning
Compared numerical features before and after preprocessing.

| Feature | Original Mean | Cleaned Mean |
|---|---:|---:|
| Price Per Unit | 23.37 | 23.35 |
| Quantity | 5.54 | 5.56 |
| Total Spent | 129.65 | 130.21 |

The number of available observations increased after missing values were handled.

### 11. Final Data Quality Check
The final cleaned dataset was checked for missing values, duplicates, data types, and transaction dates.

- Final cleaned dataset shape: **12,575 × 11**
- Missing values: **0**
- Duplicate rows: **0**
- Date range: January 1, 2022 – January 18, 2025

### 12. Automated Preprocessing Pipeline Using Scikit-learn
Implemented an automated preprocessing pipeline using:

- `SimpleImputer`
- `MinMaxScaler`
- `OneHotEncoder`
- `ColumnTransformer`
- `Pipeline`

Numerical features were imputed and scaled, while categorical features were imputed and one-hot encoded.

**Final processed dataset shape: 12,575 × 229.**

Final verification confirmed:
- No missing values.
- No infinite values.
- Pipeline completed successfully.

## Key Findings
- The original dataset contained missing values in five columns.
- No exact duplicate records were found.
- Sixty potential outliers were detected in Total Spent.
- Fifty-six flagged records matched the price × quantity calculation.
- Four flagged records did not match after imputation and require further investigation.
- Five new features were created through feature engineering.
- The automated Scikit-learn pipeline successfully processed the dataset into 229 features.

## Important Data Note
Median imputation was used for missing numerical values. Some missing Total Spent values were calculated using Price Per Unit and Quantity. Therefore, some cleaned values are estimates rather than original observations.

The four inconsistent transactions were retained because their original missing values prevent independent verification. Potential outliers were not automatically removed.

## Project Files
This repository contains the project notebook, documentation, dataset (if included), and screenshots of the implementation and outputs.

## How to Run the Project
1. Clone or download this repository.
2. Open `Task_02 - Data Cleaning & Feature Engineering.ipynb` in Google Colab or Jupyter Notebook.
3. Upload the required CSV dataset when prompted.
4. Run the notebook cells in order.
5. Review the outputs and visualizations.

## Conclusion
This project demonstrates the process of data cleaning and feature engineering using Python. It covers missing-value treatment, duplicate checking, outlier investigation, data type conversion, categorical encoding, feature scaling, and feature creation. An automated preprocessing pipeline was also implemented successfully using Scikit-learn.

The project provided practical experience in preparing a real-world retail sales dataset for further data analysis and machine learning workflows.
