https://medium.com/subhrajit-roy/cracking-the-machine-learning-interview-1d8c5bb752d8
# Modeling
### If the labels are known in a clustering project, how would you evaluate the performance of the model?
### Why use feature selection? (Solution)
### If two predictors are highly correlated, what is the effect on the coefficients in the logistic regression? What are the confidence intervals of the coefficients?
### What is the difference between K-mean and EM?
### When using a Gaussian mixture model, how do you know it is applicable?

### What is long-format vs wide-format data?
|Long Format|Wide Format|
|--- | --- |
| Here, each row of the data represents the one-time information of a subject. Each subject would have its data in different/ multiple rows.  The data can be recognized by considering rows as groups.  | Here, the repeated responses of a subject are part of separate columns.  The data can be recognized by considering columns as groups |  


**What is regularisation in regression?**  
A regularisation is a special type of regression where the coefficient estimates are constrained (or regularised) to zero. By doing this, it is possible to reduce the variance of the model while at the same time decreasing the sampling error. Regularisation is used to avoid or reduce overfitting. Overfitting happens when the model learns training data so well it undermines the model’s performance on new data. To avoid overfitting, Ridge or Lasso regularisations are usually used.

**Whe should dimensionality reduction be performed?**  
Highly dimensional data or the number of attributes exceed the number of training samples

**Assumptions in Linear Regression**
1. Sample data represents entire population
2. Linear relationship exists between input and output
3. Residual variance is same for any X value (homoscedasticity)
4. Observations are i.i.d.
5. Output is normally distributed for any input of X

**Explain L1 and L2 Regularization?**
L1 (Lasso) regularization adds the penalty term in the cost function by adding the absolute value of weight, while L2 (Ridge) regularization adds the squared value of weights in the cost function. L2 estimates mean, whilst L1 estimates median. L1 assists in feature selection by zeroing non-important features and differentiates between features that are exactly zero and features that are small but nonzero. L2 regression can be used to estimate the significance of predictors and based on that it can penalize the insignificant predictors. When L1 and L2 regularization combine together, it becomes the elastic net method, it adds a hyperparameter. Higher forms of regularization causes the model to become too sensitive to outliers (since more weight is given to anomalous points). *Squared L2* may be preffered since it is easier to compute (no square root, derivatives of the squared correspond only to single instances, whilst derivatives of the square root depend on the entire vector). *Squared L2* may not be preferred because it increases slowly near the origin.

**Why is an orthogonal matrix computationally preferred?**  
Two vectors are orthogonal when their dot product equals zero, called orthonormal. Computing an inverse is usually hard but not for the orthogonal matrix. Therefore, if we can factorize a matrix into orthogonal matrices, that will be great news. For a symmetric matrix, we can guarantee to decompose it into $Q\Lambda Q^T$ where $Q$ is an orthogonal matrix and $\Lambda$ is a diagonal matrix  

**How do you handle missing data?**
1. Replacing the missing value with the mean, median, or mode.
2. Replacing the missing values with a random value.
3. Taking all the NaN values and using them as a New Feature.
4. Replacing NaN values with the third deviation value.
5. Replacing NaN with Least or Last Outlier
6. Replacing NaN with the most frequent Category (Categorical Values)
7. Treating the missing values as a new category
8. Apply a classifier to predict NaN values
9. Drop Values

**Difference between regression and classification**  
Regression finds correlation between dependent and independent variable by predicting a continuous value, classification finds a function dividing the input data into discrete output values/classes

**Grid search vs Random Search** 

**What is logistic regression**

**How do you perform feature selection?**
Univariate Selection: In this method, we used SelectKBest Algo to find the feature score with respect to the dependent column.
Extra Tree Classifier: This technique gives you a score for each feature of the data. The higher the score, the more important and relevant that feature is. You can import the class from sklean.ensemble.
Correlation Matrix: A table that displays the correlation of all the features against each other. Each cell in the table displays a correlation between two variables. We can use a threshold value to select the less correlated variables out of the dataset.
Mutual Information: It is a classifier that generates the mutual information of each feature with respect to the dependent feature. The higher the information is relevant it is

**Why use feature selection? If two predictors are highly correlated, what is the effect on the coefficients in the logistic regression? What are the confidence intervals of the coefficients?**  
Feature selection attempts to optimize a model to be as accurate as possible (i.e. selecting new information) while also avoiding selecting redundant features.  Correlated features are likely to have unstable coefficients when training is repeated on multiple sets of data.  The confidence interval of the coefficients gives a sense of how stable the coefficients are by providing a range of expected values. 


**How do you handle categorical data?**  
One-hot encoding for nominal data, label encoding for ordinal features, or count encoding

**How do we handle outliers?**  
1. Remove all
2. Replace with a suitable value (such as the 3rd standard deviation)
3. Use a non-outlier-sensitive algorithm


**Why is feature scaling necessary?**  
In order to equalize the influence of attribute values on our final prediction, all attributes are scaled to a common range.

**How do you handle and imbalanced dataset?**  
Oversampling, undersampling or algorithm-specific aapproaches  

**What is Cross-Validation**  
t is a technique for increasing the model performance by feeding multiple sample data from the dataset. The sampling process is done by breaking the data into smaller parts that have the same number of rows. Out of all the parts, one is randomly selected for the test and another one for train sets. It consists of the following techniques:

- k-fold cross-validation
- Holdout method
- Stratified k-fold cross-validation
- Leave p-out cross-validation

**When is resampling done?**  
It is done to ensure the model is good enough by training the model on different patterns of a dataset to ensure variations are handled. It is also done in the cases where models need to be validated using random subsets or when substituting labels on data points while performing tests.

**Define the terms KPI, lift, model fitting, robustness and DOE**
- KPI: KPI stands for Key Performance Indicator that measures how well the business achieves its objectives.
- Lift: This is a performance measure of the target model measured against a random choice model. Lift indicates how good the model is at prediction versus if there was no model.
- Model fitting: This indicates how well the model under consideration fits given observations.
- Robustness: This represents the system’s capability to handle differences and variances effectively.
- DOE: stands for the design of experiments, which represents the task design aiming to describe and explain information variation under hypothesized conditions to reflect variables.

**Define confounding variables**  
Extraneous variables which influence both independent and dependent attributes causing spurious associations between associated,non-casual variables

**Explain the basic difference between Supervised, Unsupervised, and Semi-Supervised Machine Learning?**  
Supervised Learning: A model is trained on the labeled data, and then it makes predictions based on the previously labeled data. It requires a supervisor (labels) to train the data. E.g., text classification.

Unsupervised Learning: A model is trained on unlabeled data. The model tries to find patterns, relationships in the data and classify the classes according to that. We don’t have any labeled data.

Semi-Supervised Learning: It is a type of machine learning that uses some amount of labeled data and a large amount of unlabeled data to train the model. The goal of this is to classify some of the unlabeled data with the help of labeled data.  

**What do you mean by Reinforcement Learning?**  
Reinforcement learning is an area of machine learning in which the model is trained according to the rewards given to it based on its previous actions in the environment. There is an agent whose task is to give rewards and also to maximize the rewards. If the model performs the task correctly, it gets a +1 reward, but if it does a task wrong, then it gets a -1 reward.

**What are the different types of data used in Machine Learning?**
There Are Two Types of Data. Structured and Unstructured Data.

**Features vs Labels**
Features and input information, labels are the output. Features are used to predict the label, features are meant to be independent

**What is overfitting**  
Overfitting happens when the model learns training data so well it undermines the model’s performance on new data. To avoid overfitting, Ridge or Lasso regularisations are usually used.  

**What is underfitting**  
Model performance is poor on training data as well as test data. In other words, this type of model failed to generalize the new data points

**Preventing overfitting**  


**What is Scikit-Learn used for**
The Scikit-learn library contains a lot of efficient tools and classes for machine learning and statistical modeling, including classification, regression, clustering, feature selection, parameter tuning, etc. It is an efficient tool for predictive analysis. It provides all the major algorithms in the form of classes and functions. In python, it is written as ```sklearn```.  

**What are a training set and test set in Machine Learning, and why are they important?**  
The Training Set is the set given to the model for training, analyzing, and learning. The Test Set is the set that is used for testing the model locally before using it in a real application. The Training Set is Labeled data, and the Test Set has no labels.

It is important to divide the dataset into training and test sets so that the model will not go in overfitting or underfitting conditions. Also, it is a great method to evaluate the model and understand the characteristics of the data. In most cases, the split is 70/30, meaning 70% of the full data set for training and 30% for testing.

**How does Ensemble Learning work?**
Ensemble Learning is a technique in which the predictions or results of multiple models are combined to achieve better performance. Ensemble Learning can be done in two ways. One is to combine different algorithm predictions to generate a new high-accuracy prediction. Another way is to use a single algorithm multiple times and, in the end, use each model prediction to generate a better model with good accuracy.

**What is bagging and boosting**  
Bagging combines predictions of the same algorithm and reduces variance, boosting combines predictions from different algorithms (e.g. Gradient boosting where current model influenced by ppreviously built models) and reduces bias.

**What is bias-variance tradeoff?**  
Bias is the difference between the average prediction of the model and the correct value. On the other hand, variance is the variability of a data point that shows the spread of the data.
If our model has fewer parameters, then it may have high bias and low variance. Because of that, it will be consistent but inaccurate on average. A model with a large number of parameters may have low bias and high variance models, which are mostly accurate on average but inconsistent in nature. A good model always has low bias and low variance.

## Model-Specific
**How is KNN different from K-means clustering?**  
KNN is a supervised machine learning technique that is used for classification or regression problems. In KNN, the K represents the number of nearest neighbors used to predict the dependent variable. K-means clustering is an unsupervised machine learning algorithm that is used to divide the data into different clusters based on K, the number of clusters, and centroids.

**What is ‘Naive’ in the Naive Bayes Theorem?**
Naive Bayes classifier assumes that all the input variables are independent of each other, meaning they don’t have any relationship between them, which is actually an unrealistic assumption for real data. 

## Evaluation/Testing
**What is an ROC curve?**  
Graph showing performance of classifier at all classification thresholds. TP is plot against false positive. The AUC is an aggregate which gives the probability that a model ranks a random positive example more highly than a random negative sample


**Explain the confusion matrix**  
It is a table of different combinations of predicted and actual values. It is useful for measuring recall, precision, AUC-ROC curve, and accuracy. The diagonal of the matrix contains all the true or correct data. The size of the matrix depends upon the classes in the dependent variable

**Type 1 vs Type 2 Error**  
Type 1 is a false-positive, Type 2 is a false-negative

**Explain Precision, Accuracy, Recall and F1**  
Precision is the ratio of correctly predicted positive observation and total predicted positive observation. It shows how precise our model is.  
Recall is the ratio of the correct predicted positive observation and the total observation in the class.  
F1-Score is the weighted average of recall and precision.  
Accuracy is the ratio of correctly predicted positive observations to the total positive observations.

**How does ROC curve work**  
A ROC curve is a graph showing the performance of a classification model at different thresholds. It uses two curve plot parameters, True positive rate (sensitivity) and False positive rate (Specificity). The closer the curve follows the left-hand border and then the top border, the more accurate the test is.

**What is cross-validation**  
Cross-Validation is a Statistical technique used for improving a model’s performance. Here, the model will be trained and tested with rotation using different samples of the training dataset to ensure that the model performs well for unknown data. The training data will be split into various groups and the model is run and validated against these groups in rotation.

**Correlation vs Covariance**  
Correlation measures and estimates the quantitative relationship between two variaables, whilst covariance is the extent to which the variables change together in a cycle and explains the the relationship between two variables.


**What is the kernel trick?**  
Kernel functions are generalized dot product functions used for the computing dot product of vectors xx and yy in high dimensional feature space. Kernel trick method is used for solving a non-linear problem by using a linear classifier by transforming linearly inseparable data into separable ones in higher dimensions.

## Time-Series
**How are the time series problems different from other regression problems?**  
Can be thought of an extension to linear regression using autocorrelation, movement of averages etc. Forecastingg is the main goal, and there should be a relationship between desired target and time.   

**How do you perform feature selection?**  
*Filter methods* pick up intrinsic properties of features usingg a single number (such as Chi-squared test, Correlation Coefficient, etc). *Wrapper methods* peform search in a space of parameters by greedily choosing the next best feature combination (forward, backward and recursive feature elimination).

**Filter vs Wrapper methods**  
Filter methods are much faster but do not perform well in maintaing feature context, wrapper is computationally intensive but is much faster  

**What could be some issues if the distribution of the test data is significantly different than the distribution of the training data?**

**What are some ways I can make my model more robust to outliers?**

**What are some differences you would expect in a model that minimizes squared error, versus a model that minimizes absolute error? In which cases would each error metric be appropriate?**  

**Given training data on tweets and their retweets, how would you predict the number of retweets of a given tweet after 7 days after only observing 2 days worth of data?**  

**How would you predict who someone may want to send a Snapchat or Gmail to?**  

**In a search engine, given partial data on what the user has typed, how would you predict the user’s eventual search query?**  

**How would you design a model to predict a March Madness bracket**  

**You want to run a regression to predict the probability of a flight delay, but there are flights with delays of up to 12 hours that are really messing up your model. How can you address this?**  

