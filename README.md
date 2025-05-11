# Wk-7-
Basic data analysis 

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load the dataset
file_path = 'sales_data.csv'  # Replace with your actual file path
try:
    df = pd.read_csv(file_path)
    print("Dataset loaded successfully!")
except FileNotFoundError:
    print(f"Error: The file {file_path} was not found.")
except Exception as e:
    print(f"Error loading dataset: {e}")
    
# Display the first 5 rows to inspect the data
print(df.head())

# Check data types and missing values
print(df.info())
# Check for any missing values
print(df.isnull().sum())

# Example: Fill missing values with the mean for numerical columns
df.fillna(df.mean(), inplace=True)

# Or drop rows with missing values (if it's appropriate for your dataset)
# df.dropna(inplace=True)

# Get basic statistics for numerical columns
print(df.describe())

# Group by a categorical column (e.g., 'Region') and compute the mean of the 'Sales' column
grouped_data = df.groupby('Region')['Sales'].mean()
print(grouped_data)

# Check if there are regions with significantly higher sales
print(grouped_data.sort_values(ascending=False))

# Assuming the dataset has 'Date' and 'Sales' columns
df['Date'] = pd.to_datetime(df['Date'])
df.set_index('Date', inplace=True)

plt.figure(figsize=(10, 6))
plt.plot(df.index, df['Sales'], label='Sales Trend')
plt.title('Sales Trend Over Time')
plt.xlabel('Date')
plt.ylabel('Sales')
plt.legend()
plt.grid(True)
plt.show()

plt.figure(figsize=(8, 5))
sns.barplot(x=grouped_data.index, y=grouped_data.values)
plt.title('Average Sales per Region')
plt.xlabel('Region')
plt.ylabel('Average Sales')
plt.show()

plt.figure(figsize=(8, 5))
sns.histplot(df['Sales'], kde=True, bins=20)
plt.title('Distribution of Sales')
plt.xlabel('Sales')
plt.ylabel('Frequency')
plt.show()

plt.figure(figsize=(8, 5))
sns.scatterplot(x=df['Advertising Spend'], y=df['Sales'])
plt.title('Advertising Spend vs Sales')
plt.xlabel('Advertising Spend')
plt.ylabel('Sales')
plt.show()

try:
    # Try loading the dataset
    df = pd.read_csv(file_path)
    print("Dataset loaded successfully!")
except FileNotFoundError:
    print(f"Error: The file {file_path} was not found.")
except pd.errors.ParserError:
    print(f"Error: There was an issue parsing the file {file_path}.")
except Exception as e:
    print(f"Unexpected error: {e}")


import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Load dataset
file_path = 'sales_data.csv'  # Replace with your actual file path
try:
    df = pd.read_csv(file_path)
    print("Dataset loaded successfully!")
except FileNotFoundError:
    print(f"Error: The file {file_path} was not found.")
except Exception as e:
    print(f"Error loading dataset: {e}")

# Display first few rows
print(df.head())

# Check for missing values and data types
print(df.info())
print(df.isnull().sum())

# Fill missing values with the mean (or drop rows as needed)
df.fillna(df.mean(), inplace=True)

# Basic Statistics
print(df.describe())

# Group by a categorical column
grouped_data = df.groupby('Region')['Sales'].mean()
print(grouped_data)

# Line plot of Sales over Time
df['Date'] = pd.to_datetime(df['Date'])
df.set_index('Date', inplace=True)
plt.figure(figsize=(10, 6))
plt.plot(df.index, df['Sales'], label='Sales Trend')
plt.title('Sales Trend Over Time')
plt.xlabel('Date')
plt.ylabel('Sales')
plt.legend()
plt.grid(True)
plt.show()

# Bar plot of Average Sales by Region
plt.figure(figsize=(8, 5))
sns.barplot(x=grouped_data.index, y=grouped_data.values)
plt.title('Average Sales per Region')
plt.xlabel('Region')
plt.ylabel('Average Sales')
plt.show()

# Histogram of Sales
plt.figure(figsize=(8, 5))
sns.histplot(df['Sales'], kde=True, bins=20)
plt.title('Distribution of Sales')
plt.xlabel('Sales')
plt.ylabel('Frequency')
plt.show()

# Scatter plot of Advertising Spend vs Sales
plt.figure(figsize=(8, 5))
sns.scatterplot(x=df['Advertising Spend'], y=df['Sales'])
plt.title('Advertising Spend vs Sales')
plt.xlabel('Advertising Spend')
plt.ylabel('Sales')
plt.show()
