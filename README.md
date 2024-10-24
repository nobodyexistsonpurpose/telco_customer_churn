# Telco customer churn
A project for detecting customers which are going to leave the company. In other words all all work is aimed at solving the problem of binary classification.

The dataset was taken from Kaggle and locates on the following link: https://www.kaggle.com/datasets/blastchar/telco-customer-churn

During the analysis and model applying the next steps and results were done and received: (**remark** this list will be extended as new ideas for analysis and modeling will come)

## Stages


1. **Missing Values and Encoding** &ndash; The data was good collected and has no missing values. The whole dataset consists of 3 continuous variables and 16 categorical, most of which are binary. All categorical features were encoded using One Hot Encoding.
2. **EDA** &ndash; During the EDA several interesting moments were found.
    * Target varible has a strong disbalance. There are about 26.5% of objects which have class 1 (churn class which we want to detect) and 73.5% of objects of another class.
    * The longer a client has used the company's services, the less likely it is that he will leave
    * Senior citizen are more likely to churn than young customer
    * Customers which have a partner are more likely to churn than single customers
    * Customers which have no internet service have very small probability to churn
    * Customers with a long-term contracts (one or two years) have also small probability to churn. 
    * Customers who use Electronic Check payment mathod are very likely to churn.
    * Features in the dataset have no apparent correlations 
    * Dimensionality reduction with PCA shows that datapoints of each classes are located among each other. Generally the data is divided into 3 independent group, two of which has many points with class 0 (that means that we can split these two group from the whole dataset and say that points from there have large probability to be 0 class) and one group in which there are many points of each class. Moreover this group looks like a group of 0-class objects and AMONG them from one side there are many 1-class objects. The dataset has no obvious separation. For example some linear separation will have large amount of mistakes as well as some metric model like KNN. After futher research it was found that two groups which has almost all 0-class points can be splitted from the whole dataset using only three binary features.
3. **ModelApplying** &ndash; To solve this problem 5 models were tested. In addition SMOTE algorithm of sampling was used to handle the class disbalance problem. But no matter if we used SMOTE for sampling or PCA for feature transformation models have the next results on the test set:
    * **KNN** &ndash; has about an 78% accuracy, 62% precision and 46% of recall. With increasing of k_neighbours parameters f1-score of the model is converging to some value near 60%
    * **Logistic Regression** &ndash; gives us about 80% accuracy, 66% precision and 50% of recall. 
    * **SVM** &ndash; has 79% accuracy, precision of 65% and recall of 47%
    * **RandomForest** &ndash; gives 79% accuracy, 65% of precision and 44% of recall. Tuning parameters with cross validation gives us some little upgrades but not significant
    * **AdaBoost** has 80% accuracy, precision of 65% and recall 51%

### Conslusion 

Generally all of the models gives us large errors in precision and recall. That means that they give us many false positives and false negatives answers.

But such results were expected even at the analysis stage because we have seen that datapoints cannot be perfectly splitted by some simple model. We need to 

There can be two reasons for such results. Either we need to have more additional features (because our features give us not enough information) or we need to think about some non-trivial feature transformation. But if we look at visualization of our points we can assume that for all transformations our 1-class points which locate among the 0-class ones will just move to another coordinates WITH whose blue points 

**REMARK: THIS FILE IS CONTINUOUSLY UPDATING BECAUSE I SOMETIMES MAKE SOME FUTHER INVESTIGATIONS IN THE PROJECT**
