
##  Chapter 12: Parallelizing Neural Network Training with PyTorch

### Chapter Outline
- PyTorch and training performance
  - Performance challenges
  - What is PyTorch?
  - How we will learn PyTorch
  - 
- First steps with PyTorch
  - Installing PyTorch
  - Creating tensors in PyTorch
  - Manipulating the data type and shape of a tensor
  - Applying mathematical operations to tensors
  - Split, stack, and concatenate tensors
  - 
- Building input pipelines in PyTorch
  - Creating a PyTorch **DataLoader** from existing tensors
  - Combining two tensors into a joint dataset
  - **Shuffle, batch, and repeat**
  - Creating a dataset from files on your local storage disk
  - Fetching available datasets from the **torchvision.datasets** library
  - 
- Building an **NN model** in PyTorch
  - The PyTorch neural network module (torch.nn)
  - Building a linear regression model
  - Model training via the **torch.nn and torch.optim** modules 
  - **Building a multilayer perceptron** for classifying flowers in the Iris dataset
  - **Evaluating** the trained model on the test dataset
  - Saving and reloading the trained model
  - 
- Choosing **activation functions** for multilayer neural networks
  - Logistic function recap
  - Estimating **class probabilities** in multiclass classification via the **softmax function**
  - Broadening the output spectrum using a **hyperbolic tangent**
  - **Rectified linear unit activation**
  - 
- Summary

##  Chapter 13: Going Deeper – The Mechanics of PyTorch

### Chapter Outline
- The key features of 
- PyTorch's **computation graphs**
  - Understanding computation graphs
  - Creating a graph in PyTorch
  - 
- PyTorch tensor objects for storing and updating model parameters
- Computing gradients via **automatic differentiation**
  - Computing the **gradients** of the loss with respect to trainable variables
  - Understanding automatic differentiation
  - Adversarial examples
  - 
- Simplifying implementations of common architectures via the torch.nn module
  - Implementing models based on **nn.Sequential**
  - Choosing a **loss function**
  - Solving an XOR classification problem
  - Making model building more flexible with nn.Module
  - Writing **custom layers** in PyTorch
  - 
- Project one - predicting the fuel efficiency of a car
  - Working with feature columns
  - Training a **DNN regression model**
  - 
- Project two - classifying MNIST **handwritten** digits
- 
- Higher-level PyTorch APIs: a short introduction to **PyTorch Lightning**
  - Setting up the PyTorch Lightning model
  - Setting up the data loaders for Lightning
  - Training the model using the **PyTorch Lightning Trainer** class
  - Evaluating the model using **TensorBoard**
  - 
- Summary

## Next
1. PyTorch viz
2. NN ZerotoHero Series:  [[ZtoNN Series Readme|ZtoNN Series Readme]]

3. pytorch internals blog by ezyang 
	- There may be multiple tensors which share the same storage. Storage defines the dtype and physical size of the tensor, while each tensor records the sizes, strides and offset, defining the logical interpretation of the physical memory. 
	-  ![](Pasted%20image%2020241208025319.png)

- [PyTorch Official Wiki: how to author a kernel](https://github.com/pytorch/pytorch/blob/master/aten/src/ATen/native/README.md)
- [PyTorch TensorIterator Internals](https://labs.quansight.org/blog/2020/04/pytorch-tensoriterator-internals)
- [Podcast: TensorIterator](https://podcasts.apple.com/us/podcast/tensoriterator/id1566080008?i=1000523781021)
- [How to understand Pytorch Source Code?](https://jimmy-shen.medium.com/how-to-understand-pytorch-source-code-1fdbdbbf007e)
- [A Tour of PyTorch Internals: Part 1](https://pytorch.org/blog/a-tour-of-pytorch-internals-1/)
- [A Tour of PyTorch Internals: Part 2](https://pytorch.org/blog/a-tour-of-pytorch-internals-2/)
- [PyTorch — Internal Architecture Tour]](https://blog.christianperone.com/2018/03/pytorch-internal-architecture-tour/)
- [Podcast: PyTorch Developer Podcast](https://podcasts.apple.com/us/podcast/pytorch-developer-podcast/id1566080008)
- [PyTorch Wiki](https://github.com/pytorch/pytorch/wiki/)
- [PyTorch Internals by its author](http://blog.ezyang.com/2019/05/pytorch-internals/)

- First,` torch/` contains what you are most familiar with: the actual Python modules that you import and use. This stuff is Python code and easy to hack on (just make a change and see what happens). However, lurking not too deep below the surface is...
- `torch/csrc/, `the C++ code that implements what you might call the frontend of PyTorch. In more descriptive terms, it implements the binding code that translates between the Python and C++ universe, and also some pretty important pieces of PyTorch, like the autograd engine and the JIT compiler. It also contains the C++ frontend code.
- `aten/`, short for "A Tensor Library" (coined by Zachary DeVito), is a C++ library that implements the operations of Tensors. If you're looking for where some kernel code lives, chances are it's in ATen. ATen itself bifurcates into two neighborhoods of operators: the "native" operators, which are modern, C++ implementations of operators, and the "legacy" operators (TH, THC, THNN, THCUNN), which are legacy, C implementations. The legacy operators are the bad part of town; try not to spend too much time there if you can.
- `c10/`, which is a pun on Caffe2 and A"Ten" (get it? Caffe 10) contains the core abstractions of PyTorch, including the actual implementations of the Tensor and Storage data structures.
## Extra topics

> Checkout notebooks also blogs link within it
> [Link](https://github.com/rasbt/machine-learning-book//blob/376cc179b3d91994ffdf2584151b19ca44358a42/ch12) 


#### 1. Pytorch official documentation: [pytorch.org](https://pytorch.org/docs/stable/index.html)
#### 2. Pytorch vs Tensorflow: A Head-to-Head Comparison[ Link](https://viso.ai/deep-learning/pytorch-vs-tensorflow/#:~:text=PyTorch%20allows%20quicker%20prototyping%20than,have%20to%20start%20from%20scratch.)

|Feature|PyTorch|TensorFlow|
|---|---|---|
|**Ease of Use**|More Pythonic syntax and easier to debug|A steeper learning curve requires more boilerplate code|
|**Dynamic Computation Graph**|Easier to modify the computation graph during runtime|Static computation graph requires recompilation for changes|
|**GPU Support**|Multi-GPU support is easier to set up and use|Multi-GPU support is more complex and requires more setup, there is a TF API|
|**Community Support**|Newer community compared to TensorFlow, growing very fast|Large and active community with extensive resources|
|**Ecosystem**|Has fewer libraries and tools compared to TensorFlow|Has an extensive library of pre-built models and tools|
|**Debugging**|Easier to debug due to Pythonic syntax and dynamic computation graph|Debugging can be more challenging due to the static computation graph|
|**Research**|Often used for research due to its flexibility and ease of use|Often used for production applications due to its speed and scalability|
|**Math Library**|PyTorch uses TorchScript for tensor manipulation and NumPy for numerical computations|TensorFlow uses its own math library for both tensor manipulation and numerical computations|
|**Keras Integration**|PyTorch does not have a native Keras integration|TensorFlow has a native Keras integration which simplifies model building and training|
