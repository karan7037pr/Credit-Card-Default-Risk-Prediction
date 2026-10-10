```markdown
# 📝 GitHub Repository Documentation (README.md)

Below is the complete, professional `README.md` designed for your GitHub repository to showcase your work as the Lead ML Engineer on this project.

***

# Credit Card Default Risk Prediction & Multi-Model Benchmarking Pipeline

## 👤 Author: Karan Chaudhary

## 📌 Project Overview
This repository contains an end-to-end Machine Learning and Deep Learning pipeline designed to predict the probability of credit card defaults using consumer demographic information and monthly transaction history. 

Predicting credit default is a classic **imbalanced classification** problem. In this project, we explicitly demonstrate why relying on traditional metrics like **Overall Accuracy** can lead to disastrous financial decisions, and instead design a robust framework built around risk-mitigating metrics: **ROC-AUC, PR-AUC (Average Precision), and Default Recall**.

---

## 📊 The Imbalance Dilemma & Metric Justification
* **The Dataset:** Based on the *UCI Default of Credit Card Clients* dataset (30,000 clients).
* **The Challenge:** Only **22.12%** of clients in the dataset actually defaulted (Imbalance Ratio of ~3.52:1).
* **The Illusion of Accuracy:** A naive baseline model that blindly predicts "No Default" for every customer achieves an **overall accuracy of 77.88%** while catching **0% of actual defaults**. 
* **Our Strategy:** We prioritize **PR-AUC** and **Recall (Sensitivity)**. Catching a high-risk borrower (Recall) and minimizing bad loan allocations is of paramount financial importance compared to slightly higher overall accuracy.

---

## 🛠️ Feature Engineering
To enhance model detection capabilities (particularly for our Deep Learning MLP), we engineered **4 custom financial behavior metrics** from raw columns:
1. **`UTIL_RATIO_1` & `UTIL_RATIO_2`** (Credit Utilization): $\text{Bill Amount} \div \text{Limit Balance}$. Identifies clients stretching their credit capacity.
2. **`PAY_TO_BILL_1`** (Payment-to-Bill Ratio): $\text{Payment Amount} \div \text{Bill Amount}$. Captures the proportion of outstanding debt cleared month-over-month.
3. **`AMT_OWED_1`** (Total Unpaid Debt): $\text{Bill Amount} - \text{Payment Amount}$. Represents the absolute revolving debt burden.

---

## 🏆 Model Benchmarking Summary

We systematically trained and evaluated 6 different architectures. Below is the performance ranking ordered by **PR-AUC (Average Precision)**:

| Model | ROC-AUC | PR-AUC (Avg Precision) | Default Recall (Sensitivity) | Default Precision | Default F1-Score | Overall Accuracy |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **LightGBM Classifier** | **0.7757** | **0.5541** | 0.6100 | 0.4700 | 0.5300 | 76.00% |
| **XGBoost Classifier** | 0.7753 | 0.5477 | 0.6096 | 0.4753 | 0.5342 | 76.48% |
| **Random Forest** | 0.7735 | 0.5494 | 0.5600 | 0.5200 | 0.5400 | **79.00%** |
| **Multi-Layer Perceptron (MLP)**| 0.7731 | 0.5448 | 0.5900 | 0.4700 | 0.5300 | 76.00% |
| **Decision Tree** | 0.7571 | 0.5116 | 0.5516 | 0.4841 | 0.5157 | 77.08% |
| **Logistic Regression** | 0.7081 | 0.4904 | **0.6202** | 0.3672 | 0.4613 | 67.97% |

### 🔑 Key Takeaways:
1. **LightGBM** and **XGBoost** achieved the best overall balance of performance, boasting the highest PR-AUC (~0.554) and capturing over **61% of default events**.
2. **The Multi-Layer Perceptron (MLP)**, combined with custom feature engineering and class weight adjustments, matched the state-of-the-art boosting algorithms in both ROC-AUC and PR-AUC.
3. **Random Forest** achieved the highest overall accuracy (79%) but lagged slightly in raw recall compared to LightGBM and XGBoost.

---

## 🚀 Project Pipeline Structure
```bash
├── default of credit card clients.xls   # Raw Dataset
├── Credit_Card_Default_Pipeline.ipynb   # Complete Jupyter Notebook
└── README.md                            # Repository Documentation
```

## 💻 How to Run the Project
1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
   ```
2. Open `Credit_Card_Default_Pipeline.ipynb` in Google Colab or your local Jupyter environment.
3. Run all cells to replicate data loading, feature engineering, and model testing pipelines.
```
