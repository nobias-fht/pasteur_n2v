# Conda environment

## Set-up the environment

```console title="Environment"
conda create --name care python=3.7
conda activate care
conda install -c conda-forge cudatoolkit=11.3 cudnn jupyter tensorboard nb_conda
pip install tensorflow==2.5 csbdeep
```

## Download the notebooks

```console title="Clone the repository"
git clone https://github.com/CSBDeep/CSBDeep.git
```

## Start job

TODO
