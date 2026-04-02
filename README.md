# 🛡️ Outlier Detection Benchmarking

This repository contains a comprehensive evaluation and benchmarking of outlier detection estimators. The project compares popular unsupervised algorithms on real-world datasets to analyze their performance, training speed, and sensitivity to hyperparameters.

## 🛠️ Technologies & Libraries

## 📋 Project Overview

The notebook serves as a performance benchmark for two primary outlier detection algorithms:

1.  **Local Outlier Factor (LOF):** Measures the local density deviation of a given data point with respect to its neighbors.
2.  **Isolation Forest (IForest):** Isolates observations by randomly selecting a feature and then randomly selecting a split value between the maximum and minimum values of the selected feature.

### Key Objectives

  * **Performance Comparison:** Assess algorithms using the **ROC-AUC** metric.
  * **Hyperparameter Sensitivity:** Contrast how changes in parameters (like `n_neighbors` or `contamination`) affect outcomes.
  * **Scalability:** Measure and compare training speeds across different dataset sizes.
  * **Scalability Analysis:** Evaluate the impact of different scaling techniques (`StandardScaler`, `MinMaxScaler`, and `RobustScaler`) on outlier detection.

## 🚀 Methodology

The algorithms are trained in an **unsupervised** manner (without labels) on the entire dataset. Labels are only used during the evaluation phase to calculate the ROC curves.

### 1\. Data Preparation

The benchmark utilizes real-world datasets available in `sklearn.datasets`. It highlights the importance of preprocessing, specifically comparing:

  * **StandardScaler:** Standardizes features by removing the mean and scaling to unit variance.
  * **RobustScaler:** Uses statistics that are robust to outliers (IQR), preventing marginal outliers from collapsing the remaining data.
  * **MinMaxScaler:** Rescales the data to a fixed range [0, 1], though it is noted to be highly sensitive to extreme outliers.

### 2\. Evaluation Metrics

  * **ROC Curves:** Generated using `RocCurveDisplay` to visualize the trade-off between True Positive Rate and False Positive Rate.
  * **Area Under the Curve (AUC):** Used as the primary quantitative measure of detection accuracy.

## 📊 Key Insights from the Benchmarking

  * **Algorithm Suitability:** Different algorithms perform better depending on the specific characteristics of the dataset (e.g., global vs. local outliers).
  * **Scaling Impact:** `RobustScaler` is often preferred in these pipelines as it does not squash marginal outlier values, unlike `StandardScaler`.
  * **IForest Efficiency:** Isolation Forest generally demonstrates better scaling properties for high-dimensional or large-scale datasets.


## ⚙️ Setup and Usage

1.  **Clone the repository.**
2.  **Install requirements:**
    ```bash
    pip install numpy pandas matplotlib scikit-learn
    ```
3.  **Run the Benchmark:**
    Launch the Jupyter notebook and run all cells to generate the ROC comparisons and performance logs.
