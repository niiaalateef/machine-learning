# 📈 Linear Regression with CSV Dataset (Physics → Math)

This note explains reading a CSV dataset, removing missing values, training a Linear Regression model, evaluating it with MSE and R² Score, and predicting Math marks from Physics marks.

## Steps

1. Import pandas, LinearRegression, mean_squared_error, r2_score, and time.
2. Read `data.csv` using `pd.read_csv()`.
3. Remove missing values with `dropna()`.
4. Select:
   - **X = Physics** (feature)
   - **y = Math** (label)
5. Create the model using `LinearRegression()`.
6. Train the model using `model.fit(X, y)`.
7. Predict training values using `model.predict(X)`.
8. Calculate **Mean Squared Error (MSE)**.
9. Calculate **R² Score**.
10. Predict Math marks for a student who scored **80** in Physics.

## Workflow

```text
CSV -> Read -> Clean -> Select X & y -> Train -> Predict -> Evaluate (MSE & R²) -> Predict New Data
```

## Key Points

- `dropna()` removes rows with missing values.
- `X` must be written as `df[["Physics"]]` because Scikit-learn expects a 2D feature matrix.
- Lower **MSE** means better predictions.
- Higher **R²** (closer to 1) means a better model.
