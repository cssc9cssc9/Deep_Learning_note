### Example: Test-to-Image
- Traditional supervised approach ![[conditional_generated1.jpg|500]]
	- Why we get a blurry image?
		-> Because the model all the train images with different degree into consider.
		-> Model would average all the image from different degree 
		-> Generate a weird image. (not realistic)
		
		To solve this problem, machine needs to learn how to generate by the given condition.
		
### Conditional GAN
Based on the previous example, we not only want it be a** train** image but also want it should be **realistic**.

Hence, we consider the condition $c:\text{train}$  :
![[conditional_generated2.jpg|500]]
Then, in basic GAN the discriminator structure would be
![[conditional_generated3.jpg|500]]
But, clearly,** it completely ignore the given condition**.

To avoid tthis problem, we should consider the condition into discriminator:
![[conditional_generated4.jpg]]
Higher score: **True condition and realistic image**.
Lower score: **not realistic** image or **Wrong condition**.

### Algorithm
In each training iteration:
</br>

1. (Learning $D$) </br>Sample $m$ positive examples $\{(c_1, x_1)\,\dots,(c_m,x_m)\}$ from database.
2. Sample $n$ noise samples $\{z_1,\dots,z_m\}$ from a distribution.
3. Obtaining generated data $\{\tilde{x}_m,\dots,\tilde{x}_m\}$, where $\tilde{x}_i=G(c_i,z_i)$.
4. Sample $m$ objects $\{\hat{x}_1,\dots\hat{x}_m\}$ from database
5. Update discriminator $D$ parameters $\theta_d$ to maximize
	- $\tilde{v}=\frac1m\sum_{i=1}^m\log D(c_i,x_i)+\frac1m\sum_{i=1}^m\log\left(1- D(c_i,\tilde{x}_i)\right)+\frac1m\sum_{i=1}^m\log\left(1- D(c_i,\hat{x}_i)\right)$
	- $\theta_d\leftarrow\theta_d+\eta\nabla\tilde{V}(\theta_d)$
6. (Learning $G$) </br> Sample $m$ noise samples $\{z_1,\dots,z_m\}$ from a distribution.
7. Sample $m$ conditions $\{c_1,\dots,c_m\}$ from a database.
8. Update generator parameters $\theta_g$ to maximize
	- $\tilde{V}=\frac1m\sum_{i=1}^m\log(D(G(c_i,z_i)))$
	- $\theta_g\leftarrow\theta_g-\eta\nabla\tilde{V}(\theta_g)$

### Discriminator design
1. Model 1:
Almost every paper used. 
Cons:
	- If it return lower score, you cannot realize why he bad.

![[conditional_generated5.jpg|500]]

2. Model 2:
More reasonable structure.
It return two score, one for reality, other  one for true condition.
![[conditional_generated6.jpg|500]]

## Advanced GAN structure:
### Stack GAN
[StackGAN: Text to Photo-realistic Image Synthesis with Stacked Generative Adversarial Networks](https://arxiv.org/pdf/1612.03242)
![[stack gan.jpg|700]]

### Image-to-Image 
[Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/pdf/1611.07004)

![[Image-to-image.jpg|700]]
</br>

We can deal this problem with supervised learning
![[Image-to-image1.jpg|500]]
But, it would come out a blurry image .
(Model needs to fit too much condition image and it would come out an average outputs)

[Paper](https://arxiv.org/pdf/1611.07004) purposed a GAN model structure to generate more vivid images.

![[Image-to-image2.jpg|700]]

### Patch GAN
[Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/pdf/1611.07004)
If we want to deal with the large size image, normal GAN model would be low efficiency and bad result for too much parameters.

![[PatchGAN.jpg]]

To deal with this problem, it surf a frame to the image and give the score to the frame.

### Speech enhancement
![[speech-enhancement.jpg|600]]
![[speech-enhancement1.jpg|600]]