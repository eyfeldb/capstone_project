# Capstone project

## Business Problem
- An unnamed software company is offering a numbers of different subscription products in a B2C space and has millions of active users enjoying a variety of applications offered by their plans. Some customers over the course of their tenure end up switching to lower priced plans (downgrade), leading to a decrease in revenue from these customers. 
- The management wants to understand if there are any signals in customers' behavior we can pick up prior to them downgrading (and, perhaps, do some intervention in order to prevent the downgrade altogether).

## Approach
- In order to address the business question, we gathered historical data on over 2MM customers' behavior along with their descriptive characteristics such as socio-demographic and product usage history over. Each customer was also marked as whether they downgraded in the subsequent month.
- Since there are many different ways to measure usage (>40 different variables), the team grouped customers into 4 easy to understsand segments for better understanding and more actionable results (based on the original 40+ variables using K-means clustering).
- A predictive model (Logistic Regression & DecisionTree) was later run using the new 4 customer segments (+ demographic characteristics) as signals on whether somebody is likely to downgrade.

## Findings and Results
- Grouping customers into 4 segments from the original 40+ signals of different apps worked really well and can be used to simplify customer segmentation for any subsequent work (including marketing). The analysis shows that there is very little 'loss of information' when we group customers in this way. As can be seen on the chart below, the segments are all neatly separated from each other
<img width="1545" alt="Screenshot 2023-03-01 at 2 45 57 PM" src="https://user-images.githubusercontent.com/63613300/222283062-e3fb431a-5400-40d5-bed3-93eed85cca0f.png">

- Additionally, customers in each segment seem to have very distinct behaviors based on some of the original features. The chart below summarizes the overall distinction, indicating an opportunity for more qualitative analysis in order to better understand each of the segments.
<img width="1559" alt="Screenshot 2023-03-01 at 2 46 07 PM" src="https://user-images.githubusercontent.com/63613300/222283253-f2f9b6d3-9f5b-4388-a9f6-9e8521fd21a9.png">

- The final predictive model (LogisticRegression) was also successful, showing strong predictive power of customers' usage data on their downgrade outcome. Both models yielded ~65% accuracy, which is significantly better than random guessing and could be used to improve the 'health' of customers' base (change their behavior to prevent subsequent downgrades). As can be seen in the chart below, the model does have some false positives and false negatives, however, it successfully captures the majority of likely downgraders. These customers can be targeted with proactive offers and/or other special deals to improve revenue.
<img width="321" alt="Screenshot 2023-03-01 at 2 46 14 PM" src="https://user-images.githubusercontent.com/63613300/222283460-4fa6fc03-8721-4b2c-95f5-5ff12141428d.png">

- Finally, thanks to the model, we can understand the most important factors impacting customers' likelihood to downgrade. Thg top 3 features are:
  - usage cluster
  - customer tenure
  - whether the customer is new or returning

## Next Steps
- Run descriptive analysis on each of the segments and map them to the original 40+ usage features to better understand underlying behaviors of each cluster (i.e. heavy vs light vs occasional users of specific apps). This will help the business better understand each customer but also target them and design custom intervention techniques
- Gather additional data and adjust the outcome window (when they downgrade) to try and further improve the accuracy of the model 
- Design several A/B experiment targeting likely downgraders (as identified by the model) and measure effectiveness of treatment in preventing the downgrade event
- After the intitial release, continiously monitor model's performance to ensure it remains accurate in representing likely downgraders (and to ensure we capture any new potential factors in the future)
