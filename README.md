# Data Cleaning and Preprocessing — Campaign Performance Dataset

## Overview

This project focuses on cleaning and preprocessing a raw Campaign Performance dataset to prepare it for further analysis and modeling.
The dataset initially contained missing values, duplicate records, inconsistent column naming, and unstructured data formats.
All cleaning operations were performed using Python (Pandas).

## Steps Followed
🔹 Step 1: Load and Inspect Data

Loaded the dataset using pandas.read_csv().

Displayed dataset shape, data types, and sample records using .shape, .info(), and .head().

🔹 Step 2: Handle Missing Values

Identified missing values using .isnull().sum().

Filled missing numeric columns (like total_reach, unique_reach) with their respective mean values.

Dropped rows containing critical null values using .dropna() when necessary.

🔹 Step 3: Remove Duplicates

Checked for duplicate rows using .duplicated().sum().

Removed all duplicate records with .drop_duplicates(inplace=True).

🔹 Step 4: Standardize Text Data

Converted text fields to lowercase using .str.lower() and removed extra spaces using .str.strip().

Ensured consistency in categorical columns (e.g., channel_name, advertiser_name, etc.).

🔹 Step 5: Convert Dates to a Consistent Format

Converted the time column from yy-mm-dd format to a consistent dd-mm-yy format using:

df['time'] = pd.to_datetime(df['time'], errors='coerce').dt.strftime('%d-%m-%y')

🔹 Step 6: Rename Columns

Cleaned messy column names by converting them to lowercase and replacing spaces with underscores:

df.columns = df.columns.str.lower().str.replace(' ', '_')

🔹 Step 7: Fix Data Types

Converted numeric columns to the correct data type:

df['creative_width'] = df['creative_width'].astype(float)
df['creative_height'] = df['creative_height'].astype(float)


Ensured date columns are in datetime format.

🔹 Step 8: Save Cleaned Data

Saved the final cleaned dataset using:

df.to_csv('cleaned_dataset.csv', index=False)

## Operations performed

1.Missing Value Handling

2.Duplicate Removal

3.Column Renaming

4.Data Type Conversion

5.Text Standardization

## Conclusion

Cleaned and prepared a raw marketing campaign dataset for analysis.

Handled missing values, duplicates, and inconsistent formatting effectively.

Standardized column names, fixed data types, and converted date formats.

The final cleaned dataset is stored as cleaned_dataset.csv and ready for visualization or modeling.
