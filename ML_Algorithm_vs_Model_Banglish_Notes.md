# ML Algorithm vs Model 

## 🤔 Algorithm vs Model

Onek shomoy amra **Algorithm** ar **Model** ke ek jinis mone kori.
Actually duita alada.

-   **Algorithm** = Je learning method diye machine data theke shikhe.
-   **Model** = Algorithm `fit()` howar por je trained output pai.

Example:

``` python
from sklearn.linear_model import LogisticRegression

model = LogisticRegression()
model.fit(X_train, y_train)
```

Ekhane:

-   `LogisticRegression()` = Algorithm (Estimator)
-   `model.fit()` er por `model` = Trained Model

------------------------------------------------------------------------

# 🇺🇸 USA Visa Prediction

USA Visa Prediction ekta **Binary Classification** problem.

Target:

``` text
Approved
Denied
```

Tai ekhane onek classification algorithm try kora jay.

## Common Algorithms

-   Logistic Regression
-   Decision Tree
-   Random Forest
-   XGBoost
-   SVM
-   KNN
-   Naive Bayes

Example:

``` python
lr = LogisticRegression()
dt = DecisionTreeClassifier()
rf = RandomForestClassifier()

lr.fit(X_train, y_train)
dt.fit(X_train, y_train)
rf.fit(X_train, y_train)
```

Prediction:

``` python
lr_pred = lr.predict(X_test)
dt_pred = dt.predict(X_test)
rf_pred = rf.predict(X_test)
```

Tarpor prottek model-er calculate korbo:

-   Accuracy
-   Precision
-   Recall
-   F1 Score
-   Confusion Matrix

------------------------------------------------------------------------

# 🤔 Keno Multiple Algorithm Try Kori?

Age theke keu bolte pare na kon algorithm kon dataset-e best perform
korbe.

Example:

## Dataset A

  Algorithm             Accuracy
  --------------------- ----------
  Logistic Regression   82%
  Decision Tree         75%
  Random Forest         90%
  XGBoost               92%

## Dataset B

  Algorithm             Accuracy
  --------------------- ----------
  Logistic Regression   96%
  Decision Tree         91%
  Random Forest         95%

Dekha jacche ek dataset-e Logistic Regression best, abar arekta-te
XGBoost best.

👉 Tai Machine Learning-e ekadhik algorithm train kore compare kora hoy.

------------------------------------------------------------------------

# 📊 Report-e Ki Dibo?

Example comparison table:

  Model                   Accuracy   Precision   Recall   F1 Score
  --------------------- ---------- ----------- -------- ----------
  Logistic Regression         0.84        0.83     0.82       0.82
  Decision Tree               0.87        0.86     0.85       0.85
  Random Forest               0.92        0.91     0.91       0.91
  XGBoost                     0.94        0.94     0.93       0.93

Finally report-e likhte paro:

> **Random Forest achieved the highest F1-score; therefore, it was
> selected as the final model.**

------------------------------------------------------------------------

# 📌 Linear Regression Kothay Use Hobe?

Eta depend kore target variable-er upor.

## 1. Regression Problem

Target jodi continuous number hoy:

``` text
Salary
House Price
Temperature
```

Tahole use kora hoy:

-   Linear Regression
-   Ridge Regression
-   Lasso Regression
-   Decision Tree Regressor
-   Random Forest Regressor

------------------------------------------------------------------------

## 2. Classification Problem

Target jodi category/class hoy:

``` text
Visa Approved / Denied
Spam / Not Spam
Disease / No Disease
```

Tahole use kora hoy:

-   Logistic Regression
-   Decision Tree Classifier
-   Random Forest Classifier
-   SVM
-   XGBoost
-   KNN

⚠️ **Linear Regression classification-er jonno use kora hoy na**, karon
eta continuous value predict korar jonno design kora.

------------------------------------------------------------------------

# ✅ Summary

-   Algorithm = Learning method
-   Model = Trained output
-   Classification problem hole multiple classification algorithm try
    kora hoy.
-   Sob model-er Accuracy, Precision, Recall, F1 Score, Confusion Matrix
    compare kora hoy.
-   Best performing model-ke final model hisebe select kora hoy.
