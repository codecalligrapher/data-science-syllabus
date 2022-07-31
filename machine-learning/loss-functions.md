# Loss Functions  
## Probabilistic Losses 
### Cross Entropy  
Used for categorical or binary classification problems
> Cross Entropy: difference between two probability distributions for a given random variable or set of events
$$
-\sum_k p_k\log{q_k}
$$

### Poisson Loss 
> Mean of elements in a Tensor 
$$
y\_true\times \log{(y\_true)}
$$

### Kullback-Leibler Divergence
$$
\sum_{k=1}^K p_k\log{\frac{p_k}{q_k}}
$$

## Regression Losses
### Root-Mean Squared Error  
> Estimates posterior mean
Weights larger errors more heavily and hence more sensitive to outliers
Used when large errors are undesirable
Increases with the variance of the frequency distribution of error magnitudes

### Mean Absolute Error
> Estimates posterior median
Less sensitive to outliers 


### Cosine Similarity 
Difference between two non-zero vectors
Not incredibly accurate as trivial similarities result in a high metric

## Hinge Loss
> Maximum-margin separation (think SVM)
Produces the widest-possible margin between classes 
High computational complexity due to need to compare every single point against every other point  