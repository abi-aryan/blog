---
title: "Dense Associative Memory for Pattern Recognition"
categories:
  - Machine Learning
tags:
  - hopfield networks
  - deep learning
comments: true
---

> This post is based on [paper](https://arxiv.org/abs/1606.01164) that explores the duality between Associative Memory and Feed-forward Neural Nets — two methods of deep learning. Dense Associative Memory for Pattern Recognition — joint work by Dmitry Krotov and John Hopfield. Presented at NIPS  2016, this paper is an effort to bring together these two distinct  theories and be able to do pattern recognition more effectively.

## Let’s use an analogy to explain what duality means

With the advent of the nineteenth century, many physicists became enamoured by a strange fundamental question. Including them were — Albert Einstein, Thomas Young, Max Planck, Niels
Bohr, Erwin Schrödinger (yup, the man with the cat) and Werner Heisenberg — the geniuses who laid the foundation for Quantum Physics. The question was — “How does the light travel from one place to another?”. A few experiments and some abstractions later, two complementary theories were proposed to explain how light behaves and how it transmits — The Particle Theory and The Wave Theory. However, the results observed suggested that neither of these theories managed to explain the complete behaviour of light — neither was fully right or was fully wrong. Light, to this day, exhibits this strange unexplained “duality”.

For the sake of simplicity. we can roughly think of all the deep neural networks as distributed in two categories: Feed-Forward Networks (includes CNN, Auto-Encoders, GAN) and Cyclic Networks (includes RNN, Hopfield*, Markov Chain, Boltzmann Machine).

**There are two goals of this paper:**

1. Study two models of pattern recognition — feature classification and prototype recognition.
2. Establish a duality between Associative Memory Neural Networks and Feed Forward Neural Networks.

Associative memory functions are represented by **two major functions** — an **energy function** and a **dynamical update function** (or state function that just like a gradient descent rule decreases the energy at every update). The idea of associative memory is that local minima of the energy function corresponds to some meaningful patterns of images and by going down the energy surface, one can recover the
nearest local minimum which corresponds to some pattern from the
training set.

Generally associative memory network are represented by an energy function that looks something like this-

![](/assets/post-images/associative-memory/1.png)

and an update rule that looks something like this-

![](/assets/post-images/associative-memory/2.png)

where

![](/assets/post-images/associative-memory/3.png)

(*do not worry what these complex looking functions mean as of now — trust me they are not so complicated and aren’t useful to build a general understanding of this paper*)  **These conventional associative nets with these functions can store approximately 0.14N memories.** If one tries to store more patterns, several memories would converge together to create new patterns making the classification harder (there is even a term for that called Spurious Networks). However, we know that the size of the network and the number of memories stored hold a non-linear scaling relationship (proved in the paper). Thus, assuming this rule, we come up with a new class of associative models of higher order polynomial defined by the functions -

![](/assets/post-images/associative-memory/4.png)

![](/assets/post-images/associative-memory/5.png)

and the update rule mentioned above. This new associative memory model was tested on XOR and it was found to be capable of solving the problem for higher order odd values of n (the interaction vertex of two or more nuerons). Then, they used another test case : MNIST (50000 training images, 10000 test images) and results proved that it works for n>=2 and interestingly the training time was faster than that in the case of ReLU on feed forward networks thus making it more efficient to train large training sets such as ImageNet. Additionally, **this model has an exponentially increasing capacity that allows one to store N^(n-1) models (>0.14N) which can mean better and faster image classification** due to higher number of stored patterns.

**Now, how does the computation change as n varies?**

The authors selected 25 randomly selected memories and trained them using rectified polynomial energy function of orders n= 2,3,20, 30.

![](/assets/post-images/associative-memory/6.png)

So it looks like this -

![](/assets/post-images/associative-memory/7.png)

As we can see, as n increases the memories have transitioned from a set of features to a set of prototypes at approximately n=20. Depending on your particular case, it might be easier to classify an image based on features and other better as a prototype. For the sake of an example, the exact species of canine (Labrador vs. German Shepherd) be classified using prototype based classification and cats vs dogs can use a feature based classification (though it must be a bit harder than that given dogs do come in all sizes and forms). So far this has only been applied to simple models like MNIST, but in general this computational regime remains largely unexplored. Any extension outside of simple MNIST experiments would be very interesting to confirm the proposition.

Now, it only makes sense to extend the this feature-prototype based classification to feed forward networks to see if feed forward networks too can benefit from such an application.

So the authors **made a few assumptions** to deduce a relation between the two theories (**loosely like string theory in physics**) such that a computational model has two different descriptions : one in terms of associative memory and other in terms of a feedforward network -

1. The feedforward network has only one hidden layer
2. The associative memory model performs only a one step update
3. The labels contain far less information that the data itself
4. The classifications neurons of an associative model are all initialized in the state -ε

Using the above assumptions, the authors were able to create a construction such that

> f(x) = F’(x)

Where f(x) is the activation function from the visible layer to the hidden layer in a feedforward network and F(x) is the energy function of associative memory model.

![](/assets/post-images/associative-memory/8.png)


The result suggests that the activation function of feedforward network is equal to the derivative of the energy function of the associative model i.e. for every small change in x, F(x) changes by f(x). Thus, for various n the activation and energy function are related such that -

![](/assets/post-images/associative-memory/9.png)

Where RePn represents rectified polynomial of order n.

As we concluded previously, the speed of learning should increase as n increases given the higher number of stored patterns. Thus according to the table the ReLU function should be faster than tan hyperbolic function or logistic functions (used in 1980s and 90s) which is consistent with our knowledge of ReLU and thus we can also suggest that these rectified higher polynomial activation functions (ReP) might have even better computational properties than ReLU.

**Thus, at this point we can derive two things -**

1. ReP activation functions might have as good if not substantially better results than ReLU along with a few interesting attributes.
2. These attributes can be inherited to FNN to probably utilize both prototype and feature classification methods into deep learning

**Some interesting future extensions of this work for readers to explore and experiment would be-**

1. Extension of this result for multilayer network architectures.
2. Application of RePU activation functions for feedforward neural networks
3. Application of the dense associative memory models (with RePU) to problems outside MNIST.
4. Studying how regularization like weight decay, dropout etc affect the construction and duality.

**Limitations:**

The following results are only true when the stored patterns are stable.