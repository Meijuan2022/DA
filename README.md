# Classification of electrical stability of power grid networks
 ### Meijuan Xia
## Dataset comes from https://archive.ics.uci.edu/ml/datasets/Electrical+Grid+Stability+Simulated+Data+#
# ---------------------------------------------------------------------------------

## Use different classification algorithms to classify the status of electricity:stable or unstable
  - Logistic Regression
  - Naive Bayes
  - KNN
  - SVM
  - Decision Tree
  - RandomForest

## Dataset analysis and preprocessing

- Electrical grids require a balance between electricity supply and demand in order to be stable.The dataset simulates the four-node star electrical grid with centalized produntion. It is a simulated dataset in the Decentral Smart Grid Control system(DSGC), project try to build a model the the system and see how the inputs (behavior) impact the stability.

- Dataset havs 12 features and 2 goals, no null values all the featurs have continous float values and no duplicate rows.

- After correlation check, 9 features and 1 target are kept and transform the target values into int type, 1 means grid node is unstable, 0 means stable status

- Scales the feature values with standardscaler in order to get better performance

## Model selection and evaluations

- It is a binary classification, I selected several regular algorithms to build different models.
- To evaluate the models, confusion matrix, accuracy score and ROC curve are used
- Considering the interpretability,complexity and generalization ability, KNN model is more suitable for the dataset.

## Chanllenges and further improvement

- Before using the methods I would read the theories of the algoriths. They're all about mathmetics formulas and resonnings. It's tough and took a long time :(, but it can help me to understand the algorithm

- Selecting hyperparameters to optimize the models is a big chanllenge for me, I used grid search method and random search method with cross validation. But the problem is how to determine the hyperparameters range which the GridSearchCV and RandomSearch CV will search to get the best parameters with. Especially for SVC and Decision tree models. I read some articles and examples, many of them set the range from experiences. So I tried to fit the search method with different range. But if we set more values in grid search and there are many hyperparameters it will become a huge preocessing and needs a long time to fit. T.ex, SVM(kernel,degree,C,gamma,etc.). I decrease the search numbers (selected not all but 3-5 parameters according to the degree of influence on the models) to decrease the fitting time. Random forest and Decision tree have the same issue. I tried firstly use RandomSearchCV to get the approximate range of the best parameters and then used the GridSearchCV to find the global optimal prameters in the range. It seems to work. It takes much less time.

- I select the KNN as more suitable model for its interpretablity and classification score. The dataset only have 100000 observations and 9 features, so KNN has its own advantages with the numbers. If the numbers becomes much great I am not sure KNN can still have such good performance.

- The data set could be simulated data with 4-node electricity grid. The data seem to be ideal and not complicated. It is used to explore DSGC system methods and concise models to get stable electricity grids between electricity supply and demand.


