## 1.In an A/B test, how can you check if assignment to the various buckets was truly random?
* Compare metrics that will not be influenced by the test, those invariant metrics should be similar across control and test group.
* Compare distribution of profile across different groups, like platform proportion, country, age, gender, etc.
* Can consider use stat tests (like multiple comparison if you have more than 2 groups/buckets), parameter or non-parameter if data is not normally distributed. Can consider using chi-square test to see if buckets are statitically differnt for a variable tested.
