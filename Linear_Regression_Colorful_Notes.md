# 🤖 Linear Regression with Scikit-learn

> ## 🎯 Objective
Learn how to create, train, evaluate, and use a **Linear Regression** model with Scikit-learn.

---

# 📚 What is Linear Regression?

Linear Regression is a **Supervised Machine Learning** algorithm that predicts **continuous numerical values**.

### 🌍 Real-Life Examples
- 📈 Predict house prices
- 💰 Predict salary
- 📚 Predict student marks
- 🌡️ Predict temperature

---

# 🔧 Step 1: Import Libraries

```python
from sklearn.linear_model import LinearRegression
from sklearn.metrics import mean_squared_error
import time
```

| Library | Purpose |
|---|---|
| `LinearRegression` | Creates the ML model |
| `mean_squared_error` | Measures prediction error |
| `time` | Adds delay using `sleep()` |

---

# 📊 Step 2: Create the Dataset

```python
X = [[1], [2], [3], [4], [5]]
y = [40, 50, 60, 70, 80]
```

- **X** = Feature (Hours Studied)
- **y** = Label (Marks)

| Hours | Marks |
|---:|---:|
|1|40|
|2|50|
|3|60|
|4|70|
|5|80|

---

# 🏗️ Step 3: Create the Model

```python
model = LinearRegression()
```

Creates a Linear Regression model.

---

# 🚀 Step 4: Train the Model

```python
model.fit(X, y)
```

The model learns the relationship between **Hours Studied** and **Marks**.

```text
Dataset
   │
   ▼
fit(X, y)
   │
   ▼
Trained Model
```

💡 **Remember:** Without `fit()`, the model cannot make predictions.

---

# ⏳ Step 5: Training Phase

```python
print("Training...")
time.sleep(3)
```

Displays a message and pauses for 3 seconds.

---

# 🔮 Step 6: Predict Training Data

```python
y_pred = model.predict(X)
```

The model predicts marks for every training sample.

---

# 📏 Step 7: Mean Squared Error (MSE)

```python
mse = mean_squared_error(y, y_pred)
```

### Formula

```text
MSE = (1/n) × Σ(Actual − Predicted)²
```

✅ Lower MSE = Better Model

✅ MSE = 0 = Perfect Prediction

---

# 🎯 Step 8: Predict New Data

```python
prediction = model.predict([[3.5]])
print(prediction[0])
```

Expected output:

```text
Predicted Marks: 65.0
```

---

# 🔄 Complete Workflow

```text
Dataset
   │
   ▼
Create Model
   │
   ▼
fit()
   │
   ▼
Trained Model
   │
   ▼
predict()
   │
   ▼
Predicted Output
   │
   ▼
Evaluate with MSE
```

---

# ⚠️ Common Mistakes

❌ Using `predict()` before `fit()`

❌ Mixing `x` and `X`

❌ Forgetting to import required libraries

---

# 📝 Important Functions

| Function | Purpose |
|---|---|
| `LinearRegression()` | Create model |
| `fit()` | Train model |
| `predict()` | Predict values |
| `mean_squared_error()` | Calculate MSE |
| `time.sleep()` | Pause program |

---

# 🎓 Viva / Exam Questions

1. What is Linear Regression?
2. What is supervised learning?
3. What is the purpose of `fit()`?
4. What does `predict()` do?
5. What is Mean Squared Error?
6. What are Features and Labels?

---

# 📌 Quick Revision

- 🤖 Linear Regression predicts **continuous values**.
- 📘 `X` = Features (Input)
- 📗 `y` = Labels (Output)
- 🚀 `fit()` trains the model.
- 🔮 `predict()` makes predictions.
- 📏 `mean_squared_error()` measures accuracy.
- ✅ Lower MSE means a better model.
