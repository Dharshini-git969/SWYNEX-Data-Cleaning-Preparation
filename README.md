# SWYNEX – Data Cleaning & Preparation

## Project Overview

This project was completed as part of my SWYNEX Technologies internship.

The objective was to clean and prepare the UCI Online Retail dataset by identifying and handling missing values, duplicate records, incorrect data types, and unusual transaction values while preserving meaningful business information.

## Dataset

**Dataset:** Online Retail  
**Source:** UCI Machine Learning Repository  
**Original Records:** 541,909  
**Original Columns:** 8

The dataset contains retail transaction information including invoice numbers, product codes, descriptions, quantities, invoice dates, unit prices, customer IDs, and countries.

## Tools Used

- Python
- Pandas
- Google Colab
- GitHub

## Data Quality Findings

The initial investigation identified:

- 1,454 missing Description values
- 135,080 missing CustomerID values
- 5,268 exact duplicate records
- 10,624 negative-quantity records
- 2 negative UnitPrice records
- 2,515 zero-price records
- 3 non-standard adjustment records

## Cleaning Performed

### 1. Duplicate Removal
Removed 5,268 exact duplicate records.

### 2. Description Cleaning
Removed leading and trailing whitespace and standardized descriptions to uppercase.

Whitespace-only descriptions became missing values after cleaning.

### 3. CustomerID Data Type
Converted CustomerID from `float64` to Pandas nullable `Int64`.

Missing CustomerIDs were retained because there was not enough information to reliably assign customer identities.

### 4. Adjustment Records
Removed 3 records with invoice numbers beginning with `A`. These were identified as bad-debt adjustment records rather than standard retail transactions.

### 5. Cancellation and Return Records
Negative quantities were retained because they represent meaningful cancellation or return transactions.

An `IsCancellation` column was added to identify records with invoice numbers beginning with `C`.

### 6. Zero-Price Records
Zero-price records were retained because inspection showed that many represented operational or non-standard records such as damaged, found, check, adjustment, or unsaleable items.

They were not removed without sufficient evidence that they were invalid.

## Final Dataset

After cleaning:

- **Final records:** 536,638
- **Final columns:** 9
- **Duplicate records remaining:** 0
- **Negative UnitPrice values remaining:** 0

### Final Columns

1. InvoiceNo
2. StockCode
3. Description
4. Quantity
5. InvoiceDate
6. UnitPrice
7. CustomerID
8. Country
9. IsCancellation

## Repository Contents

- `SWYNEX_Data_Cleaning_Preparation.ipynb` – complete data exploration and cleaning process
- `SWYNEX_Online_Retail_Cleaned_Sample.csv` – 10,000-row representative sample of the cleaned dataset

The complete cleaned dataset contains 536,638 records and is not included in this repository because the CSV file exceeds GitHub's standard browser upload size limit.

## Key Learning

This project helped me understand that data cleaning is not simply about deleting missing or unusual values. Each data-quality issue needs to be investigated in its business context before deciding whether to remove, retain, transform, or flag the records.

## Internship

Completed as part of the **SWYNEX Technologies Internship**.

#SWYNEX #DataCleaning #DataPreparation #Python #Pandas #DataAnalytics #Internship
