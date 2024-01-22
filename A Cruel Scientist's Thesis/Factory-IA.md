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
cd scripts/factoryiademo/
rsync -e ssh -rav . jsoria@visu01:~/factoryiademo/
```

Depuis Factory-IA
```bash 
rsync -e ssh -rav jsoria@visu01:~/factoryiademo/ .
```
