# Portugese Bank Term Deposit Subscription Prediction
## Problem Statement
A bank term deposit is a fixed-term investment that offer higher interest rates than standard savings accounts. In exchanged for higher interest rates, customers agree not to withdraw their deposit for a specific period (Chen, 2024). This arrangement appeals to investors seeking low-risked investments options while providing banks with stable sources of cash for lending at higher interest rate. This study aims to utilize a marketing dataset to create a predictive model to predict wheter a client would subscribed to term deposit, revealing a valuable insight to the bank marketing function.

## Bank Marketing Dataset
The dataset used in this repository is the [Bank Marketing Full Dataset](https://archive.ics.uci.edu/dataset/222/bank+marketing) 
available publicly on UC Irvine Machine Learning Repository. The dataset contains information from an anonymous Portuguese banking direct phone call marketing campaign to promote bank term deposit subscriptions (Moro et al., 2014).

## Modelling Processes
1. Exploratory data analysis
2. Preprocessing
3. Initial Modelling
4. Model Tuning and Selection
5. Conclusion and Future Work

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

<img src=".//eda_plots//scatter-conv-sub-job.png" width="600" height="300">
<img src=".//eda_plots//scatter-med-bal-job.png" width="600" height="300">

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

### Next Steps for Modelling
- As the distribution between classes is not equivalent, training the model on imbalacce data could lead to model biases  towards major class, not subscribed. Thus, techniques such as class weighting and resampling techniques (e.g., random oversampling and random undersampling) should be explored.
- Feature variable of pcdays and previous have extremely high Spearman correlation at 0.99. As Spearman’s method does not measure the linear relationship like Pearson, this high correlation among variable will be further investigate during model evaluation to determine potential case of multicollinearity. 

## Modelling Summary
- To be updated

## References
- Chen, J. (2024) Term deposit: Definition, how it’s used, rates, and how to invest, Investopedia. Available at: https://www.investopedia.com/terms/t/termdeposit.asp (Accessed: 03 February 2025). 
- Moro, S., Rita, P., & Cortez, P. (2014). Bank Marketing [Dataset]. UCI Machine Learning Repository. https://doi.org/10.24432/C5K306.

