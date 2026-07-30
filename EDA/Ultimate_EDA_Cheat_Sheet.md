# 📊 Ultimate EDA Cheat Sheet (Universal)

> ✅ Beginner → Intermediate → Mini Professional Level  
> ✅ Almost Any Dataset Ready  
> ✅ University + Kaggle + ML Preprocessing Friendly  
> ✅ Includes Insight Hints + Auto Profiling

---

# 🚀 1️⃣ Basic Setup

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

# 🔍  Check Columns

```python
# Numeric columns
numeric_cols = df.select_dtypes(include=['number']).columns.tolist()

# Categorical columns
categorical_cols = df.select_dtypes(include=['object', 'category', 'bool']).columns.tolist()

print(f"Numeric Columns ({len(numeric_cols)}):")
print(numeric_cols)

print(f"\nCategorical Columns ({len(categorical_cols)}):")
print(categorical_cols)

print("\nSummary:")
print(f"✅ Total Columns       : {df.shape[1]}")
print(f"🔢 Numeric Columns    : {len(numeric_cols)}")
print(f"🔤 Categorical Columns: {len(categorical_cols)}")
```

```python
# Show count and proportion for each categorical column

for col in categorical_cols:
    print("=" * 60)
    print(f"Column: {col}")
    
    result = pd.DataFrame({
        "Count": df[col].value_counts(dropna=False),
        "Proportion (%)": round(df[col].value_counts(normalize=True, dropna=False) * 100, 2)
    })
    
    print(result)
    print()

```


# 📁 2️⃣ Load Dataset

```python
df = pd.read_csv("file.csv")
```

---

# 🔍 3️⃣ Basic Data Understanding

## Dataset Size

```python
df.shape
```

📌 Hint:
- More rows = more data
- More columns = more features

---

## First Rows

```python
df.head()
```

📌 Hint:
- Understand column meaning
- Detect wrong values quickly

---

## Last Rows

```python
df.tail()
```

---

## Random Sample

```python
df.sample(5)
```

---

## Column Names

```python
df.columns
```

---

## Dataset Info

```python
df.info()
```

📌 Insight:
- Check missing values
- Check datatype
- Object = categorical mostly
- int/float = numerical

---

## Statistical Summary

```python
df.describe()
```

📌 Insight:
- Mean vs Median close → normal distribution
- Large std → data spread high
- Min/max unusual → possible outlier

---

# 🧹 4️⃣ Data Cleaning

## Missing Values

```python
df.isnull().sum()
```

---

## Missing Value Percentage

```python
(df.isnull().sum()/len(df))*100
```

📌 Hint:
- >50% missing → maybe drop column
- Small missing → fill possible

---

## Duplicate Values

```python
df.duplicated().sum()
```

---

## Remove Duplicates

```python
df.drop_duplicates(inplace=True)
```

---

# 📌 5️⃣ Data Type Separation

## Numerical Columns

```python
df.select_dtypes(include=np.number)
```

---

## Categorical Columns

```python
df.select_dtypes(include="object")
```
```python

plt.figure(figsize=(15,8))
plt.suptitle('Uniovariate Anaysis of Categorical Columns',fontsize=20)

for i in range(0,len(categorical_cols)):
  plt.subplot(3,3,i+1)
  sns.countplot(x=df[categorical_cols[i]])
  plt.xlabel(categorical_cols[i])
  plt.tight_layout()

```
---

# 📊 6️⃣ Numerical Data Analysis

# Histogram

```python
plt.hist(df["col"])
plt.show()
```

📌 Insight:
- Bell shape → normal
- Right tail → positive skew
- Left tail → negative skew

---

# Distplot / KDE

```python
sns.histplot(df["col"], kde=True)
plt.show()
```

```python
# KDE Plot for all numeric columns
for col in numeric_cols:
    plt.figure(figsize=(6,4))
    sns.kdeplot(data=df, x=col, fill=True)
    plt.title(f'KDE Plot of {col}')
    plt.xlabel(col)
    plt.ylabel('Density')
    plt.grid(alpha=0.3)
    plt.show()
```

```python
for col in numeric_cols:
    plt.figure(figsize=(6,4))
    sns.histplot(data=df, x=col, kde=True, bins=30)
    plt.title(f'Histogram with KDE: {col}')
    plt.xlabel(col)
    plt.ylabel('Count')
    plt.grid(alpha=0.3)
    plt.show()
```

---

# Boxplot

```python
sns.boxplot(x=df["col"])
plt.show()
```

📌 Insight:
- Dots outside → outliers

---

# Skewness

```python
df["col"].skew()
```

📌 Hint:
- Near 0 → normal
- >1 → highly skewed

---

# Outlier Detection (IQR)

```python
Q1 = df["col"].quantile(0.25)
Q3 = df["col"].quantile(0.75)

IQR = Q3 - Q1

lower = Q1 - 1.5*IQR
upper = Q3 + 1.5*IQR

df[(df["col"] < lower) | (df["col"] > upper)]
```

---

# 📊 7️⃣ Categorical Data Analysis

# Countplot

```python
sns.countplot(data=df, x="col")
plt.show()
```

📌 Insight:
- Most frequent category easy detect

---

# Pie Chart

```python
df["col"].value_counts().plot(
    kind="pie",
    autopct="%1.1f%%"
)

plt.show()
```

📌 Hint:
- Good for percentage comparison

---

# Value Counts

```python
df["col"].value_counts()
```

---

# Unique Values

```python
df["col"].unique()
```

---

# Number of Unique Values

```python
df["col"].nunique()
```

---

# 🔥 8️⃣ Bivariate Analysis

# Numerical vs Numerical

## Scatterplot

```python
sns.scatterplot(
    data=df,
    x="col1",
    y="col2"
)

plt.show()
```

📌 Insight:
- Upward → positive relation
- Downward → negative relation

---

# Multi Scatterplot

```python
sns.scatterplot(
    data=df,
    x="col1",
    y="col2",
    hue="col3",
    style="col4"
)

plt.show()
```

---

# Numerical vs Categorical

# Barplot

```python
sns.barplot(
    data=df,
    x="cat_col",
    y="num_col"
)

plt.show()
```

📌 Insight:
- Compare average values

---

# Multi Barplot

```python
sns.barplot(
    data=df,
    x="cat_col",
    y="num_col",
    hue="another_cat"
)

plt.show()
```

---

# Boxplot

```python
sns.boxplot(
    data=df,
    x="cat_col",
    y="num_col"
)

plt.show()
```

📌 Insight:
- Distribution compare between categories

---

# Categorical vs Categorical

# Crosstab

```python
pd.crosstab(
    df["col1"],
    df["col2"]
)
```

---

# Crosstab Percentage

```python
pd.crosstab(
    df["col1"],
    df["col2"],
    normalize="columns"
)*100
```

---

# Heatmap

```python
sns.heatmap(
    pd.crosstab(df["col1"], df["col2"]),
    annot=True
)

plt.show()
```

---

# 🌡️ 9️⃣ Correlation Analysis

# All Correlation

```python
df.corr(numeric_only=True)
```

---

# One Column Correlation

```python
df.corr(numeric_only=True)["target"]
```

---

# Sorted Correlation

```python
df.corr(numeric_only=True)["target"].sort_values(
    ascending=False
)
```

📌 Insight:
- Near +1 → strong positive
- Near -1 → strong negative
- Near 0 → weak relation

---

# Correlation Heatmap

```python
plt.figure(figsize=(10,6))

sns.heatmap(
    df.corr(numeric_only=True),
    annot=True,
    cmap="coolwarm"
)

plt.show()
```

---

# 📈 🔟 Multivariable Analysis

# Pairplot

```python
sns.pairplot(df)
plt.show()
```

📌 Insight:
- Relationship between all numerical columns

---

# GroupBy Analysis

```python
df.groupby("cat_col")["num_col"].mean()
```

📌 Example:
- Gender wise salary
- Department wise marks

---

# ⚡ 1️⃣1️⃣ Auto EDA Profiling

## Install

```python
pip install ydata-profiling
```

---

## Generate Full Report

```python
from ydata_profiling import ProfileReport

profile = ProfileReport(df)

profile.to_file("report.html")
```

📌 Gives:
- Missing values
- Correlation
- Outliers
- Distribution
- Duplicates
- Warnings automatically

🔥 Very useful for professional EDA

---

# 🚀 1️⃣2️⃣ Full Quick Workflow

```python
df.shape

df.head()

df.info()

df.describe()

df.isnull().sum()

df.duplicated().sum()

df.corr(numeric_only=True)
```
```python
#Chi-Square Test of Independence (Chi-Square Test)
from scipy.stats import chi2_contingency

chi2_test = []

for feature in categorical_cols:
    p_value = chi2_contingency(pd.crosstab(df['case_status'], df[feature]))[1]

    if p_value < 0.05:
        chi2_test.append('Reject Null Hypothesis')
    else:
        chi2_test.append('Fail to Reject Null Hypothesis')

result = pd.DataFrame({
    'Column': categorical_cols,
    'Hypothesis Result': chi2_test
})

result
```
---

# 🧠 Insight Writing Guide

# If Missing Values High

✅ Write:
> Dataset contains significant missing values in some columns.

---

# If Outliers Found

✅ Write:
> Some numerical columns contain outliers which may affect model performance.

---

# If Strong Correlation Found

✅ Write:
> Certain features show strong correlation with the target variable.

---

# If Data Skewed

✅ Write:
> Some numerical features are highly skewed and may require transformation.

---

# If Categories Imbalanced

✅ Write:
> Class/category imbalance observed in categorical columns.

---

# If Distribution Normal

✅ Write:
> Data appears approximately normally distributed.

---

# 📌 Which Plot For Which Data?

| Data Type | Best Plot |
|---|---|
| Numerical | Histogram, KDE, Boxplot |
| Categorical | Countplot, Piechart |
| Num vs Num | Scatterplot |
| Num vs Cat | Barplot, Boxplot |
| Cat vs Cat | Crosstab, Heatmap |

---

# 🎯 Final EDA Goal

Always try to find:

✅ Missing values  
✅ Outliers  
✅ Correlation  
✅ Patterns  
✅ Trends  
✅ Relationships  
✅ Imbalance  
✅ Important features  
✅ Data quality issues

---

# 🔥 Final Advice

EDA mane sudhu graph na 😄

EDA means:
> “Understanding the story hidden inside the data.”
