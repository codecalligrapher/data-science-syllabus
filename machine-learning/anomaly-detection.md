# Anomaly Detection  
Automation of root-cause analysis using an anomaly detection framework  

## Challenges  
- Low signal-to-noise ratio in training data, as an anomaly is by definition an outlier and unlikely  
- Data may not be labelled and highly imbalanced  
- May be built on dynamnic systems where the definition of an anomaly may change over time  

## Design 
### Simplest  
Calculate mean, and standard deviation of a metric over a sliding window. Calculate the z-score of points and classify as anomalies if z-score exceeds a pre-defined threshold for stationary data  
<p style="color: red"><b>Issues</b></p>  
- Outliers close to anomalous points may render anomalies unclassified, as standard deviation and mean are affected.

*This can be addressed by using median and media-absolute-deviation which cause anomaly bounds to change more smoothly over time*

### Multi-Variable  
For multiple correlated metrics, unsupervised learning such as isolation forests, robust covariance and one-class SVM helps  
**Robust Covariance**  
Assume data is Gaussian and esimates shape of the joint  
**One-Class SVM**  
Identifies arbitrarily shaped regions with a high density of normal points  

Anomalies are the least dense point areas  

### Deep Learning Approach  
Autoencoders learn representation of complex data in an unsupervised manner. An autoencoder trained on normal network data learns what normal behavior looks like. When normal data points are encountered, the reconstruction error is expected to be low. But when anomalous data points are encountered, the error will be high, and the datapoints will be classified as anomalies