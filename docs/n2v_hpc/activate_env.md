# Conda environment

The first step is to activate the correct environment. Run the following
commands:

```console title="Activate environment"
source /pasteur/appa/scratch/neubias/n2v/miniconda3/bin/activate
conda activate n2v

python -m ipykernel install --user --name=n2v
conda deactivate
```
