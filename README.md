# Portuguese Bank Term Deposit Subscription Prediction
*Note:* A Kaggle implementation featuring [exploratory data analysis](https://www.kaggle.com/code/jiraleelas/bank-marketing-pt-1-exploratory-data-analysis) and [predictive modeling](https://www.kaggle.com/code/jiraleelas/bank-marketing-pt-2-predictive-modelling) is available.

## Problem Statement
A bank term deposit is a fixed-term investment that offer higher interest rates than standard savings accounts. In exchanged for higher interest rates, customers agree not to withdraw their deposit for a specific period (Chen, 2024). This arrangement appeals to investors seeking low-risked investments options while providing banks with stable sources of cash for lending at higher interest rate. This study aims to utilize a marketing dataset to create a predictive model to predict wheter a client would subscribed to term deposit, revealing a valuable insight to the bank marketing function.

## Bank Marketing Dataset
The dataset used in this repository is the [Bank Marketing Full Dataset](https://archive.ics.uci.edu/dataset/222/bank+marketing) 
available publicly on UC Irvine Machine Learning Repository. The dataset contains information from an anonymous Portuguese banking direct phone call marketing campaign to promote bank term deposit subscriptions (Moro et al., 2014).

## Exploratory Data Analysis Summary
### Who are the major bank clients?
Univariate analysis revealed that this anonymous Portuguese bank clients consisted predominantly of clients aged 35-44 years (32.1%), the majority of them having a blue-collar occupation (21.5%), with secondary education level as the common education level (51.3%), and 60.2% of the clients are married. Clients have a median annual account balance of €448, majority of them do not have credit in default (98.2%), no personal loan (84.0%), and housing loan (55.6%).  <br>

In the current campaign, clients were primarily contacted through the cellular method (64.8%), with the median contact day being the 16th day of the month, and the most contacted month being May (30.4%). The median contact times in this campaign is 2 times with each contact lasting a median time of 3 minutes. <br>

For the previous campaign, only a minority of the clients were previously contacted (18.3%). These previously contacted clients were contacted at a median of 2 times with a median recontact gap of 194 days, and failure being the majority outcome (59.36%). <br>

### Who are the term deposit subscribers?
Subscribed clients, consisting of 5,289 individuals, the predominant age group is the 25-34 years age (33.5%) bracket with management occupation being the most subscribed group (24.6%). Similar to the overall trend, the majority of the subscribed clients are married (52.1%) and have secondary education (46.3%). They have a median account balance of €733, with the majority of them does not have credit default (99%), housing (63.4%), and personal loan (90.8%). <br>

Similar to the overall trend, clients were primarily contacted through the cellular method (82.6%) and most of the contacts were done in May (17.5%) a median contact of two times. However, the median contact day for this group is 15 days of the month, and the contact duration for this group is more than 7 minutes (426 seconds). <br>

For the previous contacted campaign 36% of the subscribed clients were contacted. These clients were contacted at a median of 2 times at a shorter recontact gap of 181 days, with success being the predominant result at 51.34%. <br>

### What demographic should we target? and how should the marketing strategy improve?

Given that the majority of subscribed clients work in management, which also represents the largest percentage of the total customer base, this group stands out as a key segment. Additionally, their median account balance of €575 is significantly higher than the overall median of €448. Therefore, the marketing team should prioritize targeting this group to maximize subscriptions and the amount of term deposit. This is to improve the conversion rate. This is similar to the blue-collar clients as this occupation is among the most in the data yet the conversion rate is at its lowest. <br>

Considering both contact performance and account balance, retried clients are another group that the marketing team should prioritized to as they have among the highest conversion rate (22.79%) and having the highest median account balance €787. Given the high conversion rate of students and account balance (€502) above the overall median, this group should be contacted more to leverage the high conversion rate. <br>

<img src=".//eda_plots//scatter-conv-sub-job.png" width="600" height="400">
<img src=".//eda_plots//scatter-med-bal-job.png" width="600" height="400">

With the assocication of marial age to marital statuses, the new campaign should contact clients with older age as they are more likely to subscribe.
<br>
#### What could we learn from the current and previous contact?
Based on the current campaign, cellular data is the primary contact method, yielding the highest client subscription rate. Therefore, this method should be prioritized. Among the contacted months, March, September, October, and December have the highest conversion rates compared to other months; however, the total number of contacts during these months is relatively low, resulting in fewer overall subscribers. Future campaigns should consider increasing outreach during these months to capitalize on their high conversion rates. Meanwhile, efforts in other months should focus on optimizing contact strategies to improve overall conversion rates. 
<br>

Regarding the optimal contact days, current data indicates that days 4, 12, 13, 15, and 30 are the most effective, as they achieve high conversion rates along with a high number of total contacts and subscriptions. In contrast, while days 1 and 10 also show high conversion rates, the total number of contacts on these days is relatively low, leading to fewer final subscribers. Future campaigns should explore these two days further to enhance client conversions.
<br>

Additionally, subscribed clients tend to have a longer average contact duration (426 seconds) compared to non-subscribed clients (164 seconds). This suggests that the length of the conversation could be a key indicator of successful client subscriptions.
<br>

Finally, data from previous campaign contact days reveals that clients who subscribed to the current campaign had a shorter median contact gap of 181 days, compared to 232 days for non-subscribed clients. This indicates that to maximize conversion rates, previously contacted clients should be followed up more frequently in future campaigns.
<br>

## Modelling Summary

- To evaluate the performance of different modeling approaches to the bank marketing data under local computational strain, only 40% of the dataset was used for the training and testing data.

- Categorical variables were encoded using binary, nominal (OneHot), and ordinal encoding based on feature characteristics. Cyclical encoding was applied to days and months, while numerical variables were normalized to mitigate the impact of outliers.

- With the business goal for our model is to identify potential term deposit subscribers. This is too reduce the overall cost of contacting a large number of bank clients. Given the high cost of false negatives (misclassifying subscribers as non-subscribers), our modeling tuning priorities recall and precision-recall curve performance over the receiver operation characteristic (ROC) curve.
  
- To address class imbalance, class weighting was applied across all models to penalize model classification, ensuring the model focuses on subscribed clients (positive classes).

- To find the most suitable model, Decision Tree, Random Forest, AdaBoost, XGBoost, Logistic Regression, and Support Vector Machine models were trained and compared based on recall, the precision-recall curve, and the F1 score. From the modeling results, XGBoost emerged as the optimal model due to its high recall (87.40%), high balance between precision and recall trade-off (F1 58.18%), and strong precision-recall curve performance (PR AUG 0.607).

<img src=".//md_plots//pr-curve.png" width="600" height="400"> 

<img src=".//md_plots//params-comp.png" width="600" height="400">

- XGBoost model performance on the test dataset shows that it correctly identifies most positive cases, achieving a recall of 0.862 and a precision of 0.708. This indicates that while the model effectively captures the majority of actual subscribers, it also produces a relatively high number of false positives. Nevertheless, this model performance is suitable to our goal of reducing telemarketing efforts by focusing on potential clients.

<img src=".//md_plots//xgb-confusion.png" width="500" height="400">
<img src=".//md_plots//xgb-confus-sum.png" width="400" height="300">

- Analyzing features contributions to XGBoost’s classification decisions revealed that the most influential features are contact duration, previous campaign outcome status, and the month of contact. This finding aligns with our initial data exploration, where these features demonstrated a clear distinction between subscribed and non-subscribed clients.

<img src=".//md_plots//shap-features.png" width="600" height="400">

## References
- Chen, J. (2024) Term deposit: Definition, how it’s used, rates, and how to invest, Investopedia. Available at: https://www.investopedia.com/terms/t/termdeposit.asp (Accessed: 03 February 2025). 
- Moro, S., Rita, P., & Cortez, P. (2014). Bank Marketing [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5K306.

