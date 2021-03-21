### Machine learning v.s. Structured learning
- **Machine learning**: In brief, machine learning is to find a function $f$ such that $f:X\rightarrow Y$, where y can be represents by a particular dimension.
	- Regression: $y$ is a scalar, $y\in Y$, where $y\in\mathbb{R}$.
	- Classification: $y$ is a class, $y\in[0,1\dots,m]$.
- **Structured learning**: Output's domain cannot be assign, it is **composed of components with dependency**.
	- Output is a sequence -> Speech recognition, Text recognition(Chat-box) or Machine Translation.
	- Output can be a  matrix -> [Image to Image, colorization](https://arxiv.org/pdf/1611.07004v1.pdf), [Text to image](https://arxiv.org/pdf/1605.05396.pdf).

</br>

### Why Structured Learning Challenge?
1. One-shot/Zero-shot learning:
	- In Machine learning, each class has *some* example. 
	- In Structured learning
		- If you consider each possible output as a "class"? (Infinite class or huge class).
		- Since the output space is huge, most classes **do not have any training data**.
		- Machine has to **create new stuff** during testing. -> Need more intelligence.

2. Machine has to learn to do **planning**
	- Despite machine generates object component-by-component, it should have a big picture in its mind. -> Cannot change a lot 
	- For the dependency in each component, machine should be **considered globally**. 

### Structured Learning Approach
- Bottom-Up: Learn to generate the object at the component level. ^eb89b0
- Top-Down: Evaluating the whole object, and find the best one. ^5b73b2
![[structured learning1.jpg|500]]