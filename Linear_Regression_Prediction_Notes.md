# 🤖 Linear Regression Prediction - Notes

> ## 🎯 Objective
Train a Linear Regression model and use it to predict marks for a new input.

---

# 📚 What is Linear Regression?

Linear Regression is a **Supervised Machine Learning** algorithm used to predict **continuous numerical values**.

---

# 🔧 Step 1: Import Libraries

```python
from sklearn.linear_model import LinearRegression
import time
```

- `LinearRegression` creates the ML model.
- `time.sleep()` pauses the program.

---

# 📊 Step 2: Create the Dataset

```python
x = [[1],[2],[3],[4],[5],[6]]
y = [20,30,40,50,60,70]
```

| Hours Studied | Marks |
|---:|---:|
|1|20|
|2|30|
|3|40|
|4|50|
|5|60|
|6|70|

- `x` = Feature (input)
- `y` = Label (output)

---

# 🏗️ Step 3: Create the Model

```python
model = LinearRegression()
```

Creates a Linear Regression model.

---

# 🚀 Step 4: Train the Model

```python
model.fit(x, y)
```

The model learns the relationship between the inputs and outputs.

```text
Dataset
   │
   ▼
fit(x, y)
   │
   ▼
Trained Model
```

---

# ⏳ Step 5: Training Phase

```python
print("##########model is in training phase################")
time.sleep(5)
```

Displays a message and waits for 5 seconds.

---

# 🔮 Step 6: Prediction Phase

```python
prediction = model.predict([[9]])
```

The model predicts the marks for **9**.

Expected output:

```text
Predicted Marks: 100.0
```

Since the data increases by **10 marks** for every increase of **1** in the input, the prediction for `9` is approximately **100**.

---

# 📈 Workflow

```text
Input Data
   │
   ▼
Create Model
   │
   ▼
Train (fit)
   │
   ▼
Trained Model
   │
   ▼
Predict
   │
   ▼
Predicted Marks
```

---

# ⚠️ Common Mistakes

- Calling `predict()` before `fit()`.
- Forgetting that `predict()` expects a 2D list, e.g. `[[9]]`, not `[9]`.

---

# 📝 Important Functions

| Function | Purpose |
|---|---|
| `LinearRegression()` | Create model |
| `fit()` | Train model |
| `predict()` | Predict new values |
| `time.sleep()` | Pause execution |

---

# 🎓 Viva Questions

1. What is Linear Regression?
2. Why do we use `fit()`?
3. Why is `[[9]]` used instead of `[9]`?
4. What is the difference between features and labels?

---

# 📌 Quick Revision

- 🤖 Linear Regression predicts continuous values.
- 📘 `x` = Features.
- 📗 `y` = Labels.
- 🚀 `fit()` trains the model.
- 🔮 `predict()` predicts new values.
