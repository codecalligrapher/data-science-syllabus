# Data Cleaning  
Data cleaning is the process of fixing or removing incorrect, corrupted, incorrectly formatted, duplicate, or incomplete data within a dataset.  

#### Duplicate Removal  
Irrelavant or unwanted data points removed. This may occur after combining data sources. Irrelevant sources may skew predictions and slow down inference.  

#### Fixing Structural Errors  
Structural errors are when you measure or transfer data and notice strange naming conventions, typos, or incorrect capitalization. These inconsistencies can cause mislabeled categories or classes. For example, you may find “N/A” and “Not Applicable” both appear, but they should be analyzed as the same category.  

#### Filtering Outliers  
Owing to improper data-entry or spurious events, unwanted outliers may occur. Remove if irrelevant to analysis.  

#### Handling Missing Data  
1. Drop observations with missing values, however this drops and loses information  
2. Input missing values based on others (mean, median, etc)  or use a standard value  
3. Use a model with a 'default' option for missing data  
4. Use a simple model to impute values  

#### Handling Noisy Data  
*Noise* is random variance, and is visualized using box-plots and scatter plots  
1. Binning methods smooths sorted values by using near values  
2. Regression forces data to conform to a function  
3. Outlier analysis (clustering) can be used to detect outliers  