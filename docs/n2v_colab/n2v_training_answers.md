# N2V answers

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
