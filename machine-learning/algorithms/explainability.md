# Explainability  

## Shapely Value
> Average marginal contribution of a feature value across all possible contributions 
- Attempts to assign number to each feature depending on how much each feature contributed to a given outcome/prediction  

### Advantages  
- *Efficiency* : difference between prediction and average prediction is fairly distributed  
- Symmetric across features  

### Disadvantages  
- Computationally expensive due to exponential number of coalitions between features, can be dealt with by sampling coalitions and limiting the number of iterations  
- Ca be misinterpretted, is not a **sparse** explanation method (whichh contains only a few features), and will always use all features  

