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
### 2. Handling Missing Data
To ensure clean data, we check for missing values and remove any incomplete rows:
```
