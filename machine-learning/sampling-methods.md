# Sampling Methods
### Key Terms
**Imbalanced Data Set**  
Data with skewed class proportions.  
With imbalanced data, a model may too much (or too little) from positive/negative examples. 

## Techniques
### Downsampling
Training on a disproportionately low subset of majority class examples, by randomly sampling from the majority an number equalling the minority.
**Advantages**  
Model converges faster
Space is saved on disk  
Upweighting ensures outputs can still be interpretted as probabilities

**Disadvantages**  
Important information may be left out  
Less data may result in less generalizability of the model  


### Upweighting  
Adding example weight to downsamplied class equal to the factor by which downsampling was carried out

### Resampling
Resampling is a methodology of economically using a data sample to improve the accuracy and quantify the uncertainty of a population parameter. Given a single estimate of a population parameter, the variability is not known, this can be found by multiplie estimates of the parameter. 

This is done to estimate the accuracy of sample statistics, to sample labels on data points and validating models on random subsets

### Bootstrap
Samples are drawn from the dataset with replacement (allowing the same sample to appear more than once in the sample), where those instances not drawn into the data sample may be used for the test set.

### k-Fold Cross Validation  
A dataset is partitioned into k groups, where each group is given the opportunity of being used as a held out test set leaving the remaining groups as the training set. The k-fold cross-validation method specifically lends itself to use in the evaluation of predictive models that are repeatedly trained on one subset of the data and evaluated on a second held-out subset of the data.   

**Choosing K**  
With $K=N$, the estimator is unbiased but exhibits high variance and highlu computationally complex. Lower *K* values exhibit lower variance by higher bias.  
Cross-validation is carried out *after* feature-selection.
**Rule of thumb is to use 5- or 10-fold CV*
