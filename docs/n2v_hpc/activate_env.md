# Conda environment

The first step is to activate the correct environment. Create the following script in your folder:

```console title="activate_n2v.sh"
#!/bin/bash

source /pasteur/appa/scratch/neubias/n2v/miniconda3/bin/conda activate n2v

python -m ipykernel install --user --name=n2v
conda deactivate
```
