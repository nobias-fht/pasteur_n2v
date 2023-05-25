# Questions

Here are a few questions you can try to answer for yourself when going
through the notebook. Don't hesitate to discuss it with the people around
you and with the TAs.

## 3.1 Setting main training parameters

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

## 3.2 Data augmentation

??? question "Data augmentation methods"
    What types of data augmentation is performed in this notebook?

??? question "Why data augmentation"
    Why is data augmentation helping the network to learn and generalize better?

??? question "Other types of data augmentations"
    Can you imagine other types of augmentations?

## 3.3 Using weights from a pre-trained model

??? question "Using pre-trained weights"
    Should you avoid using a pre-trained network that was trained on vastly
    different data that the one you want to train on?

??? question "Learning rate"
    The notebook states that "it is advisable to also load the learning rate
    that was used when the training ended". Why is that?

## 4.1 Prepare the training data and model

??? question "Number of masked pixels"
    How many pixels are masked per patches?

??? question "Configuration"
    The configuration is printed to the console on the notebook. Yes yes, it is
    the very long one-liner that starts with N2VConfig.

    Here are a few questions:

    1. What do you think "means" and "stds" are and what they are used for?
    2. What is the value of the UNet depth? And what is that?
    3. Can you find the loss name?

## 4.2 Start training

??? question "Learning rate"
    Now that we are training. How is the learning rate changing?

## 5.1 Inspection of the loss function

??? question "N2V "ground-truth""
    N2V is a very peculiar deep-learning algorithm. It is a so-called
    self-supervised method. What is used as "ground-truth" in N2V?

??? question "N2V loss"
    Given your answer to the previous question, how can we interpret the N2V
    loss function value?

??? question "Low number of validation"
    What could happen to the validation loss curve if you have too little
    validation examples?

## N2V, training and predicting

N2V is a bit different from traditional deep-learning algorithms. Here are
a few more questions to help grasp why.

??? question "Training on a single image"
    Can you train N2V on a single image?

??? question "N2V learning"
    What does N2V learn? (incidentally, that is not a philosophy question)

??? question "Predicting on different images"
    Can you predict images using a N2V network trained on different images?

??? question "Multichannel"
    Should you train a N2V model using different channels from the same
    experiment?

??? question "Deconvolution"
    Is N2V some sort of deconvolution?

??? question "Pre-processing"
    Here are two cases of pre-processing:

    My images come from the same experiment, but there was drift. So I used
    an alignment algorithm to minimize displacement between them.

    In an other type of experiment, I recorded very large images. To save them,
    we downsampled them before training N2V.

    Can you spot a problem when training N2V in either of these cases?

??? question "Structured noise"
    How can structured noise affect N2V performances?

## General deep-learning questions

??? question "Diverging training and validation loss"
    What is happening when the training loss becomes very small, while the
    validation loss does not change or even increases?
