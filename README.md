# 🏡 Nashville Housing Data Cleaning Project (SQL + Tableau)

## 📌 Executive Summary
This project focuses on cleaning and transforming raw housing data to make it analysis-ready. Using SQL, the dataset was standardized, missing values were handled, columns were restructured, and duplicates were removed. The final output is a clean, structured dataset suitable for visualization in Tableau and real-world analytical use.

---

## 🛠️ Tools & Technologies
- **SQL Server (Microsoft SQL Server 2019)** – Data cleaning and transformation  
- **SQL (T-SQL)** – Queries, joins, CTEs, and window functions  
- **Microsoft Excel** – Initial dataset format  
- **GitHub** – Version control and portfolio showcase  
- **Tableau** – Data visualization (post-cleaning phase)  

---

## 🚀 Data Processing Steps

### 1. Data Import
- Imported raw Excel dataset into SQL Server
- Created a working table: `NashvilleHousing`

### 2. Standardizing Date Format
- Converted `SaleDate` from datetime to date format
- Created a new column to ensure consistency when direct updates failed

### 3. Handling Missing Values
- Identified null values in `PropertyAddress`
- Used **self-join on ParcelID** to populate missing addresses
- Applied `ISNULL()` to fill gaps using existing matching records

### 4. Splitting Columns (Feature Engineering)
#### Property Address
- Split into:
  - `PropertySplitAddress`
  - `PropertySplitCity`
- Used:
  - `SUBSTRING()`
  - `CHARINDEX()`

#### Owner Address
- Split into:
  - `OwnerSplitAddress`
  - `OwnerSplitCity`
  - `OwnerSplitState`
- Used:
  - `PARSENAME()`
  - `REPLACE()` (comma → period)

### 5. Data Standardization
- Cleaned `SoldAsVacant` column:
  - Converted `Y/N` → `Yes/No`
- Implemented using `CASE WHEN`

### 6. Removing Duplicates
- Created CTE with `ROW_NUMBER()`
- Partitioned by:
  - ParcelID, Address, SalePrice, SaleDate, LegalReference
- Removed rows where `row_num > 1`

### 7. Dropping Unused Columns
- Removed redundant columns:
  - Original address columns
  - Tax-related unused fields
- Improved dataset usability and clarity

---

## 📊 Key Insights
- Raw datasets often contain:
  - Missing values
  - Inconsistent formatting
  - Redundant and duplicate records
- Data cleaning significantly improves:
  - Query efficiency
  - Analytical accuracy
  - Visualization quality
- Structured columns (split fields) enable:
  - Better filtering and grouping in Tableau
- SQL is highly effective for scalable data cleaning workflows

---

## 💡 Recommendations
- Always clean data **before** visualization or analysis  
- Use **self-joins** to intelligently fill missing values  
- Normalize categorical data early (e.g., Yes/No consistency)  
- Avoid deleting raw data in production environments—use staging tables instead  
- Automate cleaning workflows (ETL pipelines) for scalability  
- Extend this project by:
  - Adding exploratory data analysis (EDA)
  - Building dashboards in Tableau
  - Integrating Python for advanced processing  
