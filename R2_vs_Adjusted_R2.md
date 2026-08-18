# 🏠 R² vs Adjusted R² — House Price Regression

> 📚 **Machine Learning Assignment Notes**  
> 🎯 Goal: Understand **R² vs Adjusted R²** by building regression models step-by-step.

---

## 🚀 What is this assignment about?

Imagine you are trying to predict the price of a house.

You have information like:

- 🏠 Size
- 🛏️ Bedrooms
- 🛁 Bathrooms
- 🕰️ Age
- 🌳 Lot Size
- 🚗 Garage

Your job is to build different **Linear Regression** models and see how well they predict:

> 💰 **Price**

The main question is:

> **Does adding more features actually make our model better?**

To answer that, we compare **R²** and **Adjusted R²**.

---

# 🧠 1. The Two Important Metrics

## 📈 R² — "How much does my model explain?"

R² tells us how much of the variation in the target variable is explained by the model.

For example:

```text
R² = 0.70
```

means:

> 🗣️ The model explains about **70% of the variation in house prices**.

### Easy memory trick 🧠

> **R² = How much does my model explain?**

A higher R² generally means a better fit.

---

## ⚖️ Adjusted R² — "Are those extra features actually useful?"

Adjusted R² is similar to R², but it also considers **how many features** are being used.

It penalizes the model when unnecessary features are added.

### Easy memory trick 🧠

> **Adjusted R² = How much does my model explain after considering how many features I used?**

---

## 🆚 R² vs Adjusted R²

| 📈 R² | ⚖️ Adjusted R² |
|---|---|
| Measures explained variation | Measures explained variation while considering model complexity |
| Usually increases when features are added | Can increase OR decrease |
| Does not penalize extra features | Penalizes unnecessary features |
| Good for measuring fit | Better for comparing models with different numbers of features |

### ⭐ Remember this sentence

> **R² rewards adding features, while Adjusted R² checks whether those extra features are actually useful.**

---

# 🏠 2. Our Dataset

We have **50 houses**.

| Feature | What does it mean? |
|---|---|
| 📐 Size | Living area in square feet |
| 🛏️ Bedrooms | Number of bedrooms |
| 🛁 Bathrooms | Number of bathrooms |
| 🕰️ Age | Age of the house |
| 🌳 LotSize | Total land area |
| 🚗 Garage | Number of garage spaces |
| 💰 Price | House price — our target |

### 🎯 Target variable

```text
Price
```

### 🔧 Predictor variables

```text
Size
Bedrooms
Bathrooms
Age
LotSize
Garage
```

Think of it like:

```text
🏠 House Features
       ↓
🤖 Regression Model
       ↓
💰 Predicted Price
```

---

# 🧮 3. Adjusted R² Formula

The formula used is:

```text
Adjusted R² = 1 - (1 - R²) × (n - 1) / (n - k - 1)
```

Where:

- `n` = number of observations
- `k` = number of predictor features
- `R²` = R-squared

For our dataset:

```text
n = 50
```

---

# 🧪 TASK 1 — Start Simple

We begin with just **Size**.

```text
Size → Price
```

### 📊 Results

| Metric | Result |
|---|---:|
| Observations | 50 |
| Features (k) | 1 |
| R² | **0.6991** |
| Adjusted R² | **0.6928** |

### 🔍 What does this mean?

R² = `0.6991`

So:

> 🗣️ **Size alone explains about 69.91% of the variation in house prices.**

Adjusted R² = `0.6928`

So after considering the number of features:

> 🗣️ The model explains about **69.28%** of the variation.

Not bad for using just one feature! 🎯

---

# 🧪 TASK 2 — Add Features One by One

Now we make the model smarter by adding features sequentially.

### Model 1

```text
Size
```

### Model 2

```text
Size + Bedrooms
```

### Model 3

```text
Size + Bedrooms + Bathrooms
```

### Model 4

```text
Size + Bedrooms + Bathrooms + Age
```

### Model 5

```text
Size + Bedrooms + Bathrooms + Age + LotSize
```

### Model 6

```text
Size + Bedrooms + Bathrooms + Age + LotSize + Garage
```

We're basically asking:

> 🤔 "What happens when I give the model more information?"

---

# 📊 TASK 3 — The Big Comparison Table

| Model | Features Used | k | R² | Adjusted R² |
|---|---|---:|---:|---:|
| 🟢 Model 1 | Size | 1 | 0.6991 | 0.6928 |
| 🟢 Model 2 | Size, Bedrooms | 2 | 0.7007 | 0.6879 |
| 🟢 Model 3 | Size, Bedrooms, Bathrooms | 3 | 0.7644 | 0.7491 |
| 🟢 Model 4 | Size, Bedrooms, Bathrooms, Age | 4 | 0.7752 | 0.7552 |
| 🟢 Model 5 | Size, Bedrooms, Bathrooms, Age, LotSize | 5 | 0.9373 | 0.9302 |
| 🏆 Model 6 | Size, Bedrooms, Bathrooms, Age, LotSize, Garage | 6 | **0.9482** | **0.9409** |

---

# 🔎 TASK 4 — Analyze the Results

## 📈 What happened to R²?

R² increased every time we added a feature:

```text
0.6991
   ↓
0.7007
   ↓
0.7644
   ↓
0.7752
   ↓
0.9373
   ↓
0.9482
```

### Answer:

> **R² never decreased.**

Why?

Because adding predictors gives the model more information that it can use to explain Price.

### 🧠 Easy way to remember

> **More information → R² can stay the same or go up.**

---

# ⚖️ What happened to Adjusted R²?

Adjusted R² was:

```text
0.6928
   ↓
0.6879  ⬅️ DROP!
   ↓
0.7491
   ↓
0.7552
   ↓
0.9302
   ↓
0.9409
```

### 🚨 Important!

Adjusted R² **did NOT always increase**.

The only drop happened here:

```text
Model 1 → Model 2

0.6928 → 0.6879
```

We added **Bedrooms**.

But Bedrooms did not improve the model enough to justify the extra complexity.

So Adjusted R² basically said:

> 🤨 "Are you sure you needed that extra feature?"

😂

After that, Adjusted R² increased as more useful features were added.

---

# 🏆 Which Model is Best?

## Model 6 wins! 🥇

Model 6 uses:

```text
📐 Size
🛏️ Bedrooms
🛁 Bathrooms
🕰️ Age
🌳 LotSize
🚗 Garage
```

And gets:

```text
R²            = 0.9482
Adjusted R²   = 0.9409
```

### Why is it the winner?

Because it has:

🥇 Highest R²  
🥇 Highest Adjusted R²

It explains about:

> **94.82% of the variation in house prices.**

And after accounting for the six predictors:

> **Adjusted R² = 94.09%**

### 🏆 Final answer

> **Model 6 provides the best overall fit among the six models.**

---

# 🤔 Why Do We Need Adjusted R²?

Imagine this:

You keep adding random features to your model.

```text
Feature 1
Feature 2
Feature 3
Feature 4
Feature 5
Feature 6
Feature 7
Feature 8
...
```

R² may keep getting higher.

But does that mean the model is actually getting better?

🤷 Not necessarily!

Adjusted R² asks:

> **"Did this new feature really help enough to justify adding it?"**

That's why Adjusted R² is useful.

### ⭐ Super simple explanation

> **R² likes more features. Adjusted R² is more careful.**

---

# 🧪 TASK 5 — Try a Different Feature Order

We changed the order.

Instead of:

```text
Size → Bedrooms → Bathrooms → Age → LotSize → Garage
```

we tried:

```text
Garage → LotSize → Age → Bathrooms → Bedrooms → Size
```

### 📊 Results

| Model | Features | k | R² | Adjusted R² |
|---|---|---:|---:|---:|
| Model 1 | Garage | 1 | 0.0639 | 0.0444 |
| Model 2 | Garage + LotSize | 2 | 0.4877 | 0.4659 |
| Model 3 | Garage + LotSize + Age | 3 | 0.4961 | 0.4632 |
| Model 4 | Garage + LotSize + Age + Bathrooms | 4 | 0.5591 | 0.5200 |
| Model 5 | Garage + LotSize + Age + Bathrooms + Bedrooms | 5 | 0.5702 | 0.5214 |
| 🏆 Model 6 | Garage + LotSize + Age + Bathrooms + Bedrooms + Size | 6 | **0.9482** | **0.9409** |

---

# ❓ Does the Final Adjusted R² Change?

## ❌ No!

The final Adjusted R² is still:

```text
0.9409
```

Why?

Because the final model contains the exact same six features.

The order doesn't matter once all the features are included.

### Think about it like this:

You can travel:

```text
🏠 → A → B → C → D → 🏆
```

or:

```text
🏠 → D → B → A → C → 🏆
```

You took different routes, but you reached the same destination.

🚗💨

---

# 🔀 Does the Path of Adjusted R² Change?

## ✅ Yes!

The intermediate values change because we're adding different features at each stage.

### Original order

```text
0.6928
↓
0.6879
↓
0.7491
↓
0.7552
↓
0.9302
↓
0.9409
```

### Different order

```text
0.0444
↓
0.4659
↓
0.4632
↓
0.5200
↓
0.5214
↓
0.9409
```

So:

> 🔀 **Different feature order = different path**

But:

> 🎯 **Same final features = same final model**

---

# 💻 6. Python — The Main Function

The assignment uses a function to calculate all the metrics:

```python
def compute_metrics(X, y):
    model = LinearRegression()
    model.fit(X, y)

    y_pred = model.predict(X)

    r2 = r2_score(y, y_pred)

    n = len(y)
    k = X.shape[1]

    adj_r2 = 1 - (1 - r2) * (n - 1) / (n - k - 1)

    return r2, adj_r2, k
```

## 🔍 What does each line do?

### Create the model

```python
model = LinearRegression()
```

🤖 Creates a linear regression model.

### Train the model

```python
model.fit(X, y)
```

🎓 Teaches the model using the data.

### Make predictions

```python
y_pred = model.predict(X)
```

🔮 Predicts the house prices.

### Calculate R²

```python
r2 = r2_score(y, y_pred)
```

📈 Calculates R².

### Count observations

```python
n = len(y)
```

👥 Number of houses = 50.

### Count features

```python
k = X.shape[1]
```

🔢 Counts how many predictors are being used.

### Calculate Adjusted R²

```python
adj_r2 = 1 - (1 - r2) * (n - 1) / (n - k - 1)
```

⚖️ Calculates Adjusted R².

---

# 🐍 7. Important Python Terms

| Python | Meaning |
|---|---|
| `df` | DataFrame containing the dataset |
| `X` | Predictor/input features |
| `y` | Target variable |
| `Price` | Target variable |
| `model.fit()` | Trains the model |
| `model.predict()` | Makes predictions |
| `r2_score()` | Calculates R² |
| `X.shape[1]` | Number of features |
| `n` | Number of observations |
| `k` | Number of features |

---

# 🎤 8. Teacher Questions — Cheat Sheet

## ❓ What are you predicting?

> **Price.**

---

## ❓ What are your predictor variables?

> **Size, Bedrooms, Bathrooms, Age, LotSize, and Garage.**

---

## ❓ What is R²?

> **R² tells us how much of the variation in Price is explained by the model.**

---

## ❓ What is Adjusted R²?

> **Adjusted R² measures explained variation while also considering the number of features.**

---

## ❓ Why can Adjusted R² decrease?

> **It can decrease when a new feature does not provide enough useful information to justify adding it.**

---

## ❓ Which model is best?

> **Model 6, because it has the highest R² (0.9482) and highest Adjusted R² (0.9409).**

---

## ❓ Why is Adjusted R² useful?

> **It helps compare models with different numbers of features because it penalizes unnecessary features.**

---

## ❓ Why did R² increase?

> **Adding predictors gives the model more information to explain the target variable, so R² does not decrease when predictors are added.**

---

## ❓ Why did Adjusted R² decrease when Bedrooms was added?

> **Bedrooms did not improve the model enough to justify the additional feature, so the penalty caused Adjusted R² to decrease.**

---

## ❓ Why did changing feature order not change the final result?

> **Because the final model contained the same six features. The order does not affect the final regression model.**

---

# 🎓 9. One-Minute Explanation for Your Teacher

If your teacher says:

> **"Explain your assignment."**

You can say:

> "I used a dataset of 50 houses to predict Price using linear regression. I started with Size as one feature and then added Bedrooms, Bathrooms, Age, LotSize, and Garage one at a time. For each model, I calculated R² and Adjusted R². R² increased every time a feature was added, but Adjusted R² decreased when Bedrooms was added because it did not improve the model enough. After that, Adjusted R² increased. Model 6 was the best because it had the highest R² of 0.9482 and Adjusted R² of 0.9409. I also tested a different feature order. The intermediate Adjusted R² values changed, but the final value stayed at 0.9409 because the final model contained the same six features."

---

# 🧠 10. Super Quick Revision

Before talking to your teacher, remember these:

```text
🏠 Dataset:
50 houses

🎯 Target:
Price

🔧 Predictors:
Size
Bedrooms
Bathrooms
Age
LotSize
Garage

📈 R²:
How much does the model explain?

⚖️ Adjusted R²:
How much does the model explain after considering
the number of features?

🏆 Best model:
Model 6

📊 Model 6:
R² = 0.9482
Adjusted R² = 0.9409
k = 6

📈 R² trend:
Always increased.

⚖️ Adjusted R² trend:
Dropped from Model 1 → Model 2,
then increased.

🔀 Different feature order:
Different intermediate path,
same final result.
```

---

# ⭐ Final Takeaway

The most important lesson from this assignment is:

> **Adding more features can make R² look better, but Adjusted R² helps us decide whether those extra features are actually worth adding.**

And remember:

```text
R²            → "How much can I explain?"
Adjusted R²   → "How much can I explain without
                 unnecessarily complicating my model?"
```

🏠 + 🤖 + 📊 = 🎯 **Better understanding of regression models!**
