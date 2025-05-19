# 🔧 Detecting and Preventing Data Leakage in Machine Learning  
### A Case Study Using Predictive Maintenance Data

---

## 📌 Overview

**Data leakage** is one of the most critical pitfalls in building machine learning models. It occurs when information from outside the training dataset—or future information—is used to create the model, leading to artificially high performance and poor generalization to real-world data.

This project explores data leakage using a **predictive maintenance dataset**, where the goal is to predict whether a machine will fail based on sensor readings.

---

## 📊 Dataset Description

We use a public dataset related to machine predictive maintenance, available on [Kaggle](https://www.kaggle.com/datasets/shivamb/machine-predictive-maintenance-classification).

- **Target Variable:** `failure` (binary)
- **Features Include:**
  - Sensor readings (e.g., torque, rotational speed)
  - Operating conditions
  - Machine type
  - `failure_type` (categorical: reason for failure)

---

## 🚨 What is Data Leakage?

Data leakage can occur in two primary forms:

1. **Target Leakage**  
   Features contain information that wouldn't be available at prediction time (e.g., `failure_type`).

2. **Train-Test Contamination**  
   Information from the test set unintentionally influences model training.

---

## 🛠️ Handling Data Leakage

### ✅ 1. Explore the Dataset

- Understand each feature.
- Check for columns that might directly or indirectly reveal the target.
- Use correlation analysis and domain knowledge.

### ✅ 2. Remove or Transform Leaky Features

- Drop features like `failure_type` if it directly indicates failure.
- Use techniques like:
  - **One-Hot Encoding** for categorical features
  - **Imputation** for missing values
  - **Feature selection** based on importance and leakage risk

### ✅ 3. Proper Data Splitting

- Split data into training, validation, and test sets *before* any preprocessing that may leak information.
- Typical split: 80% training / 10% validation / 10% testing

---

## 🧠 Model Building

- Use models such as **Logistic Regression**, **Random Forest**, or **Naive Bayes**.
- Compare model performance:
  - **With leakage** (e.g., using `failure_type`)
  - **Without leakage** (clean features only)

---

## 📈 Evaluation Metrics

Assess model performance using standard metrics:

- Accuracy
- Precision
- Recall
- F1-Score

Analyze and compare results to illustrate the impact of leakage.

---

## 🔍 Detecting Data Leakage

### 1. Feature Importance Analysis

- Tree-based models can rank feature importance.
- High importance for a feature like `failure_type` may indicate leakage.

### 2. Correlation Inspection

- High correlation between input features and the target might be a red flag.

### 3. Model Debugging Techniques

- Permutation feature importance
- SHAP values
- Manual audit with domain experts

---

## ⚠️ Challenges in Detecting Leakage

- Leakage is often subtle and context-dependent.
- Requires strong domain knowledge.
- Can come from preprocessing pipelines or temporal data mismanagement.

---

## 📚 Conclusion

Data leakage can severely mislead the effectiveness of machine learning models. It's crucial to:

- Understand the data deeply
- Avoid using features that won't be available in production
- Properly split and preprocess data
- Regularly audit models for signs of leakage

By preventing leakage, we ensure our models generalize better and reflect real-world performance.
