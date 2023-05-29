---
tags:
  - deep-learning
  - help
---

# What is a neural network?

## Architecture

A neural network is a network of connected nodes. These nodes, the neurons, are
arranged in layers. Each node performs a calculation by applying a linear
scaling to its inputs. This linear scaling is determined by the weights of the
neuron. Finally, the output of the neurons are passed to a non-linear function,
the activation function.

<p align="center">
    <img src="https://github.com/nobias-fht/restoration/blob/main/docs/images/neural_network.png?raw=true">
</p>-

Why are such networks so powerful? Because they can approximate very complex
functions!

??? question "Why are the activation functions "non-linear"?"
    If the activation functions were linear, then the whole network could
    be simplified as a linear equation. Then, the only thing it could learn
    would be a linear interpolation!

    Non-linear functions introduce complexity.

In bioimage analysis, the [UNet](https://lmb.informatik.uni-freiburg.de/people/ronneber/u-net/)
is the most popular architecture. The layers are organised in several levels,
in between which the size of the layers are downsampled or upsampled,
depending on the level.

The UNet architecture is based on convolutional layers, which learn many
filters applied to the layer input. That makes UNets perfect for image
analysis!

UNets are relatively simple, yet they are powerful and do not need much data
to train, at least compared to more complex networks.

## Training

!!!Note
    Refer to the [Lexicon](https://nobias-fht.github.io/pasteur_n2v/how-to/lexicon/)
    when you have a doubt about the meaning of something!
