# Credit Card Default Risk Prediction & Multi-Model Benchmarking Pipeline

An end-to-end Machine Learning and Deep Learning pipeline for predicting credit card default risk using customer demographics, repayment history, and financial behavior.

## 👤 Author

**Karan Chaudhary**

## 📌 Project Overview

This repository contains an end-to-end Machine Learning and Deep Learning pipeline designed to predict the probability of credit card defaults using consumer demographic information and monthly transaction history.

Credit default prediction is a classic **imbalanced classification problem**. This project demonstrates why relying solely on traditional metrics such as overall accuracy can be misleading and evaluates models using risk-focused metrics, including **ROC-AUC, PR-AUC (Average Precision), and Default Recall**.

The project benchmarks six machine learning and deep learning models to identify effective approaches for detecting customers who are likely to default on their credit card payments.

## 📊 The Imbalance Dilemma & Metric Justification

- **Dataset:** UCI Default of Credit Card Clients dataset, containing 30,000 client records.
- **Challenge:** The dataset contains approximately 22.12% default cases, creating an imbalanced classification problem.
- **The Accuracy Trap:** A baseline model that predicts "No Default" for every customer can achieve high accuracy while failing to identify any actual defaults.
- **Our Strategy:** We evaluate models using PR-AUC, ROC-AUC, Recall, Precision, and F1-score to understand their ability to identify high-risk customers.

**Why does this matter?**

In credit risk assessment, failing to identify a customer who will default can have significant financial consequences. Therefore, evaluating a model requires more than just measuring its overall accuracy.

## 🛠️ Feature Engineering

To improve the models' ability to identify high-risk customers, we engineered four custom financial behavior features from the original dataset.

| Feature | Description | Purpose |
|---|---|---|
| `UTIL_RATIO_1` | Credit utilization ratio for the first billing period | Measures credit utilization relative to the available credit limit. |
| `UTIL_RATIO_2` | Credit utilization ratio for the second billing period | Captures credit utilization patterns across billing periods. |
| `PAY_TO_BILL_1` | Payment-to-bill ratio | Measures payments relative to the outstanding bill amount. |
| `AMT_OWED_1` | Outstanding debt estimate | Estimates the difference between the bill amount and payment amount. |

These features help capture customer financial behavior and provide additional information that may improve default risk classification.

**Note:** The exact feature formulas and handling of zero denominators should match the implementation in the Jupyter notebook.

## 🏆 Model Benchmarking Summary

Six different model architectures were trained and evaluated. The following table summarizes their performance.

| Model | ROC-AUC | PR-AUC | Default Recall | Default Precision | Default F1-Score | Accuracy |
|---|---:|---:|---:|---:|---:|---:|
| **LightGBM Classifier** | **0.7757** | **0.5541** | 0.6100 | 0.4700 | 0.5300 | 76.00% |
| **Random Forest** | 0.7735 | 0.5494 | 0.5600 | 0.5200 | 0.5400 | **79.00%** |
| **XGBoost Classifier** | 0.7753 | 0.5477 | 0.6096 | 0.4753 | 0.5342 | 76.48% |
| **Multi-Layer Perceptron (MLP)** | 0.7731 | 0.5448 | 0.5900 | 0.4700 | 0.5300 | 76.00% |
| **Decision Tree** | 0.7571 | 0.5116 | 0.5516 | 0.4841 | 0.5157 | 77.08% |
| **Logistic Regression** | 0.7081 | 0.4904 | **0.6202** | 0.3672 | 0.4613 | 67.97% |

### 🔑 Key Takeaways

1. **LightGBM achieved the highest reported PR-AUC:** With a PR-AUC of 0.5541, it demonstrated the strongest overall performance among the evaluated models according to this metric.
2. **XGBoost delivered competitive performance:** It achieved a ROC-AUC of 0.7753 and a PR-AUC of 0.5477, making it a strong alternative to LightGBM.
3. **Random Forest achieved the highest reported accuracy:** Its accuracy of 79.00% was higher than that of the other evaluated models, although its default recall was lower than that of LightGBM and XGBoost.
4. **Logistic Regression achieved the highest reported default recall:** With a recall of 0.6202, it identified the largest proportion of actual default cases among the evaluated models, but its precision was comparatively low.
5. **Metric selection depends on business objectives:** A model with higher accuracy does not necessarily identify more defaulting customers. PR-AUC, recall, and precision provide additional insight into the trade-offs involved in credit risk prediction.

*Note: Verify the reported metrics against the notebook's evaluation outputs before publication. Ensure all models were evaluated on the same test set and that recall, precision, F1-score, and accuracy correspond to the same classification thresholds.*

## ⚙️ Technologies Used

- **Programming Language:** Python
- **Data Processing:** Pandas, NumPy
- **Machine Learning:** Scikit-learn
- **Gradient Boosting:** XGBoost, LightGBM
- **Deep Learning:** Multi-Layer Perceptron (MLP)
- **Experiment Tracking:** MLflow
- **Data Visualization:** Matplotlib
- **Development Environment:** Jupyter Notebook / Google Colab

## 🔬 Project Workflow

1. **Data Loading:** Load the UCI credit card default dataset.
2. **Exploratory Data Analysis:** Analyze customer demographics, repayment history, financial attributes, and target distribution.
3. **Data Preprocessing:** Prepare features, handle data quality issues, and create training and testing datasets.
4. **Feature Engineering:** Derive additional financial behavior metrics from billing and payment information.
5. **Model Training:** Train six machine learning and deep learning models.
6. **Model Evaluation:** Compare models using ROC-AUC, PR-AUC, recall, precision, F1-score, and accuracy.
7. **Experiment Tracking:** Use MLflow to track experiments and model evaluation results.
8. **Performance Comparison:** Analyze the strengths and weaknesses of different classification approaches.

## 📁 Repository Structure

```text
Credit-Card-Default-Risk-Prediction/
├── default of credit card clients.xls
├── Credit_Card_Default_Pipeline.ipynb
└── README.md
```

- `default of credit card clients.xls` — Dataset used for training and evaluation.
- `Credit_Card_Default_Pipeline.ipynb` — Notebook containing data preprocessing, feature engineering, model training, evaluation, and experiment tracking.
- `README.md` — Project documentation.

## 🚀 How to Run the Project

### 1. Clone the Repository

Replace `YOUR_USERNAME` and `YOUR_REPO_NAME` with your actual GitHub username and repository name.

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
cd YOUR_REPO_NAME
```

### 2. Install Dependencies

```bash
pip install pandas numpy scikit-learn xgboost lightgbm mlflow matplotlib jupyter xlrd
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 4. Run the Pipeline

Open `Credit_Card_Default_Pipeline.ipynb` and execute the cells sequentially to reproduce the data preprocessing, feature engineering, model training, and evaluation workflow.

Alternatively, upload the notebook and dataset to Google Colab.

## 📚 Dataset

**Dataset:** Default of Credit Card Clients  
**Source:** UCI Machine Learning Repository

[Access the UCI Credit Card Default Dataset](https://archive.ics.uci.edu/dataset/350/default+of+credit+card+clients)

The dataset contains customer demographic information, credit limits, repayment status, bill statements, payment amounts, and the target variable indicating default payment in the following month.

## 🎯 Future Improvements

- Hyperparameter optimization using Optuna or similar tools.
- Probability calibration for more reliable default risk estimates.
- Decision-threshold optimization based on business costs.
- Explainability using SHAP feature importance.
- Cross-validation and statistical comparison of model performance.
- Model deployment through a FastAPI inference service.
- Production monitoring for model drift and changing default rates.
- A reproducible MLflow pipeline for tracking experiments and model versions.
```
