

import pandas as pd


print("Loading dataset...")
df = pd.read_csv("sales_data.csv")

print("\nFirst 5 rows of dataset:")
print(df.head())



print("\nDataset Shape (Rows, Columns):")
print(df.shape)

print("\nColumn Names:")
print(df.columns)

print("\nDataset Information:")
print(df.info())


print("\nChecking missing values:")
print(df.isnull().sum())

# Fill missing numerical values with mean
df.fillna(df.mean(numeric_only=True), inplace=True)

# Remove duplicate rows
df.drop_duplicates(inplace=True)

print("\nMissing values after cleaning:")
print(df.isnull().sum())


print("\n--- Sales Analysis ---")

total_sales = df['Total_Sales'].sum()
average_sales = df['Total_Sales'].mean()
highest_sale = df['Total_Sales'].max()
lowest_sale = df['Total_Sales'].min()

print("Total Sales:", total_sales)
print("Average Sales:", average_sales)
print("Highest Sale:", highest_sale)
print("Lowest Sale:", lowest_sale)


if 'Product' in df.columns:
    best_product = df.groupby('Product')['Total_Sales'].sum().idxmax()
    print("Best Selling Product:", best_product)


print("\n===== FINAL REPORT =====")
print(f"Total Records     : {len(df)}")
print(f"Total Revenue     : {total_sales}")
print(f"Average Sales     : {average_sales}")
print(f"Highest Sale      : {highest_sale}")
print(f"Lowest Sale       : {lowest_sale}")
print("Data Cleaning     : Completed")
print("Analysis Status   : Successful")

print("\n✅ Project Completed Successfully!")
