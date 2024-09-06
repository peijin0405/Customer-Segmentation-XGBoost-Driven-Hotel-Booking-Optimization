# Customer Behavior Segmentation and XGBoost-Driven Predictive Modeling for Hotel Booking Optimization

### Project Overview
This project leverages advanced machine learning techniques, specifically **XGBoost**, to predict user behavior such as booking and churn within the context of an online travel agency (OTA). Additionally, **Principal Component Analysis (PCA)** is applied for dimensionality reduction, simplifying the feature space while retaining the most important information. The project segments customers into distinct groups based on their behavior and purchasing patterns using RFM (Recency, Frequency, Monetary) analysis and **K-Means clustering**. The goal is to derive insights into customer behavior and develop data-driven strategies for optimizing hotel booking processes and personalized marketing.

#### Overall Workflow Summary:
- **Data Import and Preprocessing**: This includes handling outliers, missing values, and data standardization.
- **Feature Engineering**: Analyzing feature correlations and applying PCA for dimensionality reduction.
- **Model Training and Evaluation**: Using XGBoost to train and predict based on important features.
- **RFM Model Analysis**: Segmenting customers using the RFM model.
- **Customer Segmentation and Profiling**: Using K-Means clustering and heatmaps to visualize the characteristics of different user groups.
- **Customer Analysis**: Developing personalized marketing strategies for different customer segments.


### XGBoost Model & Data

[XGBoost](https://xgboost.readthedocs.io) is a highly efficient and scalable machine learning algorithm used for predictive analytics in this project. It is specifically leveraged to predict user behavior, such as booking and churn, within the OTA context.

To install the XGBoost model, you can use pip by executing the following command: `！pip install xgboost`

The data used come from an online travel agency(OTA), and the XGBoost model was employed to predict user order and user churn. Key features include user engagement metrics (e.g., the number of hotel visits, booking frequency, cancellation rates), financial aspects (e.g., consumption level, spending amount), and temporal factors (e.g., time since the last booking or visit). This dataset enables a comprehensive analysis of customer behavior and purchasing patterns, which forms the basis for customer segmentation and predictive modeling.

You can access the dataset and its description through this [Google Drive Link](https://drive.google.com/drive/folders/1D3boa4qNm-v0w3xFEaV3aWexcZudLFfc?usp=sharing).


### Feature Engineering

![Hotel Info Correlation Heatmap](https://github.com/peijin0405/ML-XGBoostModel-for-Deal-and-User-Churn-Forecast/assets/89746479/64a9e404-1c8b-47d6-b6b8-ce13588abbd6)

![User Feature Correlation Heatmap](https://github.com/peijin0405/ML-XGBoostModel-for-Deal-and-User-Churn-Forecast/assets/89746479/de2db495-b104-4245-bb2e-e3278b387d8a)


These heatmaps show the correlations between hotel information and user features, which were used to guide the feature selection process. Analyzing these correlations helps in identifying key features that contribute most to user behavior predictions.

### Model Training and Evaluation

#### XGBoost Model Overview:：
In this project, XGBoost is employed as a classification model to predict user behavior (e.g., booking, order cancellations). It offers robust performance by efficiently handling large datasets and focusing on the most important features.

Key steps in the modeling process include:

- Performance Evaluation: The model’s performance is measured using metrics like AUC (Area Under the Curve) and accuracy to ensure the predictions are reliable.
- Feature Importance: The model provides insight into which features most significantly impact predictions, informing business decisions and customer behavior analysis.

#### Feature Importance Chart
![Feature Importance Chart](https://github.com/peijin0405/ML-XGBoostModel-for-Deal-and-User-Churn-Forecast/assets/89746479/9b8906d1-cd87-4d10-974e-312997c1431d)

The chart highlights the importance of several key features in the model, including:

* iforderpv_24h: Indicates recent engagement and intent to book.
* historyvisit_avghotelnum: Shows the user's general browsing activity.
* hotelcr: Reflects the conversion rate from visits to bookings.
* ordercanceledprecent: Represents the historical cancellation rate for the current hotel.
* starprefer: Reflects user preference for hotel star ratings.
  
### RFM Model Analysis:
The RFM (Recency, Frequency, Monetary) model is used to classify customers into different segments based on their purchase behavior.

* R (Recency): Time since the last order (lasthtlordergap).
* F (Frequency): Number of user orders in the past year (ordernum_oneyear).
* M (Monetary): User consumption level (consume_level).

These values allow for the identification of user groups, which are then used to tailor customer engagement strategies.

### Customer Segmentation and Profiling

![Customer Segmentation](https://github.com/user-attachments/assets/a5794a91-2d75-4380-bdcf-45a108a79e95)

This donut chart visualizes customer segmentation based on their RFM (Recency, Frequency, Monetary) scores. Below is the interpretation of each segment:

1. **At-Risk Customer (12.3%)**
   - These customers have shown lower engagement or recency but still have some spending history. They are considered at risk of churning or disengaging completely.
   - Action: Focus on re-engagement strategies to retain these customers.

2. **Emerging Customer (8.9%)**
   - Relatively new or with lower engagement, these customers have potential to grow.
   - Action: Target these customers with special offers or promotions to increase their interaction and engagement.

3. **Growth Potential Customer (7.0%)**
   - These customers have high monetary value but lower recency or frequency.
   - Action: Focus on converting them into more frequent or loyal customers through personalized communication or incentives.

4. **Loyal Customer (40.7%)**
   - The largest segment, representing customers who regularly engage and spend with the business.
   - Action: Maintain their loyalty through rewards programs or personalized service.

5. **Premium Customer (5.5%)**
   - These top-tier customers provide significant value to the business through high engagement and spending.
   - Action: Prioritize retaining these customers by offering premium benefits or exclusive deals.

6. **Retention Focus Customer (4.5%)**
   - These customers have high value but low recent engagement.
   - Action: Implement personalized promotions or outreach to re-engage them before they churn.

7. **Stable Customer (10.1%)**
   - These customers have consistent engagement and spending, though not at the highest level.
   - Action: Continue offering value to maintain their steady contribution.

8. **Value Customer (11.0%)**
   - These customers provide decent engagement and spending but are not in the top tiers.
   - Action: Offer additional value propositions or promotions to increase their overall contribution.


Key Insights:
- **Loyal Customers** make up the largest portion (40.7%), indicating a strong presence of repeat customers who frequently engage with and contribute to the business.
- **At-Risk Customers** (12.3%) represent a significant portion, suggesting a need for re-engagement strategies.
- **Emerging Customers** (8.9%) and **Growth Potential Customers** (7.0%) could be areas for potential growth with proper nurturing.

#### User Profile Heatmap

The following heatmap shows the characteristics of three user groups segmented using K-Means clustering:

<p align="center">
  <img src="https://github.com/user-attachments/assets/897d9f39-da2b-457b-b630-30834ce86536" width="400" alt="User Profile Heatmap"/>
  <img src="https://github.com/user-attachments/assets/c43da44a-07e6-4504-b247-3934acb3253a" width="400" alt="User Profile"/>
</p>

#### Heatmap Interpretation

Heatmap Interpretation
* Group 0: High decision-making habits and frequent hotel visits, indicating strong interest in hotel browsing.
* Group 1: Lower cancellation rates and moderate consumption levels, representing stable customers.
* Group 2: High consumption but higher cancellation rates, with a sensitivity to pricing.

### Customer Analysis

**Analysis of Top-Tier Customers**

Top-tier customers are characterized by their high consumption levels and preference for premium, high-quality hotels. They exhibit both high visit and booking frequencies, and tend to make quick decisions with shorter booking windows. Despite their fast decision-making (evidenced by fewer average daily visits), they also demonstrate a high order cancellation rate. This group is heavily associated with business-related travel, often booking at the last minute and cancelling when necessary due to their flexible travel schedules.

A majority of top-tier customers are repeat clients, exhibiting sensitivity to price but a preference for cost-effective yet high-quality products. Their booking behavior is often observed during off-peak hours, such as late at night or early in the morning.

Given their importance to the business, personalized marketing strategies should be implemented for this segment, including:

* Providing more detailed information about hotels at their frequent travel destinations;
* Recommending reputable, cost-effective business hotels or hotel chains to attract their attention;
* Sending timely reminders during non-working day peak hours, such as at 11:00 AM and 5:00 PM.


**Analysis of Moderate-Value Customers**

Moderate-value customers exhibit lower overall consumption levels and do not prioritize high-end hotels. However, they have a high frequency of visits, and their booking windows are the longest of the three customer segments. This group tends to spend considerable time browsing hotels before making a decision, suggesting that they are cautious and deliberate in their choice. It is reasonable to infer that their bookings are often travel-related, reflecting a more considered approach to selecting accommodations.

To effectively engage moderate-value customers, the following strategies should be implemented:

* Regularly send hotel information two to three weeks prior to holidays;
* Promote high-end hotels and local travel destinations to capture their interest, as they are more likely to travel;
* Collaborate with hotel agents in tourist areas to offer personalized recommendations, focusing on more affordable hotel options to align with their preferences.

**Analysis of Entry-Level Customers**

Entry-level customers exhibit minimal demand for high-end hotels and are primarily driven by lower prices. They have short decision-making times, low visit frequencies, and infrequent reservations. Many customers in this group are new, with their behavior suggesting a need for cultivating brand loyalty and engagement.

For this group, the following approaches are recommended:

* Limit marketing expenditures for this segment while focusing on enhancing the initial customer experience through introductory offers or discounts to encourage repeat business. Regularly promote budget-friendly hotel options to develop their consumption habits;
* Target this group with promotional content, such as major sales events, to capture their attention;
* Given that this segment constitutes a large portion of the overall customer base, conducting churn analysis to understand the factors contributing to customer loss will help inform strategies to reduce attrition.
