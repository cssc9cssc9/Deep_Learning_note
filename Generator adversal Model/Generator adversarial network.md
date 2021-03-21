### Generation 
- Image generation: 
![[GAN01.jpg|500]]
- Sentence generation:
![[GAN02.jpg|500]]

In practical, we want to control what to generator latter $\rightarrow$ **Conditional Generation**.
</br>

### Basic idea of GAN

- **Generator**: To generate the image or sentence to fool discriminator. (It is a [[Structured Learning#^eb89b0|Bottom-Up]] approach in structured learning )
	![[GAN03.jpg|800]]
- **Discriminator**: To score(classify) the image or sentence is true or not. (It is a [[Structured Learning#^5b73b2|Top-Down]] approach in structured learning )
	![[GAN04.jpg|800]]
	(Generator and discriminator can be a function or a network)
- **Adveriosarial**: 
	1. Discriminate the data conbined with the real and the generated and** feedback the score to the generator**
	2. Based on the score, **generate the better image** to misunderstand the discriminator.
	3. Based on the label, we can **improve the discriminator** and then score the image and feedback to the generator
	4. Keeps going.
</br>

### Algorithm of basic GAN
>- Initialize the generator $G$ and discriminator $D$
>- In each epoch:
>	1. Fix generator $G$, and update discriminator $D$:
>		- Sample the image from the database and mix with the generated image.
>		- Assume **the real images have the higher score and the generated have the lower**.
>		- Based on the score,  use optimization method to impove discriminator $D$.
>	2. Fix discrimintaor $D$, and update generator $G$:
>		- Receive the score from discriminator, we need to make the score higher. (Gradient  ascent)
>
>	According the following, we can look the generator and discriminator as a large network and the one hidden layer is a image representation.
	
 Initializer $\theta_d$ for discriminator $D$ and $\theta_g$ for generator $G$
  In each training iteration:
 - (Learning discriminator $D$)
 	- Sample $m$ examples $\{x_1, \dots, x_m\}$ form database.
	 - Sample $m$ noise samples $\{\vec z_1, \dots, \vec z_m\}$ from as distribution. (not necessary)
 	- Obtain generated data $\{\tilde{x_1},\dots,\tilde{x_m}\}$, where $\tilde{x_i}\in G(\vec z_i)$ .
	- Update discriminator parameter $\theta_d$ to maximize $\tilde{V}=\frac1m\sum^m_{i=1}\log D(x_i)+\frac1m\sum_{i=1}^m\log(1-D(\tilde{x_i}))$. 
	 ($\tilde{V}$ is just the one way to score, it is not the best optimization function.)
		- $\theta_d\leftarrow\theta_d+\eta\nabla \tilde{V}(\theta_d)$
- (Learning generator $G$)
	-	Sample $m$ noises sample $\{\vec z_1, \dots, \vec z_m\}$ from a distribution
	-	Update generator parameters $\theta_g$ to maximize $\tilde{V}=\frac1m\sum^m_{i=1}\log D(G(\vec z_i))$
		-	$\theta_g\leftarrow\theta_g+\eta\nabla \tilde{V}(\theta_g)$
