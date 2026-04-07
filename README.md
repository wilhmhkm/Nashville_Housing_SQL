# 🏡 Nashville Housing

## 📌 Executive Summary
 
In this project, I focus on cleaning and transforming raw housing data to make it analysis-ready. I use SQL to standardize the dataset, handle missing values, restructure columns, and remove duplicates.  

The final output is a clean and structured dataset that is ready for visualization in Tableau and suitable for real-world analytical use.

---

## 🛠️ Tools & Technologies
- **SQL Server (Microsoft SQL Server 2019)** – Data cleaning and transformation  
- **SQL (T-SQL)** – Queries, joins, CTEs, and window functions  
- **Microsoft Excel** – Initial dataset format  
- **GitHub** – Version control and portfolio showcase  

---

## 🚀 Data Processing Steps
  
I begin by importing the raw Excel dataset into SQL Server and creating a working table called `NashvilleHousing`.  

I convert the `SaleDate` column from datetime to date format. When direct updates are not effective, I create a new column to ensure consistency.  

I identify null values in the `PropertyAddress` column and use a self-join on `ParcelID` to populate missing entries. I then apply `ISNULL()` to fill any remaining gaps using matching records.  

For the property address, I split the data into `PropertySplitAddress` and `PropertySplitCity` using `SUBSTRING()` and `CHARINDEX()`.  

For the owner address, I split it into `OwnerSplitAddress`, `OwnerSplitCity`, and `OwnerSplitState` using `PARSENAME()` and `REPLACE()` to standardize delimiters.  

I clean the `SoldAsVacant` column by converting `Y/N` values into `Yes/No` using `CASE WHEN` for consistency.  

I create a CTE using `ROW_NUMBER()` and partition the data by ParcelID, Address, SalePrice, SaleDate, and LegalReference. I then remove rows where the row number is greater than one.  

Finally, I remove redundant columns, including original address fields and unused tax-related data, to improve the dataset’s clarity and usability.

---

## 📊 Key Insights

From this project, I observe that raw datasets often contain missing values, inconsistent formatting, and duplicate records.  

I also see that proper data cleaning significantly improves query efficiency, analytical accuracy, and the overall quality of visualizations.  

By restructuring columns into more granular fields, I enable better filtering and grouping in tools like Tableau.  

This project also reinforces how effective SQL is when it comes to handling scalable data cleaning workflows.

---

## 💡 Recommendations

Based on this experience, I focus on a few key practices. I always clean data before moving into visualization or analysis, and I use self-joins to intelligently handle missing values.  

I also standardize categorical data early to maintain consistency, and I avoid deleting raw data in production by working with staging tables instead.  

To scale this approach, I look toward automating cleaning workflows through ETL pipelines. I also see opportunities to extend this project further by adding exploratory data analysis, building dashboards in Tableau, and integrating Python for more advanced processing.
