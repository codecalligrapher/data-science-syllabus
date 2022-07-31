# Bias-Variance Tradeoff  
The rror of a given model using squared-error loss cann be thought of as
$$
Err(x_0) = \text{Irreducible Error} + \text{Bias}^2 + \text{Variance}
$$  
**Irreducible Error** is the variance of the target about its true mean  
**Bias** is the amount by which the average of the estimate varies from the true mean  
**Variance**  is the expected squared deviation of our estimate about its mean  

**ROC Curve**  
Plot of *True-positive rate* against *False-positive rate*. Visually shows trade-off between sensitivity (recall) and specificity (or TPR for FPR)

**AUC**  
*Area-Under-Curve* for ROC, aiming for high AUC $X\%$ implies that model will be able to distinguish between output class $X\%$ of the time

**PRC**  
*Precision-Recall Curve* plots Precision against Recall. This is analagous to the *bias-variance* tradeoff.

**AIC**  
*Akeikie Information Criterion* estimates the amount of information lost by a model, promoting goodness of fit whilst penalizing complexity.  
Both AIC and *BIC* (or *Schwarz criterion*) are applicable where fitting is carried out by maximization of a log-likelihood. *BIC* is proportional to AIC, but penalizes complex models more heavily.

**MDL**  
*Minimum-Description-Length* derived as a result of Occam's Razor, which favours simpler models. The best hypothesis to describe data is the one that compresses it the most


# Overfitting and Underfitting
In overfitting, a statistical model describes random error or noise instead of the underlying relationship.
Overfitting occurs when a model is excessively complex, such as having too many parameters relative to
the number of observations. A model that has been overfitted, has poor predictive performance, as it
overreacts to minor fluctuations in the training data.

**Addressing Overfitting**  
1. Add noise
2. Feature selection  
3. Increase training set size  
4. Regularization 
5. Cross-validation  
6. Boosting and bagging  
7. Dropout  
8. Early stopping   


**Addressing Underfitting**  
1. Add features  
2. Increase training time  
3. Increase model complexity  

Underfitting occurs when a statistical model or machine learning algorithm cannot capture the underlying
trend of the data. Underfitting would occur, for example, when fitting a linear model to non-linear data.
Such a model too would have poor predictive performance.