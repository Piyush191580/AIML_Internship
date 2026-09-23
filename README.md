# 🚀 AI/ML Internship Portfolio

<p align="center">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=24&pause=1000&color=36BCF7&center=true&vCenter=true&width=700&lines=AI%2FML+Internship+Projects;Regression+%7C+Classification;Feature+Engineering+%7C+Model+Optimization;Model+Validation+%7C+Imbalanced+Learning" alt="Typing SVG" />
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Tasks-4-success?style=for-the-badge">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?style=for-the-badge&logo=python">
  <img src="https://img.shields.io/badge/scikit--learn-Machine%20Learning-orange?style=for-the-badge&logo=scikitlearn">
  <img src="https://img.shields.io/badge/Status-Completed-brightgreen?style=for-the-badge">
</p>

---

## 📖 Overview

This repository contains the four tasks completed during the AI/ML Internship. The projects were designed to build a complete machine learning workflow, beginning with a simple regression model and progressing toward model optimization, validation, hyperparameter tuning, and classification on imbalanced data.

Each task includes:

* 📓 Jupyter Notebook
* 📄 PDF Report
* 📝 Individual README
* 📊 Model Evaluation & Analysis

---

## 🛣️ Internship Journey

```text
Task 1 ──► Task 2 ──► Task 3 ──► Task 4

Regression      Feature        Validation      Classification
Fundamentals    Engineering    & Tuning        & Imbalanced Data

R² 0.496  ──►  R² 0.797  ──►  R² 0.815  ──►  Recall 0.79
```

The internship gradually shifted focus from simply training models to understanding model reliability, evaluation methodology, and real-world decision making.

---

## 📂 Tasks Overview

| Task   | Title                                                                | Problem Type   | Dataset              |
| ------ | -------------------------------------------------------------------- | -------------- | -------------------- |
| Task 1 | Linear Regression House Price Predictor                              | Regression     | California Housing   |
| Task 2 | Feature Engineering, Model Optimization & Performance Comparison     | Regression     | California Housing   |
| Task 3 | Model Validation, Overfitting Control & Hyperparameter Tuning        | Regression     | California Housing   |
| Task 4 | Classification Models, Evaluation Metrics & Handling Imbalanced Data | Classification | Telco Customer Churn |

---

# 📊 Task 1: Linear Regression House Price Predictor

### Objective

Build a baseline machine learning pipeline for predicting California housing prices using Linear Regression.

### Key Concepts

* Data loading and preprocessing
* Exploratory Data Analysis (EDA)
* Train-test split
* Linear Regression
* Regression evaluation metrics

### Results

| Metric   | Value               |
| -------- | ------------------- |
| MAE      | 0.538797 (~$53,880) |
| RMSE     | 0.812622 (~$81,262) |
| R² Score | 0.496070            |

### Takeaway

This project established the foundation for all subsequent tasks. While the model explained roughly 50% of the variance in housing prices, it highlighted the limitations of a basic linear approach and created a benchmark for future improvements.

---

# ⚙️ Task 2: Feature Engineering, Model Optimization & Performance Comparison

### Objective

Improve prediction performance through feature engineering and comparison of multiple machine learning models.

### Enhancements

* Added `RoomsPerPerson`
* Added `BedroomRatio`
* Feature scaling
* Multi-model comparison

### Model Comparison

| Model             |      MAE |     RMSE | R² Score |
| ----------------- | -------: | -------: | -------: |
| Random Forest     | 0.339168 | 0.515623 | 0.797111 |
| Linear Regression | 0.482436 | 0.673856 | 0.653481 |
| Ridge Regression  | 0.482428 | 0.673860 | 0.653477 |
| Decision Tree     | 0.496911 | 0.712963 | 0.612094 |

### Best Model

🏆 **Random Forest Regressor**

### Takeaway

Feature engineering and ensemble learning dramatically improved performance. Random Forest increased the R² score from **0.496 → 0.797**, demonstrating the value of better features and more sophisticated models.

---

# 🔬 Task 3: Model Validation, Overfitting Control & Hyperparameter Tuning

### Objective

Evaluate model reliability using validation techniques and optimize performance through hyperparameter tuning.

### Key Concepts

* Cross-validation
* Overfitting detection
* GridSearchCV
* Hyperparameter optimization

### Observations

* Default Decision Tree achieved a training RMSE of 0
* Test RMSE increased to 72,949
* Clear evidence of overfitting
* 5-fold cross-validation produced more reliable estimates

### Tuned Model Performance

| Model                    |    MAE |   RMSE | R² Score |
| ------------------------ | -----: | -----: | -------: |
| Random Forest (Tuned)    | 32,901 | 49,302 |   0.8145 |
| Decision Tree (Tuned)    | 40,721 | 61,265 |   0.7136 |
| Linear Regression        | 48,243 | 67,385 |   0.6535 |
| Ridge Regression (Tuned) | 48,221 | 67,414 |   0.6532 |

### Best Model

🏆 **Tuned Random Forest Regressor**

### Takeaway

This task demonstrated that strong test-set performance alone is insufficient. Cross-validation and hyperparameter tuning provided a more trustworthy estimate of model quality while improving predictive performance.

---

# 🎯 Task 4: Classification Models, Evaluation Metrics & Handling Imbalanced Data

### Objective

Predict customer churn while addressing class imbalance and selecting appropriate evaluation metrics.

### Dataset

* Telco Customer Churn
* 7,043 customer records
* Binary classification problem

### Class Distribution

| Class    | Percentage |
| -------- | ---------: |
| No Churn |      73.5% |
| Churn    |      26.5% |

### Model Comparison

| Model                          | Accuracy | Precision | Recall | F1 Score |    AUC |
| ------------------------------ | -------: | --------: | -----: | -------: | -----: |
| Logistic Regression (Baseline) |    0.807 |      0.66 |   0.57 |     0.61 | 0.8418 |
| Logistic Regression (Balanced) |    0.740 |      0.51 |   0.79 |     0.62 | 0.8414 |
| Decision Tree (Default)        |    0.726 |      0.48 |   0.48 |     0.48 | 0.6465 |

### Selected Model

🏆 **Logistic Regression with `class_weight="balanced"`**

### Why?

Although overall accuracy decreased, recall increased substantially. Since identifying potential churners was the primary objective, recall became more important than raw accuracy.

### Takeaway

This task reinforced that the best model depends on the business objective. Accuracy alone can be misleading when classes are imbalanced.

---

# 📈 Performance Evolution

| Stage  | Best Model                   | Primary Metric |
| ------ | ---------------------------- | -------------- |
| Task 1 | Linear Regression            | R² = 0.496     |
| Task 2 | Random Forest                | R² = 0.797     |
| Task 3 | Tuned Random Forest          | R² = 0.815     |
| Task 4 | Balanced Logistic Regression | Recall = 0.79  |

---

# 🏅 Key Achievements

* Built complete regression and classification pipelines
* Improved regression performance from R² 0.496 to R² 0.815
* Applied feature engineering to enhance predictive accuracy
* Compared multiple machine learning algorithms
* Used Cross-Validation for reliable model evaluation
* Applied GridSearchCV for hyperparameter optimization
* Learned to handle imbalanced datasets effectively
* Evaluated models using MAE, RMSE, R², Precision, Recall, F1-Score, and AUC

---

# 🛠️ Tools & Technologies

### Languages & Libraries

* Python
* Pandas
* NumPy
* Matplotlib
* Scikit-Learn

### Models Used

* Linear Regression
* Ridge Regression
* Decision Tree Regressor
* Decision Tree Classifier
* Random Forest Regressor
* Logistic Regression

### Techniques

* Feature Engineering
* Feature Scaling
* Cross Validation
* GridSearchCV
* Model Evaluation
* Imbalanced Data Handling

### Development Environment

* Google Colab
* Jupyter Notebook

---

# 🎓 Final Reflection

Across all four tasks, the internship evolved from building a simple predictive model to understanding how machine learning systems should be evaluated and trusted.

The strongest regression model was the **Tuned Random Forest Regressor**, achieving an R² score of **0.8145**. For classification, **Balanced Logistic Regression** provided the best tradeoff between identifying churners and maintaining overall performance.

The most important lesson from this internship was that machine learning is not only about achieving high scores. Proper validation, selecting the correct evaluation metric, understanding data characteristics, and balancing tradeoffs often matter more than marginal improvements in model accuracy.

---

⭐ If you found this repository useful, consider giving it a star.
