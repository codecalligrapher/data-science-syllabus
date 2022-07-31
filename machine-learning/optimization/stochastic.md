# Stochastic Methods
*Source: [Algorithms for Optimization](https://algorithmsbook.com/optimization/files/optimization.pdf)  

> Uses randomization strategy to escape local optima by means of random number generation 

## Noisy Descent  
- Adds Gaussian nonise to each step of gradient descent, reduced over time. 
- $\sigma$ of noise typically decreased over time 
- Noise assists in escaping saddle points

## Simulated Annealing 
- *Temperature* controls randomness, which starts high and decreases, allowing the process to freely move about the search space, with the hope that in this phase the process will find a good region with the best local minimum  
- Escapes local minima easily  
- Candidate selected based on *Metropolis* criterion, even if proposal is worse than current 
- Logarithmic cooling schedule guaranteed to reach global optimum, but can be very slow
- Exponential schedule is more common

## Cross Entropy  
- maintains an explicit probability distribution over the design space 
- At each iteration, we sample from the proposal distribution and then update the proposal distribution to fit a collection of the best samples
- 

