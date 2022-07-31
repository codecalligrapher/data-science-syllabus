# Curse of Dimensionality  
Most points in a high-dimensional hypercube are very close to the border, and the average distance increases as the number of dimensions go up. High-dimensional datasets are the risk of being very sparse, as most training instances will be very far each other meaning models fail to generalize adequately.

# Dimensionality Reduction  
## Projection  
When training instances lie within a lower-dimensional subspace, these can be mapped by *projecting* onto this subspace. 

### PCA  
Identifies hyperplane close to data, projecting data onto it whilst preserving maximum variance. 

**Explained Variance Ratio**  
Indicates the proportion of variance which lies along a principal component  
Choosing the number of principal components can by done by plotting the EVR against $k$, or by finding the number of dimensions presering $95/%$ variance  

#### Variations  
**Randomized PCA**  
Stochastic approximation of the first $d$ principal components, and is dramatically faster than PCA  

**Incremental PCA**  
PCA reuquires entire dataset to fit into memory, which may not be possible. Incremental splits training set into batches and feed an IPCA algorithm.  

**Kernel PCA**  
Allows nonlinear projections for dimensional reductionl

## Manifold Learning  
A manifold is an N-dimensional shape bent and twisted in a higher-dimensional space.  
Assumes that high-dimensional data lies in lower-dimensional subspace, however does not always hold  

### Locally Linear Embedding  
Measuring how each training instance linearly relates to its closest neighbours, and then looks for a lower-dimensional representation of the training set where these local relationships are preserved. Very good at swiss-roll. Distance to points however are not preserved.