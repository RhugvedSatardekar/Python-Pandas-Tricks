### 1. Show Installed Versions
To check the installed version of `pandas` and other related libraries:
```python
pd.__version__  # Returns the version of pandas
pd.show_versions()  # Displays detailed version information about pandas and dependencies
```

### 2. Create an Example DataFrame
Creating a simple DataFrame and another one with random values:
```python
df = pd.DataFrame({'Name': ['Rhugved', 'Sanjay', 'Satardekar'], 'Age': ['10', '']})
print(df)

# Creating a DataFrame with random values
df_random = pd.DataFrame(np.random.rand(4, 8), columns=list('abcdefgh'))
print(df_random)
```

### 3. Rename Columns
Renaming and manipulating column names:
```python
# Checking initial columns
print(drinks.columns)

# Renaming columns
df.rename(columns={'Name': 'name'}, inplace=True)

# Replacing spaces in column names with underscores
df.columns = df.columns.str.replace(' ', '_')
print(df.columns)

# Adding prefixes and suffixes to column names
df_with_prefix = df.add_prefix('X_')
df_with_suffix = df.add_suffix('_Y')
print(df_with_prefix.columns)
print(df_with_suffix.columns)
```

### 4. Reverse Row Order
Reversing the order of rows in the DataFrame:
```python
# Sorting rows in descending order by index
drinks_sorted = drinks.sort_index(ascending=False)
print(drinks_sorted.head())

# Reversing rows and resetting index
drinks_reversed = drinks.loc[::-1].reset_index(drop=True)
print(drinks_reversed.head())
```

### 5. Reverse Column Order
Reversing the order of columns in the DataFrame:
```python
# Reversing the column order
drinks_columns_reversed = drinks.loc[:, ::-1]
print(drinks_columns_reversed.head())
```

### 6. Select Columns by Data Type
Selecting numeric columns:
```python
# Selecting numeric columns
numeric_cols = drinks.select_dtypes(include='number')
print(numeric_cols.head())
```

### 7. Convert Strings to Numbers
Converting string columns to numeric:
```python
# Creating a sample DataFrame
df = pd.DataFrame({
    'col_one': ['1.1', '2.2', '3.3'],
    'col_two': ['4.4', '5.5', '6.6'],
    'col_three': ['7.7', '8.8', '-']
})

# Replacing '-' with '' and converting to float
df.col_three.replace('-', '', inplace=True)
df.col_three = df.col_three.astype('float', errors='ignore')

# Applying conversion to all columns
df_all_numeric = df.apply(pd.to_numeric, errors='coerce').fillna(0)
print(df_all_numeric)

# Converting specific columns to float
df_specific_numeric = df.astype({
    'col_one': 'float',
    'col_two': 'float',
    'col_three': 'float'
}, errors='ignore')
print(df_specific_numeric)
```

### 8. Reduce DataFrame Size
Optimizing DataFrame memory usage:
```python
# Checking memory usage
drinks.info(memory_usage='deep')

# Reading specific columns
cols = ['beer_servings', 'continent']
small_drinks = pd.read_csv('http://bit.ly/drinksbycountry', usecols=cols)
small_drinks.info(memory_usage='deep')

# Converting categorical columns
dtypes = {'continent': 'category'}
smaller_drinks = pd.read_csv('http://bit.ly/drinksbycountry', usecols=cols, dtype=dtypes)
smaller_drinks.info(memory_usage='deep')
```

### 9. Build a DataFrame from Multiple Files (Row-wise)
Combining multiple DataFrames:
```python
# Assuming df1 and df2 are the same DataFrame for demonstration
df1 = df
combined_df = df.append(df1)
print(combined_df)
```



### 10. Build a DataFrame from Multiple Files (Column-wise)
To combine multiple CSV files column-wise:
```python
import pandas as pd
from glob import glob

# List all CSV files matching the pattern
stock_files = sorted(glob('data/stocks*.csv'))

# Read each file and concatenate them column-wise
combined_df = pd.concat((pd.read_csv(file) for file in stock_files), axis=1)
print(combined_df)
```

### 11. Append DataFrames
To append one DataFrame to another:
```python
df1 = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
df2 = pd.DataFrame({'A': [7, 8, 9], 'B': [10, 11, 12]})
df_combined = df1.append(df2, ignore_index=True)
print(df_combined)
```

### 12. Merge DataFrames
To merge two DataFrames on a common column:
```python
df1 = pd.DataFrame({'key': ['A', 'B', 'C'], 'value1': [1, 2, 3]})
df2 = pd.DataFrame({'key': ['A', 'B', 'D'], 'value2': [4, 5, 6]})
df_merged = pd.merge(df1, df2, on='key', how='inner')
print(df_merged)
```

### 13. Join DataFrames
To join two DataFrames using their indices:
```python
df1 = pd.DataFrame({'A': [1, 2, 3]}, index=['a', 'b', 'c'])
df2 = pd.DataFrame({'B': [4, 5, 6]}, index=['a', 'b', 'd'])
df_joined = df1.join(df2, how='inner')
print(df_joined)
```

### 14. Group By and Aggregate
To group by a column and aggregate data:
```python
df = pd.DataFrame({'key': ['A', 'B', 'A'], 'data': [1, 2, 3]})
grouped_df = df.groupby('key').sum()
print(grouped_df)
```

### 15. Pivot Tables
To create a pivot table:
```python
df = pd.DataFrame({'A': ['foo', 'foo', 'bar', 'bar'], 'B': ['one', 'two', 'one', 'two'], 'C': [1, 3, 2, 4]})
pivot_df = df.pivot_table(values='C', index='A', columns='B', aggfunc='sum')
print(pivot_df)
```

### 16. Apply Function to DataFrame
To apply a function to each element in a DataFrame:
```python
df = pd.DataFrame({'A': [1, 2, 3], 'B': [10, 20, 30]})
df_applied = df.apply(lambda x: x * 2)
print(df_applied)
```

### 17. Handle Missing Data
To handle missing data by filling NaNs:
```python
df = pd.DataFrame({'A': [1, 2, None], 'B': [None, 5, 6]})
df_filled = df.fillna(0)
print(df_filled)
```

### 18. Handle Missing Data by Dropping
To drop rows with missing data:
```python
df = pd.DataFrame({'A': [1, 2, None], 'B': [None, 5, 6]})
df_dropped = df.dropna()
print(df_dropped)
```

### 19. Create Date Range
To create a date range and use it as an index:
```python
date_range = pd.date_range(start='2020-01-01', end='2020-01-10')
print(date_range)
```

### 20. Resample Time Series Data
To resample time series data:
```python
date_range = pd.date_range(start='2020-01-01', periods=10, freq='D')
df = pd.DataFrame({'value': range(10)}, index=date_range)
resampled_df = df.resample('2D').sum()
print(resampled_df)
```

### 21. Read JSON into DataFrame
To read JSON data into a DataFrame:
```python
json_data = '{"name": ["Alice", "Bob"], "age": [25, 30]}'
df = pd.read_json(json_data)
print(df)
```

### 22. Write DataFrame to CSV
To write a DataFrame to a CSV file:
```python
df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
df.to_csv('output.csv', index=False)
```

### 23. Read CSV from URL
To read a CSV file directly from a URL:
```python
url = 'http://example.com/data.csv'
df = pd.read_csv(url)
print(df)
```

### 24. Plot Data
To plot data from a DataFrame:
```python
import matplotlib.pyplot as plt

df = pd.DataFrame({'A': [1, 2, 3], 'B': [4, 5, 6]})
df.plot(kind='bar')
plt.show()
```

### 25. Create a MultiIndex DataFrame
To create a MultiIndex DataFrame:
```python
arrays = [['bar', 'bar', 'baz', 'baz'], ['one', 'two', 'one', 'two']]
index = pd.MultiIndex.from_arrays(arrays, names=('first', 'second'))
df = pd.DataFrame({'A': [1, 2, 3, 4]}, index=index)
print(df)
```
