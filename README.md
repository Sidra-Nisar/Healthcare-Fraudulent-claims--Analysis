# Healthcare Provider Fraud Detection Analysis

## Project Overview

Healthcare fraud causes significant financial losses and affects the quality and affordability of healthcare services. This project analyses Medicare healthcare claims data to identify patterns associated with potentially fraudulent healthcare providers.

The project focuses on data preparation, exploratory data analysis, class imbalance handling, feature engineering, machine-learning model development, and model evaluation.

## Project Objectives

- Analyse healthcare claims data for possible fraud patterns
- Clean and prepare multiple healthcare datasets
- Identify important characteristics of potentially fraudulent providers
- Handle class imbalance between fraudulent and non-fraudulent providers
- Train machine-learning models for fraud detection
- Evaluate model performance using appropriate classification metrics

## Dataset

The dataset used in this project was obtained from Kaggle.

**Dataset:** Healthcare Provider Fraud Detection Analysis  
**Source:** [Kaggle Dataset](https://www.kaggle.com/datasets/rohitrox/healthcare-provider-fraud-detection-analysis)

Due to file-size considerations, the dataset is not included in this repository. Download the dataset from Kaggle and place the files inside a `data/` folder before running the notebook.

## Dataset Files

The original dataset contains healthcare information related to:

- Inpatient claims
- Outpatient claims
- Beneficiary information
- Provider fraud labels
- Training and testing datasets

## Project Workflow

1. Import required Python libraries
2. Load healthcare claims datasets
3. Inspect and clean the data
4. Handle missing values and duplicate records
5. Merge relevant datasets
6. Perform exploratory data analysis
7. Engineer useful fraud-detection features
8. Examine class imbalance
9. Prepare training and testing data
10. Train machine-learning models
11. Evaluate and compare model performance

## Technologies Used

- Python
- Jupyter Notebook
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
## Projects Screenshots
### Fraud Distribution
![Fraud Distribution](Images/fraud_distribution.png)

## Imbalanced Data
![Imbalanced Data](Images/imbalance_data.png)

## Logistic Regression Metrics
![Logistic Regression Metrics](Images/Logisticregression_Metrics.png)

## Catboost Metrics
![Catboost Metrics](Images/Catboost_Metrics.png)

## Catboost Random undesampling Metrics
![Catboost Random undesampling Metrics](Images/Catboost_MetricsRUS.png)


## Model Performance Results

| Model | TN | FP | FN | TP | Precision | Recall | F1 Score | ROC-AUC | PR-AUC |
|---|---:|---:|---:|---:|---:|---:|---:|---:|---:|
| Logistic Regression | 37,485 | 31,598 | 10,583 | 31,977 | 0.503 | 0.751 | 0.603 | 0.697 | 0.562 |
| CatBoost | 57,248 | 11,835 | 13,037 | 29,523 | 0.714 | 0.694 | 0.704 | 0.835 | 0.726 |
| CatBoost with Random Undersampling | 54,214 | 14,869 | 9,911 | 32,649 | 0.687 | 0.767 | 0.725 | **0.855** | 0.783 |
| CatBoost with Class Weights | 53,977 | 15,106 | **9,860** | **32,700** | 0.684 | **0.768** | 0.724 | 0.855 | **0.784** |

- **Logistic Regression** achieved a relatively high recall of 0.751 but produced a large number of false-positive predictions, resulting in low precision, ROC-AUC and PR-AUC scores.
- **Standard CatBoost** substantially improved precision from 0.503 to 0.714 and reduced false positives from 31,598 to 11,835.
- **CatBoost with Random Undersampling** produced the highest F1 score of 0.725 and the highest ROC-AUC score of 0.855.
- **CatBoost with Class Weights** achieved the highest recall of 0.768 and the highest PR-AUC score of 0.784. It also generated the lowest number of false negatives, indicating that it detected the greatest number of fraudulent claims.

  ## Conclusion

The results demonstrate that CatBoost-based models performed considerably better than Logistic Regression for healthcare fraud detection. Although Logistic Regression detected a relatively high proportion of fraudulent claims, its low precision and large number of false positives indicate that many legitimate claims were incorrectly classified as fraudulent.

The standard CatBoost model provided a more balanced performance by improving precision and reducing false alarms. However, incorporating techniques for handling class imbalance further improved fraud detection. CatBoost with Random Undersampling achieved the highest F1 score and ROC-AUC score, showing the strongest overall balance between precision and recall.

CatBoost with Class Weights produced the highest recall and PR-AUC score while recording the lowest number of false negatives. This model may therefore be the most appropriate option when the main objective is to minimise missed fraudulent claims. Overall, the findings show that class-imbalance-aware CatBoost models are more effective and reliable than Logistic Regression for identifying potentially fraudulent healthcare claims.

## Repository Structure

```text
Healthcare-Fraudulent-claims--Analysis/
│
├── Healthcare-fraudAnalysis.ipynb
├── README.md
└── Images/
    ├── fraud_distribution.png
    ├── imbalance_data.png
    ├── Logisticregression_Metrics.png
    └── Catboost_Metrics.png
## Catboost Class weights Metrics
![Catboost Class weights Metrics](Images/CatboostCW_Metrics.png)
