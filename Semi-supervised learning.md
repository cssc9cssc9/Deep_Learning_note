## Introduction
- Supervised learning-> Dataset $D=\{(x_r,y_r)^R_{r=1}\}$ 
E.g., image $x_r$ must have corresponding label $y_r$
- Semi-supervised learning: Dataset $D=\{\{x_r,y_r\}_{r=1}^R, \{x_u\}_{u=R+1}^{R+U}\}$
	- Have a set of unlabeled data, usually $U\gg R$
	1. **Transductive learning**: unlabeled data is the testing data.
	2. **Inductive learning**: unlabeled data is not the testing data.
##### Why we need semi-supervised learning?
1. Collecting data is easy, but **collecting 'labelled' data is expensive**.
2. We do semi-supervised learning in our lives.

##### Why semi-supervised learning helps?
 The distribution of the unlabeled data tell us something.
 ! Semi-supervised learning usually with some **assumptions**-> The exact assumption is important.
 
 ## Semi-supervised learning for Generative model
 Given labelled training examples $x_r\in C_1, C_2$
 - Looking for most likely probability $P(C_i)$ and class-dependent probability $P(x|C_i)$
 - $P(x|C_i)$ is a Gaussian parameterized by $\mu_i$ and $\Sigma$ 
With $P(C_1), P(C_2),\mu_1,\mu_2,\Sigma$, 
$$P(C_1|x)=\frac{P(x|C_1)P(C_1)}{P(x|C_1)P(C_1)+P(x|C_2)P(C_2)}$$
In semi-supervised learning, if we just consider the labelled data then we have</br>
![[generative model.jpg|400]]
then, if we consider the unlabeled data and labelled data, we maybe get
![[generative model1.jpg|400]]
In this example, we can know the unlabeled would affect the decision.
Then, how to deal with the unlabeled data?
	- Algorithm:
		1. Initialization: $\theta=\{P(C_1), P(C_2), \mu_1, \mu_2, \Sigma \}$.