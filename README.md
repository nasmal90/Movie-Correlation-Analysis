# 🎬 Movie Correlation Analysis

## 📝 Introduction
This project explores the **correlations** between various movie attributes, such as **budget**, **revenue**, and **user votes**, using **Python**. The goal is to understand how these factors influence one another and provide visual insights into the relationships through data analysis.

## 🎯 Objective
The main objectives of this project are:
- Analyzing relationships between movie attributes like **budget**, **revenue**, and **user votes**.
- Determining the correlation between **budget**, **votes**, and **gross revenue**.
- Visualizing these relationships using **scatter plots**, **regression plots**, and **heatmaps**.

## 🛠️ Tools Used
- **Python**: Core language for data analysis.
- **Pandas**: Data manipulation and cleaning.
- **Seaborn**: Data visualization library.
- **Matplotlib**: Plotting and graphing.

## 📊 Dataset
The dataset is sourced from **Kaggle** and includes over 7,000 movies. Key fields in the dataset include:
- **Budget**: The production budget of the movie.
- **Gross Revenue**: The total revenue earned by the movie.
- **Votes**: The number of user votes received by the movie.
- **Non-numeric fields**: Columns like `company`, `country`, `genre` which are converted to numeric codes for analysis.

## 🔍 Key Steps in Analysis

### 1. Loading the Dataset
We load the movie dataset using **Pandas** and preview its structure:

```python
import pandas as pd

# Load the dataset
df = pd.read_csv('data/movies.csv')

# Display the first few rows
df.head()

```
### 2. Handling Missing Data
We check for missing data and drop rows with missing values to ensure clean data:
#### Check for missing data
```
for col in df.columns:
    pct_missing = df[col].isnull().mean() * 100
    print(f'{col} - {pct_missing:.2f}% missing data')

# Drop rows with missing data
df = df.dropna()
```
### 3. Converting Non-Numeric Fields to Numeric Codes
Convert non-numeric columns into numeric codes:
```
# Convert non-numeric columns to numeric codes
df['company'] = df['company'].astype('category').cat.codes
df['country'] = df['country'].astype('category').cat.codes
df['genre'] = df['genre'].astype('category').cat.codes
```
### 4. Correlation Matrix
Calculate and display the correlation matrix:
```
# Calculate the correlation matrix
correlation_matrix = df.corr()

# Display the correlation matrix
print(correlation_matrix)
```
### 5. Visualization of Correlations
Visualize the correlation matrix using a heatmap:
```
import seaborn as sns
import matplotlib.pyplot as plt

# Plot the heatmap
plt.figure(figsize=(12, 8))
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')
plt.title('Correlation Matrix for Movie Attributes')
plt.show()
```
### 6. Scatter Plot: Budget vs Gross Revenue
Explore the relationship between budget and gross revenue using a scatter plot:
```
# Scatter plot of Budget vs Gross Revenue
plt.figure(figsize=(10, 6))
plt.scatter(df['budget'], df['gross'], alpha=0.5)
plt.title('Budget vs Gross Revenue')
plt.xlabel('Budget')
plt.ylabel('Gross Revenue')
plt.show()
```
### 7. Regression Plot: Budget vs Gross Revenue
Visualize the relationship with a regression line:
```
# Regression plot
sns.regplot(x='budget', y='gross', data=df, scatter_kws={'color':'red'}, line_kws={'color':'blue'})
plt.title('Regression Plot: Budget vs Gross Revenue')
plt.show()
```
## Results & Insights
- **BudgetBudget and Gross Revenue:** Budget There is a strong positive correlation (~0.71) between budget and gross revenue. Higher-budget films generally generate more revenue.
- **BudgetVotes and Revenue:** Budget A significant correlation exists between the number of votes a movie receives and its gross revenue. Movies with more votes tend to make more money.
## Screenshots or Visualizations
To view detailed analyses and visualizations, check out the plots and outputs in the Jupyter notebook or generate them using the provided code.
