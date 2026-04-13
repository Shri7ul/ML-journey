
# 🚀 Simple Linear Regression (ML Project)

## 🧠 Overview
Simple Linear Regression is a supervised machine learning algorithm used to predict continuous values.

👉 Example: Predicting **salary (package)** based on **CGPA**

---

## 🎯 Problem Statement
Given a student's CGPA, predict their expected placement package (in LPA).

---

## 📊 Dataset

| CGPA | Package |
|------|--------|
| 5.5  | 2.5    |
| 6.7  | 3.0    |
| 7.7  | 5.0    |
| 9.1  | 9.5    |

- **Feature (X):** CGPA  
- **Target (y):** Package  

---

## 📈 Data Visualization

```python
import matplotlib.pyplot as plt

plt.scatter(df['cgpa'], df['package'])
plt.xlabel('CGPA')
plt.ylabel('Package (in LPA)')
plt.show()
````

👉 Each point represents a student
👉 Helps understand the relationship between CGPA and Package

---

## 📉 Mathematical Model

```
y = mx + b
```

* `m` = slope (rate of change)
* `b` = intercept

👉 Final equation:

```
Package = m × CGPA + b
```

---

## ⚙️ Data Preparation

```python
X = df.iloc[:, 0:1]   # Feature (CGPA)
y = df.iloc[:, -1]    # Target (Package)
```

---

## 🔀 Train-Test Split

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=2
)
```

* 80% → Training
* 20% → Testing

---

## 🤖 Model Training

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train, y_train)
```

---

## 🔮 Prediction

```python
y_pred = model.predict(X_test)
```

---

## 📊 Visualization with Best Fit Line

```python
plt.scatter(df['cgpa'], df['package'])
plt.plot(X_train, model.predict(X_train))
plt.xlabel('CGPA')
plt.ylabel('Package')
plt.show()
```

---

## 📏 Model Evaluation

```python
from sklearn.metrics import r2_score

r2_score(y_test, y_pred)
```

👉 Closer to **1** means better model performance

---

## 🧩 Key Insights

* Works best for linear relationships
* Sensitive to outliers
* Foundation for advanced ML models

---

## 🧠 Example Prediction

If:

* m = 0.7
* b = 1.2

Then for CGPA = 8:

```
Package = 0.7 × 8 + 1.2 = 6.8 LPA
```

---

## 🔥 Full Pipeline

1. Load data
2. Visualize data
3. Split dataset
4. Train model
5. Make predictions
6. Evaluate performance

---

## 📌 Notes

* Simple Linear Regression is easy to understand
* Helps build intuition for machine learning
* Can be extended to Multiple Linear Regression

---

## 📎 Resources

* Google Colab Notebook:
  [https://colab.research.google.com/drive/1axZxH0b8_Ft3EkEp2mMxwDBa4-I9f-xx](https://colab.research.google.com/drive/1axZxH0b8_Ft3EkEp2mMxwDBa4-I9f-xx)

* Reference Notes:
  Simple Linear Regression PDF

---
