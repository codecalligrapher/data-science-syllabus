# Sample  
Subset of data from a larger set called the population  

## Inferential Statistics 
#### Standard Deviation
Indicates the level of dispersion of the mean, or how accurately the mean represents the sample  data  
$$
\sigma = \sqrt{\frac{\sum (x_i - \bar{x})^2}{n-1}}
$$

#### Standard Error of the Mean  
Estimate of how far sample mean is likely to be from population mean  
$$
\sigma_{\bar{x}} = \frac{\sigma}{\sqrt{n}}
$$

#### Margin of Error  
The sample size required to obtain a $(1-\alpha)$ confidence interval for $p$ with margin-of-error $E$:
$$
n = \hat{p}(1-\hat{p})\left(\frac{z_{\alpha/2}}{E}\right)^2
$$

## Random Sampling  
Each available member of the population has the same chance of being chosen for the sample   

## Stratified Sampling  
Divides population into homogenous subgroups with common characteristics or *strata* and select randomly from each *strata*  

## Bias  
Systematic errors in measurement produced by the sampling process, this is **not** due to random chance, as the errors due to bias will have a non-zero mean 
*e.g. bias in mean*  
$$
\text{Bias} = \bar{x} - \mu
$$

### Sample Bias  
Sample that misrepresents a population  

### Selection Bias  
Selectively choosing data which leads to a misleading conclusion  

### Vast Search Effect  
Result of hypothesis test appears statistically significant due strictly to the size of the parameter search space and may be due purely to chance  
This can be alleviated by using a holdout set and target shuffling  

### Regression to the Mean  
Outlier data points typically are followed by data closer to the overall mean

## Sampling Distribution  
Distribution of sample statistic over many samples drawn from the same population  

### Central Limit Theorem  
Tendency of sampling distribution to take on a normal shape as sampling size rises 

### Standard Error  
The variability of a **sample statistic** over many samples  

### Standard Deviation  
Variability of **individual** data values

## The Bootstrap  
Draw additional samples with replacement from the sample and recalculate the statistic for each resample  
*Does not assume data is normally distributed*

### Bootstrap Confidence Interval  
Calculate statistic from multiple bootstrap samples and remove $\frac{100-x}{2}\%$ of the data from either end of the distribution, where $x$ is the desired confidence. The upper and lower endpoints represent the $x\%$ bootstrap confidence interval  

## Distributions  
#### Standardize  
Subtract the mean and divide by standard-deviation  
#### $z$-Score  
Result of standardizing an individual data point  
#### Q-Q Plot  
Shows how close a sample distribution is to a specified distribution  
Plots z-scores against quantiles of the standard normal