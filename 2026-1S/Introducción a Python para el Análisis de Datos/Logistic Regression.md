Statistic technique useful for machine learning, imagine that we want to classify how many hours do students need for pass the  final exam. As every supervised learning task we need **training #data**.
Image that we are using #Linear #regression, and we use some variables for searching a [[Second Exam#Curve Fitting|Curve Fitting]] an now we find the next result:
![[Pasted image 20260724124909.png]]
This is not the best option because how we are going to manage values as 1.1, $-1.03$ ¿That have sense? Nop, this is the main from Logistic Regression, using the sigmoide function we can use a smooth shaped curve that maps any number to a value into $[0;1]$:
![[Pasted image 20260724125151.png]]
$$\sigma(x) = \dfrac{1}{1+e^x}$$
and now we can interpret any output we get as a probability (remember that all output values are in $[0,1]$ domain).
we can minimize the error using another #loss function diferentt as Mean Squared  Error (MSE), the main problem from #MSE is that the model penalize by **True Error** differences, not by factor (using factors is better in this cases), in this cases we will use logarithm, imagine that real probablity is $p$ but you stimated $2p$, we will take the differences and this will penalize our model in $log(2)$, this doesn't matter about which is the real probability.
$$log(n\times p) - log(p) = log(n)$$
returning to our #logistic #model we can see that the next probabilities:
$$\text{Student passed?: } p\quad; \quad \text{Student Failed?: } 1-p$$
![[Pasted image 20260724131129.png]]

Tags: #Regression #Linear #data #loss #MSE #logistic #model