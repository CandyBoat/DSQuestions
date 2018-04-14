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

## 4. What are some differences you would expect in a model that minimizes squared error, versus a model that minimizes absolute error? In which cases would each error metric be appropriate?
* Following is the answer from [Ben Packer on Quora](https://www.quora.com/How-would-a-model-change-if-we-minimized-absolute-error-instead-of-squared-error-What-about-the-other-way-around)
* Minimizing sqaured error you get mean, minimizing absolute error you get median.
* Minimizing squared error is easy to solve becuase the derivatives of the objective function are continuous, we can set the derivative to be 0 then get the minimizer. While we do not have closed form if we use MAE, though this does not mean we cannot solve it to get the minimizer.
* Median is robust to outliers, while mean is not.
* In summary, it depends on our data and problem. If many outliers, you can consider use MAE as our objective function.
* Another comment here is that: if your underlying model is Gaussian without regularization, then minimizer of MSE is the same with MLE.

## 5. What error metric would you use to evaluate how good a binary classifier is? What if the classes are imbalanced? What if there are more than 2 groups?
* We can consider error rate, AUC area, recall, precision, F1 score to evaluate a binary classifier. Recall, precision and F1 score can be considered if we have imbalanced data.
* Confusion matrix to get error rate, recall, precision for each class (one vs all other).
* [Find better answer for this question.](https://github.com/kojino/120-Data-Science-Interview-Questions/blob/master/predictive-modeling.md#2-what-could-be-some-issues-if-the-distribution-of-the-test-data-is-significantly-different-than-the-distribution-of-the-training-data) I should mention how to construct each metric and the pros and cons for each metric like answer in this link. For example, pros for error rate is easy to interpret, but can be helpless when we have unbalanced data. AUC curve is constructed with false positive rate on x axis, true positive rate on y axis, it measures what the two rates when we set different threshold of 1. Pros is that we do not need to have a threshold if our predicted value is probability and we can use this to find the optimal threshold. Cons is that we cannot explain the uncertainty of the model. Recall is the number of correct predicted positive devided by all true positive (among all true cases how many we find them), precision is the number corrected true positive divided by all predicted positive (among all cases we predicted as truth how many of them are actually true). F1 score can balance precision and recall.

## 6. What are various ways to predict a binary response variable? Can you compare two of them and tell me when one would be more appropriate? What’s the difference between these? (SVM, Logistic Regression, Naive Bayes, Decision Tree, etc.)
* We can consider logistic regression, SVM, Naive Bayes, LDA/QDA, decision tree, random forest, gradient boosting tree, neural network.
* Logistic regression: 
   * pros: vey easy to build logisitc regression model, generates linear (of the input predictors) decision boudary. Also easy to interpret because it can generate estimated parameters so that we can interpret the relationship between predictor and response variable. Output is probability.
   * cons: high bias, needs to do feature engineering carefully
* SVM:
  * pros: works well when you have linear unseperable cases, then can leverage kernel tricks to find the unlinear boundry.
  * cons: data size should be relative large.
* Naive Bayes:
  * pros: 
  * cons: assume each predictor is independent with each other, which might not be true in most cases.
* LDA/QDA:
  * pros: works well when the assumption meets.
  * cons: assume classes are from multivariate Gaussian distribution, LDA even assumes the variance matrix are the same across different classes, QDA assumes different.
* Decision tree:
  * pros: easy to interpret, robust to outliers, good with categorical variable
  * cons: high bias, high variance
* Random Forest:
  * pros: a bagging method, low bias, robust to outliers
  * cons: lose interpretability though you can look at variable importance plot and partial dependency plot to have a sense of importance
* Gradient Tree:
  * pros: a boosting method, combine weak learners to get a strong learner, so usually model has low bias
  * cons: needs large data size, tuning parameters needs more computation than the methods mentioned above, likely to overfit (need to do cross validation), lose interpretability though you can look at variable importance plot and partial dependency plot to have a sense of importance
* Neural network:
  * pros: low bias
  * cons: need a lot of data, likely to overfit (add regularization), expensive computation, lose interpretability

## 7. What is regularization and where might it be helpful? What is an example of using regularization in a model?
* We usually add L1 (LASSO) or L2 (ridge) penalty on the objective function, where L1 norm is the sum of the absolute value of the estimated parameters and we usually do not count intercept term, L2 norm is the sum of the sqaured term of the estimated parameters. We can also use them both, which is called elastic net.
* It is useful:
  * to avoid overfitting.
  * when number of obs is less than the number of predictor.
  * to deal with correlated variables.
  * LASSO can be used to do variable selection.
* We always use regularization when we have a lot of variables, especially when the variables are highly correlated. Examples are using regularization in neural network, in logistic regression, etc.


 




