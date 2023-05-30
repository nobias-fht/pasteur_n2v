# Data and notebooks

Then, we want to get the data and the notebooks. Here, we've already downloaded
some data for you, which you can find
in `/pasteur/appa/scratch/neubias/n2v/exercise/data`.

Simply copy the `exercise` folder to your folder, using the following command:

```bash title="Copying the exercises"
cp -r /pasteur/appa/scratch/neubias/n2v/exercise n2v_exercise
```

!!!Note
    Instead of the SEM data, you could use your own data. Copy your data in
    the `exercise/data` folder instead of the tiff files. You will need to
    adapt the notebook to make sure that the data is correctly loaded and the
    array shape fitting the network expectations.

    Note that the notebook expects tiff images to be in the `data` folder.
