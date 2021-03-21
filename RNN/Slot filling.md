![[slot_filling.jpg|500]]
You can solve this problem by using MLP
![[slot_filling_1.jpg|500]]
and input 'TAIPEI' you can represented by
1. One-hot encoding
2. Beyond 1-of-N encoding
	![[slot_filling_2.jpg|450]]
But it can not help model to specify the question we ask, like
![[slot_filling_3.jpg|500]]
The words `leave` and `arrive` are both classify into "other" class, in neural network, it seen as same input array -> It cannot classify two different meaning.