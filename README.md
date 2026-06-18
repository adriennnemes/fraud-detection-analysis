# Fraud Detection and Anomaly Analysis

## Project Overview

This project focuses on detecting fraudulent transactions in a highly imbalanced dataset using supervised, unsupervised, and semi-supervised machine learning techniques.

Fraud detection is a challenging business problem because fraudulent transactions typically represent only a very small fraction of all observations. Traditional machine learning models often achieve high accuracy by simply predicting the majority class, making accuracy an unreliable metric for evaluation.

The objective of this project was therefore not to maximize overall accuracy, but to identify as many fraudulent transactions as possible while maintaining an acceptable false positive rate.

The project compares multiple approaches and demonstrates how different machine learning strategies perform when dealing with rare-event classification problems.


## Business Context

Fraud detection is a critical use case in banking, retail, insurance, and e-commerce.

Missing a fraudulent transaction can lead to significant financial losses, while too many false alarms can negatively impact customer experience and increase operational costs.

This project explores the trade-off between:

* Detecting as many fraud cases as possible (high recall)
* Reducing unnecessary alerts (high precision)
* Maintaining a balanced and reliable model performance (F1-score)

The analysis focuses on metrics that are meaningful for imbalanced datasets rather than relying on accuracy alone.


## Project Workflow

### 1. Data Preparation

The dataset was inspected and cleaned before model development.

Key preprocessing steps included:

* Handling missing values
* Data quality checks
* Feature engineering
* Creating additional variables to improve anomaly detection
* Preparing data for model training and evaluation

A new feature (`Unit Price`) was created from transaction value and quantity to better identify unusual pricing behavior and potential fraud patterns.


### 2. Train-Test Split

The dataset was divided into training and test sets using stratified sampling to preserve the original class distribution.

This ensures that fraudulent transactions remain represented in both datasets and allows for realistic model evaluation.


### 3. Unsupervised Anomaly Detection

Several techniques were evaluated without relying on class labels.

#### Boxplot Rule

A statistical baseline approach using the Interquartile Range (IQR) method to identify extreme observations.

#### Local Outlier Factor (LOF)

Density-based anomaly detection that identifies observations which significantly differ from their local neighborhood.

This method demonstrated strong anomaly detection capabilities but also generated a larger number of false positives.


### 4. Supervised Machine Learning Models

Several classification algorithms were trained and compared.

#### Naive Bayes

Used as a simple baseline model for comparison.

#### Random Forest

Implemented with class balancing techniques to address class imbalance and improve fraud detection performance.

#### Random Forest + SMOTE + GridSearchCV

The minority class was oversampled using SMOTE (Synthetic Minority Oversampling Technique).

Hyperparameter optimization was performed using GridSearchCV to improve model performance and robustness.

#### XGBoost

Gradient boosting approach evaluated both with and without SMOTE.

Hyperparameter tuning was applied to maximize predictive performance.

#### AdaBoost

Included as an additional ensemble-learning benchmark.


### 5. Semi-Supervised Learning

Semi-supervised approaches were explored using Self-Training Classifiers.

The following models were evaluated:

* Self-Training Random Forest
* Self-Training XGBoost

The models iteratively generated pseudo-labels for unlabeled observations and incorporated highly confident predictions into the training process.

This approach demonstrates how machine learning can leverage partially labeled datasets, a common challenge in real-world fraud detection systems.


## Model Evaluation

Because fraud detection is a highly imbalanced classification problem, evaluation focused on metrics that better reflect business value:

* Precision
* Recall
* F1-Score
* PR-AUC (Precision-Recall Area Under Curve)

These metrics provide a more realistic assessment of model performance than accuracy alone.


## Key Learnings

This project highlights several important concepts in applied machine learning:

* Handling highly imbalanced datasets
* Fraud detection and anomaly detection techniques
* Feature engineering for business problems
* Comparison of supervised, unsupervised, and semi-supervised learning
* Model evaluation beyond accuracy
* Hyperparameter optimization
* Synthetic oversampling using SMOTE
* Business trade-offs between false positives and false negatives
  

## Technology Stack

* Python
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* Imbalanced-learn (SMOTE)
* Matplotlib
* Seaborn


## Future Improvements

Potential future extensions include:

* Cost-sensitive learning approaches
* Threshold optimization based on business requirements
* Ensemble fraud detection systems
* Explainable AI techniques (SHAP, feature importance analysis)
* Real-time fraud monitoring pipelines
* Deployment as a fraud scoring service
