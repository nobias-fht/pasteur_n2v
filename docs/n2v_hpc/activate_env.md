# Conda environment

## HPC

Connect to the Pasteur HPC. :desktop_computer:

## N2V environment

The first step is to activate the correct environment. Run the following
commands:

```bash title="Activate environment"
source /pasteur/appa/scratch/neubias/n2v/miniconda3/bin/activate
conda activate n2v

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CONDA_PREFIX/lib/ # (1)!

python -m ipykernel install --user --name=n2v
conda deactivate
```

1. This is important to tell TensorFlow how to use cuda, i.e. the GPU! :fire:
