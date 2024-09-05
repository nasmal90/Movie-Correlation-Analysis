{\rtf1\ansi\ansicpg1252\cocoartf2761
\cocoatextscaling0\cocoaplatform0{\fonttbl\f0\fswiss\fcharset0 Helvetica;}
{\colortbl;\red255\green255\blue255;}
{\*\expandedcolortbl;;}
\paperw11900\paperh16840\margl1440\margr1440\vieww11520\viewh8400\viewkind0
\pard\tx566\tx1133\tx1700\tx2267\tx2834\tx3401\tx3968\tx4535\tx5102\tx5669\tx6236\tx6803\pardirnatural\partightenfactor0

\f0\fs24 \cf0 # Movie Correlation Analysis\
\
## Introduction\
This project explores correlations between various attributes of movies, such as budget, revenue, and user votes, using Python. The goal is to analyze the relationships between different movie factors and provide visual insights into the data.\
\
## Objective\
The main objectives of this project are:\
- Analyzing the relationships between different movie attributes such as budget, revenue, and user votes.\
- Determining the correlation between budget, votes, and gross revenue.\
- Visualizing these relationships using scatter plots, regression plots, and heatmaps.\
\
## Tools Used\
- **Python**: Primary language for data analysis.\
- **Pandas**: For data manipulation and cleaning.\
- **Seaborn**: For data visualization.\
- **Matplotlib**: For plotting.\
\
## Dataset\
The dataset, sourced from Kaggle, includes over 7,000 movies with fields such as:\
- **Budget**: The production budget of the movie.\
- **Gross Revenue**: Total revenue earned by the movie.\
- **Votes**: Number of votes received by the movie.\
- **Non-numeric fields**: Fields like `company`, `country`, `genre` which are later converted to numeric codes.\
\
## Key Steps in Analysis\
\
### 1. Loading the Dataset\
The first step is to load the dataset using Pandas:\
\
```python\
import pandas as pd\
\
# Load the dataset\
df = pd.read_csv('data/movies.csv')\
\
# Display the first few rows\
df.head()\
```\
\
### 2. Handling Missing Data\
We check for any missing data and drop rows with missing values to ensure clean data for analysis:\
\
```python\
# Check for missing data\
for col in df.columns:\
    pct_missing = df[col].isnull().mean() * 100\
    print(f'\{col\} - \{pct_missing:.2f\}% missing data')\
\
# Drop rows with missing data\
df = df.dropna()\
```\
\
### 3. Converting Non-Numeric Fields to Numeric Codes\
Convert non-numeric columns (like `company`, `country`, `genre`) into numeric codes for correlation analysis:\
\
```python\
# Convert non-numeric columns to numeric codes\
df['company'] = df['company'].astype('category').cat.codes\
df['country'] = df['country'].astype('category').cat.codes\
df['genre'] = df['genre'].astype('category').cat.codes\
```\
\
### 4. Correlation Matrix\
We calculate the correlation matrix between movie attributes such as budget, gross revenue, and votes:\
\
```python\
# Calculate the correlation matrix\
correlation_matrix = df.corr()\
\
# Display the correlation matrix\
print(correlation_matrix)\
```\
\
### 5. Visualization of Correlations\
The correlation matrix can be visualized using a heatmap, which provides a clear visual representation of how the attributes are related:\
\
```python\
import seaborn as sns\
import matplotlib.pyplot as plt\
\
# Plot the heatmap\
plt.figure(figsize=(12, 8))\
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')\
plt.title('Correlation Matrix for Movie Attributes')\
plt.show()\
```\
\
### 6. Scatter Plot: Budget vs Gross Revenue\
We also explore the relationship between `budget` and `gross revenue` using scatter plots:\
\
```python\
# Scatter plot of Budget vs Gross Revenue\
plt.figure(figsize=(10, 6))\
plt.scatter(df['budget'], df['gross'], alpha=0.5)\
plt.title('Budget vs Gross Revenue')\
plt.xlabel('Budget')\
plt.ylabel('Gross Revenue')\
plt.show()\
```\
\
### 7. Regression Plot: Budget vs Gross Revenue\
Adding a regression line helps visualize the strength and direction of the relationship between budget and gross revenue:\
\
```python\
# Regression plot\
sns.regplot(x='budget', y='gross', data=df, scatter_kws=\{'color':'red'\}, line_kws=\{'color':'blue'\})\
plt.title('Regression Plot: Budget vs Gross Revenue')\
plt.show()\
```\
\
## Results & Insights\
- **Budget and Gross Revenue**: The analysis revealed a strong positive correlation between budget and gross revenue (~0.71). This means that higher-budget films tend to generate more revenue.\
- **Votes and Revenue**: We also found a significant correlation between the number of votes a movie receives and its gross revenue. Popular movies (as indicated by votes) tend to make more money.\
\
\
\
## Screenshots or Visualizations\
To explore the detailed analysis and visualizations, you can view the plots and outputs in the Jupyter notebook or generate them using the provided code.\
\
}