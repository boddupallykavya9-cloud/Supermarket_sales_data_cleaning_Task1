## Dataset Description

- **Source:** Kaggle - Supermarket Sales Data
- **Rows:** 1,000
- **Columns:** 17
- **Main Columns:**
  - `invoice_id`, `branch`, `city`, `customer_type`, `gender`
  - `product_line`, `unit_price`, `quantity`, `tax_5%`, `sales`
  - `date`, `time`, `payment`, `cogs`, `gross_margin_percentage`, `gross_income`, `rating`

This dataset contains detailed sales records from a supermarket, including transaction details, product categories, customer demographics, and financial information.

## Data Cleaning Summary

This notebook includes the following data cleaning steps:

- **Removed duplicate rows:** Checked and removed any duplicate entries in the dataset to ensure the integrity of the data. No duplicates remained after this step.

- **Handled missing values:** Inspected all columns and found there were no missing values. Therefore, no rows had to be dropped or filled for null data.

- **Standardized categorical columns to lowercase:** Converted the values in text-based columns (such as gender, product_line, and city) to lowercase for consistency.

- **Standardized column names:** Renamed all columns to lowercase and replaced spaces with underscores for easier access in code (e.g., `Product line` became `product_line`).

- **Converted data types for numeric columns:** Ensured that all numerical columns (`unit_price`, `quantity`, `tax_5%`, `sales`, `gross_income`, etc.) were of the appropriate numeric datatype.

- **Standardized date column:** Converted the `date` column to datetime format for proper time-series analysis.

- Below is the code used for cleaning and preprocessing the supermarket sales dataset as part of this project:

# Remove duplicates
df = df.drop_duplicates()

# Standardize categorical columns
df['gender'] = df['gender'].str.lower()
df['product_line'] = df['product_line'].str.lower()
df['city'] = df['city'].str.lower()

# Standardize column names
df.columns = df.columns.str.lower().str.replace(' ', '_')

# Fix datatypes
df['quantity'] = pd.to_numeric(df['quantity'])
df['sales'] = pd.to_numeric(df['sales'])
df['unit_price'] = pd.to_numeric(df['unit_price'])
df['tax_5%'] = pd.to_numeric(df['tax_5%'])
df['gross_income'] = pd.to_numeric(df['gross_income'])
df['gross_margin_percentage'] = pd.to_numeric(df['gross_margin_percentage'])

# Convert date column
df['date'] = pd.to_datetime(df['date'], format='%m/%d/%Y', errors='coerce')
