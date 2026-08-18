# 🚢 Titanic Regression Models

> A beginner-friendly machine learning project comparing **LightGBM, CatBoost, ElasticNet, and Ridge Regression** on the Titanic dataset.

---

## 📌 Project Overview

In this project, we apply four different regression algorithms to the **Titanic dataset**.

The goal is to predict a passenger's **Fare** using information such as:

- 👤 Age
- 🎟️ Passenger Class
- 👨‍👩‍👧‍👦 Number of siblings/spouses
- 👨‍👩‍👧 Number of parents/children

### Models Used

| # | Model | Type |
|---|---|---|
| 1 | 🌱 LightGBM Regression | Tree-based |
| 2 | 🐱 CatBoost Regression | Tree-based |
| 3 | 🧬 ElasticNet Regression | Linear + Regularization |
| 4 | 🏔️ Ridge Regression | Linear + Regularization |

---

# 🎯 Objective

The main objective is to:

1. Load and clean the Titanic dataset.
2. Select useful features.
3. Split the data into training and testing sets.
4. Train four regression models.
5. Predict passenger fares.
6. Evaluate each model.
7. Compare their performance.
8. Analyze residuals.

---

# 📊 Dataset

We use the **Titanic dataset**.

For this project:

### Features (X)

```text
Pclass
Age
SibSp
Parch
```

### Target (y)

```text
Fare
```

In simple words:

> We give the model information about a passenger and ask it to predict their ticket fare.

---

# 🧠 Why `Fare`?

The Titanic dataset is commonly used for **classification**, where the goal is to predict whether a passenger survived.

However:

```text
Survived = 0 or 1
```

is a classification target.

For this project, we want to perform **regression**, so we use:

```text
Fare = continuous numerical value
```

This makes `Fare` appropriate for regression.

---

# 🔄 Machine Learning Workflow

The overall workflow looks like this:

```text
              Titanic Dataset
                     │
                     ↓
              Data Cleaning
                     │
                     ↓
             Select Features
                     │
                     ↓
              Train / Test Split
                     │
           ┌─────────┴─────────┐
           ↓         ↓         ↓
        LightGBM  CatBoost  ElasticNet  Ridge
           │         │         │         │
           └─────────┴─────────┴─────────┘
                     │
                     ↓
                 Predictions
                     │
                     ↓
               Evaluation
                     │
                     ↓
              Model Comparison
```

---

# 🧹 Data Preprocessing

Before training the models, we need to prepare the data.

## Handling Missing Values

The Titanic dataset contains missing values, especially in the `Age` column.

We replace missing ages with the median:

```python
X["Age"] = X["Age"].fillna(X["Age"].median())
```

### Why median?

The median is less affected by extreme values than the mean.

For example:

```text
Age = 20, 22, 25, 28, 80
```

The median is:

```text
25
```

So missing values can be replaced with a reasonable central value.

---

# ✂️ Train-Test Split

We divide the dataset into two parts:

```text
80% → Training data
20% → Testing data
```

The training data teaches the model.

The testing data checks whether the model can make predictions on data it hasn't seen before.

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)
```

### Why do this?

Imagine studying for an exam.

If you practice the exact questions that appear on the exam, you may memorize them.

But that doesn't mean you actually understand the subject.

Machine learning works similarly.

We want to know if the model can **generalize** to unseen data.

---

# 🌱 1. LightGBM Regression

## What is LightGBM?

**LightGBM** stands for:

> Light Gradient Boosting Machine

It is a fast and efficient **tree-based machine learning algorithm** developed by Microsoft.

It builds multiple decision trees and combines them to improve predictions.

---

## 🌳 How does it work?

Imagine the model asking questions:

```text
Is Pclass <= 2?
       │
       ├── Yes → Is Age <= 30?
       │             │
       │             └── Predict Fare
       │
       └── No → Predict lower Fare
```

It creates many trees like this.

Each new tree attempts to improve the mistakes made by previous trees.

This process is called:

> **Gradient Boosting**

---

## ⭐ Advantages

- Very fast
- Good predictive performance
- Works well with large datasets
- Handles complex relationships
- Often requires less memory than traditional boosting methods

---

## ⚠️ Disadvantages

- Can overfit if not tuned properly
- More difficult to interpret than simple linear models
- Hyperparameter tuning can be complicated

---

## Example

```python
from lightgbm import LGBMRegressor

model = LGBMRegressor(
    n_estimators=200,
    learning_rate=0.05,
    max_depth=5,
    random_state=42
)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

# 🐱 2. CatBoost Regression

## What is CatBoost?

**CatBoost** is a gradient boosting algorithm based on decision trees.

The name comes from:

> **Category + Boosting**

It was developed by Yandex.

CatBoost is especially famous for handling **categorical data** effectively.

---

## 🌳 How does it work?

Like LightGBM, CatBoost creates multiple decision trees.

Each tree tries to correct errors from previous trees.

```text
Tree 1
   ↓
Make predictions
   ↓
Find errors
   ↓
Tree 2
   ↓
Correct errors
   ↓
Tree 3
   ↓
Better predictions
```

Eventually, the trees work together to produce a strong prediction.

---

## ⭐ Advantages

- Excellent performance
- Handles categorical variables well
- Good with small and medium-sized datasets
- Reduces some common forms of overfitting
- Easy to use

---

## ⚠️ Disadvantages

- Can be slower than LightGBM
- Can consume more memory
- Still requires hyperparameter tuning

---

## Example

```python
from catboost import CatBoostRegressor

model = CatBoostRegressor(
    iterations=200,
    learning_rate=0.05,
    depth=5,
    verbose=False
)

model.fit(X_train, y_train)

y_pred = model.predict(X_test)
```

---

# 🧬 3. ElasticNet Regression

## What is ElasticNet?

ElasticNet is a **linear regression model with regularization**.

It combines two techniques:

```text
Lasso Regression
        +
Ridge Regression
        =
ElasticNet
```

That's why it's called:

> **ElasticNet**

---

## 🧠 Why regularization?

Imagine you have a model that becomes too complicated and starts memorizing the training data.

This is called:

> **Overfitting**

Regularization adds a penalty to discourage unnecessarily large coefficients.

---

## ElasticNet combines:

### L1 Regularization

From Lasso.

It can push some coefficients toward zero.

This can help with **feature selection**.

### L2 Regularization

From Ridge.

It shrinks coefficients and helps keep the model stable.

---

## ⭐ Advantages

- Helps reduce overfitting
- Useful when there are many features
- Can perform feature selection
- Combines Lasso and Ridge strengths

---

## ⚠️ Disadvantages

- Usually requires feature scaling
- Not as good at capturing complex nonlinear relationships
- Requires tuning of `alpha` and `l1_ratio`

---

## Example

```python
from sklearn.linear_model import ElasticNet

model = ElasticNet(
    alpha=0.1,
    l1_ratio=0.5,
    max_iter=10000
)

model.fit(X_train_scaled, y_train)

y_pred = model.predict(X_test_scaled)
```

---

# 🏔️ 4. Ridge Regression

## What is Ridge Regression?

Ridge Regression is a variation of linear regression that uses:

> **L2 Regularization**

It adds a penalty to large coefficients.

---

## 🧠 Why use Ridge?

Normal linear regression might produce very large coefficients when features are strongly related to each other.

Ridge keeps those coefficients under control.

Think of it as:

```text
Normal Regression
        ↓
Very large coefficients 😵
        ↓
Ridge adds penalty
        ↓
Smaller / more stable coefficients 😌
```

---

## ⭐ Advantages

- Simple
- Fast
- Reduces overfitting
- Works well with correlated features
- Easy to interpret

---

## ⚠️ Disadvantages

- Assumes a linear relationship
- Does not automatically remove features
- Usually needs feature scaling
- May perform poorly when relationships are highly nonlinear

---

## Example

```python
from sklearn.linear_model import Ridge

model = Ridge(alpha=1.0)

model.fit(X_train_scaled, y_train)

y_pred = model.predict(X_test_scaled)
```

---

# ⚖️ LightGBM vs CatBoost vs ElasticNet vs Ridge

| Feature | LightGBM | CatBoost | ElasticNet | Ridge |
|---|---|---|---|---|
| 🌳 Decision Trees | ✅ | ✅ | ❌ | ❌ |
| 📈 Linear Model | ❌ | ❌ | ✅ | ✅ |
| 🔥 Boosting | ✅ | ✅ | ❌ | ❌ |
| Regularization | ✅ | ✅ | ✅ | ✅ |
| Handles Nonlinear Data | ✅ | ✅ | ❌ | ❌ |
| Feature Scaling Needed | ❌ | ❌ | ✅ | ✅ |
| Easy to Interpret | Medium | Medium | High | High |
| Speed | Very Fast | Fast | Very Fast | Very Fast |

---

# 📏 Model Evaluation

After training the models, we need to measure their performance.

We use four important metrics:

```text
MSE
RMSE
MAE
R²
```

---

# 1️⃣ MSE — Mean Squared Error

MSE calculates the average squared difference between actual and predicted values.

```text
MSE = Average((Actual - Predicted)²)
```

### Lower is better ✅

Large errors are punished heavily because the errors are squared.

---

# 2️⃣ RMSE — Root Mean Squared Error

RMSE is simply the square root of MSE.

```text
RMSE = √MSE
```

It is easier to interpret because it is in the same units as the target.

### Lower is better ✅

---

# 3️⃣ MAE — Mean Absolute Error

MAE calculates the average absolute difference.

```text
MAE = Average(|Actual - Predicted|)
```

Example:

```text
Actual = 50
Predicted = 45

Error = |50 - 45|
      = 5
```

### Lower is better ✅

---

# 4️⃣ R² Score

R² tells us how well the model explains the variation in the target.

Generally:

```text
R² = 1.0 → Excellent
R² = 0.8 → Very good
R² = 0.5 → Moderate
R² = 0.0 → Poor
```

### Higher is better ✅

---

# 📊 Evaluation Matrix

The four models can be compared using a table:

| Model | MSE | RMSE | MAE | R² |
|---|---:|---:|---:|---:|
| LightGBM | ↓ | ↓ | ↓ | ↑ |
| CatBoost | ↓ | ↓ | ↓ | ↑ |
| ElasticNet | ↓ | ↓ | ↓ | ↑ |
| Ridge | ↓ | ↓ | ↓ | ↑ |

Remember:

> **MSE ↓ = Better**  
> **RMSE ↓ = Better**  
> **MAE ↓ = Better**  
> **R² ↑ = Better**

---

# 📉 Residual Analysis

A residual is:

```text
Residual = Actual Value - Predicted Value
```

For example:

```text
Actual Fare     = 50
Predicted Fare  = 45

Residual = 50 - 45
         = 5
```

A residual plot shows these errors visually.

Ideally, residuals should be:

```text
       •       •
  •        •
---------------------- 0
      •    •      •
   •       •
```

They should be randomly scattered around zero.

### 🚨 Patterns can indicate problems

If the residuals form a curve or clear pattern, the model may not be capturing the relationship correctly.

---

# 🧪 Why Use Four Models?

Using multiple models allows us to compare different approaches.

### 🌱 LightGBM

> "Let's use powerful decision trees and boosting."

### 🐱 CatBoost

> "Let's use boosting with strong handling of categorical data."

### 🧬 ElasticNet

> "Let's use linear regression with both L1 and L2 regularization."

### 🏔️ Ridge

> "Let's use linear regression with L2 regularization."

The goal isn't to assume one model is always the best.

The goal is to **test them and let the evaluation metrics tell us which performs better on our dataset.**

---

# 🏆 Final Takeaway

This project demonstrates how different machine learning algorithms can approach the same regression problem.

The complete process is:

```text
📂 Load Data
      ↓
🧹 Clean Data
      ↓
🎯 Select Features & Target
      ↓
✂️ Train/Test Split
      ↓
🤖 Train Models
      ↓
🔮 Make Predictions
      ↓
📏 Evaluate Models
      ↓
📊 Compare Results
      ↓
🏆 Select Best Model
```

---

# 💡 Key Concepts to Remember

| Concept | Simple Meaning |
|---|---|
| Feature | Input used to make a prediction |
| Target | Value we want to predict |
| Training Data | Data used to teach the model |
| Testing Data | Unseen data used to evaluate the model |
| Regression | Predicting a numerical value |
| Residual | Actual − Predicted |
| Overfitting | Model memorizes training data too much |
| Regularization | Technique used to reduce overfitting |
| MSE | Average squared error |
| RMSE | Square root of MSE |
| MAE | Average absolute error |
| R² | How well the model explains the target |

---

# 🚀 Conclusion

In this project, four regression algorithms were applied to the Titanic dataset:

**LightGBM, CatBoost, ElasticNet, and Ridge Regression.**

The models were evaluated using **MSE, RMSE, MAE, and R² Score**.

The best model should be selected based on the evaluation results rather than simply assuming that one algorithm is always superior.

> **Different datasets → different winners. 🏆**

---

## 📚 Technologies Used

- Python 🐍
- Pandas
- NumPy
- Scikit-learn
- LightGBM
- CatBoost
- Matplotlib
- Jupyter Notebook / Google Colab

---

## 👨‍💻 Project Structure

```text
Titanic-Regression/
│
├── titanic.csv
├── LightGBM.py
├── CatBoost.py
├── ElasticNet.py
├── Ridge.py
├── evaluation.py
└── README.md
```

---

⭐ **Made for learning and experimenting with regression models.**
