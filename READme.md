# 📊 Attrition Analytics

## 📌 Project Overview

This project performs **Exploratory Data Analysis (EDA)** on an employee dataset to understand the factors associated with **employee attrition**.

The analysis includes data inspection, missing-value treatment, identification of numerical and categorical features, outlier handling, duplicate removal, and visualization of employee attrition across different demographic and organizational factors.

## 🎯 Objectives

* Understand the structure of the employee dataset.
* Identify numerical and categorical features.
* Detect and handle missing values.
* Identify and handle outliers using the **IQR method**.
* Remove duplicate records.
* Analyze employee attrition based on:

  * Gender
  * Age Group
  * Education Field
  * Salary Slab
  * Years at Company
  * Department
* Calculate the total number and percentage of employees who left the organization.
* Visualize important patterns and trends in employee attrition.

## 🛠️ Technologies Used

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Google Colab / Jupyter Notebook**

## 📂 Dataset

The project uses an employee attrition dataset named:

`Attrition_Analytics.csv`

The dataset contains employee-related attributes such as:

* Employee ID
* Age
* Age Group
* Department
* Gender
* Education Field
* Salary Slab
* Years at Company
* Monthly Income
* Attrition

## 🔍 Project Workflow

### 1. Import Libraries

The required Python libraries are imported:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

### 2. Load the Dataset

The CSV dataset is loaded using Pandas.

### 3. Data Exploration

The following operations are performed:

* Dataset shape
* First and last records
* Data types
* Column names
* Dataset information
* Descriptive statistics
* Missing-value count

### 4. Missing Value Treatment

Missing values in `YearsWithCurrManager` are handled by replacing them with the **mean** of the column.

### 5. Feature Identification

The dataset is divided into:

* Numerical columns
* Categorical columns

### 6. Data Visualization

Histograms and boxplots are used to understand the distribution of numerical variables and identify potential outliers.

### 7. Feature Selection

Important features are selected for further attrition analysis:

```text
EmpID
Age
AgeGroup
Department
Gender
EducationField
SalarySlab
YearsAtCompany
MonthlyIncome
Attrition
```

An additional numerical feature, `Attrition_Numeric`, is created:

* `Yes` → 1
* `No` → 0

### 8. Outlier Treatment

The **Interquartile Range (IQR)** method is used to identify and limit outliers.

Outlier treatment is performed on:

* `YearsAtCompany`
* `MonthlyIncome`

### 9. Duplicate Removal

Duplicate employee records are identified and removed to create the final cleaned dataset.

### 10. Attrition Analysis

Employee attrition is analyzed using different visualizations:

* Attrition by Gender
* Attrition by Education Field
* Attrition by Age Group
* Attrition by Salary Slab
* Attrition by Years at Company
* Attrition by Department
* Attrition vs Stable Employees

### 11. Attrition Percentage

The project calculates:

* Total employees who left the organization
* Total number of employees
* Overall attrition percentage

## 📈 Key Analysis

The notebook provides visual insights into how employee attrition varies across different employee characteristics.

The analysis can help identify patterns related to **salary, age, education, department, gender, and years of experience within the organization**.


## 🚀 How to Run

1. Clone or download this repository.
2. Open `Attrition_Analytics.ipynb` using:

   * Google Colab
   * Jupyter Notebook
   * VS Code
3. Make sure `Attrition_Analytics.csv` is available.
4. Run the notebook cells sequentially.
5. Explore the generated analysis and visualizations.

## 📌 Conclusion

This project demonstrates a complete **EDA workflow for employee attrition analysis**, starting from raw data inspection and preprocessing to visualization and calculation of attrition metrics.

It provides a foundation for understanding employee turnover patterns and can be further extended with **statistical analysis and machine learning models for attrition prediction**.

## 👩‍💻 Author

**Manaswi Bolla**

B.Tech – Computer Science & Engineering
Data Science
