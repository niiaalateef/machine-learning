# 🏔️ Ridge Regression with Scikit-learn

## 🎯 Objective
Train a **Ridge Regression** model to predict **Math** marks from **Physics** marks, evaluate it using **MSE** and **R² Score**, and predict the Math marks for a student scoring **80** in Physics.

---

## 📚 Libraries

```python
import pandas as pd
from sklearn.linear_model import Ridge
from sklearn.metrics import mean_squared_error, r2_score
import time
```

| Library | Purpose |
|---|---|
| pandas | Read the CSV dataset |
| Ridge | Create the Ridge Regression model |
| mean_squared_error | Measure prediction error |
| r2_score | Measure model performance |
| time | Pause execution |

---

## 🧹 Read and Clean Data

```python
df = pd.read_csv("data.csv")
df = df.dropna()
```

- Reads the dataset.
- Removes rows with missing values.

---

## 🎯 Features and Target

```python
X = df[["Physics"]]
y = df["Math"]
```

- **Feature (X):** Physics marks
- **Target (y):** Math marks

---

## 🤖 Create the Ridge Model

```python
model = Ridge(alpha=0.5)
```

### What is `alpha`?

`alpha` controls the amount of regularization.

- Small `alpha` → Model behaves more like Linear Regression.
- Large `alpha` → Stronger regularization to reduce overfitting.

---

## 🚀 Train the Model

```python
model.fit(X, y)
```

The model learns the relationship between Physics and Math.

---

## 🔮 Predict Training Data

```python
y_pred = model.predict(X)
```

Predicts Math marks for the training data.

---

## 📏 Mean Squared Error (MSE)

```python
mse = mean_squared_error(y, y_pred)
```

- Lower MSE = Better predictions.
- MSE = 0 = Perfect predictions.

---

## ⭐ R² Score

```python
r2 = r2_score(y, y_pred)
```

- R² close to **1** → Good model.
- R² close to **0** → Poor model.

---

## 🎯 Predict New Data

```python
prediction = model.predict(pd.DataFrame({
    "Physics": [80]
}))
```

Predicts the expected Math marks for a student with **80** Physics marks.

---

## 🔄 Workflow

```text
CSV
 │
 ▼
Read Data
 │
 ▼
Remove Missing Values
 │
 ▼
Create Ridge Model
 │
 ▼
fit()
 │
 ▼
Predict
 │
 ▼
Evaluate (MSE & R²)
 │
 ▼
Predict New Student
```

---

## ⚠️ Common Mistakes

- Forgetting `dropna()`.
- Calling `predict()` before `fit()`.
- Setting `alpha` too high without testing.

---

## 🎓 Viva Questions

1. What is Ridge Regression?
2. What is regularization?
3. What does `alpha` do?
4. When would you use Ridge instead of Linear Regression?
5. What do MSE and R² measure?

---

## 📌 Quick Revision

- 📂 `read_csv()` loads data.
- 🧹 `dropna()` removes missing values.
- 🏔️ `Ridge(alpha=0.5)` creates the model.
- 🚀 `fit()` trains the model.
- 🔮 `predict()` makes predictions.
- 📏 `mean_squared_error()` measures error.
- ⭐ `r2_score()` measures model quality.
