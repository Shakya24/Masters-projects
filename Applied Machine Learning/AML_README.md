# Credit Card Fraud Prediction

Table of Contents

- [Project Background](#project-background)
- [About the Data](#about-data)
- [Feature Engineering](#feature-Engineering)
- [Model Building](#model-building)
- [Model Comparison](#model-comparison)
- [Feature Importance](#feature-importance)
- [Recommendations](#recommendations)

***

## Project Background
This academic project on Credit Card Fraud Prediction focuses on implementing strategies and technologies to proactively identify and mitigate fraudulent activities in credit transactions. By leveraging machine learning algorithms and data analysis, the project aims to develop a robust system that can detect unusual patterns and suspicious behaviors indicative of fraud.

## About-data

The dataset was downloaded from [Kaggle](https://www.kaggle.com/datasets/kartik2112/fraud-detection).The simulation process was conducted utilizing the Sparkov Data Generation tool developed by Brandon Harris. This tool facilitated the generation of synthetic transactional data by defining a range of merchants, customers, and transaction categories. Our data contains 22 columns and ~1 million rows pertaining to credit card
information of 1,000 customers doing transactions with a pool of 800 merchants.

## Feature Engineering

I used features such as amount_spent in original form while created new features as summarized below to emulate the markers of credit card fraud.

| Feature         | Description                         |
|-----------------|-------------------------------------|
| Amt             | Transaction Amount                  |
| Gender_Numeric  | Encoded gender of customer          |
| City_pop        | Population of the customer city     |
| Cc_count        | Count of credit cards per customer  |
| address_multiple_customer_flag  | Checks if an address has more than one customer  |
| fraud_likelihood_merchant  | Checks the % of fraud transactions by each merchant out of total transactions by the merchant. Flag if % is more than 1.|
| fraud_likelihood_category  | Checks if an item category belongs to high, medium or low risk.<ul><li> Categories with >20% fraud transactions are high risk.</li><li> Categories with 5-20% fraud transactions are medium risk</li></ul>|
| transaction_distance  | Calculates distance between merchant and customer for transaction  |
| fraud_likelihood_job  | Checks if a job category belongs to high, medium or low risk.<ul><li>Categories with >2% fraud transactions are high risk.</li><li> Categories with >1% fraud transactions are medium risk</li></ul>|
| fraud_likelihood_age | Classifies age-groups into highly likely and less likely with respect to fraud likelihood |
| address_multiple_card_flag | Checks if multiple cards are linked to the same address |
| multiple_cards_large_orders | Checks if large orders are made through multiple cards by one person |
| first_time_shopper | Checks if a customer is a first time shopper or not |


## Model Building

1. **Data Preprocessing:**
    - No missing or duplicate values were present.
    - Categorical features, such as gender, were encoded into binary values.
    - The dataset was split into 70% training, 10% validation, and 20% test data, ensuring stratification to maintain class balance across splits.

2. **Handling class Imbalance:** To address the extreme imbalance (0.57% of fraud class) in the dataset, SMOTE (Synthetic Minority Oversampling Technique) was applied to the training data. Fraudulent transactions in the training set were **increased to 50% using SMOTE**, ensuring models had sufficient representation of the minority class for learning patterns indicative of fraud.

3. **Model Selection:** Six machine learning algorithms were implemented to compare their performances
    - Logistic Regression
    - Decision Tree
    - Random Forest
    - XGBoost
    - AdaBoost
    - Multi-Layer Perceptron (MLP)

   Randomized Search was used for hyperparameter tuning to balance performance and computational cost.

## Model Comparison

Models were evaluated using metrics critical for fraud detection, including Accuracy, Recall, Precision, F1 Score, and AUC (Area Under Curve). Given the business objective of minimizing missed fraudulent transactions, **Recall was prioritized.**

![Model1](https://github.com/Shakya24/Masters-projects/blob/main/Applied%20Machine%20Learning/Visualizations/Model1.png)

![Model2](https://github.com/Shakya24/Masters-projects/blob/main/Applied%20Machine%20Learning/Visualizations/Model2.png)

The choice of model should determined based on precision and recall scores, as well as the explainability of the model. Given that the model users are from a financialorganization that values explainability, the following models are the top choices based on the performance:

- Logistic Regression: Logistic regression is chosen for its simplicity and ease of explainability. It offers straightforward interpretations of coefficients, making it ideal for transparent decision-making processes.
- Adaboost: Adaboost is recommended when the focus is on catching more fraud cases, even if it results in a higher number of false positives. It effectively improves recall, which is critical for detecting fraudulent transactions.
- Multilayer Perceptron (MLP): MLP is suggested for organizations seeking to balance false positives and false negatives. With a more complex structure than logistic regression, MLP provides a balance between precision and recall, optimizing overall performance.

Considering the seriousness of credit card fraud and the project's goal to mitigate it, **Adaboost emerges as a highly suitable solution**. Its ability to achieve a high recall rate enhances the likelihood of detecting fraudulent transactions, aligning closely with the organization's objective to combat fraud effectively. However, the final choice depends on the organization's priorities and strategies, with careful evaluation of the trade-offs between precision and recall.
