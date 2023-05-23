---
tags:
  - deep-learning
  - help
---

# Lexicon

??? example "Back-propagation"
    Back-propagation is the algorithm used to updated the weights of a network
    according to its output, usually using a loss function.

??? example "Batch size"
    Number of images, named patches (see below), that the network sees at each
    training step.

??? example "Model"
    The neural network, consisting of a set of layers, each with various number
    of nodes, and the connections between these nodes. The neural network is
    capable of performing calculations by inputing an image (pixel values)
    in its input layer, propagating the values through its layers and outputting
    a prediction. Each node performs a simple calculation, often amounting to
    applying a function to the input value multiplied by a weight, to which
    an offset is added.

??? example "GPU"
    Graphical Processing Unit, which allows performing a large number of small
    computations in parallel. GPUs allow accelerating the training and
    prediction of neural networks.

??? example "Learning rate"
    Parameter regulating the magnitude of the weights update.

??? example "Loss function"
    TODO

??? example "Patch size"
    In order to "fit" in the GPU memory, which is often the limiting factor,
    images need to be all cropped. What the network is trained on is a number
    of patches, i.e. image crops. These patches are all the same size and 
    are aggregated in batches. A single batch is presented to the network during
    a single step of each epoch.

??? example "Prediction"
    TODO

??? example "Test set"
    TODO

??? example "Training"
    TODO

??? example "Training epoch"
    TODO

??? example "Training set"
    TODO

??? example "Training step"
    TODO

??? example "UNet"
    TODO

??? example "Validation set"
    TODO

??? example "Weights"
    The parameters of a Model that define all the neural network node 
    calculations.



