# N2V, training and predicting

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
