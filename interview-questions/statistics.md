# Statistics
### In what situation would you consider mean over median?   
The median splits the data roughly into two halves. Advantages of median:\n- Robust to outliers, e.g. median of (121, 124, 132, 142, 171)with outlier and (142, 124, 121, 151, 132) without outlier is the same, whilst mean is not\n- Robust to skewed distributions, general approach is to calculate both, if the mean is vastly different it could indicate highly skewed or noisy data However, the mean can be used if the data distribution is symmetric and continuous
### How do you ineterpret the standard error of the median and mean? 
The standard error of the mean how far the sample mean is likely to be from the true population mean, whilst the standard error of the median is the same for median. It indicates roughly by how much the sample statistics will vary from the actual population statistics, and will generally approach the population statistics as the number of samples increase.


### What is the probability integral transform?
Result thata data values modeled as being rando from any continuous distribution can be converted to standard uniform, provided that distribution being used is the true distribution of the random variables. One use for the probability integral transform in statistical data analysis is to provide the basis for testing whether a set of observations can reasonably be modelled as arising from a specified distribution. Specifically, the probability integral transform is applied to construct an equivalent set of values, and a test is then made of whether a uniform distribution is appropriate for the constructed dataset. Examples of this are P–P plots and Kolmogorov–Smirnov tests.  

### For sample size n, the margin of error is 3. How many more samples do we need to make the margin of error 0.3? 
"Formula for margin-of-error:
$$
E = z_{\alpha/2}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}}
$$
To scale $E$ from 3 to 0.3 would require an increase in sample-size by $\sqrt{10}$"

### What is the assumption of error in linear regression?**  
"- There is not a relationship between the residuals and the  variable; in other words,  is independent of errors. Check this assumption by examining a scatterplot of “residuals versus fits”; the correlation should be approximately 0. In other words, there should not look like there is a relationship.  
- The residuals must be approximately normally distributed. Check this assumption by examining a normal probability plot; the observations should be near the line. You can also examine a histogram of the residuals; it should be approximately normally distributed
 
### Given data from two product campaigns, how could you do an A/B test if we see a 3% increase for one product?
Pick one variable to test, in this case it would be the $3\%$ increase *(clarify what type of increase, or increase in what specific metric)*.  Create a control and a challenger, which changes (two different product campaigns), and split the sample groups equally and randomly. Determine how significant these results have to be, for a smaller increase, we want higher confidence level, since at such a small level of increase, random variance may play a larger part in the test. Our null hypothesis is our intervention (the challenger) having a positive effect (or a negative effect no larger than a margin)Statistical significance is calculated by simulating assignments of both campaigns randomly to conversions for a large number of simulations, and comparing the distribution of these conversions to the actual conversions rate.

### I have a deck and take one card at random. What is the probability you guess it right?  
$$
\frac{1}{52}
$$

### Explain a probability distribution that is not normal and how to apply that.  
*See [Distributions](../statistics/distributions.md)

### Given uniform distributions X and Y and the mean 0 and standard deviation 1 for both, what’s the probability of 2X > Y?  
Informal method, $2X \in [-2a, 2a]$ and $Y\in[-a, a]$. Probability is $\frac{1}{}$

### There are four people in an elevator and four floors in a building. What’s the probability that each person gets off on a different floor?  
"This is a basic permutation/counting question:
$$
\frac{\text{Number of ways for 4 people to get off on 4 floors}}{\text{Number of ways each passenger can get off the elevator}} = \frac{5C1\cdot 4C1\cdot 3C1\cdot 2C1 \cdot 1C1}{5\cdot 5\cdot5\cdot5\cdot5}
$$"

#### Make an unfair coin fair 
Mathematician John von Neumann is credited with figuring out how to take a biased coin (whose probability of coming up heads is p, not necessarily equal to 0.5) and “simulate” a fair coin. Simply flip the coin twice. If it comes up heads both times or tails both times, then flip it twice again. Eventually, you’ll get two different flips — either a heads and then a tails, or a tails and then a heads, with each of these two cases equally likely. Once you get two different flips, you can call the second of those flips the outcome of your “simulation.”


**What is an example of a data type with non-Gaussian distribution**  
A Gaussian distribution is a distribution where a certain known percentage of the data can be found when examining standard deviations from the mean, otherwise known as a normal distribution. Some of the examples of the non-Gaussian distribution can be exponential distribution or binomial distribution.

**Eigenvectors vs Eigenvalues**  
Eigenvectors are column vectors or unit vectors whose length/magnitude is equal to 1. They are also called right vectors. Eigenvalues are coefficients that are applied on eigenvectors which give these vectors different values for length or magnitude.

**Are there any differences between the expected value and mean value?**  
There are not many differences between these two, but it is to be noted that these are used in different contexts. The mean value generally refers to the probability distribution whereas the expected value is referred to in the contexts involving random variables.

**What do you understand by Survivorship Bias?**   
This bias refers to the logical error while focusing on aspects that survived some process and overlooking those that did not work due to lack of prominence. This bias can lead to deriving wrong conclusions.


**What is bias-variance tradeoff?**  
Normally, as you increase the complexity of your model, you will see a reduction in error due to lower bias in the model. However, this only happens until a particular point. As you continue to make your model more complex, you end up over-fitting your model and hence your model will start suffering from high variance.

**List properties of the normal distribution**
Unimodal, symmetrical, bell-shaped (maximum height or mode at the mean), mean mode and median are at the center and asymptotic

**Why do we need selection bias?**
Where no randomized way of picking a sample.

**Difference between a point estimate and a confidence interval**  
Point estimation gives a particular value as an estimate of a population parameter, confidence interval gives us range of values which is likely to contain the population parameter.

**What is A/B testing?**  
Hypothesis test for a randomized experiment with two variables.




# Graphs
**Differentiate between box plot and histogram**  
Box plots and histograms are both visualizations used for showing data distributions for efficient communication of information.
Histograms are the bar chart representation of information that represents the frequency of numerical variable values that are useful in estimating probability distribution, variations and outliers.
Boxplots are used for communicating different aspects of data distribution where the shape of the distribution is not seen but still the insights can be gathered. These are useful for comparing multiple charts at the same time as they take less space when compared to histograms.

