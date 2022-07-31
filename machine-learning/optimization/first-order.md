# First Order Methods 
*Source: [Algorithms for Optimization](https://algorithmsbook.com/optimization/files/optimization.pdf)  

> Relies on gradient information to directly minimize a function

## Assumptions  
- Objective function is smooth
- Size of optimization step is small
- Gradient is not zero (stationary point)  

## Types
#### Batch  
Error for each example calculated within the training set after all examples have been evaluated. 
- Computationally efficient, stable error gradient and stable convergence  
- May over-converge, requires entire training set be in memory

#### Stochastic 
Updates parameters for *each* training example in training set 
- Can be faster than batch, rate of improvement very detailed
- Computationally expensive, noisy gradients 

--- 

## Disadvantages 
- Performs poorly in narrow valleys, since step of optimization is always orthogonal to the last
- Can perform poorly on a flat surface, **Nestorov** momentum "speeds up" gradient descent on flat areas and slows it down in local optima to reduce overshoot 
- Adagrad, RMSProp and Adadelta are all ways of adjusting learning rate on a parameter-basis to reduce impact of high-gradient parameters  