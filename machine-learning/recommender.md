# Recommender Systems  
Information filtering system aiming to predict future users' interests based on past behaviour  

## Business Case  
Customer rarely knows exactly what they wish to buy, or what they need to search to buy  

Recommenders are multi-staged: *retrieval, ranking and post-ranking*, which iteratively narrows down possible recommendations 

Typically requires inference in less than 100ish milliseconds

## Key Terms  
**Ranking**  
Relative order of items aimed to serve the most relevant items in the correct spots  

# Approaches
## Content-Based 
Use item features to recommend items similar to which was consuemed prior  

## Collaborative
Uses similarity between users and items simultaneously recommending items to user A based on interests of a similar user B

**<p style="color: green">Advantages</p>**  

## Challenges
### Training  
Training data hard to come by  
Perfect recommenders are creepy  
Large scale models with high-dimensional sparse embedding features  
Multiple objectives to optimize for  
*e.g. Should YouTube optimize for watch length or likes*

### Evaluation  
Defining useful metric is ambiguous  
Long-term model drift is less easily quantified  

### Deployment  
Huge vocabulary of data means retrieval system must be very efficient  
Multi-stage nature requires complexity  