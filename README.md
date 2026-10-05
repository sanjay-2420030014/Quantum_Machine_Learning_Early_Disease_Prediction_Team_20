# Quantum Machine Learning for Early Disease Prediction

## 📌 Project Overview

This project implements a hybrid classical–quantum machine learning approach for heart disease prediction using the **UCI Heart Disease dataset**.

The system combines classical data preprocessing techniques with Quantum Machine Learning (QML). Principal Component Analysis (PCA) is used to reduce the original 13 clinical features to 4 components, which are then processed using a quantum feature map and quantum kernel.

A **Quantum Support Vector Classifier (QSVC)** is compared with a classical **Support Vector Classifier (SVC)** using the same training and testing samples.

> **Note:** This project is a proof-of-concept research implementation and is not intended to provide clinical diagnosis or replace professional medical judgment.

---

## 🎯 Objectives

- To implement a hybrid classical–quantum machine learning workflow for heart disease classification.
- To preprocess and transform clinical data for machine learning.
- To reduce the feature space using Principal Component Analysis (PCA).
- To implement a quantum feature map using `ZZFeatureMap`.
- To perform classification using `FidelityQuantumKernel` and `QSVC`.
- To compare QSVC performance with a classical SVC baseline.
- To evaluate the models using standard classification metrics.

---

## 📊 Dataset

The project uses the **UCI Heart Disease – Cleveland dataset**.

### Dataset Information

- **Samples:** 303
- **Clinical features:** 13
- **Target:** Binary classification
  - `0` → No heart disease
  - `1` → Heart disease present

The dataset contains clinical attributes such as:

- Age
- Sex
- Chest pain type
- Resting blood pressure
- Cholesterol
- Fasting blood sugar
- Resting ECG
- Maximum heart rate
- Exercise-induced angina
- ST depression
- Slope
- Number of major vessels
- Thalassemia

The dataset is automatically downloaded by the Python implementation from the UCI Machine Learning Repository.

---

## 🛠️ Technologies Used

- **Python**
- **Pandas** – data loading and preprocessing
- **NumPy** – numerical operations
- **Scikit-learn** – preprocessing, PCA, SVC, train/test split and evaluation
- **Qiskit** – quantum computing framework
- **Qiskit Machine Learning** – quantum kernel and QSVC
- **Matplotlib** – result visualization

---

## 🔄 Methodology

The implemented workflow consists of the following steps:

1. **Data Collection**
   - The UCI Heart Disease dataset is downloaded automatically.

2. **Data Preprocessing**
   - Missing values represented by `?` are identified.
   - Missing numerical values are handled using median values.
   - The target variable is converted into a binary classification target.

3. **Train-Test Split**
   - The dataset is divided using an **80:20 stratified split**.
   - 242 samples are used for training.
   - 61 samples are used for testing.

4. **Feature Scaling**
   - `StandardScaler` is applied to standardize the clinical features.

5. **Feature Reduction**
   - PCA reduces the original 13 features to **4 principal components**.

6. **Matched Training Setup**
   - A stratified subset of **120 training samples** is selected.
   - The same 120 training samples are used for both SVC and QSVC.
   - The same 61 test samples are used for evaluation.

7. **Classical Classification**
   - A classical RBF-based Support Vector Classifier (SVC) is trained using the reduced features.

8. **Quantum Feature Mapping**
   - The four PCA components are encoded using a **4-qubit ZZFeatureMap** with 2 repetitions and linear entanglement.

9. **Quantum Kernel**
   - A `FidelityQuantumKernel` is used to calculate similarities between quantum feature representations.

10. **Quantum Classification**
    - The quantum kernel is provided to a **Quantum Support Vector Classifier (QSVC)**.

11. **Performance Evaluation**
    - Both models are evaluated using:
      - Accuracy
      - Precision
      - Recall
      - F1-score
      - Confusion matrix

---

## 🧠 Quantum Machine Learning Workflow

```text
UCI Heart Disease Dataset
          ↓
Data Preprocessing
          ↓
Feature Scaling
          ↓
PCA
13 Features → 4 Components
          ↓
     ┌───────────────┐
     │               │
     ↓               ↓
Classical Path    Quantum Path
     ↓               ↓
   SVC          ZZFeatureMap
                     ↓
             Fidelity Quantum
                  Kernel
                     ↓
                   QSVC
     │               │
     └───────┬───────┘
             ↓
 Heart Disease Classification
             ↓
      Performance Evaluation
