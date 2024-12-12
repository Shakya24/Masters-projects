# Customer-Analytics

Table of Contents

- [Project Background](#project-background)
- [About the Data](#about-data)
- [Summary of Insights](#summary-of-insights)
- [Technical Analysis](#technical-analysis)
- [Recommendations](#recommendations)

***

## Project Background
Established in 2018, this beauty store (retail and online) offers a diverse range of skincare, makeup, and personal care products to customers in Singapore and Malaysia. In this project, I partnered with this brand's Digital Campaign Manager to analyse real customer data to uncover trends in behavior, product preferences, and operational efficiency. The analysis addressed critical challenges, including customer retention, decision fatigue caused by an extensive product range, and the need for personalized shopping experiences.Based on the findings, I delivered actionable recommendations to enhance customer engagement and drive sustainable business growth.

## About-data

The dataset provides comprehensive information on customer transactions for 2022 and 2023, covering details such as purchase dates, countries, stores, brands, product categories, sales channels, and other product-specific information. This rich dataset offers a holistic view of customer purchasing behavior across various dimensions, enabling in-depth analysis and actionable insights.

Steps taken to clean and prepare the dataset for analysis can be found [here]([Data Cleaning Document](https://github.com/Shakya24/Masters-projects/blob/main/Customer%20Analytics/Data%20cleaning%20Customer.pdf)
)


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
    ![popularity](Customer%20Analytics/Visualizations/popularity.webp)
    Brand Popularity

**Sales Channel and Store Analysis**

  - Country and Channel Breakdown:
    83.52% of transactions originate from Singapore, while 16.48% are from Malaysia.
    Retail is the dominant channel, contributing 88.8% of total revenue followed by eCommerce stores contributing 10.4% of total revenue.
    In Malaysia, 100% of sales are through Retail and eCommerce, with no Corporate or Third-Party Marketplace sales recorded.

  - Yearly Trends:
    Retail orders in 2023 increased by 25% compared to 2022, with significant growth across all months except January and February.
    


## Technical Analysis
