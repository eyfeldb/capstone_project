# Capstone project

The goal of the project is to identify behavioral factors that have highest impact on customers likelihood to downgrade their subscription in the next 30 days and predict customers with highest likelihood to downgrade.

The initial dataset is based on over 2M customer records and the outcome of whether they downgraded in the subsequent 30 days after their behavior snapshot. The overall classes are highly imbalanced as the downgrade event is an extremely rare occurence (less than 1%). The feature set has a number of categorical variables and over 40 characteristics defining customers usage over the course of the previous month. 

After resampling the data (mostly downsampling negative class records) to the 50/50 ratio, the next step was to condence the usage factors into 4 clusters using K-means clustering to make any subsequent recommendations easier to interpret and implement. After the clusters were computed, PCA was run to map out cluster performance and their centers and identify how good of a job the clustering algorithm does at separating customers.

<img width="1545" alt="Screenshot 2023-03-01 at 2 45 57 PM" src="https://user-images.githubusercontent.com/63613300/222283062-e3fb431a-5400-40d5-bed3-93eed85cca0f.png">

As a subsequent step, we take a closer look at the clusters and their parallel coordinates among the original 41 usage-based dimensions. We see that clusters have pretty defined values across the dimensions that can be later used to give more meaningful names to each of the 4 clusters.

<img width="1559" alt="Screenshot 2023-03-01 at 2 46 07 PM" src="https://user-images.githubusercontent.com/63613300/222283253-f2f9b6d3-9f5b-4388-a9f6-9e8521fd21a9.png">

Finally, in order to predict actual outcomes and likelihood to downgrade, two approaches were used: a decision tree classifier and a logistic regression (both optimized via RandomizedSearchCV for optimal hyperparameters w/ default cross-validation). Both yielded similar accuracy on test data (~66%) with the following confusion matrix

<img width="321" alt="Screenshot 2023-03-01 at 2 46 14 PM" src="https://user-images.githubusercontent.com/63613300/222283460-4fa6fc03-8721-4b2c-95f5-5ff12141428d.png">

Running feature permutation importance we observe that factors with highest impact on likelihood downgrade are:
- usage cluster
- customer tenure
- whether the customer is new or returning
