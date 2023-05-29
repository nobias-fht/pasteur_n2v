# 3.2 Answers

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
