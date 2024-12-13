# Credit Card Fraud Prediction

Table of Contents

- [Project Background](#project-background)
- [About the Data](#about-data)
- [Feature Engineering](#feature-Engineering)
- [Technical Analysis](#technical-analysis)
- [Recommendations](#recommendations)

***

## Project Background
This project on Credit Card Fraud Prediction focuses on implementing strategies and technologies to proactively identify and mitigate fraudulent activities in credit transactions. By leveraging machine learning algorithms and data analysis, the project aims to develop a robust system that can detect unusual patterns and suspicious behaviors indicative of fraud.

## About-data

The dataset was downloaded from [Kaggle](https://www.kaggle.com/datasets/kartik2112/fraud-detection).The simulation process was conducted utilizing the Sparkov Data Generation tool developed by Brandon Harris. This tool facilitated the generation of synthetic transactional data by defining a range of merchants, customers, and transaction categories. Our data contains 22 columns and ~1 million rows pertaining to credit card
information of 1,000 customers doing transactions with a pool of 800 merchants.

Steps taken to clean and prepare the dataset for analysis can be found [here](https://github.com/Shakya24/Masters-projects/blob/main/Customer%20Analytics/Data%20cleaning%20Customer.pdf)


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


