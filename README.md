# 🩺 Diabetes Prediction Project (GDG 1st Place Winner 🏆)

An end-to-end Machine Learning project developed using the **CRISP-DM** methodology to predict diabetes with high reliability and zero bias. This project was awarded **1st Place** in the Google Developer Groups (GDG) competition for its robust data preprocessing framework and high clinical deployment readiness.

---

## 📌 Project Overview
Diabetes is a chronic medical condition with a significant global footprint. Early and accurate detection is critical to preventing severe complications. This project leverages advanced predictive analytics to classify individuals as diabetic or non-diabetic based on diagnostic measurements, achieving an optimal balance between precision and recall to ensure clinical safety.

---

## 🛠️ Methodology & Architecture (CRISP-DM)

The project strictly adheres to the **CRISP-DM** lifecycle to ensure systematic engineering:

### 1. Business Understanding
* **Goal:** Build a highly reliable binary classifier for diabetes prediction.
* **Clinical Safety Constraint:** Minimize False Negatives (High Recall) to ensure no diabetic patient goes undetected, while maintaining strong Precision.

### 2. Data Understanding & Exploratory Data Analysis (EDA)
* Thorough statistical analysis of features (Glucose, BloodPressure, SkinThickness, Insulin, BMI, etc.).
* Identified and handled anomalies where structural zeros existed in biologically impossible fields.

### 3. Data Preparation (The Core Strength)
* **Structural Zero Imputation:** Replaced invalid `0` values in critical features with the conditional `Median` calculated based on the target class (`Outcome`), preventing severe data skew.
* **Outlier Removal:** Applied the **IQR (Interquartile Range)** method to eliminate statistical noise.
* **Feature Scaling:** Implemented **RobustScaler** to scale features efficiently while remaining resilient to any remaining marginal outliers.
* **Feature Selection (Multicollinearity Check):** Calculated the **VIF (Variance Inflation Factor)** to guarantee zero linear dependence among independent variables.
* **Class Imbalance Mitigation:** Handled the heavy dataset imbalance using **SMOTE** (Synthetic Minority Over-sampling Technique) to ensure the model learns both classes equally.

### 4. Modeling & Hyperparameter Tuning
We evaluated three robust machine learning architectures using **Stratified K-Fold Cross-Validation** and optimized them via **GridSearchCV**:
* Logistic Regression (Baseline)
* Random Forest Classifier
* XGBoost Classifier 🚀 *(Champion Model)*

---

## 📊 Evaluation Results

The models showed outstanding performance after fine-tuning. **XGBoost** emerged as the champion model due to its exceptional capability to handle non-linear health boundaries.

| Model | Accuracy | Precision | Recall (Sensitivity) | F1-Score |
| :--- | :---: | :---: | :---: | :---: |
| **XGBoost Classifier** | **92.1%** | **91.5%** | **92.4%** | **91.9%** |
| Random Forest | 89.4% | 88.9% | 89.1% | 89.0% |
| Logistic Regression | 78.2% | 77.5% | 79.0% | 78.2% |

### Key Takeaway:
The **XGBoost** model achieved a **92.4% Recall**, ensuring that the model has an incredibly low rate of missing actual diabetic patients, making it highly viable for real-world medical pre-screening.

---

## 📁 Repository Structure

```text
├── data/
│   └── diabetes.csv           # Raw Dataset
├── src/
│   ├── preprocessing.py       # Imputation, IQR Outliers, Scaling & SMOTE
│   └── train.py               # Model training and Hyperparameter tuning
├── gdg_final_project.ipynb    # Full exploratory and experimental Notebook
├── README.md                  # Professional documentation
└── requirements.txt           # Project dependencies
