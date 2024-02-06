*Michele Alberti*
Paper: https://arxiv.org/pdf/2203.00938.pdf

Neuro-symbolic AI: 
> This is often done in a hybrid fashion where a neural network acts as a perception module that interfaces with a symbolic reasoning system

Property definitions of:
- fairness
- adversarial robustness

Défauts dans la recherche sur la vérification:
- propriétés simples
	- propriétés intéressantes qui ne peuvent pas être exprimées correctement
- propriétés locales ou globales uniquement
	- ce qui nous intéresse c'est le comportement sur les données dans la distribution (pas OoD)
- les contre-exemples sont souvent out-of-distribution (et donc peu de valeur)

Idée fondamentale
-> utiliser réseaux de neurones (_specification networks_) pour capturer les propriétés de _correctness_
-> proposer un langage NeSAL