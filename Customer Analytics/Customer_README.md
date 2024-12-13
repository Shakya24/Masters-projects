# Customer-Analytics

Table of Contents

- [Project Background](#project-background)
- [About the Data](#about-data)
- [Summary of Insights](#summary-of-insights)
- [Technical Analysis](#technical-analysis)
- [Recommendations](#recommendations)

***

## Project Background
Established in 2018, Store-X beauty store (retail and online) offers a diverse range of skincare, makeup, and personal care products to customers in Singapore and Malaysia. In this project, I partnered with this brand's Digital Campaign Manager to analyse real customer data to uncover trends in behavior, product preferences, and operational efficiency. The analysis addressed critical challenges, including customer retention, decision fatigue caused by an extensive product range, and the need for personalized shopping experiences.Based on the findings, I delivered actionable recommendations to enhance customer engagement and drive sustainable business growth.

## About-data

The dataset provides comprehensive information on customer transactions for 2022 and 2023, covering details such as purchase dates, countries, stores, brands, product categories, sales channels, and other product-specific information. This rich dataset offers a holistic view of customer purchasing behavior across various dimensions, enabling in-depth analysis and actionable insights.

Steps taken to clean and prepare the dataset for analysis can be found [here](https://github.com/Shakya24/Masters-projects/blob/main/Customer%20Analytics/Data%20cleaning%20Customer.pdf)


## Summary of Insights

The exploratory data analysis phase of the project helped me uncover following key insights:

**Sales and Brand Insights**

  - Sales by Brand:
    92% of products are sold primarily in retail stores, while 8% are sold through eCommerce channels.
    Brand D and Brand B have a significantly higher share of eCommerce sales (30%) compared to other brands (average of 5%).
    Home collection products contribute to 25% of total sales for Brand D and Brand F, making it a key category for these brands.

 -  Free Product Distribution:
   Fragrances account for 45% of free products distributed, followed by skincare at 30%.
   65% of free skincare products were distributed via eCommerce channels compared to 35% via retail.
   Despite this, the sales of skincare products declined by 12% over the last year, suggesting limited effectiveness of free sample strategies.

**Customer Demographics and Behavior**

  - Gender Breakdown:
  Gender information is missing for 43% of retail customers and 66% of eCommerce customers.
  Among known genders, 78% of retail purchases and 91% of eCommerce purchases are made by females, emphasizing the strong influence of female buyers.

  - Age Distribution:
  The average customer age is 39.88 years, with 114 customers over 100 years old, likely input errors for promotional benefits.
  Customers aged 25-45 contribute to 60% of total transactions, highlighting a key demographic for targeted marketing.

  - Customer Transactions:
   69% of customers have only one transaction, while 18% have two transactions, and 13% have three or more transactions.
   Customers with three or more transactions account for 45% of total revenue, indicating the importance of repeat customers.

  - Brand Popularity:
    The wordcloud represents regional preferences in brand popularity across categories, which can be leveraged for targeted marketing and inventory planning.
    ![popularity](https://github.com/Shakya24/Masters-projects/blob/main/Customer%20Analytics/Visualizations/popularity.webp)
    Brand Popularity

**Sales Channel and Store Analysis**

  - Country and Channel Breakdown:
    83.52% of transactions originate from Singapore, while 16.48% are from Malaysia.
    Retail is the dominant channel, contributing 88.8% of total revenue followed by eCommerce stores contributing 10.4% of total revenue.
    In Malaysia, 100% of sales are through Retail and eCommerce, with no Corporate or Third-Party Marketplace sales recorded.

  - Yearly Trends:
    Retail orders in 2023 increased by 25% compared to 2022, with significant growth across all months except January and February.
    


## Technical Analysis

**Customer Segmentation**
Customer segmentation was performed using the RFM (Recency, Frequency, Monetary) framework to analyze customer behaviors and create actionable insights for targeted strategies.

**RFM Framework Construction:**
  -  Recency (R):Quantified as the number of days since the customer’s last purchase. Binned into three quantile-based splits, ensuring an equal distribution of customers in each bin.
  -  Frequency (F):Number of purchase transactions per customer. Binned based on whether customers interacted 2, 3, or 4 times during the observation period.
  -  Monetary (M):Average order size (AOS) for each customer. Binned into three levels:
    -  Low (<0.5x AOS)
    -  Medium (0.5–1x AOS)
    -  High (>1x AOS)

These attributes were concatenated into unique RFM segments representing customer groups with varying behaviors and value

**Derived Customer Segments**
  - **High Value customers** characterized by - Very recent purchase, High frequency of purchase and High total value amount of purchase
  - **At Risk Customers** characterized by - Last purchase in first 8 months of study,High frequency of purchase and High total value amount of purchase
  - **Low Value Customers** characterized by - Only 2 purchases in entire time period and Low total value amount of purchase

**Customer Churn**
1. **Cohort Analysis**: Before building a churn prediction model, the first step was to define the churn. I performed cohort analysis by grouping customers based on their first purchase month and tracking their retention rates over time. I visualized these retention trends using a heatmap ((as shown below) to easily identify patterns and insights.

 ![cohort](https://github.com/Shakya24/Masters-projects/blob/main/Customer%20Analytics/Visualizations/cohort.webp)

From this chart, we can observe that are in the first 2 month cohort of 2022, especially in the first month, there is an abnormal rate in repurchasing rate for customers which starts to stabilize in the 3rd cohort of 2022. At first glance, we can observe that customers tend to repurchase every 6 to 8 months. This is especially evident for cohorts that are more active, for example, cohort 2022-03 and 2022-08. Based on this I decided to set churn period of customers to be **7 months**.

2. **Feature Engineering**: Derived critical features from the dataset to capture customer behavior:
- Frequency: Total number of purchases by a customer.
- Average Basket Size and Basket Value: Indicators of spending behavior.
- Free Quantity: Total number of free samples received.
- Last Purchase Date: Used to compute churn labels; Assign churn label ‘1’ if customer last purchase is more than 7 months ago, otherwise label ‘0’ is given

Correlation analysis ensured low to moderate correlation among features to prevent redundancy in the model

3. **Machine Learning Model and Hyperparameter Tuning**: XGBoost was selected for its robustness in handling tabular data.
Steps included:
- SMOTE to address class imbalance in churned vs. active customers.
- Hyperparameter tuning using random search for optimal model performance.

The model achieved an **ROC AUC score of 0.98** and an **F1-score of 0.91**, reflecting strong predictive capabilities

4. **Feature Importance**: Using SHAP values, key churn predictors were identified:
- Frequency of Purchases: Customers with higher purchase frequencies were less likely to churn.
- Free Quantity Received: Free samples reduced churn likelihood.
- Spending on Fragrance: Higher spending on fragrance correlated with lower churn.
- Basket Size: Larger basket sizes increased churn probability, suggesting the importance of frequent, smaller purchases 

 ![shap](https://github.com/Shakya24/Masters-projects/blob/main/Customer%20Analytics/Visualizations/SHAP.webp)


 
**Market Basket Analysis**

Market Basket Analysis (MBA) was performed to identify relationships and associations between products purchased together, uncovering insights into customer buying patterns.I calculated **LIFT** values across category and brand to determine which products and categories are most frequently purchased together, enabling targeted cross-selling and bundling strategies.A lift value greater than 1 indicates a strong positive association between products/categories.Below are the summary of observations. (_Please note that the brands have been anonymized_)

 ![shap](https://github.com/Shakya24/Masters-projects/blob/main/Customer%20Analytics/Visualizations/LIFT.webp)


## Recommendations

**1. Customer Engagement Cycle:** Based on the Cohort Analysis, I found that customers tend to repurchase within the 6-8 months period. With this information, Store-X can consider planning promotions and replenishing inventory based on the identified customer purchasing period to achieve allocative efficiency.
  - Stock replenishment rate can follow customer purchase cycle to reduce aging inventory
  - Based on this purchasing cycle, promotion campaign can also be planned to secure customers' orders

**2. Customer Churn:** Based on the churn model, I identified that the main factors affecting churn are the frequency of customer purchases, the number of freebies obtained, the average basket size, and the amount of fragrance purchased. To reduce customer churn, Store-X should focus on keeping customers engaged to encourage them to remain active and continue purchasing. Providing **samples can be an effective strategy** to retain customer interest. Since basket size has a direct impact on churn, Store-X should prioritize **increasing the frequency of customer purchases** rather than solely trying to grow the basket size.

**3. Cross Selling Strategies** :Based on the segmentation analysis using RFM results, the following recommendations are proposed to optimize cross-selling strategies and enhance customer engagement across different segments:
**High-Value and At-Risk Customers:**
- Cross-Selling Across Categories:
  - Focus on promoting product combinations across Skin Care, Home Collection, Bath & Body, and Fragrance categories.
  - Leverage positive associations between these categories to create curated bundles and drive larger basket sizes.
- Experimentation with Brands:
  - Expand cross-selling strategies to include additional brands beyond existing associations, to identify whether customer preferences are driven by product type or brand loyalty
  - Highlight strong brand pairings such as Brand B Fragrance, Brand D, and Brand M to deepen customer engagement.
**Low-Value Customers:**
- Increasing Purchase Frequency and Basket Size:
  Encourage purchases from other categories beyond their typical choices of Skin Care and Fragrance by offering:
    - Free Samples: Introduce complementary products to increase category awareness and drive trial.
    - Bundling Deals: Create value bundles combining commonly purchased items (e.g., Byredo Fragrance, The Ordinary, and Diptyque) with products from other categories.
-  Focus on Frequent Purchases:
   Design promotions that incentivize repeat purchases, such as "Buy 2, get 1 free" or loyalty points for purchases across multiple categories.
