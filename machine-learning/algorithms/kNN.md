# k-Nearest Neighbours  
## Intuition  
Estimates conditional distribution of $Y$ given $X$, and then classifies a given observation to the class/average withe the highest estimated probability  
**Classification** 
$$
Pr(Y=j|X=x_0) = \frac{1}{K}\sum_{i\in N_0}I(y_i = j)
$$

**Regression**  
$$
\hat{f}(x_0) = \frac{1}{K}\sum_{x_i\in N_0}y_i
$$
## Key Terms  
### K  
Number of points considered in test-point-classification. Resultant class is that which has majority probability   
*k* is inversely proportional to bias but directly proportional to variance  

#### Similarity Measure
Similarity can be measured using *Euclidean*, *Cosine*, *Hamming*, *Manhattan* or *Minkowski* distances  


### Non-parametric Approach  
Does not explicitly assume a parametric form for $f(X)$

<span style="color:green;">**Advantages**</span>  
- Does not assume much about data distribution   
- Simple to interpret  
- Applicable in multiple cases and ver high accuracy  

<span style="color:red">**Disadvantages**</span>  
- Very sensitive to outliers, data curation is necessary  
- Memory-intensive, data can be stored on disk and indexed using a **k-d** tree to improve performance  
- Computational complexity increases exponential to size of dataset, kNN can be made stochastic by taking a random sample from the dataset to make predictions  
- Struggles in high-dimensional space 
- Performs best in normalized data