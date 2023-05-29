# 4.1 Answers

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
    dimension is necessary due to the network architecture. If you have multiple
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
