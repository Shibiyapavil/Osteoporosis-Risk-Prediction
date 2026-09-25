# Predicting Osteoporosis Risk Using Machine Learning

## Project Overview

This project develops a machine learning classification model to predict osteoporosis risk using demographic, lifestyle, and health-related factors.

The project includes data cleaning, exploratory data analysis, preprocessing, model comparison, cross-validation, hyperparameter tuning, and final model evaluation.

> **Note:** This project is for educational and research purposes. The model is not intended to provide medical diagnosis or replace professional medical assessment.

---

## Objective

The main objectives of this project are to:

* Identify patterns and factors associated with osteoporosis risk.
* Compare different machine learning classification algorithms.
* Evaluate model performance using multiple classification metrics.
* Improve the selected model using cross-validation and hyperparameter tuning.

---

##  Dataset

The dataset contains **1,958 records** and **16 original columns**.

### Target Variable

**Osteoporosis**

* `0` — No Osteoporosis
* `1` — Osteoporosis

The target variable is balanced:

* Class 0: **979 records**
* Class 1: **979 records**

### Main Features

* Age
* Gender
* Hormonal Changes
* Family History
* Race / Ethnicity
* Body Weight
* Calcium Intake
* Vitamin D Intake
* Physical Activity
* Smoking
* Alcohol Consumption
* Medical Conditions
* Medications
* Prior Fractures

---

##  Data Preprocessing

The following preprocessing steps were performed:

* Checked the dataset structure and data types.
* Identified missing values.
* Replaced missing values in selected categorical columns with `Unknown`.
* Checked for duplicate records and repeated IDs.
* Removed `Id` because it is an identifier rather than a predictive feature.
* Removed the `Age Group` column from the machine learning features because it was created only for exploratory analysis.
* Separated the features and target variable.
* Applied One-Hot Encoding to categorical variables.
* Obtained **16 encoded features**.
* Split the dataset into:

  * **80% training data — 1,566 records**
  * **20% testing data — 392 records**
* Used stratified splitting to maintain the target class distribution.

---

##  Exploratory Data Analysis

Exploratory analysis was performed to understand the dataset and identify patterns.

Key observations included:

* Age ranged from **18 to 90 years**.
* Mean age was approximately **39.1 years**.
* The target classes were perfectly balanced.
* A particularly strong relationship between age and the target variable was observed.

In this dataset, **all records aged 40 years and above were labelled as having osteoporosis**.

This is considered a dataset-specific pattern and should not be interpreted as a general clinical conclusion.

---

##  Machine Learning Models

Four classification algorithms were trained and evaluated:

1. **Logistic Regression**
2. **Decision Tree**
3. **Random Forest**
4. **K-Nearest Neighbors (KNN)**

The models were evaluated using:

* Accuracy
* Precision
* Recall
* F1-Score
* ROC-AUC

---

##  Initial Model Performance

| Model               |  Accuracy | Precision | Recall | F1-Score | ROC-AUC |
| ------------------- | --------: | --------: | -----: | -------: | ------: |
| Logistic Regression |     80.9% |     85.8% |  74.0% |    79.5% |   88.0% |
| Decision Tree       |     81.9% |     83.8% |  79.1% |    81.4% |   81.9% |
| Random Forest       |     82.9% |     94.5% |  69.9% |    80.4% |   88.6% |
| KNN                 | **83.4%** |     94.6% |  70.9% |    81.0% |   88.3% |

KNN showed the highest initial test accuracy and was selected for further tuning.

---

##  Cross-Validation

5-fold cross-validation was used to evaluate model consistency across different subsets of the training data.

| Model               | 5-Fold CV Accuracy |
| ------------------- | -----------------: |
| Logistic Regression |             82.70% |
| Decision Tree       |             85.25% |
| Random Forest       |             86.08% |
| KNN                 |         **87.29%** |

---

##  Hyperparameter Tuning

GridSearchCV was used to test different KNN parameter combinations.

The parameters tested included:

* Number of neighbors
* Weighting method
* Distance metric

### Best Parameters

* **Number of Neighbors:** 15
* **Weights:** Uniform
* **Distance Metric:** Euclidean

The tuned KNN model achieved a **5-fold cross-validation accuracy of 88.44%**.

---

##  Final Model

The tuned **K-Nearest Neighbors (KNN)** model was selected as the final model.

### Final Test Performance

| Metric             |     Result |
| ------------------ | ---------: |
| Test Accuracy      | **85.20%** |
| Precision          |    **99%** |
| Recall             |    **71%** |
| F1-Score           |    **83%** |
| ROC-AUC            | **87.63%** |
| 5-Fold CV Accuracy | **88.44%** |

### Confusion Matrix

|          | Predicted 0 | Predicted 1 |
| -------- | ----------: | ----------: |
| Actual 0 |         194 |           2 |
| Actual 1 |          56 |         140 |

---

##  Feature Importance

Random Forest feature importance was used to understand the relative contribution of features in one of the trained models.

**Age** had the highest feature importance at approximately **64.6%**.

This finding is consistent with the strong age-target relationship observed during exploratory analysis.

Feature importance is model-specific and does not establish a causal relationship between a feature and osteoporosis.

---

##  Limitations

* The dataset contains a very strong relationship between age and the target variable.
* All records aged 40 years and above were labelled as having osteoporosis.
* The dataset contains 1,958 records, which is relatively small for broader healthcare applications.
* The results may not generalize to other populations or datasets.
* The final model achieved 71% recall, meaning some actual osteoporosis cases were not identified.
* The model has not undergone clinical validation.

---

##  Potential Application

A validated version of a system like this could potentially support:

* Early risk identification
* Further patient assessment
* Preventive follow-up decisions
* Healthcare decision-support workflows

However, larger and more diverse datasets and proper clinical validation would be required before real-world healthcare use.

---

##  Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Scikit-learn**
* **Jupyter Notebook**

---

##  Project Structure

```text
Osteoporosis-Risk-Prediction/
│
├── Osteoporosis_Risk_Prediction.ipynb
├── osteoporosis.csv
└── README.md
```


##  Conclusion

This project demonstrates an end-to-end machine learning workflow for osteoporosis risk prediction, including data preprocessing, exploratory analysis, model comparison, cross-validation, hyperparameter tuning, and final evaluation.

The tuned KNN model achieved **85.2% test accuracy** and **88.4% 5-fold cross-validation accuracy** on the available dataset.

The results are dataset-specific and should not be considered clinical validation. Further testing with larger, diverse, and clinically representative datasets would be necessary before considering real-world healthcare applications.
