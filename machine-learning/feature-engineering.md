# Data Transforms  
#### Smoothing  
Eliminating noise in the data to see more data patterns.

#### Attribute/feature construction  
New attributes are constructed from the given set of attributes  

#### Aggregation  
Summary and aggregation operations are applied on the given set of attributes to come up with new attributes  

#### Normalization  
The data in each attribute is scaled between a smaller range, for example, 0 to 1 or -1 to 1  

#### Discretization  
Raw values of the numeric attributes are replaced by discrete or conceptual intervals, which can be further organized into higher-level intervals  

#### Concept hierarchy generation for nominal data  
Values for nominal data are generalized to higher-order concepts.

 
## Binarization  
Conversion of a value to two classes by setting an appropriate threshold  

## Quantization  
Quantization maps a continuous number to a discrete one. 
Raw counts across several orders of magnitude would decrease the effectiveness of OLS in regression and other distance measures, a large count in one element would severely outweight similariyt between other elements  

### Quantile Binning  
To deal with large gaps in counts of data (if some bins are very empty), bins can be adaptively positions based on the data distribution using *quantiles*  
*Quantiles are values dividing data into equal proportions*  

## Power Transforms  
These are *variance-stabilizing* transforms  

### Box-Cox Transform  
Generalization of the square-root and log transforms and works for only positive data.  
*Negative data can be handled by shifting the data by a fixed constant*   
$$
 \bar{x} =
    \begin{cases}
      \frac{x^\lambda - 1}{\lambda} & \lambda\neq 0\\
      \ln{x} & \lambda=0
    \end{cases}       
$$
### Log Transformation  
Compresses the range of large numbers and expands the range of small numbers  
Useful in dealing with positive numbers from a heavy-tailed distribution by compressing the long tails in the high end and expanding the tail in the low end.  
Has the effect of increasing bin spacing  
Does not change the shape of the distribution (as in log and other power transforms)

## Scaling and Normalization  
Certain models are affected by scales of data
#### Min-Max Scaling  
Squeezes data points fo be wtihin $[0,1]$ range  
#### Standardization  
*Variance scaling*  
Results in feature with mean $0$ and variance unity  
$$
\tilde{x} = \frac{x - mean(x)}{\sqrt{var(x)}}
$$
#### $l^2$ Normalization  
Divides feature by its Euclidean norma  

## Handling Interaction Features  
A simple pairwise interaction feature is the product of two features 
Extending a model to account for multiplication between features can capture logical/mathematical predictions based on combinations of features  
Expensive to use, as traning time increased.
For multi-collinear attributes, every combination of every level of attributes studies in a cross-design experiment, model with latent variables or cluster data into sets