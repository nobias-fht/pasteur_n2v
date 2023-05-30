---
tags:
  - deep-learning
  - answers
---

# 3.1 Answers

??? question "Number of images seen during training"
    Given the following parameters:

    - `batch_size = 16`
    - `number_of_steps = 200`
    - `number_of_epoches = 50`

    How many images are seen during training in total? (including duplicates,
    because images are seen multiple times)

    :right_arrow: `batch_size * number_of_steps * number_of_epoches = 160 000`

??? question "Default number of steps"
    What is the default value of the number of steps? And why?

    :right_arrow: The default value is the number of patches divided by the batch size.
    Recall that the batch size is the number of patches that are seen at each
    step. So, for all of the patches to be seen during one epoch, the number
    of steps needs to be equal to the total number of patches divided by the
    batch size.

    In effect:

    steps = total patches / patches per step

??? question "Lots of steps or lots of epochs?"
    In the case of our specific implementation, given a constant
    `number_of_steps * number_of_epochs`.  Is it better
    to train with more steps or with more epochs?

    :right_arrow: It does not matter, the only thing that matters is the number of times
    the whole dataset has been shown to the network. The number of steps
    determines how much of the whole dataset is seen during each epoch. The
    number of epochs gives us timepoints at which to examine the performances.
    In general, the community prefers to have a number of steps corresponding
    to the whole dataset being seen during an epoch. This makes the loss curve
    easier to interpret.

??? question "Ratio between training and validation"
    Some of the patches are used as validation set, while others are used
    in the training set.

    What is the difference between training and
    validation set? And how much data should you use in the validation set?

    :right_arrow: The training set is used to compute the gradients that are themselves
    used to update the weights of the network. The validation set is not used
    for training, but rather to evaluate how well the network is performing
    throughout training.

    We actively train the network to perform well on the training set, so we
    cannot trust the performances on the training images to judge how well
    the network is doing!

    On a side note, we use the validation set to assess when training is done.
    That means that the validation set can also NOT be used to judge how the
    network performs objectivaly. Why? Well we stopped training when it was
    doing well on the validation set.

    That's why we also need a test set: images that were never used during
    training, neither as training nor as validation data. In general, only
    report performance values on the test set.

    Now, N2V is special because the data is actually the pixels, not the the
    whole image and the loss actually doesn't mean much in terms of actual
    performance.

??? question "Initial learning rate"
    Why is the learning rate parameter called "initial" here? And why is this
    important?

    :right_arrow: The learning rate is scaling the value of the gradients used to
    update the weights of the network. If the learning rate is constant, the
    network might find itself jumping around an optimum (in the landscape of
    all the possible weights), without ever reaching it. It is therefore
    advantageous to reduce the learning rate while training is progressing.

    It is like hiking without following a trail: first we make large steps
    towards the mountain, then we try to make smaller steps to get towards the
    correct mountain pass, finally we try to follow small scale features to be
    able to get to the top. :mountain:
