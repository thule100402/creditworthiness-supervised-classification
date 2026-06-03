# Creditworthiness Supervised Classification

## Overview

This project evaluates and compares multiple supervised machine learning algorithms for credit risk classification using banking customer data.

The objective is to determine which classification technique best predicts customer credit ratings while balancing predictive performance, interpretability, and business applicability.

Models evaluated include:

- Decision Tree
- Random Forest
- Support Vector Machine (SVM)
- Naïve Bayes
- Logistic Regression

---

## Business Problem

Banks rely on accurate credit assessment systems to minimise lending risk while maintaining operational efficiency.

Given a dataset of previously assessed customers, the goal is to automatically predict customer credit ratings based on demographic information, credit history, employment characteristics, and account balance records.

Credit ratings are defined as:

| Rating | Risk Level |
|----------|----------|
| A | Low Risk |
| B | Medium Risk |
| C | High Risk |

The project also investigates a binary classification scenario:

```text
Rating A vs Non-A
```

to assess whether customers qualify as low-risk borrowers.

---

## Dataset

The dataset contains:

- 1,961 assessed customers
- 46 predictor variables
- 3-class credit rating target

### Feature Categories

- Demographics
- Employment characteristics
- Credit bureau information
- Credit history indicators
- 12 months of account balance history

### Class Distribution

| Class | Proportion |
|---------|------------|
| A | 24.7% |
| B | 50.2% |
| C | 25.2% |

---

## Methodology

### Decision Tree

- Information Gain splitting criterion
- Entropy-based feature selection
- Prediction path analysis for a median customer

### Random Forest

Grid search over:

- mtry
- ntree
- nodesize

Best configuration:

```text
mtry = 6
ntree = 500
nodesize = 1
```

### Support Vector Machine

Two models were evaluated:

- Default RBF SVM
- Tuned RBF SVM

Hyperparameter tuning:

```text
gamma ∈ {0.001, 0.01, 0.1}
cost ∈ {0.1, 1, 10}
```

### Naïve Bayes

- Bayesian classification
- Conditional probability analysis
- Posterior probability computation

### Logistic Regression

Binary classification:

```text
Rating A vs Non-A
```

Used to identify significant predictors of low-risk borrowers and compare ROC performance against SVM.

---

## Results

| Model | Test Accuracy |
|---------|-------------|
| Tuned SVM | 73.3% |
| Random Forest | 58.0% |
| Decision Tree | 56.2% |
| Naïve Bayes | 53.2% |
| Default SVM | 50.6% |

### Best Performing Model

The tuned Support Vector Machine achieved the highest classification accuracy at 73.3%.

### Key Finding

Class C (high-risk customers) remained difficult to classify across all models, suggesting significant overlap between medium-risk and high-risk financial profiles.

---

## Significant Predictors

Logistic Regression identified several strong indicators of low-risk customers:

- Functionary status
- Positive FI3O credit score
- Rebalanced overdrawn account
- No previous credit refusal

These variables were highly significant predictors of Rating A customers.

---

## Repository Structure

```text
README.md

report/
│
└── Credit_Classification_Report.pdf
└── Credit_Classification_R-code_results.pdf

data/
│
├── creditworthiness.csv
└── definitions.txt

code/
│
├── Credit_Classification.R
```

---

## Technologies

- R
- rpart
- randomForest
- e1071
- ROCR

---
