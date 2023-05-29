# Jupyter module

Now, we just need to load the `jupyter` module:

```console title="Load Jupyter module"
module load Jupyter-Notebook/6.4.3
```

Then, we want

And submit a job:

```console title="Submit GPU job"
srun --time=04:00:00 --job-name=<your.name> -p neubias --gres=gpu:1 --qos=gpu  jupyter-notebook --no-browser --ip='0.0.0.0'
```

You should now have a `jupyter` server running on a GPU node. Click on the link to connect to it!
