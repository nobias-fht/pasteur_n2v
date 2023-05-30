---
tags:
  - deep-learning
  - answers
---
# General answer

??? question "Diverging training and validation losses"
    What is happening when the training loss becomes very small, while the
    validation loss does not change or even increases?

    :right_arrow: If the training loss becomes very small, that means that the network is
    learning to predict on the training dataset very well. But if at the same
    time the validation loss does not decrease, or even worse incrases, that
    means that the network is performing worse on the validation data.

    It is called overfitting, and it means that your network will not generalize
    well!
