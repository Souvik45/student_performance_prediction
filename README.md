# 🎓 Student Performance Prediction

A machine learning project that predicts whether a student will pass or fail based on demographic and socio-economic features — without using correlated score data to ensure a leakage-free, real-world applicable model.

## 📌 Problem Statement
Can we predict a student's academic performance using only background information — such as gender, parental education, lunch type, and test preparation — before any exam scores are available?

This project builds a binary classification model to answer that question using the Students Performance in Exams dataset.

## 📂 Project Structure
```
student-performance-prediction/
│
├── data/
│   └── StudentsPerformance.csv
│
├── Student_Performance_Prediction.ipynb
├── README.md
└── requirements.txt
```

## 📊 Dataset

| Feature                     | Description                                |
| --------------------------- | ------------------------------------------ |
| gender                      | Student's gender (male/female)             |
| race/ethnicity              | Ethnic group (A–E)                         |
| parental level of education | Highest education level of parent          |
| lunch                       | Standard or free/reduced lunch             |
| test preparation course     | Completed or none                          |
| math score                  | Used only to derive target variable        |

**Note:** `reading score` and `writing score` were deliberately dropped to prevent data leakage, as they correlate ~0.8+ with `math score`.

**Target Variable:** `performance` → `1` if math score ≥ 50, else `0`

## 🔬 Approach
```
Raw Data
   ↓
Exploratory Data Analysis (EDA)
   ↓
Preprocessing (Target Encoding, One-Hot Encoding, Leakage Removal)
   ↓
Train-Test Split (80/20)
   ↓
Model Training & Comparison
   ↓
Evaluation (Accuracy, F1, Classification Report, Confusion Matrix)
   ↓
Cross Validation + Hyperparameter Tuning (GridSearchCV)
   ↓
Final Pipeline (StandardScaler + Logistic Regression)
```

## 🤖 Models Compared

| Model               | Train Accuracy | Test Accuracy | F1 Score |
| ------------------- | -------------- | ------------- | -------- |
| Decision Tree       |      1.0000    |     0.850     | 0.910180 |
| Logistic Regression |      0.9525    |     0.905     | 0.943620 |
| Random Forest       |      1.0000    |     0.875     | 0.926254 |

*Run the notebook to populate results. The final model was selected based on the best F1 score and generalization balance.*

## ✅ Key Highlights
*   **Leakage-free design** — `reading` & `writing` scores excluded from features.
*   Train vs Test accuracy tracked to detect **overfitting**.
*   Pipeline with `StandardScaler` + `Logistic Regression` for clean, reproducible inference.
*   **GridSearchCV** for hyperparameter tuning (`C`, `solver`).
*   **Classification report** for all models — precision, recall, F1 per class.
*   **Feature importance** visualization via Random Forest.
*   **Cross-validation (5-fold)** for robust F1 estimation.

## 🛠️ Tech Stack
*   Python 3.10+
*   scikit-learn
*   pandas, numpy
*   matplotlib, seaborn
*   Google Colab / Jupyter Notebook

## 🚀 How to Run

1.  **Clone the repository**
    ```bash
    git clone https://github.com/souvik45/student_performance_prediction.git
    cd student-performance-prediction
    ```

2.  **Install dependencies**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Add the dataset**
    Download the dataset from [Kaggle](https://www.kaggle.com/datasets/spscientist/students-performance-in-exams) and place it in the `data/` folder as `StudentsPerformance.csv`.

4.  **Run the notebook**
    ```bash
    jupyter notebook Student_Performance_Prediction.ipynb
    ```

## 📈 EDA Insights
*   Most students score in the 60–80 range across all subjects.
*   Students who completed test preparation perform significantly better.
*   Lunch type (a proxy for socio-economic status) strongly influences performance.
*   Female students outperform in language subjects; males excel in math.

## 🙋 Author
*   **Souvik** — B.Tech CSE (Data Science), MCKV Institute of Engineering

## 📄 License
This project is open-source under the [MIT License](./LICENSE).
