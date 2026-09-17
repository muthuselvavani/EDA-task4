# 📊 Exploratory Data Analysis – Shopify Stock

## 📌 Project Overview

This project performs **Exploratory Data Analysis (EDA)** on Shopify stock market data using Python. The analysis is performed on historical Shopify stock data to understand price movements, daily returns, price ranges, trading volume, and moving-average trends.

The project includes data loading, data inspection, data cleaning, feature engineering, statistical analysis, and data visualization.

## 🎯 Objectives

- To load and examine the Shopify stock dataset.
- To understand the structure and characteristics of the data.
- To check and handle missing values.
- To convert and organize the date column.
- To calculate daily price change.
- To calculate daily return percentage.
- To calculate daily price range.
- To perform statistical analysis.
- To visualize stock price and return-related information.
- To analyze closing prices using moving averages.
- To understand the distribution of daily returns.

## 🛠️ Technologies Used

- **Python**
- **Pandas**
- **Matplotlib**
- **Jupyter Notebook / Google Colab**

## 📂 Dataset

The dataset used in this project is:

`SHOP_2015-05-21_2025-03-16.csv`

The dataset contains **2469 rows and 7 columns**.

### Dataset Columns

| Column | Description |
|---|---|
| `date` | Trading date |
| `open` | Opening stock price |
| `high` | Highest price during the day |
| `low` | Lowest price during the day |
| `close` | Closing stock price |
| `adj_close` | Adjusted closing price |
| `volume` | Trading volume |

## 🔍 Exploratory Data Analysis

### 1. Importing Libraries

```python
import pandas as pd
import matplotlib.pyplot as plt
```

### 2. Loading the Dataset

```python
df = pd.read_csv("/content/SHOP_2015-05-21_2025-03-16.csv")
```

The first five records are displayed using:

```python
print(df.head())
```

### 3. Checking Dataset Shape

```python
print(df.shape)
```

**Output:**

```text
(2469, 7)
```

Therefore, the dataset contains **2469 records and 7 columns**.

### 4. Checking Data Information

The `info()` function is used to examine the column names, data types, and non-null values.

```python
print(df.info())
```

The dataset contains:

- 1 object column – `date`
- 5 float columns – stock price-related columns
- 1 integer column – `volume`

All 2469 records contain non-null values.

### 5. Checking Missing Values

```python
print(df.isnull().sum())
```

The result shows **0 missing values** in all columns.

## 🧹 Data Cleaning

### 6. Converting Date Column

```python
df["date"] = pd.to_datetime(
    df["date"],
    format="mixed",
    errors="coerce"
)
```

### 7. Sorting the Data

```python
df = df.sort_values("date")
```

### 8. Setting Date as Index

```python
df = df.set_index("date")
```

### 9. Removing Missing Values

```python
df = df.dropna()
```

After cleaning, the dataset contains **2469 records**.

## ⚙️ Feature Engineering

### 10. Daily Price Change

Daily price change is calculated as the difference between closing price and opening price.

```python
df["Daily_Price_Change"] = df["close"] - df["open"]
```

**Formula:**

```text
Daily Price Change = Close Price − Open Price
```

### 11. Daily Return Percentage

```python
df["Daily_Return_%"] = (
    (df["close"] - df["open"]) / df["open"]
) * 100
```

**Formula:**

```text
Daily Return (%) = ((Close − Open) / Open) × 100
```

### 12. Price Range

```python
df["Price_Range"] = df["high"] - df["low"]
```

**Formula:**

```text
Price Range = High Price − Low Price
```

## 📊 Statistical Analysis

The `describe()` function is used to obtain statistical information about the dataset.

```python
df.describe()
```

### Important Results

| Measure | Value |
|---|---:|
| Mean Daily Return | 0.0864 |
| Return Variance | 9.7331 |
| Return Standard Deviation | 3.1198 |
| Mean Price Range | 2.1577 |

## 📈 Mean Return

```python
print(
    "Mean Return:",
    df["Daily_Return_%"].mean()
)
```

**Result:**

```text
Mean Return: 0.08640631099421993
```

## 📉 Return Variance

```python
print(
    "Return Variance:",
    df["Daily_Return_%"].var()
)
```

**Result:**

```text
Return Variance: 9.733081984179565
```

## 📐 Return Standard Deviation

```python
print(
    "Return Standard Deviation:",
    df["Daily_Return_%"].std()
)
```

**Result:**

```text
Return Standard Deviation: 3.1197887723657773
```

## 📊 Data Visualization

Matplotlib is used to visualize the Shopify stock data and understand its patterns.

The notebook includes analysis of:

- Trading volume
- Daily returns
- Stock price
- OHLC prices
- Closing price
- Moving averages
- Distribution of daily returns

## 📈 Moving Average Analysis

Moving averages are calculated to analyze the closing-price trend.

A **20-day moving average** represents the average closing price over a 20-day period.

A **50-day moving average** represents the average closing price over a 50-day period.

These moving averages are compared with the closing price to observe changes in the stock-price trend.

## 📌 Output Screenshots

Only the **last two visual outputs** are included here.

### 1. Closing Price and Moving Averages

Upload the screenshot inside the `images` folder with the filename:

`moving_averages.png`

(<img width="1257" height="617" alt="Screenshot 2026-09-17 202627" src="https://github.com/user-attachments/assets/f167e17b-102f-4cb1-8636-6c4dc69ba454" />
)

### 2. KDF of Shopify Daily Returns

Upload the screenshot inside the `images` folder with the filename:

`kde_returns.png`

<img width="1073" height="587" alt="Screenshot 2026-09-17 202645" src="https://github.com/user-attachments/assets/519717a3-a920-44f3-b4e3-cf1b0ebc8d66" />


## 📁 Project Structure

```text
EDA_TASK_3/
│
├── EDA_TASK_3_iynb.ipynb
├── SHOP_2015-05-21_2025-03-16.csv
├── README.md
│
└── images/
    ├── moving_averages.png
    └── kde_returns.png
```

## ✅ Conclusion

This project performs Exploratory Data Analysis on Shopify stock market data using Python. The dataset was inspected, cleaned, and transformed by creating daily price change, daily return percentage, and price range features.

Statistical measures such as mean, variance, and standard deviation were calculated. Visualization and moving-average analysis were also used to understand stock price behaviour and daily return distribution.

Overall, the project demonstrates the use of **Pandas for data analysis** and **Matplotlib for data visualization** in an Exploratory Data Analysis workflow.

