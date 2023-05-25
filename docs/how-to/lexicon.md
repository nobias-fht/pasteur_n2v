---
tags:
  - deep-learning
  - help
---

# Lexicon

The definition of technical terms sometime fluctuates in deep-learning. In this
lexicon we adopt definition that fit the
[CSBDeep](https://github.com/CSBDeep/CSBDeep) and
[N2V](https://github.com/juglab/n2v) libraries.

??? example "Activation function"
    Non-linear function applied to the result of a neuron's calculation. See
    [these examples](https://en.wikipedia.org/wiki/Activation_function#Table_of_activation_functions)

??? example "Back-propagation"
    Back-propagation is the algorithm used to updated the weights of a network
    according to its output, usually using a loss function.

??? example "Batch size"
    Number of images, named patches, that the network sees at each
    training step.

??? example "Model"
    The neural network, consisting of a set of layers, each with various number
    of neurons, and the connections between these nodes. The neural network is
    capable of performing calculations by inputing an image (pixel values)
    in its input layer, propagating the values through its layers and outputting
    a prediction. Each neuron of a layer performs a simple calculation, that is
    then aggregated for the whole layer and passed to the next layer.

??? example "GPU"
    Graphical Processing Unit, which allows performing a large number of small
    computations in parallel. GPUs allow accelerating the training and
    prediction of neural networks.

??? example "Ground-truth"
    "Reality" of what we want the network to output. For instance, if we want
    to perform denoising, the ground-truth are clean images where noise is
    minimal, as opposed to the inputs which should be noisy images.

??? example "Layer"
    A set of neurons working in parallel.

??? example "Learning rate"
    Parameter regulating the magnitude of the weights update.

??? example "Loss function"
    Function aimed at judging "how good" the network performs by comparing
    the prediction output to a "ground-truth" value. Throughout training,
    we visualise the loss function on both the training and validation
    sets in order to assess how well the training is going.

??? example "Neuron"
    A unit in the neural network. A neuron performs a simple calculation on
    inputs, usually by multiplying inputs by weights, adding an offset (bias)
    and applying a non-linear function (activation function) to the sum.

    Example:
    With input $x_1$ and $x_2$, a neuron would typically output:

    $out = f(x_1 * w_1 + x_2 * w_2 + b)$

    where $f$ is an [activation function](https://en.wikipedia.org/wiki/Activation_function#Table_of_activation_functions).

??? example "Patch size"
    In order to "fit" in the GPU memory, which is often the limiting factor,
    images need to be all cropped. What the network is trained on is a number
    of patches, i.e. image crops. These patches are all the same size and
    are aggregated in batches. A single batch is presented to the network during
    a single step of each epoch.

??? example "Prediction"
    Output of the network.

??? example "Test set"
    A set of images that the network never saw during training. It is important
    for these images never to be added to the training or the validation set.
    The test set is used to assess the performances of the network on unsee
    data, that is to say how well it generalizes to similar images.

??? example "Training"
    Training a network is the act of changing the weights of the neural
    network until its performances do not increase anymore. During training,
    at each step, a subset of the training images is presented to the network,
    the loss is computed between the predictions and the "ground-truth". Then,
    gradients are built from the value of the loss, and the weights of the
    network are updated accordingly. At the end of each epoch, the loss is
    computed on the validation set for reference.

??? example "Training epoch"
    An ensemble of training steps. At the end of each epoch, the validation
    loss is computed.

??? example "Training set"
    Ensemble of images the network is trained on.

??? example "Training step"
    An iteration of learning.

??? example "UNet"
    A specific model architecture popular in bioimage analysis.

??? example "Validation set"
    Ensemble of images used to assess the performances of the network during
    training. The validation set is not used to train the network, only to
    assess that the training is going well.

??? example "Weights"
    The parameters of a Model that define all the neural network node
    calculations.
