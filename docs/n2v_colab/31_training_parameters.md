# 3.1 Training parameters

Section 3.1.

??? question "Number of images seen during training"
    Given the following parameters:

    - `batch_size = 128`
    - `number_of_steps = 100`
    - `number_of_epoches = 200`

    How many images are seen during training in total? (including duplicates,
    because images are seen multiple times)

??? question "Default number of steps"
    What is the default value of the number of steps? And why?

??? question "Lots of steps or lots of epochs?"
    In the case of our specific implementation, given a constant
    `number_of_steps * number_of_epochs`. Is it better to train with
    to train with more steps or with more epochs?

??? question "Ratio between training and validation"
    Some of the patches are used as validation set, while others are used
    in the training set.

    What is the difference between training and
    validation set? And how much data should you use in the validation set?

??? question "Initial learning rate"
    Why is the learning rate parameter called "initial" here? And why is this
    important?
