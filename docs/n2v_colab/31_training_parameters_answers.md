# 3.1 Answers

??? question "Number of images seen during training"
    Given the following parameters:

    - `batch_size = 16`
    - `number_of_steps = 200`
    - `number_of_epoches = 50`

    How many images are seen during training in total? (including duplicates,
    because images are seen multiple times)

    => `batch_size * number_of_steps * number_of_epoches = 160 000`

??? question "Default number of steps"
    What is the default value of the number of steps? And why?

    => The default value is the number of patches divided by the batch size. Recall that the batch size is the number of patches that are seen at each step. So, for all of the patches to be seen during one epoch, the of number of steps needs to be equal to the total number of patches divided by the batch size. In effect:

    steps = total patches / patches per step

??? question "Lots of steps or lots of epochs?"
    In the case of our specific implementation, given a constant
    `number_of_steps * number_of_epochs`. Is it better to train with
    to train with more steps or with more epochs?

    => It does not matter, the only thing that matters is the number of times
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

    => The training set is used to compute the gradients that are themselves
    used to update the weights of the network. The validation set is not used
    for training, but rather to evaluate how well the network is performing
    throughout training.

??? question "Initial learning rate"
    Why is the learning rate parameter called "initial" here? And why is this
    important?

    => The learning rate is scaling the value of the gradients used to
    update the weights of the network. If the learning rate is constant, the
    network might find itself jumping around an optimum (in the landscape of
    all the possible weights), without ever reaching it. It is therefore
    advantageous to reduce the learning rate while training is progressing.

    It is like hiking without following a trail: first we make large steps
    towards the mountain, then we try to make smaller steps to get towards the
    correct mountain pass, finally we try to follow small scale features to be
    able to get to the top.
