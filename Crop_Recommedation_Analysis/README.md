# 🌱 Crop Recommendation Dataset Analysis

## 📌 Project Overview

This project performs **Exploratory Data Analysis (EDA)** on the **Crop Recommendation Dataset**.

The main objective is to understand the dataset, analyze the distribution of different agricultural and environmental features, identify and treat potential outliers, and explore relationships between the features and different crop types.

The analysis is performed using **Python, Pandas, NumPy, Matplotlib, and Seaborn**.

---

## 🎯 Objectives

The main objectives of this project are:

* Load and inspect the Crop Recommendation dataset.
* Understand the structure and characteristics of the data.
* Identify the number of rows and columns.
* Examine column names and data types.
* Check for missing values.
* Generate descriptive statistics.
* Visualize numerical feature distributions.
* Detect potential outliers using box plots.
* Detect outliers using the **IQR (Interquartile Range) method**.
* Treat outliers using **capping**.
* Analyze relationships between environmental features.
* Study soil pH distribution across different crops.
* Compare potassium levels among crops.
* Calculate the average phosphorus requirement for each crop.

---

## 📊 Dataset

The dataset contains information about soil and environmental conditions that can be used for crop analysis.

### Features

| Column        | Description                    |
| ------------- | ------------------------------ |
| `N`           | Nitrogen content in the soil   |
| `P`           | Phosphorus content in the soil |
| `K`           | Potassium content in the soil  |
| `temperature` | Temperature                    |
| `humidity`    | Humidity                       |
| `ph`          | Soil pH value                  |
| `rainfall`    | Rainfall                       |
| `label`       | Crop type                      |

The dataset contains **2200 rows and 8 columns**.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Jupyter Notebook / Google Colab**

---

## 🔍 Exploratory Data Analysis

### 1. Importing Libraries

The following libraries were used:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization

---

### 2. Loading the Dataset

The dataset is loaded using Pandas:

```python
df = pd.read_csv("Crop_recommendation.csv")
```

The data is stored in a Pandas DataFrame named `df`.

---

### 3. Dataset Inspection

The following functions were used to understand the dataset:

```python
df.tail()
df.shape
df.info()
df.describe()
df.dtypes
```

These operations help identify:

* Number of records
* Number of features
* Column names
* Data types
* Statistical properties
* Number of non-null values

---

## 🧹 Data Quality Check

### Missing Value Analysis

Missing values were checked using:

```python
df.isnull().sum()
```

The dataset was checked for missing values before performing further analysis.

---

# 📈 Data Visualization

## Histograms

Histograms were created to understand the distribution of numerical variables.

```python
df.hist(bins=15, figsize=(10,10))
plt.show()
```

Histograms help understand:

* Data distribution
* Concentration of values
* Spread of values
* Possible unusual observations

---

## 📦 Box Plot Analysis

Box plots were created for numerical features such as:

* Nitrogen (`N`)
* Phosphorus (`P`)
* Potassium (`K`)
* Temperature
* Humidity
* Soil pH

Example:

```python
sns.boxplot(y='temperature', data=df)
plt.show()
```

Box plots were used to identify potential outliers.

---

# 🚨 Outlier Detection

Outliers were detected using the **IQR method**.

### Interquartile Range

The IQR is calculated as:

$$
IQR = Q3 - Q1
$$

where:

* `Q1` = 25th percentile
* `Q3` = 75th percentile

The lower and upper boundaries are:

$$
Lower\ Bound = Q1 - 1.5(IQR)
$$

$$
Upper\ Bound = Q3 + 1.5(IQR)
$$

Values below the lower bound or above the upper bound are considered potential outliers.

---

## 🔧 Outlier Treatment

A function was created to calculate the lower and upper limits:

```python
def remove_outliers(col_name):
    Q1, Q3 = col_name.quantile([0.25, 0.75])
    IQR = Q3 - Q1
    lower_range = Q1 - (1.5 * IQR)
    upper_range = Q3 + (1.5 * IQR)
    return lower_range, upper_range
```

Instead of deleting the outliers, **capping** was performed.

For example:

```python
df['P'] = np.where(
    df['P'] > high,
    high,
    np.where(df['P'] < low, low, df['P'])
)
```

This replaces values outside the acceptable range with the corresponding boundary value.

Outlier treatment was performed for relevant numerical features including:

* Phosphorus
* Temperature
* Humidity
* Soil pH
* Potassium

---

# 📊 Relationship Analysis

## Humidity vs Temperature

A scatter plot was created to study the relationship between humidity and temperature.

```python
sns.scatterplot(
    x='humidity',
    y='temperature',
    data=df,
    hue='label'
)
plt.show()
```

The `hue='label'` parameter helps distinguish different crop types.

This visualization helps understand how temperature and humidity vary for different crops.

---

# 🌾 Soil pH Distribution by Crop

A violin plot was used to analyze soil pH for different crop types.

```python
sns.violinplot(
    x='label',
    y='ph',
    data=df,
    hue='label'
)
```

The violin plot shows the distribution and concentration of pH values for each crop.

The crop labels were rotated for better readability.

---

# 🥔 Potassium Analysis by Crop

A bar plot was used to compare potassium (`K`) values across different crop types.

```python
sns.barplot(
    y='label',
    x='K',
    data=df
)
plt.show()
```

This provides a visual comparison of potassium levels associated with different crops.

---

# 🧮 Crop-wise Phosphorus Analysis

The average phosphorus value for each crop was calculated using:

```python
df.groupby('label')['P'].mean().sort_values(ascending=False)
```

This performs the following operations:

1. Groups records according to crop type.
2. Selects the phosphorus (`P`) column.
3. Calculates the mean phosphorus value.
4. Sorts the results from highest to lowest.

This helps identify crops according to their average phosphorus levels.

---

# 📌 Key Concepts Used

### Exploratory Data Analysis (EDA)

EDA is the process of analyzing a dataset using statistical methods and visualizations to understand its structure, patterns, distributions, and potential problems.

### Outlier

An outlier is a data point that is significantly different from the majority of observations.

### IQR

The Interquartile Range represents the middle 50% of the data.

$$
IQR = Q3-Q1
$$

### Outlier Capping

Outlier capping replaces extreme values with predefined lower or upper boundaries instead of deleting the observations.

### GroupBy

`groupby()` is used to divide data into groups based on a column and perform aggregate operations such as mean, sum, or count.

---

# 📁 Project Structure

```text
Crop-Recommendation-Analysis/
│
├── Crop_recommendation_Analysis.ipynb
├── Crop_recommendation.csv
└── README.md
```

---

# 🚀 How to Run the Project

### 1. Clone the repository

```bash
git clone <your-repository-url>
```

### 2. Open the project

Open the notebook using:

* Jupyter Notebook
* JupyterLab
* Google Colab
* VS Code

### 3. Install required libraries

```bash
pip install pandas numpy matplotlib seaborn
```

### 4. Run the notebook

Open:

```text
Crop_recommendation_Analysis.ipynb
```

and execute the cells sequentially.

---

# 📌 Conclusion

This project provides an exploratory analysis of the Crop Recommendation dataset.

The dataset was examined using statistical methods and visualizations. Missing values were checked, numerical feature distributions were studied, and potential outliers were identified using box plots and the IQR method.

Outliers were treated using capping rather than removing observations. Scatter plots, violin plots, and bar plots were then used to understand relationships between environmental and soil features and different crop types.

The analysis provides a better understanding of the dataset and prepares the data for further machine learning tasks such as **crop classification or recommendation**.

---

## 👩‍💻 Author

**Manaswi Bolla**

B.Tech – Computer Science & Engineering (Data Science)
