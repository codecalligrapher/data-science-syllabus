# Linear Regression 

## Intuition/Operating Principle
$$
    \hat{\textbf{Y}} = \beta_{1}\textbf{X} + \beta_2 + \epsilon
$$
Continuous output is a linear combination of scaled inputs plus a bias and an error, fit (most commonly) by minimizing the RSS using an analytic approach  
$$
\text{Response} = \text{Predictor(s)} + \text{Bias} + \text{Error}
$$

## Key Terms  
**Synergy Interaction**  
The effects of a combination of predictors is more than the sum of the effects of individual predictors  

**Residual**  
Difference between $i^{th}$ observed value and the $i^{th}$ response value predicted  

**Residual Sum of Squares**  
Measures variance left unexplained by predictor attributes after fitting a linear model  
$$
\text{RSS} = (y_1-\hat{y}_1)^2 + (y_2-\hat{y}_2)^2 + ... + (y_n-\hat{y}_n)^2
$$

**Standard Error**  
Average amount a parameter varies from its actual, unobserved value 
$$
Var(\hat{\mu}) = SE(\hat{\mu})^2 = \frac{\sigma^2}{n}
$$

**Residual Standard Error**  
Estimate of the standard error of model fit, lower RSE implies better fit 
*Caveat is RSE is in units of $Y$, hence a good vs bad RSE heavily depends on the physical quantity represented by Y$  
$$
\text{RSE} = \sqrt{\frac{RSS}{n-p-1}}
$$  

**Residual Plot**   
$y_i - \hat{y_i}$ vs $x_i$ OR vs $y_i$   
Ideally, residual plot should show no discernable pattern (residual should be non-correlated with predictors and predicted)  
Can be used to detect outliers (unusually large error)  

**Pearson's $\text{R}^2$**  
Proportion of variance in response as explained by input predictors  

**$F$-statistic**  
Hypothesis test for disproving the null that all predictor coefficients are zero   
When n is large, an F-statistic that is just a little larger than 1 might still provide evidence against H0 . In contrast, a larger F-statistic is needed to reject H0 if n is small.  

**Collinearity**  
Two or more predictor variables are closely related to one another  


**Variance Inflation Factor**  
Ratio of variance of coefficients $\hat{\beta}_j$ when fitting the full model divided by the variance of $\hat{\beta}_j$ if fit on its own. $VIF=1$ implies zero collinearity   
Denominator is the difference between $R^2$ of $j^th$ parameter when regressed against all other parameters  
$$
\text{VIF}(\beta_j) = \frac{1}{1-R^2_{X_j | X_{-j}}}
$$


**Bias**   
$\Delta$ between actual (unobserved) and calculated parameter values  

**$t$-test**   
If the standard error of $\hat{\beta}_1$ is small, then relatively small values of $\hat{\beta}_1$ may provide strong evidence that $\beta_1\neq 0$. The *t-test* is used to determine the significance of individual predictors, which measures how many standard deviations that $\hat{\beta}_1$ is away from $0$  
$$
t = \frac{\hat{\beta}_1}{\text{SE}(\hat{\beta}_1)}
$$ 


<h2 style="color:#00A">Assumptions</h2>  

- Errors $\epsilon$ are approximately standard Gaussian and for each observation uncorrelated with variance  
- Relation between predictors and response is approximately linear  
- $n$ observations are uncorrelated   
- Residuals have constant variance 

## Combatting Issues with Assumptions 
- Non-constant variances in residuals (hetereoschedasticity) addressed by concave function transforms to the output such as $\log{Y}$ or $\sqrt{Y}$  

<h2 style="color:#0A0">Advantages</h2>
- Average of large number of *OLS* estimates approaches true, unobserved parameters  

<h2 style="color:#A00">Disadvantages</h2>
- 

## Variants