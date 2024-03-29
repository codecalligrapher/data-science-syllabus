# Probability
**Given 3 i.i.d. variables from a uniform distribution of 0 to 4, what’s the chance the median is greater than 3?**   
The answer is 5/32. In order to make the median greater than 3 ,atleast 2 i.i.d should be greater than 3. Hence the probability of getting median greater than 3 is equal to the probability of getting 2 i.i.d greater than 3 + the probability of getting 3 i.i.d greater than 3. The probability of getting 2 i.i.d greater than 3 is equal to 9/64 and the probability of getting 3 i.i.d greater than 3 is 1/64 , which adds up to give 5/32  
P(exactly two variables > 3) * 3 + P(all three variables >3)  

**What is the probability of getting a pair by drawing two cards separately in a 52-card deck?**  
This first card you draw can be whatever, so it does not impact the result other than that there is one card less left in the deck. Once the first card is drawn, there are three remaining cards in the deck that can be drawn to get a pair. So, the chance of matching your first card with a pair is 3 out of 51 (remaining cards). This means that the probability of this event occurring is 3/51 or 5.89%.

**In any 15-minute interval, there is a 20% probability that you will see at least one shooting star. What is the probability that you see at least one shooting star in the period of an hour?**  
1 - P(Not seeing any star) = $1 - (0.8)^4 = 0.5904$

**How can you generate a random number between 1 – 7 with only a die?**  
Any die has six sides from 1-6. There is no way to get seven equal outcomes from a single rolling of a die. If we roll the die twice and consider the event of two rolls, we now have 36 different outcomes. To get our 7 equal outcomes we have to reduce this 36 to a number divisible by 7. We can thus consider only 35 outcomes and exclude the other one. A simple scenario can be to exclude the combination (6,6), i.e., to roll the die again if 6 appears twice. All the remaining combinations from (1,1) till (6,5) can be divided into 7 parts of 5 each. This way all the seven sets of outcomes are equally likely.

**How would you determine if two factors are dependent from a contingency table?**  
Step 1: Compute the row and column totals. Step 2:  Compute the relative marginal frequencies for the row variable and column variable. Step 3: Use the Multiplication Rule for Independent Events to compute the expected proportion of observations within each cell,assuming independence Step 4: Multiply the proportions by 2985, the sample size, to obtain the expected counts within each cell Follow this by carrying out the $\chi^2$ test for parameter independence.
[Good example](https://www.jmp.com/en_au/statistics-knowledge-portal/chi-square-test/chi-square-test-of-independence.html)


**Let A and B be events on the same sample space, with P (A) = 0.6 and P (B) = 0.7. Can these two events be disjoint?**  
These two events cannot be disjoint because P(A)+P(B) >1.$$ P(AꓴB) = P(A)+P(B)-P(A\cap B).$$ An  event is disjoint if P(A\cap B) = 0. If A and B are disjoint $P(A\cup B) = 0.6+0.7 = 1.3$ And since probability cannot be greater than 1, these two mentioned events cannot be disjoint.

**Alice has 2 kids and one of them is a girl. What is the probability that the other child is also a girl? You can assume that there are an equal number of males and females in the world**  
The outcomes for two kids can be {BB, BG, GB, GG}. Since it is mentioned that one of them is a girl, we can remove the BB option from the sample space. Therefore the sample space has 3 options while only one fits the second condition. Therefore the probability the second child will be a girl too is 1/3.

**Consider a tetrahedral die and roll it twice. What is the probability that the number on the first roll is strictly higher than the number on the second roll?**
There are 6 out of 16 possibilities where the first roll is strictly higher than the second roll.

[120 Data Science Questions](../pdfs/interview-questions/1643783409499.pdf) is one of the few where every question makes sense, type the answers in the following:


**For sample size n, the margin of error is 3. How many more samples do we need to make the margin of error 0.3?**  
Margin of error is related to population size by $\frac{1}/{\sqrt{N}}$. To decrease margin by factor of $10$ would require 100 times n the original samples  


**A researcher is studying the population of a small town in India of  people. She's interested in estimating  for several yes/no questions on a survey. How many people  does she have to randomly sample (without replacement) to ensure that her estimates  are within  of the true proportions ?**

Goal is to find $\hat{p} \pm 0.04$, using:
$$
\hat{p}\pm z_{\alpha /2}\sqrt{\frac{\hat{p}(1-\hat{p})}{n}\cdot\frac{N-n}{N-1}}
$$

**What is the probability of a Type-I error**  
Probability of type 1 error is based on confidence interval chosen, lets assume 5% 1-tailed test then P(type-1 error) = 5% . Originally if the Mean from the sampling test was falling above the confidence interval of H0, then we were concluding H0 is rejected, i.e when i say the mean was falling beyond i mean the p-value of test statistic was really small. However if the p-value was > 5% (i.e. mean was falling to the left of the 5% mark we were concluding that the sample belongs to H0) ... when you truncate the values of the sample smaller than the Mean of the original sample and recalculate the new mean it will be higher than old mean and is more likely to fall beyond the set confidence interval, hence you are more likely to reject H0. (you maybe increasing the Type 2 error by ignoring values lower than the mean of sample)


**What is the standard error of the mean**  
[Standard Error of the Mean](https://www.scribbr.com/statistics/standard-error/#:~:text=The%20standard%20error%20of%20the,from%20within%20a%20single%20population)
