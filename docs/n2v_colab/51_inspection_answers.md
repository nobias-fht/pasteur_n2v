---
tags:
  - deep-learning
  - answers
---
# 5.1 Answers

??? question "N2V "ground-truth""
    N2V is a very peculiar deep-learning algorithm. It is a so-called
    self-supervised method. What is used as "ground-truth" in N2V?

    :right_arrow: The "ground-truth" is the actual pixel value of the noisy pixels that
    are masked during training.

??? question "N2V loss"
    Given your answer to the previous question, how can we interpret the N2V
    loss function value?

    :right_arrow: The loss function is the difference between the predicted pixel values
    and the original masked pixel values. Therefore, the loss will never
    go to 0 (unless the network is learning the identity function, which
    by design it cannot here). There must be a difference between the
    prediction and the original value, but its absolute value is meaningless.

??? question "Low number of validation"
    What could happen to the validation loss curve if you have too little
    validation examples?

    :right_arrow: It could fluctuate massively if you have too little validation data.
    That's why the minimum of validation data in the notebook is 10% of the
    total amount of data.
