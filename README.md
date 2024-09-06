## Customer Behavior Segmentation and XGBoost-Driven Predictive Modeling for Hotel Booking Optimization

#### Overall Workflow Summary:
- Data Import and Preprocessing: This includes handling outliers, missing values, and data standardization.
- Feature Engineering: Analyzing feature correlations and applying PCA for dimensionality reduction.
- Model Training and Evaluation: Using XGBoost to train and predict based on important features.
- RFM Model Analysis: Segmenting customers using the RFM model.
- Customer Segmentation and Profiling: Using K-Means clustering and heatmaps to visualize the characteristics of different user groups.
- Customer Analysis: Developing personalized marketing strategies for different customer segments.


## XGBoost Model & Data

XGBoost Website: https://xgboost.readthedocs.io

To install the XGBoost model, we can use the pip installation method, for example, in the Windows operating system, Win+R shortcut keys to bring up the run box, enter cmd, enter the code in the pop-up interface and run: `！pip install xgboost`

The data used come from an online travel agency(OTA), and the XGBoost model was employed to predict user order and user churn. Key features include user engagement metrics (e.g., the number of hotel visits, booking frequency, cancellation rates), financial aspects (e.g., consumption level, spending amount), and temporal factors (e.g., time since the last booking or visit). This dataset enables a comprehensive analysis of customer behavior and purchasing patterns, which forms the basis for customer segmentation and predictive modeling.

Data and Data Description Catalog of **XGBoost for User Churn Prediction** is accessible through this link: https://drive.google.com/drive/folders/1D3boa4qNm-v0w3xFEaV3aWexcZudLFfc?usp=sharing


## Feature Engineering

### Hotel Info Correlation Heatmap
### User Feature Correlation Heatmap

<div style="display: flex; justify-content: space-between;">
  <img src="https://github.com/peijin0405/ML-XGBoostModel-for-Deal-and-User-Churn-Forecast/assets/89746479/64a9e404-1c8b-47d6-b6b8-ce13588abbd6" alt="Hotel Info Correlation Heatmap" style="width: 45%;"/>
  <img src="https://github.com/peijin0405/ML-XGBoostModel-for-Deal-and-User-Churn-Forecast/assets/89746479/de2db495-b104-4245-bb2e-e3278b387d8a" alt="User Feature Correlation Heatmap" style="width: 45%;"/>
</div>

## Model Training and Evaluation

XGBoost在该项目中的作用总结：
分类任务：XGBoost 作为一种高效的分类模型，被用来预测用户的行为（例如预订、取消订单等）。
性能评估：通过计算AUC和准确率等指标，评估模型在测试集上的表现，从而了解模型对用户行为的预测能力。
特征重要性：通过分析特征的重要性，XGBoost 帮助我们理解哪些特征对用户行为的预测影响最大，从而为业务决策和个性化推荐提供依据。

### Feature Importance Chart
![Feature Importance Chart](https://github.com/peijin0405/ML-XGBoostModel-for-Deal-and-User-Churn-Forecast/assets/89746479/9b8906d1-cd87-4d10-974e-312997c1431d)

* Important features include whether the user visited the order filling page within the last 24 hours (**iforderpv_24h**), which indicates recent engagement and intent to book; the average number of hotel visits by the user per day over the past 3 months (**historyvisit_avghotelnum**), showing the user’s general browsing activity and interest in hotels; the current hotel conversion rate (**hotelcr**), reflecting the percentage of visits that resulted in bookings; and the historical order cancellation rate for the current hotel (**ordercanceledprecent**), indicating how often users cancel bookings at this hotel. Additional key factors include the user's preference for hotel star ratings (**starprefer**), which can reflect their quality expectations or budget; the user's overall cancellation rate across previous bookings (**cancellationrate**), showing how likely they are to cancel reservations; the number of visits to detailed hotel pages by the user (**historyvisit_visit_detailpagenum**), which can indicate the level of interest and information seeking before making a decision; and the user's sensitivity to price changes (**price_sensitive**), based on past behavior. Also included are the unique visitor count for the current hotel (**hoteluv**), a measure of the hotel's popularity, and the business rate of the most viewed hotels in the last 24 hours (**businessrate_pre**), reflecting the user's interest in hotels that cater to business travelers or have business-oriented amenities.
  
### RFM Model Analysis:
* R(Rencency): Last consumption
* F(Frequency): Consumption frequency
* M(Monetary): Spending amount

The values of **lasthtlordergap (time since last order)**, **ordernum_oneyear (number of user annual orders)**, and **consumption_level (user consumption level)** are chosen as R, F, and M, respectively, for clustering the user groups.

### Customer Segmentation and Profiling
![Customer Segmentation](https://github.com/user-attachments/assets/a5794a91-2d75-4380-bdcf-45a108a79e95)

Customer Segmentation Analysis

This donut chart visualizes customer segmentation based on their RFM (Recency, Frequency, Monetary) scores. Below is the interpretation of each segment:

1. **At-Risk Customer (12.3%)**
   - These customers have shown lower engagement or recency but still have some spending history. They are considered at risk of churning or disengaging completely.
   - **Action**: Focus on re-engagement strategies to retain these customers.

2. **Emerging Customer (8.9%)**
   - Relatively new or with lower engagement, these customers have potential to grow.
   - **Action**: Target these customers with special offers or promotions to increase their interaction and engagement.

3. **Growth Potential Customer (7.0%)**
   - These customers have high monetary value but lower recency or frequency.
   - **Action**: Focus on converting them into more frequent or loyal customers through personalized communication or incentives.

4. **Loyal Customer (40.7%)**
   - The largest segment, representing customers who regularly engage and spend with the business.
   - **Action**: Maintain their loyalty through rewards programs or personalized service.

5. **Premium Customer (5.5%)**
   - These top-tier customers provide significant value to the business through high engagement and spending.
   - **Action**: Prioritize retaining these customers by offering premium benefits or exclusive deals.

6. **Retention Focus Customer (4.5%)**
   - These customers have high value but low recent engagement.
   - **Action**: Implement personalized promotions or outreach to re-engage them before they churn.

7. **Stable Customer (10.1%)**
   - These customers have consistent engagement and spending, though not at the highest level.
   - **Action**: Continue offering value to maintain their steady contribution.

8. **Value Customer (11.0%)**
   - These customers provide decent engagement and spending but are not in the top tiers.
   - **Action**: Offer additional value propositions or promotions to increase their overall contribution.


Key Insights:
- **Loyal Customers** make up the largest portion (40.7%), indicating a strong presence of repeat customers who frequently engage with and contribute to the business.
- **At-Risk Customers** (12.3%) represent a significant portion, suggesting a need for re-engagement strategies.
- **Emerging Customers** (8.9%) and **Growth Potential Customers** (7.0%) could be areas for potential growth with proper nurturing.

### User Profile Heatmap

<p align="center">
  <img src="![User Profile Heatmap](https://github.com/user-attachments/assets/897d9f39-da2b-457b-b630-30834ce86536)
" width="400" />
  <img src="![User Profile](https://github.com/user-attachments/assets/c43da44a-07e6-4504-b247-3934acb3253a)
" width="400" /> 
</p>

#### Heatmap Interpretation

This heatmap visualizes the characteristics of three user groups (Group0, Group1, Group2) based on various features after applying K-Means clustering. The values in each cell represent the prominence of the feature for each group. Here's a brief summary:

Group 0:
- **High in "decisionhabit_user" (decision habits)** and **"historyvisit_avghotelnum" (average hotel visits)**. This indicates that users in this group frequently visit hotels and have strong decision-making habits.
- The other features are neutral or low, suggesting that their consumption behavior and preferences are relatively stable or moderate.

Group 1:
- **Low in "ordercanncelednum" (order cancellations)** and **"consume_level" (consumption level)**, showing that users in this group cancel fewer orders and have a lower overall consumption level.
- The values across all features are relatively balanced, indicating that these users have a moderate behavior pattern without strong tendencies in any particular feature.

Group 2:
- **High in "ordercanncelednum" (order cancellations)** and **"ordercanceledprecent" (order cancellation rate)**, suggesting that this group tends to cancel orders more frequently.
- **High in "consume_level" (consumption level)** and **"price_prefer" (price preference)**, indicating that these users have a higher spending power and are more sensitive to price.

Summary:
- **Group 0** users are frequent hotel browsers with strong decision habits.
- **Group 1** users show balanced behavior across most features and are more stable consumers.
- **Group 2** users tend to have high consumption but also exhibit higher cancellation rates and strong price sensitivity.



**Analysis of Top-Tier Customers**


Top-tier customers are characterized by their high consumption levels and preference for premium, high-quality hotels. They exhibit both high visit and booking frequencies, and tend to make quick decisions with shorter booking windows. Despite their fast decision-making (evidenced by fewer average daily visits), they also demonstrate a high order cancellation rate. This group is heavily associated with business-related travel, often booking at the last minute and cancelling when necessary due to their flexible travel schedules.

A majority of top-tier customers are repeat clients, exhibiting sensitivity to price but a preference for cost-effective yet high-quality products. Their booking behavior is often observed during off-peak hours, such as late at night or early in the morning.

Given their importance to the business, personalized marketing strategies should be implemented for this segment, including:

1. Providing more detailed information about hotels at their frequent travel destinations;
2. Recommending reputable, cost-effective business hotels or hotel chains to attract their attention;
3. Sending timely reminders during non-working day peak hours, such as at 11:00 AM and 5:00 PM.



**Analysis of Moderate-Value Customers**

Moderate-value customers exhibit lower overall consumption levels and do not prioritize high-end hotels. However, they have a high frequency of visits, and their booking windows are the longest of the three customer segments. This group tends to spend considerable time browsing hotels before making a decision, suggesting that they are cautious and deliberate in their choice. It is reasonable to infer that their bookings are often travel-related, reflecting a more considered approach to selecting accommodations.

To effectively engage moderate-value customers, the following strategies should be implemented:

1. Regularly send hotel information two to three weeks prior to holidays;
2. Promote high-end hotels and local travel destinations to capture their interest, as they are more likely to travel;
3. Collaborate with hotel agents in tourist areas to offer personalized recommendations, focusing on more affordable hotel options to align with their preferences.



**Analysis of Entry-Level Customers**

Entry-level customers exhibit minimal demand for high-end hotels and are primarily driven by lower prices. They have short decision-making times, low visit frequencies, and infrequent reservations. Many customers in this group are new, with their behavior suggesting a need for cultivating brand loyalty and engagement.

For this group, the following approaches are recommended:

1. Limit marketing expenditures for this segment while focusing on enhancing the initial customer experience through introductory offers or discounts to encourage repeat business. Regularly promote budget-friendly hotel options to develop their consumption habits;
2. Target this group with promotional content, such as major sales events, to capture their attention;
3. Given that this segment constitutes a large portion of the overall customer base, conducting churn analysis to understand the factors contributing to customer loss will help inform strategies to reduce attrition.
