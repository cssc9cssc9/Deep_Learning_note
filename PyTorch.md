The reason we need to learn PyTorch:
- **Automatic differentiation** is a powerful tool
- PyTorch implements common functions used in deep learning
- Data Processing with PyTorch DataSet
- **Mixed Presision** Training in PyTorch (Decrease the memory used)

## 1 Data Structure
PyTorch's basic buliding block is `tensor`, and the structure is similar to numpy's `ndarray`, and there is some way to transform each other.

## 2 Properties

#### 2.1. Broadcasting semantic
Two tensors are **Broadcastable** if the following rules hold:
1. Each tensor has at least one dimension.
2. The dimension is read *from right to left*, and only the highest dimension of tensor can be empty.
3. When iterating over the dimension size, starting at the trailling dimension, the dimension sizes must be **equal, one of them is one, or one of them does not exist.**

#### 2.2. Computation graph
PyTorch can implicitly dynamically creates a computation graph in the background. It is a way to record the process of operation.
There is a algorithm **to compute the gradients of all variables of computation graph in time on the same order**.

Consider the expression $e=(a+b)*(b+1)$ with values $a=2,\ b=1$. We can draw the evaluated computation graph as

![[tree-eval.png|800]]

#### 2.3 CUDA semantics
PyTorch can copy tensor from cpu to gpu or from gpu to cpu, such that it can be computed faster by the device you choose.

</br>

## The step to deal with the project
#### 1. Set down the device option
- Choose the device you want to use (GPU or CPU)
- The random seed.

#### 2. Data Preprocessing
- Data Exploration Analysis.
- Data Clean: Make data be the shape you want. (Torchvision provides `transform`)
- Split the validation from the training data.
#### 3. Construct the structure
##### 3.1 Dataset
The first thing you need to do is to design the **dataset**, and it must contain three block:
###### torch.utils.data.Dataset:
- `__init__`: Describe the data imformation (like labels, features).
- `__len__`: Assign the size of dataset, you need to return the dataset size.
-  `__getitem__`: Assign the way to get the imformation from the data set, you need to assign the query way.

However, we are losing a lots features by using a simple `for` loop over the data, In particular we are missing out on:
- Batching the data
- Shuffling the data
- Load the data in parallel using **multiprocessing** worker.

###### torch.utils.data.DataLoader
 `torch.utils.data.DataLoader` is an iterator which provides all these features. It provides much properties, see [here](https://pytorch.org/docs/stable/data.html#data-loading-order-and-sampler).
 
 #### 3.2 Design the model
 ##### torch.nn.Module
 You need to contain two block:
 - `__init__`: Define the parameter of neuron.
 - `forward`: Define how the model process in neural network.
 
</br>

source: 
[PyTorch Tutorial (Hung-yi Lee)](https://www.youtube.com/watch?v=kQeezFrNoOg&ab_channel=Hung-yiLee)
[PyTorch Official Tutorials document](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqbVZ4aXdrXzNHWjVNRG04WUhWeUI2U0RvVjE1UXxBQ3Jtc0tuSlJ0VHkxZlJ5dWVJRnd5WHlXZXRjWnhOLTVIbVRBb0FUbkMwcjk1RGE0eXFCaTB1Qkxla0FmRF9XMHVPZ25GdHVfVlRjTzFIblEzTnItVE1UcmRheDJ2c1liTF9EUHA3NXFqb2JNNUNsX2h1UnFLZw&q=https%3A%2F%2Fpytorch.org%2Ftutorials%2F)