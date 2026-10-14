# OIBSIP Task 3 — Cleaning Data

## 📌 Project Overview

This project is part of the **Oasis Infobyte (OIBSIP) Data Analytics Internship — Level 1, Task 3: Cleaning Data**.

The objective is to clean and prepare a deliberately dirty cafe sales dataset for further analysis by identifying and handling missing values, invalid entries, duplicates, inconsistent data, outliers, and incorrect data types.

---

## 📂 Dataset

**Dataset:** Cafe Sales – Dirty Data for Cleaning Training

The original dataset contains **10,000 rows and 8 columns**:

| Column           | Description                            |
| ---------------- | -------------------------------------- |
| Transaction ID   | Unique identifier for each transaction |
| Item             | Product purchased                      |
| Quantity         | Number of items purchased              |
| Price Per Unit   | Price of one item                      |
| Total Spent      | Total amount spent in the transaction  |
| Payment Method   | Payment method used                    |
| Location         | Transaction location                   |
| Transaction Date | Date of the transaction                |

The original dataset contained missing values, `UNKNOWN` and `ERROR` entries, and incorrect data types.

---

## 🛠️ Technologies Used

- Python
- Pandas
- NumPy
- Jupyter Notebook

---

## 🧹 Data Cleaning Process

### 1. Data Quality Assessment

An initial data quality report was created to identify:

- Missing values
- Duplicate rows
- Incorrect data types
- Invalid values
- Numerical value ranges

The original dataset contained **10,000 rows** and all columns were initially loaded as object/string-like data types.

---

### 2. Missing Data Handling

Different strategies were applied according to the type of variable.

#### Numerical Columns

`Quantity`, `Price Per Unit`, and `Total Spent` contained invalid or missing values.

Invalid values such as `UNKNOWN` and `ERROR` were converted to missing values and replaced using the **median** of the valid observations.

The median was chosen because it is less sensitive to extreme values than the mean.

#### Categorical Columns

`Item`, `Payment Method`, and `Location` contained missing or invalid categorical values.

These values were replaced using the **mode** of each column.

The mode was selected because it is appropriate for categorical variables and preserves the existing categories.

#### Transaction Date

The valid transaction dates were converted to datetime format.

There were **460 invalid or missing transaction dates**:

- 159 `UNKNOWN`
- 142 `ERROR`
- 159 missing values

Because reliable dates could not be inferred for these records, the affected rows were removed.

This resulted in **9,540 remaining records**.

---

## 🔄 Standardisation

Categorical values were checked for consistency.

The final categories were:

- **Item:** Coffee, Cake, Cookie, Salad, Smoothie, Juice, Sandwich, Tea
- **Payment Method:** Credit Card, Cash, Digital Wallet
- **Location:** Takeaway, In-store

The `Transaction Date` column was converted to a datetime type.

The valid dates range from:

**January 1, 2023 to December 31, 2023**

---

## 📊 Outlier Detection

The **Interquartile Range (IQR)** method was used to detect outliers in the numerical columns.

### Quantity

- Q1: 2.0
- Q3: 4.0
- IQR: 2.0
- Bounds: -1.0 to 7.0
- Outliers: **0**

No outliers were detected.

### Price Per Unit

- Q1: 2.0
- Q3: 4.0
- IQR: 2.0
- Bounds: -1.0 to 7.0
- Outliers: **0**

No outliers were detected.

### Total Spent

- Q1: 4.0
- Q3: 12.0
- IQR: 8.0
- Bounds: -8.0 to 24.0
- Detected outliers: **250**

All 250 detected values were **25.0**.

Although these values were identified as statistical outliers by the IQR method, they were retained because `25.0` is a valid value in the dataset and there was no evidence that these records represented data-entry errors.

---

## 🔧 Data Type Correction

The final data types were corrected as follows:

| Column           | Final Data Type |
| ---------------- | --------------- |
| Transaction ID   | String          |
| Item             | String          |
| Quantity         | Integer         |
| Price Per Unit   | Float           |
| Total Spent      | Float           |
| Payment Method   | String          |
| Location         | String          |
| Transaction Date | Datetime        |

All **8 columns** have appropriate data types after cleaning.

---

## 📈 Before vs. After

| Metric               | Before Cleaning | After Cleaning |
| -------------------- | --------------: | -------------: |
| Row count            |          10,000 |          9,540 |
| Total missing values |           7,226 |              0 |
| Duplicate rows       |               0 |              0 |
| Correct data types   |           0 / 8 |          8 / 8 |

---

## 📁 Project Structure

```text
DataAnalytics-L1-CleaningData/
│
├── 01_data_cleaning.ipynb
│
├── data/
│   ├── dirty_cafe_sales.csv
│   └── cleaned_cafe_sales.csv
│
└── README.md
```

### Files

- `01_data_cleaning.ipynb` — Jupyter Notebook containing the complete cleaning process.
- `data/dirty_cafe_sales.csv` — Original dirty dataset.
- `data/cleaned_cafe_sales.csv` — Final cleaned dataset.
- `README.md` — Project documentation.

---

## ✅ Final Result

The dataset was successfully cleaned and prepared for further analysis.

The final dataset contains:

- **9,540 records**
- **8 columns**
- **0 missing values**
- **0 duplicate rows**
- **Correct data types**
- Standardized categorical values
- Properly formatted transaction dates
- Outliers evaluated using the IQR method

The cleaned dataset is saved as:

`data/cleaned_cafe_sales.csv`

---

## 🎯 Internship Task

**Oasis Infobyte — OIBSIP Data Analytics Internship**

**Level 1 — Task 3: Cleaning Data**

**Author:** Majd Zouaoui
