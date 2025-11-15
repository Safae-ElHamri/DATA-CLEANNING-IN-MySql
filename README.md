# 🧹 Data Cleaning Project in MySQL  
Cleaning and Preparing Layoff Data for Analysis (2022 Dataset)

## 📌 Project Overview
This project focuses on **cleaning and preparing raw layoff data** using **MySQL**.  
The dataset contains global layoff information collected during 2022 and includes common issues such as duplicates, missing values, inconsistent formats, and unstructured date fields.

The goal of this project is to transform messy raw data into a **clean, consistent, analysis-ready dataset**.

---

## 🗂️ Project Files
| File | Description |
|------|-------------|
| `Portfolio Project - Data Cleaning.sql` | Full SQL script used to clean and transform the dataset |
| `layoffs.csv` | Raw dataset imported from Kaggle |

---

## 🧬 Database Schema (After Cleaning)
Below is the clean, structured schema of the final table `layoffs_staging2`.

+--------------------------+
| layoffs_staging2 |
+--------------------------+
| company | TEXT
| location | TEXT
| industry | TEXT
| total_laid_off | INT
| percentage_laid_off | TEXT
| date | DATE
| stage | TEXT
| country | TEXT
| funds_raised_millions | INT
+--------------------------+


---

## ✔️ Data Cleaning Steps
The following pipeline was applied to transform the raw data:

### **1️⃣ Create a Staging Table**
A copy of the raw table is created to apply all cleaning procedures safely.

### **2️⃣ Identify and Remove Duplicates**
- Used `ROW_NUMBER()` window function to detect duplicates.
- Removed duplicated rows based on all relevant fields.

### **3️⃣ Standardize and Fix Inconsistent Data**
Performed standardization on:
- Industry names (e.g., `CryptoCurrency`, `Crypto Currency` → `Crypto`)
- Country names (removed trailing punctuation such as `"United States."`)
- Converted date strings using `STR_TO_DATE()` and updated column type to `DATE`

### **4️⃣ Handle Missing Values**
- Replaced empty strings with NULL.
- Filled NULL industry values using rows from the same company where data was available.

### **5️⃣ Remove Non-Useful Rows**
Rows where both:
- `total_laid_off IS NULL` **and**  
- `percentage_laid_off IS NULL`  
were deleted.

These rows add no analytical value.

---

## 🛠️ Technologies Used
- **MySQL**
- **Window Functions (`ROW_NUMBER()`)**
- **CTE (Common Table Expressions)**
- **Data Cleaning & Standardization Techniques**
- **Date Formatting & Type Conversion**

---

## 📊 Dataset Source
Kaggle Dataset:  
🔗 https://www.kaggle.com/datasets/swaptr/layoffs-2022

---

## 🚀 Final Output
After the cleaning pipeline:
- All duplicates removed  
- Industries and countries standardized  
- Dates converted and unified  
- Missing values handled appropriately  
- Final dataset is fully ready for EDA, BI dashboards, and statistical analysis
