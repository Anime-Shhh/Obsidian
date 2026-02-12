Pandas has Series(Arrays) and DataFrame(2d (or more maybe)arrays)
code
```python
import pandas as pd
d = pd.Series([1,2.5,3,4,4.5])
df = pd.DataFrame([1,2,3,4,5])
```
d will just print an array while df will print as a table.
![[Pasted image 20251013161128.png]]




Cheat sheet:
Pandas and DF operations:
```python
# Create a pivot table showing total revenue per Store and Category
def revenue_summary(df):
    return df.pivot_table(values='Revenue', index='Store', columns='Category', aggfunc='sum')
# Get the top 3 products with the highest average revenue per sale (Revenue / Units_Sold)
top3 = df.assign(avg_revenue=df['Revenue'] / df['Units_Sold']).groupby('Product')['avg_revenue'].mean().nlargest(3)
# Convert all revenue values from euros to USD using a given conversion rate
df['Revenue'] = df['Revenue'] * euro_to_usd# euro_to_usd=1.09
# Add a new column 'Profit' calculated as 0.8 × Revenue − (0.5 × Units_Sold)
df['Profit'] = 0.8 * df['Revenue'] - (0.5 * df['Units_Sold'])
```
**Indexing and File Processing:**
Read txt files in a folder:
```python
# Read all .txt files and build a dictionary: product → list of bins
import os
def build_index(foldername):
    index = {}
    for filename in os.listdir(foldername):
        if filename.endswith('.txt'):
            with open(os.path.join(foldername, filename)) as f:
                for line in f:
                    product, bin_id = line.strip().split(',')
                    index.setdefault(product.strip(), []).append(bin_id.strip())
    return index

```
- **Duplicates:** Convert each product’s bin list to a **set** to remove repeated entries.
- ```python
  index[product] = list(set(index[product]))
  ```
  **Misspellings:** Standardize text (lowercase, trim spaces) and use **string similarity matching** to merge variants (e.g., “sock”, “socks”, “Sok”) into a single product key.
Similar strings: difflib helps find similar strings to a word, used to move an entry to another one
```python
import difflib
similar = difflib.get_close_matches('sok', index.keys(), n=1, cutoff=0.8)
# Save the index dictionary as a JSON file
import json
with open('warehouse_index.json', 'w') as f:
    json.dump(index, f, indent=2)

```
data transformation and feature engineering:
```python
# How to standardize a numeric column (subtract mean, divide by std)
def standardize(df, col):
    df[col] = (df[col] - df[col].mean()) / df[col].std()
    return df
# How to do One-hot encoding for Payment_Method column
import pandas as pd
Payment_Method = ['Card', 'Cash', 'Card', 'Online', 'Online', 'Cash']
df = pd.DataFrame({'Payment_Method': Payment_Method})
pd.get_dummies(df, columns=['Payment_Method'])
```
Problem with one hot encoding a column with many unique categories is that it will create too many new columns and make the dataset inneficient. to handle this, just make a few new columns and group the infrequent categories into a category called "other"
```python
# how to replace all missing numeric values with their column median
df = df.fillna(df.median(numeric_only=True))
#how to merge dfs and clean their values and stuff
# Merge the datasets on customer_id using an outer join to detect missing matches
merged_df = pd.merge(df1, df2, on='customer_id', how='outer', indicator=True)
# Detect missing matches
# Rows only in df1 (no total_spent)
missing_total_spent = merged_df[merged_df['_merge'] == 'left_only']
# Rows only in df2 (no age/income)
missing_customer_info = merged_df[merged_df['_merge'] == 'right_only']
# Handle missing matches
clean_df = merged_df.dropna(subset=['income', 'total_spent'])
# Compute correlation between income and total_spent
correlation = clean_df['income'].corr(clean_df['total_spent'])

def total_revenue(df):
    # Sum the 'Revenue' column across all rows
    return df['Revenue'].sum()
max_revenue_store = df.groupby('Store')['Revenue'].sum().idxmax()
avg_units_per_product = df.groupby('Product')['Units_Sold'].mean()

#function to get all words in a a filepath's txt files
import os

def listofwords(foldername):
    all_words = []  # list to store all words
    # Loop over all files in the folder
    for filename in os.listdir(foldername):
        if filename.endswith('.txt'):  # only process .txt files
            filepath = os.path.join(foldername, filename)
            with open(filepath, 'r', encoding='utf-8') as file:
                # Read the file, split into words, and extend the list
                words = file.read().split()
                all_words.extend(words)
    return all_words

def outliers(df, colname):
    # Compute Q1 (25th percentile) and Q3 (75th percentile)
    Q1 = df[colname].quantile(0.25)
    Q3 = df[colname].quantile(0.75)
    IQR = Q3 - Q1  # interquartile range
    # Return values outside the range [Q1 - 1.5*IQR, Q3 + 1.5*IQR]
    return df[(df[colname] < Q1 - 1.5 * IQR) | (df[colname] > Q3 + 1.5 * IQR)][colname]

```
