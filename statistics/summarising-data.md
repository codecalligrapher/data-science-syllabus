# Summarising Data  
> Three main features of data: **shape, center** and **spread**  

## Population Mean  
*Is a parameter*  
$$
\mu = \frac{\sum_{\text{Entire Population}}x_i}{\text{Population Size}}
$$

## Mode  
*Most frequent observation of the variable that occurs in the data set*  

## Sample Mean  
*Is a statistic*  
Same as above but for sample  

## Mean vs Median  
- Median is **resistant** to outliers, unlike mean  
- Mean uses all data, median does not

## Standard Deviation  
*Square root of the sum of squared deviations about the population mean divided by number of observations - 1*   
- Larger s.d. is more dispersion (for symmetric distribution) 

## Variance  
*Square of the standard deviation*

---  

## $z$-Score  
*the distance that a data value is from the mean in terms of the number of standard deviations*  
$$
z = \frac{x-\bar{x}}{s}
$$

## Percentiles  
*The kth percentile, denoted Pk, of a set of data is a value such that k percent of the observations are less than or equal to the value*  

### Quartiles  
*Divides data into fourths*  
- $25th, 50th$ and $75th$ percentiles $Q_1, Q_2$ and $Q_3$ 

### Interquartile Range  
- Unlike standard deviation, is **resistant** since medians are used to calculate this  
$$
IQR = Q_3 - Q_1
$$  

### Checking for Outliers  
1. Determine the first and third quartiles of the data 
2. Compute the interquartile range.
3. Determine the fences. Fences serve as cutoff points for determining outliers. 
$$
\text{Lower fence} = Q_1 - 1.51IQR_2\\
\text{Upper fence} = Q_3 + 1.51IQR_2\\
$$
4. If a data value is less than the lower fence or greater than the upper fence, it is considered an outlier