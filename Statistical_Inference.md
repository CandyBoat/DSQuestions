## 1.In an A/B test, how can you check if assignment to the various buckets was truly random?
* Compare metrics that will not be influenced by the test, those invariant metrics should be similar across control and test group.
* Compare distribution of profile across different groups, like platform proportion, country, age, gender, etc.
  * Visually look at bar chart, box plot, density curve.
  * Can consider use stat tests (like multiple comparison if you have more than 2 groups/buckets), parameter or non-parameter if data is not normally distributed. Can consider using chi-square test to see if buckets are statitically differnt for a variable tested when this varaible is categorical. Can consider a ANOVA or non-paramtetric method like KS test to see if they are different if variable is continuous.

## 2. What might be the benefits of running an A/A test, where you have two buckets who are exposed to the exact same product?
* AA test can be used to test if the metrics you defined are too sensitive. For example, in AA test, you would not want to see metrics shift, if you see significant difference in metrics from AA test, then you get insights that this metric is too sensitive.
* AA test can be run to do experiments to check if your experiment set up is right. For example, you can run AA test 50 times, then using our significance level, you would expect to see 50 * alpha false positive.
* AA test can be used to identify learning effect. You run a AA test prior to your experiment, making sure metrics from test and control groups are consistent. Then you run AB test. After AB test, you run a post period AA test. If in the post period AA test, test and control group are significant different, then this is a sign of learning effect.
