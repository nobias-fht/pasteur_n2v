---
tags:
  - deep-learning
  - answers
---
# N2V answers

N2V is a bit different from traditional deep-learning algorithms. Here are
a few more questions to help grasp why.

??? question "Training on a single image"
    Can you train N2V on a single image?

    :right_arrow: You absolutely can. Remember that N2V is not trained using
    actual ground-truth, therefore we did not bias the algorithm towards a
    certain result.

    You can train a network for each image, if you are worried that your images
    have different SNR.

??? question "N2V learning"
    What does N2V learn?

    Incidentally, that is not a philosophy question. :classical_building:

    :right_arrow: N2V learns the noise model of the image, that is to say
    the amount of pixel noise to expect for certain "true" values. It uses this
    representation to estimate the "true" values of the pixels.

    :warning: But that's not all, it also learns features of the images.
    Therefore it is important to not train on certain structures and predict
    on vastly different images.

    In segmentation task, it is easy to tell when a network "hallucinates". :rainbow:
    Because our brain is really good at telling that the segmentation is not
    perfect. But it is very hard with noise and image restoration. Therefore,
    always question the structures in the images. Repeat the experiments with
    different images and different trained networks as a control.

    [DivNoising](https://github.com/juglab/DivNoising) and
    [HDN](https://github.com/juglab/HDN) are algorithms that help refine our
    understanding of the uncertainty in the network.

??? question "Predicting on different images"
    Can you predict images using a N2V network trained on different images?

    :right_arrow: Yes, but only if the image has been acquired similarly to the
    training data. It must contains similar features and have similar SNR.

    In the end, N2V is easy to train. It is therefore easier to retrain a
    network on a new image.

??? question "Multichannel"
    Should you train a N2V model using different channels (different structures)
    from the same experiment?

    :right_arrow: This is not advisable as different channels will have
    different noise model and features. Best is to train a N2V model per channel.

??? question "Deconvolution"
    Is N2V some sort of deconvolution?

    :right_arrow: Absolutely not! Deconvolution uses an approximation of the PSF
    to estimate the image without the effect of diffraction. N2V only estimates
    the amount of per pixel noise.

??? question "Pre-processing"
    Here are two cases of pre-processing:

    My images come from the same experiment, but there was drift. So I used
    an alignment algorithm to minimize displacement between them before training.

    In an other type of experiment, I recorded very large images. To save them,
    we downsampled them before training N2V.

    Can you spot a problem when training N2V in either of these cases?

    :right_arrow: Anything that messes around with the amount of per pixel noise,
    and introduce correlations between pixels, will cause N2V underlying
    hypothesis to be violated. :broken_heart:

    Both alignment and downsampling can potentially mix up pixel values between
    neighboring pixels. Alignment by translating an image in X and Y by an
    integer number of pixels is fine, as the per pixel noise is unchanged.

??? question "Structured noise"
    How can structured noise affect N2V performances?

    :right_arrow: Structured noise is noise correlated across pixels. This
    violates the main N2V assumption. Other algorithms have been designed to
    tackle structured noise, such as structN2V (available in the same library
    than N2V) and [HDN](https://github.com/juglab/HDN).
