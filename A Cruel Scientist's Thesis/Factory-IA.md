# Launching CaBRNet Experiments
[[CaBRNet - TODO]]
##### MNIST
```bash
protolib --device cuda:0 --verbose explain_global --model-config runs/test_prototree_mnist/best/model.yml --model-state-dict runs/test_prototree_mnist/best/model_state.pth --output-dir runs/test_prototree_mnist/explanations --prototype-dir runs/test_prototree_mnist/prototypes/
```

##### StanfordCars
```bash
protolib --device cpu --seed 42 --logger-level DEBUG train --model-config configs/prototree/stanford_cars/model.yml --dataset configs/prototree/stanford_cars/data.yml --training configs/prototree/stanford_cars/training.yml --training-dir logs/
```

##### Cub200
```bash
protolib --device cpu --seed 42 --logger-level DEBUG train --model-config configs/prototree/cub200/model.yml --dataset configs/prototree/cub200/data.yml --training configs/prototree/cub200/training.yml --training-dir logs/
```


# Install

install mamba first !!
```bash
mamba env create -n factory -f factory.yaml
mamba activate factory
mamba env remove -n factory
mamba create -n factory python=3.11
```
> lorsque l'on crée un environnement à partir d'un fichier: `mamba env create`
> lorsque l'on crée un environnement vierge: `mamba create`

## Copy elements

Depuis mon ordinateur jusqu'au serveur
```bash
cd /localfolderpath/
rsync -e ssh -rav . jsoria@visu01:~/folderpath/
```

Depuis Factory-IA
```bash 
rsync -e ssh -rav jsoria@visu01:~/folderpath/ .
```

## Run slurm
```bash
sbatch xxxxx.slurm
```

see my jobs
```bash
squeue --me
```

follow the logs live
```bash
tail -f -n {a number} {filepath}
```

use _sprofile_
```bash
pip install py-spy sprofile
```

# Template

```shell
#!/usr/bin/env bash

# Specify resource requirements
#SBATCH --time=1:12:00
#SBATCH --partition=classicgpu
#SBATCH --nodes=1
#SBATCH --ntasks-per-node=1
#SBATCH --cpus-per-task=7
#SBATCH --mem=8G
#SBATCH --gres=gpu:1

# Start recording consumed resources 
srun sprofile start

# Do experiment
mamba activate factory

echo “CUDA devices: $CUDA_VISIBLE_DEVICES”
echo “Starting...”

# srun python train.py
srun protolib --device cpu --seed 42 --logger-level DEBUG train --model-config configs/prototree/cub200/model.yml --dataset configs/prototree/cub200/data.yml --training configs/prototree/cub200/training.yml --training-dir logs/
mamba deactivate
# Print consumed resources
srun sprofile stop

```


# Future work
use `simple_slurm` instead to use a  `Python`  script rather than `shell` 

# Follow scripts

```bash
sshfs {source_folder(distant one)} {target_folder(my computer)} 
```

# Elegant rsync

```bash
#!/bin/bash
rsync -e ssh -rav --exclude-from=.gitignore {source_folder} {target_folder}
```

```bash
#!/bin/bash
rsync -e ssh -rav . jsoria@visu01:dev/cabrnet --exclude=".*" --exclude-from=.gitignore
```