# Corporate Sales Record Cleaner
### Automated Data Sanitization Pipeline — Week 1 Internship Milestone

## Overview
This project demonstrates a repeatable data-cleaning workflow using Python, Pandas, and NumPy. It starts with a deliberately imperfect sample sales dataset and produces a cleaned CSV and summary statistics.

## Files
- `sales_data_cleaner.ipynb` — step-by-step notebook for the complete pipeline.
- `raw_sales.csv` — synthetic example input containing exact duplicate rows, missing values, and inconsistent text formatting.
- `cleaned_sales.csv` — sample cleaned output.
- `summary_statistics.csv` — descriptive statistics generated from the cleaned dataset.
- `requirements.txt` — Python dependencies.

## Cleaning steps
1. **Ingestion:** load `raw_sales.csv` with `pandas.read_csv()`.
2. **Audit:** inspect shape, data types, null counts (`isnull().sum()`), exact duplicates (`duplicated()`), and baseline `describe()` output.
3. **Duplicate removal:** remove exact repeated rows with `drop_duplicates()`.
4. **Text standardization:** strip leading/trailing whitespace; standardize city/customer/product capitalization and lowercase payment-method categories.
5. **Missing-value handling:** fill numeric columns (`Age`, `Price`, `Quantity`) with their medians; fill categorical columns (`City`, `Payment_Method`, `Customer`, `Product`) with their modes.
6. **Validation:** check for remaining missing values and duplicates, and run basic non-negative price/quantity checks.
7. **Export:** write `cleaned_sales.csv` and `summary_statistics.csv`.

## Imputation rationale
- **Median for numeric columns:** median is less sensitive to unusually high or low values than the mean, which can be useful for skewed sales amounts.
- **Mode for categorical columns:** the mode supplies the most common observed category. For sensitive or identity-related fields, a business-approved placeholder such as `Unknown` may be more appropriate than inventing a value.
- **Text normalization:** whitespace and inconsistent capitalization can create avoidable category mismatches during analysis.

## Before/after shape comparison
Run the notebook to see the exact row/column counts and validation output. The supplied sample has 21 raw rows and 9 columns, including one exact duplicate. After removing the duplicate, the cleaned sample has 20 rows and 9 columns. Imputation and formatting do not change the row or column count.

## Run locally
1. Install Python 3.10+.
2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Open the notebook:
   ```bash
   jupyter notebook sales_data_cleaner.ipynb
   ```
4. Run all cells from top to bottom. Keep `raw_sales.csv` in the same folder as the notebook.

You can also upload all files to Google Colab and run the notebook there.

## Data privacy
The included records are synthetic sample data. Do not publish real customer information or confidential company data in a public GitHub repository without explicit authorization.

## Technologies
Python · Pandas · NumPy · Jupyter Notebook
