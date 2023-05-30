---
tags:
  - deep-learning
  - answers
---
# 3.3 Answers

??? question "Using pre-trained weights"
    Should you avoid using a pre-trained network that was trained on vastly
    different data that the one you want to train on?

    :right_arrow: Using a pre-trained network can be useful as this network might have
    learned something well, possibly on a lot more data than you have. By
    re-training the model, also called fine-tuning, you want to make sure
    than the model is trained to perform well on your type of data.

??? question "Learning rate"
    The notebook states that "it is advisable to also load the learning rate
    that was used when the training ended". Why is that?

    :right_arrow: If you are training on the same images, or on very similar images, then
    part of the training as already been done. By fine-tuning, starting with the
    initial learning rate, the network might take longer to converge.

    Why go all the way back to the parking lot while you are already close to
    the mountain top? :mountain:
