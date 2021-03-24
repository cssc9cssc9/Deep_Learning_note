## How to deal with semantic segmentation data?
### idea1 : Sliding window approach
Surfing window on images and the window center is the window's label -> classify with CNN
![[semantic segmentation-sliding window.jpg|600]]
Disadventage: Too expensive, not **reusing shared features** between overlapped patches.

### idea2: Fully convolutional
![[fully-convolutional.jpg|600]]
output: The categories of labelled region $C\times H\times W$
Problem: A batch of convolutional layers with same size of input image -> Too expensive.
 
-> **Downsampling** and **Upsampling**
 ![[fully-convolutional_downsampling_upsampling.jpg|600]]
 Downsampling: Pooling, strided convolution
 Upsampling: **Unpooling**
 ![[upsampling-unpooling.jpg|500]]
1. Max Unsampling
 ![[max-pooling-max-unpooling.jpg|500]]
 2. Transpose Convolution(Learnable upsampling)
 As know as Deconvolution, Upconvolution, Fractionally strided convolution, Backward stride convolution. 
![[transpose convolution.jpg|500]]