# 📊 KNN Height & Weight Classifier

A Machine Learning web application built with **Python**, **Scikit-learn**, and **Streamlit** that predicts whether a person belongs to **Class 0 (Lower BMI)** or **Class 1 (Higher BMI)** based on their **Height** and **Weight**.

---

## 🚀 Features

- 🤖 K-Nearest Neighbors (KNN) Classification
- 🎨 Beautiful Streamlit User Interface
- 📏 Predicts class using Height & Weight
- ⚡ Fast predictions with a cached model
- 📊 Displays confidence scores
- 📈 Shows model accuracy
- 💻 Easy to use

---

# 🛠 Technologies Used

| Technology | Purpose |
|------------|---------|
| Python | Programming Language |
| Streamlit | Web Application |
| Pandas | Data Processing |
| NumPy | Numerical Computing |
| Scikit-learn | Machine Learning |
| StandardScaler | Feature Scaling |
| KNeighborsClassifier | Classification |

---

# 📂 Project Structure

```text
KNN-Height-Weight-Classifier
│
├── app.py
├── README.md
├── backend_notes.md
├── frontend_notes.md
├── requirements.txt
├── data.csv
└── images/
```

---

# 📊 Dataset

The dataset contains the following columns:

| Height (cm) | Weight (kg) | Class |
|-------------|-------------|-------|
|160|55|0|
|165|60|0|
|170|65|0|
|175|70|1|
|180|75|1|
|185|80|1|

Where:

- **Height** → Feature
- **Weight** → Feature
- **Class** → Target Variable

---

# 🧠 How the Model Works

```text
Dataset
   │
   ▼
Train/Test Split
   │
   ▼
StandardScaler
   │
   ▼
KNN Classifier
   │
   ▼
Model Training
   │
   ▼
Prediction
```

---

# ⚙️ Installation

Clone the repository:

```bash
git clone https://github.com/YOUR_USERNAME/KNN-Height-Weight-Classifier.git
```

Go to the project folder:

```bash
cd KNN-Height-Weight-Classifier
```

Install the required libraries:

```bash
pip install -r requirements.txt
```

---

# ▶️ Run the Application

```bash
streamlit run app.py
```

Once the server starts, open the local URL shown in the terminal (usually `http://localhost:8501`) in your browser.

---

# 🖥️ Application Preview

## 🏠 Home Screen

> Add a screenshot here after running the app.

```text
images/homepage.png
```

---

## 🔮 Prediction Result

> Add a screenshot of the prediction page.

```text
images/prediction.png
```

---

# 📈 Prediction Process

1. Enter **Height**.
2. Enter **Weight**.
3. Click **Predict Class**.
4. The input is scaled using **StandardScaler**.
5. The KNN model predicts the class.
6. The application displays:
   - Predicted Class
   - Confidence Scores
   - Model Accuracy

---

# 📚 Machine Learning Concepts Used

- K-Nearest Neighbors (KNN)
- Feature Scaling
- Train/Test Split
- Model Training
- Prediction
- Accuracy Score

---

# 📦 Requirements

```text
streamlit
pandas
numpy
scikit-learn
```

Install them with:

```bash
pip install -r requirements.txt
```

---

# 🚀 Future Improvements

- Upload custom datasets
- Compare multiple ML algorithms
- Add charts and graphs
- Deploy online using Streamlit Cloud
- Improve UI with more visualizations

---

# 👨‍💻 Author

**Your Name**

Python & Machine Learning Developer

GitHub: https://github.com/YOUR_USERNAME

---

# 📄 License

This project is licensed under the **MIT License**.

---

## ⭐ Support

If you found this project useful:

- ⭐ Star this repository
- 🍴 Fork it
- 📢 Share it with others

Happy Coding! 🚀
