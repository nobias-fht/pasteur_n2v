# Answers

Here are some element of answers to the questions of the previous section. Try
to spend some time thinking and discussing with others before looking up the
answer.

## 3.1 Setting main training parameters

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

    => The default value is the number of patches divided by the batch size. Recall that the batch size is the number of patches that are seen at each step. So, for all of the patches to be seen during one epoch, the of number of steps needs to be equal to the total numbert of patches divided by the batch size. In effect:

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

## 3.2 Data augmentation

??? question "Data augmentation methods"
    What types of data augmentation is performed in this notebook?

    => The augmentations are 90 degrees rotations and horizontal flip. This is
    fine with most biological images, because cells and other specimen do
    not have a preferred orientation. They can be upside down, rotated by 30
    degrees, etc...
    It is important that the augmentations correspond to something that happens
    to the objects in the image. For instance, you would not flip vertically
    landscape images because most likely the sky is never at the bottom of the
    image. You could, however, flip this image horizontally.

??? question "Why data augmentation"
    Why is data augmentation helping the network to learn and generalize better?

    => Simply by increasing the number of images and the diversity in the
    dataset.

??? question "Other types of data augmentations"
    Can you imagine other types of augmentations?

    => Actually there are plenty of different type of augmentations,
    depending on the problem at hand. You could think of stretching and scaling,
    changing pixel values, addiding different type of noise etc.
    The important thing is to make sure that these augmentations are not
    detrimental to what you are trying to learn, otherwise the network can
    hallucinate.

## 3.3 Using weights from a pre-trained model

??? question "Using pre-trained weights"
    Should you avoid using a pre-trained network that was trained on vastly
    different data that the one you want to train on?

    => Using a pre-trained network can be useful as this network might have
    learned to something well, possibly on a lot more data than you have. By
    re-training the model, also called fine-tuning, you want to make sure
    than the model is trained to perform well on your type of data.

??? question "Learning rate"
    The notebook states that "it is advisable to also load the learning rate
    that was used when the training ended". Why is that?

    => If you are training on the same images, or on very similar images, then
    part of the training as already been done. By fine-tuning starting with the
    initial learning rate, the network might take longer to converge.

## 4.1 Prepare the training data and model

??? question "Number of masked pixels"
    How many pixels are masked per patches?

    => It depends on the patch size, but the configuration method has a
    parameter called `n2v_perc_pix` which by default is equal to 0.198%.
    With a patch size of 64 pixels, that leads to:
    $64^2 * 0.2 / 100 = 8$ pixels.

??? question "Training dataset dimensions"
    What are the dimensions of the training set? What is the last dimension?

    => Default is (512, 64, 64, 1). The channel dimension is at the end. If your
    images are multichannel, they should end up there. But careful! The channel
    dimension is necessary due to the netwrok architecture. If you have multiple
    channels, they will be aggregated and the network will learn noise model
    and image features from both channels together. That is usually not a good
    idea.
    The reason to have the channel dimension as is, is to be compatible with
    RGB images.

??? question "Configuration"
    The configuration is printed to the console on the notebook. Yes yes, it is
    the very long one-liner that starts with N2VConfig.

    Here are a few questions:

    1. What do you think "means" and "stds" are and what they are used for?
    2. What is the value of the UNet depth? And what is that?
    3. Can you find the loss name?

    => Here are the answers:

    1. The `means` and `stds` deviation are the means and standard deviations of
    the training dataset pixel values. They are used to normalize the patches.
    this allows to have pixel values in similar ranges across patches, leading
    to more stable training.
    2. The UNet depth is 2 by default. This is the number of downsampling and
    upsampling that the UNet performs.
    3. The loss is `mse`, which stands for `mean square error`.

## 4.2 Start training

??? question "Learning rate"
    Now that we are training. How is the learning rate changing?

    => Every now and then, at the end of an epoch, the learning rate is halved
    after 10 epochs without improvemnt in loss.

## 5.1 Inspection of the loss function

??? question "N2V "ground-truth""
    N2V is a very peculiar deep-learning algorithm. It is a so-called
    self-supervised method. What is used as "ground-truth" in N2V?

    => The "ground-truth" is the actual pixel value of the noisy pixels that
    are masked during training.

??? question "N2V loss"
    Given your answer to the previous question, how can we interpret the N2V
    loss function value?

    => The loss function is the difference between the predicted pixel values
    and the original masked pixel values. Therefore, the loss will never
    go to 0 (unless the network is learning to the identity function, which
    by design it cannot in N2V). There must be a difference between the
    prediction and the original value, but its absolute value is meaningless.

??? question "Low number of validation"
    What could happen to the validation loss curve if you have too little
    validation examples?

    => It could fluctuate massively if you have too little validation data.
    That's why the minimum of validation data in the notebook is 10% of the
    total amount of data.

## N2V, training and predicting

N2V is a bit different from traditional deep-learning algorithms. Here are
a few more questions to help grasp why.

??? question "Training on a single image"
    Can you train N2V on a single image?

    => You absolutely can.
    TODO add more explanation

??? question "N2V learning"
    What does N2V learn? (incidentally, that is not a philosophy question)

    => N2V learns the noise model of the image, that is what amount of
    pixel noise to expect for certain "true" values. But that's not all,
    it also learns features of the images. Therefore it is important to
    TODO: what if diversity in the dataset?

??? question "Predicting on different images"
    Can you predict images using a N2V network trained on different images?

    => Yes, but only if the image has been acquired similarly to the training
    data, that it contains similar feature and that the noise is similar.

    In the end, N2V is easy to train. It is therefore easier to retrain a
    network on a new image.

??? question "Multichannel"
    Should you train a N2V model using different channels from the same
    experiment?

    => This is not advisable as different channels will have different noise
    model and different features. Best is to train a N2V model per channel.

??? question "Deconvolution"
    Is N2V some sort of deconvolution?

    => Absolutely not! Deconvolution uses an approximation of the PSF to
    estimate the image without the effect of diffraction. N2V only estimates
    the amount of per pixel noise.

??? question "Pre-processing"
    Here are two cases of pre-processing:

    My images come from the same experiment, but there was drift. So I used
    an alignment algorithm to minimize displacement between them.

    In an other type of experiment, I recorded very large images. To save them,
    we downsampled them before training N2V.

    Can you spot a problem when training N2V in either of these cases?

    => Anything that messes around with the amount of per pixel noise, and
    introduce correlation, will cause N2V underlying hypothesis to be violated.

    Both alignment and downsampling can potentially mix up pixel values between
    neighboring pixels. Alignment by translating an image in X and Y by an
    integer number of pixels is fine, as the per pixel noise is unchanged.

??? question "Structured noise"
    How can structured noise affect N2V performances?

    => Structured noise is noise correlated across pixels. This violates the
    main N2V assumption. Other algorithms have been designed to tackle
    structured noise, such as structN2V and HDN.

## General deep-learning questions

This is a general question about deep-learning and should not be thought as
being related to N2V.

??? question "Diverging training and validation loss"
    What is happening when the training loss becomes very small, while the
    validation loss does not change or even increases?

    => If the training loss becomes very small, that means that the network is
    learning to predict on the training dataset very well. But if at the same
    time the validation loss does not decrease, or even worse incrases, that
    means that the network is performing worse on the validation data.

    It is called overfitting, and it means that your network will not generalize
    well!
