## 1. (Given a Dataset) Analyze this dataset and give me a model that can predict this response variable.
* Check the size of the data, type of the response variable and distribution of reposonse variable, then have a rouge range of model that I can choose. For example, if this is a regression problem or classification problem, if data size allows us to use complex model.
* Ask for purpose of the model, easy to interpret or better accuracy, then make choice between a model easy to inteprete (like GLM, decision tree) or model without parameters (like machine learning models gbm, xgboost, neural network).
* Ask for data definition, including all potential predictive variables, correlated variables, data collection issue if any (manually input or machine recorded).
* Start EDA, visulize the data, can try univariate type plots, bi-variate plot, check potential correlation, outliers, missing value.

## 2. What could be some issues if the distribution of the test data is significantly different than the distribution of the training data?
* If we have distribution shift between training and test, then model fits training data well might not perform well on test data. This can happen when you split your test and training by time (data change over time),
