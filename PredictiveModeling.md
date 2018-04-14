## 1. (Given a Dataset) Analyze this dataset and give me a model that can predict this response variable.
* Check the size of the data, type of the response variable and distribution of reposonse variable, then have a rouge range of model that I can choose. For example, if this is a regression problem or classification problem, if data size allows us to use complex model.
* Ask for purpose of the model, easy to interpret or better accuracy, then make choice between a model easy to inteprete (like GLM, decision tree) or model without parameters (like machine learning models gbm, xgboost, neural network).
* Ask for data definition, including all potential predictive variables, correlated variables, data collection issue if any (manually input or machine recorded).
* Start EDA, visulize the data, can try univariate type plots, bi-variate plot, check potential correlation, outliers, missing value.

## 2. What could be some issues if the distribution of the test data is significantly different than the distribution of the training data?
* If we have distribution shift between training and test, then model fits training data well might not perform well on test data. This can happen when you split your test and training by time (data change over time).

## 3. What are some ways I can make my model more robust to outliers?
* From model perspective: consider tree based model, which is not that sensitive to outliers comparing with linear regression methods.
* From feature engineering perspective: create buckets for outliers if identified, or cap it, or have data transformation like log transformation when data is right skewed.
* From optimization perspective: try objecitive function that are not senstitive to outliers, like huber loss instead of sum of squared error.
* In general, you should ask why outliers like this, if they are data input issue or something else might give you other insights about the data. For data input issue, you can delete them if they are not a lot.

## 4. What are some differences you would expect in a model that minimizes squared error, versus a model that min- imizes absolute error? In which cases would each error metric be appropriate?
* 

