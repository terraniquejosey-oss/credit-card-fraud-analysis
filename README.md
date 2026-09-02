# Credit Card Fraud Detection & Risk Analysis

## Project Overview

Credit card fraud presents a challenging classification problem because fraudulent transactions represent only a small fraction of overall transaction activity.

This project analyzes **339,607 credit card transactions** using SQL, Python, statistical testing, and machine learning to identify fraud patterns and develop a predictive fraud detection model.

The analysis moves beyond simply maximizing model accuracy and focuses on the business trade-off between detecting fraudulent transactions and minimizing unnecessary false-positive alerts.

---

## Business Problem

A credit card company wants to improve its ability to identify potentially fraudulent transactions while minimizing unnecessary alerts for legitimate customers.

The analysis addresses three primary questions:

- What transaction characteristics are associated with higher fraud risk?
- Which machine learning approach provides the strongest fraud detection performance?
- What classification threshold provides a practical balance between fraud detection and false-positive alerts?

---

## Tools & Technologies

- **SQL** — Data exploration, aggregation, and fraud-rate analysis
- **Python** — Data preparation, statistical analysis, modeling, and visualization
- **Pandas & NumPy** — Data manipulation and feature engineering
- **SciPy** — Statistical hypothesis testing
- **Scikit-learn** — Machine learning and model evaluation
- **Matplotlib** — Data visualization
- **DataLab** — Analysis environment
- **GitHub** — Project documentation and version control

---

## Dataset

The dataset contains **339,607 transactions** with information including:

- Transaction amount
- Merchant category
- Transaction date and time
- Customer age
- State
- City population
- Fraud status

Fraudulent transactions account for approximately **0.52% of the dataset**, creating a highly imbalanced classification problem.

Because of this imbalance, overall accuracy was not treated as the primary measure of model performance.

---

## Exploratory Data Analysis

SQL and Python were used to investigate fraud patterns across several dimensions, including:

- Transaction amount
- Merchant category
- Transaction hour
- Geographic location
- Customer age

The exploratory analysis indicated that **transaction amount and transaction timing were particularly important indicators of fraud risk**.

Fraud rates also varied across merchant categories and geographic areas.

---

## Statistical Analysis

A chi-square test of independence was performed to determine whether customer age group and fraud status were statistically associated.

**Results:**

- Chi-square statistic: **190.98**
- Degrees of freedom: **5**
- p-value: **< 0.001**
- Cramér's V: **0.0237**

Although the relationship was statistically significant, Cramér's V showed that the practical strength of the relationship was **very weak**.

This demonstrates the importance of evaluating both statistical significance and effect size.

---

## Machine Learning Models

Three classification approaches were evaluated:

1. Baseline Logistic Regression
2. Class-Balanced Logistic Regression
3. Random Forest

Because fraud represented only approximately 0.52% of transactions, model performance was evaluated using metrics appropriate for imbalanced classification, including:

- Fraud recall
- Fraud precision
- F1 score
- Confusion matrix
- Precision-Recall AUC

---

## Model Results

### Random Forest

The Random Forest substantially outperformed the logistic regression approaches.

At the default 0.50 classification threshold, the model achieved approximately:

- **Fraud Recall: 86.5%**
- **Fraud Precision: 50.3%**
- **Fraud F1 Score: 0.64**
- **PR-AUC: 0.85**

The model correctly identified **308 of 356 fraudulent transactions** in the test set while producing **304 false-positive alerts**.

---

## Classification Threshold Analysis

Classification thresholds from **0.10 through 0.90** were evaluated to understand the trade-off between fraud detection and false-positive alerts.

A threshold of **0.60** was selected as a practical initial operating point.

At this threshold, the Random Forest achieved approximately:

- **Fraud Recall: 80.1%**
- **Fraud Precision: 65.7%**
- **Fraud F1 Score: 0.72**
- **Fraudulent Transactions Detected: 285**
- **Fraudulent Transactions Missed: 71**
- **False Positives: 149**

Increasing the threshold from 0.50 to 0.60 substantially reduced false-positive alerts while maintaining strong fraud detection performance.

---

## Feature Importance

The Random Forest identified **transaction amount** as the strongest predictor of fraud, followed by **transaction hour**.

Top predictive features included:

1. Transaction Amount
2. Transaction Hour
3. Customer Age
4. City Population
5. Merchant Category

Transaction amount accounted for approximately **54% of model feature importance**, while transaction hour accounted for approximately **21%**.

---

## Key Findings

- Fraud represented only approximately **0.52% of all transactions**, making class imbalance a major modeling consideration.
- Transaction amount was the strongest predictor of fraudulent activity.
- Transaction timing was the second-most influential model feature.
- Customer age had a statistically significant but practically weak relationship with fraud.
- Random Forest substantially outperformed both logistic regression approaches.
- Classification threshold selection materially affected the trade-off between fraud detection and false-positive alerts.
- A **0.60 probability threshold** provided a strong initial balance between recall and precision.

---

## Business Recommendations

### 1. Deploy Random Forest as the preferred fraud-screening model

Random Forest demonstrated substantially stronger fraud detection performance than the logistic regression approaches.

### 2. Use 0.60 as an initial classification threshold

The 0.60 threshold provides a practical balance between detecting fraudulent transactions and limiting unnecessary alerts.

Transactions exceeding this threshold could initially be routed for additional verification or fraud review rather than automatically declined.

### 3. Prioritize high-value transactions

Because transaction amount was the strongest model predictor, higher-value transactions should receive increased scrutiny when combined with other risk indicators.

### 4. Incorporate transaction timing into fraud controls

Transaction hour was the second-most important predictive feature. Higher-risk transaction periods can be incorporated into fraud-screening rules and authentication procedures.

### 5. Use multiple risk factors

Demographic or geographic characteristics should not be used independently to make fraud decisions. Fraud screening should combine transaction amount, timing, merchant category, and other behavioral indicators.

---

## Repository Structure

`credit_card_fraud_analysis.ipynb` — Complete SQL, Python, statistical analysis, machine learning, model evaluation, and visualizations.

`README.md` — Project overview, methodology, results, and business recommendations.

---

## Skills Demonstrated

This project demonstrates practical experience with:

**SQL | Python | Pandas | Statistical Testing | Machine Learning | Random Forest | Logistic Regression | Imbalanced Classification | Feature Engineering | Model Evaluation | Data Visualization | Business Analytics**

---

## Author

**Terranique Josey**

M.S. Business Analytics
