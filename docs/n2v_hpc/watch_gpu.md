---
tags:
  - help
---
# Watch GPU consumption

In this section, we demonstrate how to watch the GPU consumption of your
jupyter job on the compute node.

## Check the compute node

```bash title=""
squeue | grep <your-job-name>
```

You should see something like `maestro-####`, write down the `####` numbers.

## Connect to the compute node

Open a new terminal and ssh into the compute node

```bash
ssh m####
```

where `####` are the numbers from the previous section

## Watch GPU consumption

```bash
watch nvidia-smi
```
