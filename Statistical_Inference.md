## 1.In an A/B test, how can you check if assignment to the various buckets was truly random?
* Compare metrics that will not be influenced by the test, those invariant metrics should be similar across control and test group.
* Compare distribution of profile across different groups, like platform proportion, country, age, gender, etc.
  * Visually look at bar chart, box plot, density curve.
  * Can consider use stat tests (like multiple comparison if you have more than 2 groups/buckets), parameter or non-parameter if data is not normally distributed. Can consider using chi-square test to see if buckets are statitically differnt for a variable tested when this varaible is categorical. Can consider a ANOVA or non-paramtetric method like KS test to see if they are different if variable is continuous.

## 2. What might be the benefits of running an A/A test, where you have two buckets who are exposed to the exact same product?
* AA test can be used to test if the metrics you defined are too sensitive. For example, in AA test, you would not want to see metrics shift, if you see significant difference in metrics from AA test, then you get insights that this metric is too sensitive.
* AA test can be run to do experiments to check if your experiment set up is right. For example, you can run AA test 50 times, then using our significance level, you would expect to see 50 * alpha false positive. If not, then you might want to check the experiment set up, if groups are not randomly split, test process is not set up right, etc.
* AA test can be used to identify learning effect. You run a AA test prior to your experiment, making sure metrics from test and control groups are consistent. Then you run AB test. After AB test, you run a post period AA test. If in the post period AA test, test and control group are significant different, then this is a sign of learning effect.

## 3. What would be the hazards of letting users sneak a peek at the other bucket in an A/B test?
* User might perform differently then in their bucket. Using an extreme exmple, if your users are kids and if they know other groups is having something they are more interested, then they may not behave as what they would behave, they might ask for treatment in that gruop.

## 4. What would be some issues if blogs decide to cover one of your experimental groups?
* Then you lose control in that group, you have confounding factors that is hard to iolate.

## 5. How would you conduct an A/B test on an opt-in feature?
* Use FB's receiving updates from close friends via text as an example:
 * Ask for the objective for this feature, if it is for improving user engagment, then choose metrics like the number of active users per month (need to define this more), time spent on FB daily, the number of visits daily, etc.
* Then calculate size based on the effect you want to detect, alpha level, power. Then considering the total traffic for the site, get a sense about how much traffic this experiment should run on and how long. Things to consider are weekend/weekday pattern, holiday pattern, roll our gradually, etc.
* Then split users to test and control.
* After reaching the size for each group, then start the analysis.

## 6. How would you run an A/B test for many variants, say 20 or more?
