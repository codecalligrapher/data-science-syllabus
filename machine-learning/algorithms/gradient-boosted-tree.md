# Gradient Boosting Trees  
Gradient boosting works by building simpler (weak) prediction models sequentially where each model tries to predict the error left over by the previous model. Because of this, the algorithm tends to overfit rather quick.  

**Bagging**   
Training a bunch of models in parallel way. Each model learns from a random subset of the data *(i.e. Random Forest)*  
Easier to train, good for distributed computing  

**Boosting** 
Training a bunch of models sequentially. Each model learns from the mistakes of the previous model, takes longer to train

## Hyperparameters  
**Learning Rate**  
How fast the model learns, magnitude of modification, slower LR means model is more robust and efficient, however takes longer  

**n_estimators**   
Number of trees, if LR is low, we need more trees to train the model, too many trees may result in it overfitting  