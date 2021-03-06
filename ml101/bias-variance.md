 #  Bias and variance 


# What's bias-variance trade-off?

__Bias__: Difference between the expected(or average) prediction of our model and the correct value which we are trying  to predict. Higher bias means underfitting and the model we got is simple.
__Variance__: Error from sensitivity to small fluctuations in the training set. higher variance means that our model is overfitting and it's a way complex model.
 ![](/assets/Screen Shot 2017-10-27 at 9.49.43 PM.png)
 
 
__Bias_variance tradeoff__: The bias–variance tradeoff is a central problem in supervised learning. Ideally, one wants to choose a model that both accurately captures the regularities in its training data, but also generalizes well to unseen data. Unfortunately, it is typically impossible to do both simultaneously. High-variance learning methods may be able to represent their training set well, but are at risk of overfitting to noisy or unrepresentative training data. In contrast, algorithms with high bias typically produce simpler models that don't tend to overfit, but may underfit their training data, failing to capture important regularities
 

[1] [Understanding the Bias-Variance Tradeoff](http://scott.fortmann-roe.com/docs/BiasVariance.html)

[2] [Andrew Ng's CS229 notes on learning theory](http://cs229.stanford.edu/no tes/cs229-notes4.pdf)
 
[3] [Wikipedia Bias–variance_tradeoff](https://en.wikipedia.org/wiki/Bias–variance_tradeoff)

# Derivation of the bias-variance decomposition for squared error:

If we have training data as $$(x_1,y_1)$$, $$(x_2, y_2)$$....$$(x_n,y_n)$$, all sampled from the same joint distribution $$P(x,y)$$. We assume that there's a function with noise $$ y = f(x)+ \epsilon $$, where the noise, $$\epsilon$$ has zero mean and variance $$\sigma^2$$. We want to find a function $$\hat f(x)$$ to estimate $$f(x)$$.

The expected error can be denoted as:


$$
\begin{aligned}
E[(y-\hat f)^2] & = E[y^2 + \hat f^2 - 2y \hat f^2 ] \\ 
                & =  E[y^2] + E[\hat f^2] - 2fE[\hat f] \\
                & = Var[y] + E[y]^2 + Var[\hat f] + E[\hat f]^2 - 2fE[\hat f] \\
                & = Var[y] + Var[\hat f] + (f^2 - 2fE[\hat f] + E[\hat f]^2) \\
                & = \sigma^2 + Var[\hat f] +(f-E[\hat f])^2 \\
                & = \sigma^2 + Var[\hat f] + Bias[\hat f]^2

\end{aligned}
$$
where $$\sigma^2$$ is called irreducible error. Since all these three terms are non-negative, this forms a lower bond ongthe expected derror on unseen samples.


[1] [Wikipedia Bias–variance_tradeoff](https://en.wikipedia.org/wiki/Bias–variance_tradeoff)

## How to solve high bias and high variance situation?

__High bias(underftiting)__: try some more complex methods(e.g, for deep learning, try bigger networks)
__High variance(overfitting)__: 1. more data. 2. regularization 

Pre deep learning era, we generally  don't have a tool to reduce bias without hurting variance, vice versa. However, for deep learning, we can drive down bias and just drive down bias, or drive down variance and just rive down variance, without really hearing the other thing that much. Like, train bigger network and at the same time add more data.

[][Andrew Ng Cousera's video](https://www.coursera.org/learn/deep-neural-network/lecture/ZBkx4/basic-recipe-for-machine-learning)
## **What's overfitting?**

A: Overfitting refers to a model that models the training data too well. Overfitting happens when a model learns the detail and noise in the training data to the extent that it negatively impacts the performance of the model on new data.



E: Overfitting is more likely with nonparametric and nonlinear models that have more flexibility when learning a target function. As such, many nonparametric machine learning algorithms also include parameters or techniques to limit and constrain how much detail the model learns. For example, decision trees are a nonparametric machine learning algorithm that is very flexible and is subject to overfitting training data. This problem can be addressed by pruning a tree after it has learned in order to remove some of the detail it has picked up.

R:[ https://machinelearningmastery.com/overfitting-and-underfitting-with-machine-learning-algorithms](https://machinelearningmastery.com/overfitting-and-underfitting-with-machine-learning-algorithms/)

## Why overfitting happens?

Overfitting occurs when a model is excessively complex, such as having too many [parameters](https://en.wikipedia.org/wiki/Parameter) relative to the number of observations. Or the number of training data is not large enough!

R: [https://en.wikipedia.org/wiki/Overfitting\](https://en.wikipedia.org/wiki/Overfitting)

## How to avoid overfitting?

Early Stopping, Data argumentation\(numbers of parameter is much smaller than the data \), cross-validation,  Regularization (L1, L2\), Dropout... 

R:  [https://www.quora.com/What-are-ways-to-prevent-over-fitting-your-training-set-data-Is-it-possible-to-test-if-you-have-done-so](https://www.quora.com/What-are-ways-to-prevent-over-fitting-your-training-set-data-Is-it-possible-to-test-if-you-have-done-so)


## What's early stopping?


Early stopping is a form of regularization used to avoid overfitting when training a learner with an iterative method, such as gradient descent.Divide the training data into new_train and validation data.

After each epoch, evaluate the accuracy(error) on the validation data, if the accuracy doesn't improve over N epochs, then we that the accuracy won't increase accuracy. N can be 10, 20,.....

Early stopping rules provid guidance as to how many iterations can be run before the learner begins to over-fit. 

R: [https://en.wikipedia.org/wiki/Early_stopping](https://en.wikipedia.org/wiki/Early_stopping)

## What's dropout?

At each training stage, individual nodes are either "dropped out" of the net with probability 1−p or kept with probability p, so that a reduced network is left; incoming and outgoing edges to a dropped-out node are also removed. Only the reduced network is trained on the data in that stage. The removed nodes are then reinserted into the network with their original weights.

The technique seems to reduce node interactions, leading them to learn more robust features that better generalize to new data.

R:[1] [https://en.wikipedia.org/wiki/Convolutional_neural_network#Dropout](https://en.wikipedia.org/wiki/Convolutional_neural_network#Dropout)
  [2] [http://cs231n.github.io/neural-networks-2/](http://cs231n.github.io/neural-networks-2/)














