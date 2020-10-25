title: "Introduction to TensorLayer"
categories:
  - Machine Learning
tags:
  - open source
  - large scale ML systems
  - deep learning

As we are moving towards the next leap in deep learning, there has been a lot of progress on the engineering front, esp the framework front. Within the past few years, we have seen a huge number of machine learning libraries and frameworks to enable us to build machine learning models — faster, scalable and accessible.

Two of the most prominent of these frameworks are — TensorFlow and PyTorch. While it is incredibly tempting to do a side by side comparison for both but I think, to sum it up, one can say that PyTorch is easier to use, lighter and flexible (dynamic computational graph) whereas TensorFlow is a complete production level tool. While it has more abstractions and a steep learning curve but it is extremely powerful and tops everything else when it comes to scalability for your deep learning models.

When working with deep learning models however, this low-level architecture mastery for TensorFlow and the high-level architecture mastery for deep learning can seem like a ridiculously tall order.
Image for post
Image for post

It leads to an abstraction gap that demands for some bridging tools. These bridging tools need to fulfill few key requirements in order to be effective:

    Simplicity
    Flexibility
    Functionality
    Portability
    Scalability
    Performance

Thus, over the past few years a few excellent bridging tools or libraries have been developed. These include TensorLayer, Keras, TFLearn etc.
Image for post
Image for post

And, how do they compare?
Image for post
Image for post
So what is TensorLayer?
Image for post
Image for post

TensorLayer, is a part of Google’s popular machine learning and numerical computational framework TensorFlow. It provides popular Deep Learning and Reinforcement Learning modules that can be easily customized and assembled for tackling real-world machine learning problems. The idea behind this library was to facilitate a modular approach to Deep Learning as well as Reinforcement Learning to tackle complex as well as iterative tasks for when it comes to large neural networks and their interactions.
How?

    It provides high-level state-of-the-art deep learning modules

Image for post
Image for post

2. It enables the users to build a model using native Tensorflow APIs
Image for post
Image for post
Also,
Image for post
Image for post

3. It enables the users to define their own computational operations
Image for post
Image for post

4. It enables the users to define their own training logic
Image for post
Image for post

5. The users can glue different modules together (e.g., connected with TF-Slim and Keras).
Image for post
Image for post

6. It provides zero-cost abstraction (or negligible overhead)
Image for post
Image for post

7. It allows easy scaling of your models from laptops to clouds.

    In fact, it is because of these incredibly powerful features that TensorLayer was awarded the 2017 Best Open Source Software by the prestigious ACM Multimedia Society.

Quick Recap:

    Speed: It is basically designed in order to speed-up experimentation and developments by providing a higher-level API to TensorFlow.
    Flexibility: TensorLayer APIs are transparent in nature hence leaving the user with massive hooks that support diverse low-level tuning.
    Customizable: TensorLayer is quite easily extensible as well as modifiable.
    Zero-cost Abstraction: TensorLayer has the ability to achieve the performance of TensorFlow at its fullest.
    Modular Reference Layers: The highlighting feature of TensorLayer lies in the IDE-like approach where the host of operations such as neural networks, their states, data and other parameters are assorted into easily accessible modules.
    When compared with TensorFlow, TensorLayer closely fares the same when classic ML models of neural networks are performed. Although it might look like a setback, it allows the layer module in TensorLayer to cater to customized models. But on the other hand, it uses indexing concepts for quicker row selection while handling datasets. Also, the cache is stored locally to handle workloads with larger data for optimal performance. In addition, it also helps the workflow module to implement Deep Learning models using ‘asynchronous training’.

How does TensorLayer Work?

TensorLayer relies on TensorFlow’s computational engine for training using MongoDB as the storage backend.

Citations:

    ArXiv Paper: TensorLayer: A Versatile Library for Efficient Deep Learning Development
    TensorLayer Documentation
    What Is TensorLayer And How Is It Different From TensorFlow’s Other Machine Learning Libraries?
    Presenting TensorLayer for Researchers and Engineers: A transparent Deep Learning and Reinforcement Learning Library

I I would like to thank TFLayer creators Hao Dong, Luo Mai and TFLayer core-contributors Johanthan Dekhtiar, and LG for help with the content and code examples.