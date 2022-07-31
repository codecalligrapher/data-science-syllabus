# Probability 
> *The likelihood of some event or outcome*  

### The Law of Large Numbers  
As the number of repetitions of a probability experiment increases, the proportion with which a certain outcome is observed gets closer to the probability of the outcome.  

## Key Terms  
#### Sample Space $S$
Collection of all possible outcomes  



### Event $E$ 
Collection of outcomes from a probability experiment  
$$
0 \leq P(E) \leq 1
$$

#### Disjoint Events  
$$
P(E\text{ or }F) = P(E) + P(F)
$$
Events with no outcomes in common, also known as *mutually exclusive*   

#### General Addition Rule  
*If events $E$ and $F$ are **NOT** disjoint*
$$
P(E \text{ or }F) = P(E)+P(F)-P(E\text{ and }F)  
$$

#### Complement $E^c$  
All outcomes in the sample splace that are not outcomes in $E$
$$
P(E^c) = 1-P(E)
$$

#### Independent Events  
- Two events $E$ and $F$ are independent if the occurence does not affect the probability of event $F$.  
- Disjoint events cannot be independent, as knowing that one event occurs implies that the other does not
$$
P(E\text{ and }F) = P(E)\times P(F)
$$

in terms of conditional probabilities  
$$
P(E|F) = P(E)\text{ or equivalently }P(F|E) = P(F)
$$


#### Conditional Probability 
$$
P(F|E) = \frac{(E\text{ and }F)}{P(E)}
$$

#### General Multiplication Rule  
$$
P(E\text{ and }F) = P(E)\cdot P(F|E)
$$

<!-- #### Contingency Table  
Relates two categories of data   -->

### Counting  
#### Permutations  
> The number of arrangements of $r$ objects from $n$ distinct objects with repetition  
$$
n^r
$$
> The number of arrangements of $r$ objects from $n$ distinct objects without repetition
$$
{}_{n}P_r = \frac{n!}{(n-r)!}
$$

#### Combinations 
> The number of collections of $r$ objects from $n$ distinct objects without repetition where order does not matter
- There are $r!$ number of orderings of $r$ objects, eliminate orderings of duplicate elements from the permutations formula by dividing. 
$$
_nC_r = \frac{_{n}P_r}{r!} = \frac{n!}{r!(n-r)!}
$$



## Empirical Method  
$$
P(E) \approx \text{relative frequency of }E = \frac{\text{Frequency of }E}{\text{Number of trials in experiment}}
$$
- Requires that experiment actually be performed 

## Classical Method  
$$
P(E) = \frac{\text{Number of ways that $E$ can occur}}{\text{Number of possible outcomes}}
$$
