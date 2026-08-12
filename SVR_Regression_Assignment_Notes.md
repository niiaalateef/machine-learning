# 🤖 SVR Regression Model — Assignment

> 🎯 **Goal:** Implement Support Vector Regression using **RBF** and **Polynomial** kernels on a new dataset.

---

## 📝 Task

### 🚀 Implement an SVR model of regression using:

- 🔵 **RBF Kernel**
- 🟣 **Polynomial (Poly) Kernel**

The models should be trained on a new dataset, evaluated, compared, and used to make predictions.

---

## 🛒 Dataset — Supermarket Sales

For this assignment, I used the **Supermarket Sales** dataset.

🎯 **Target variable:**

```text
Rating
```

📊 Some of the features in the dataset:

- 🏢 Branch
- 🌆 City
- 👤 Customer Type
- 🚻 Gender
- 🛍️ Product Line
- 💰 Unit Price
- 🔢 Quantity
- 🧾 Tax
- 💵 Total
- 💳 Payment
- 📦 COGS
- 📈 Gross Income
- ⭐ Rating

---

## 🔧 What I Did

### 1️⃣ Loaded the Dataset

Loaded the supermarket sales Excel file using **Pandas**.

```python
import pandas as pd

df = pd.read_excel("supermarket_sales.xlsx")
```

### 2️⃣ 🎯 Selected the Target

Used `Rating` as the target variable.

```python
X = df.drop(columns=["Rating"])
y = df["Rating"]
```

### 3️⃣ 🧹 Prepared the Data

Separated:

- 🔢 Numerical features
- 🏷️ Categorical features

Categorical features were converted using **One-Hot Encoding**.

Numerical features were scaled using **StandardScaler**.

### 4️⃣ ✂️ Split the Data

The dataset was divided into:

- 🏋️ **80% Training data**
- 🧪 **20% Testing data**

```python
X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.20,
    random_state=42
)
```

---

# 🤖 SVR Models

## 🔵 1. SVR — RBF Kernel

The first model used the **Radial Basis Function (RBF)** kernel.

```python
SVR(
    kernel="rbf",
    C=100,
    gamma="scale",
    epsilon=0.1
)
```

### ⚙️ Main parameters

- `C=100` → Controls the penalty for errors
- `gamma="scale"` → Controls the influence of individual data points
- `epsilon=0.1` → Defines the epsilon-insensitive region

💡 RBF is useful for finding **non-linear relationships** in the data.

---

## 🟣 2. SVR — Polynomial Kernel

The second model used the **Polynomial** kernel.

```python
SVR(
    kernel="poly",
    C=100,
    degree=3,
    gamma="scale",
    epsilon=0.1
)
```

### ⚙️ Main parameters

- `C=100` → Controls the penalty for errors
- `degree=3` → Uses a third-degree polynomial
- `gamma="scale"` → Controls feature influence
- `epsilon=0.1` → Defines the error-insensitive region

💡 The Polynomial kernel can model relationships that follow a **polynomial pattern**.

---

# 📏 Model Evaluation

To compare the two models, I used four regression metrics:

| 📊 Metric | 🧠 Meaning | 🏆 Better |
|---|---|---|
| MAE | Average absolute error | ⬇️ Lower |
| MSE | Average squared error | ⬇️ Lower |
| RMSE | Square root of MSE | ⬇️ Lower |
| R² | Explained variance | ⬆️ Higher |

### 🧮 Evaluation code

```python
mae = mean_absolute_error(y_test, prediction)
mse = mean_squared_error(y_test, prediction)
rmse = np.sqrt(mse)
r2 = r2_score(y_test, prediction)
```

---

# 🆚 RBF vs Polynomial

The two models were compared based on their test performance.

| 🤖 Model | MAE | MSE | RMSE | R² |
|---|---:|---:|---:|---:|
| 🔵 SVR-RBF | — | — | — | — |
| 🟣 SVR-Poly | — | — | — | — |

> 📌 The actual values depend on the dataset and model configuration.

🏆 The better model is the one with:

- ⬇️ Lower MAE
- ⬇️ Lower MSE
- ⬇️ Lower RMSE
- ⬆️ Higher R²

---

# 🔮 Predicting New Data

After training, the best-performing model can be used to predict ratings for new supermarket transactions.

```python
prediction = best_model.predict(new_data)

print("⭐ Predicted Rating:", prediction[0])
```

The new data needs to contain the same input features used during training.

---

# 🐛 Debugging — FileNotFoundError

While working on the assignment, I encountered this error:

```text
FileNotFoundError:
[Errno 2] No such file or directory:
'supermarket_sales.xlsx'
```

### 🔍 Why did this happen?

Python could not find the Excel file in the current working directory.

### ✅ How I fixed it

I made sure that the Excel file was in the correct project folder or provided the correct file path.

Example:

```python
df = pd.read_excel(
    r"C:\Users\HP\OneDrive\Desktop\python_practive\2-machine _learning\supermarket_sales.xlsx"
)
```

💡 **Lesson:** Always check the file name and file location when using `pd.read_excel()` or `pd.read_csv()`.

---

# 🧠 What I Learned

Through this assignment, I learned how to:

- 🤖 Implement **Support Vector Regression**
- 🔵 Use the **RBF kernel**
- 🟣 Use the **Polynomial kernel**
- 🧹 Preprocess numerical and categorical data
- 📏 Scale features before using SVR
- ✂️ Split data into training and testing sets
- 📊 Evaluate regression models
- 🆚 Compare different kernels
- 🔮 Make predictions on new data
- 🐛 Debug file-path errors
- 🐍 Work with Pandas and Scikit-learn

---

# 🏁 Final Workflow

```text
📂 Load Dataset
       ↓
🧹 Prepare Data
       ↓
🎯 Select Target (Rating)
       ↓
🏷️ Encode Categorical Features
       ↓
📏 Scale Numerical Features
       ↓
✂️ Train/Test Split
       ↓
🔵 Train SVR-RBF
       ↓
🟣 Train SVR-Poly
       ↓
📊 Evaluate Both Models
       ↓
🆚 Compare Results
       ↓
🏆 Select Best Model
       ↓
🔮 Predict New Data
```

---

## 🎉 Assignment Complete!

> 💻 **Machine Learning technique:** Support Vector Regression  
> 📚 **Kernels:** RBF + Polynomial  
> 🛒 **Dataset:** Supermarket Sales  
> 🎯 **Target:** Rating  
> 🐍 **Language:** Python  
> 🤖 **Library:** Scikit-learn

⭐ **Next step:** Experiment with `C`, `gamma`, `epsilon`, and `degree` to see how they affect model performance!
