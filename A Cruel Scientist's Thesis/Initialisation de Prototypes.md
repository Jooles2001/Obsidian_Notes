- Greedy initialization: 
	- On prend tous les candidats (i.e., tous les vecteurs latents d'une classe) du set de projection, et on choisit itérativement le meilleur
	- On peut aussi refaire cette étape _pendant_ l'entraînement (à chaque projection)
	- Possible extension avec du beam search
- K-Means clustering avec/sans contraintes sur le nombre de vecteurs d'une image dans un cluster donné
	- à vérifier ?
- Initialiser avec des candidats aléatoires est **pire** qu'avec des vecteurs aléatoires
	- pourquoi ? --> difficile de se sortir d'un _local minimum_ 
	- investigation:
		- avec la même init, faire une hyper-parameter search ? (BO ou grid search)
		- tester avec plusieurs init et comparer les hyper-paramètres donnés ?
- Quid d'initialiser avec des candidats qui correspondent à des pixels qui font partie de la segmentation (quand elle existe) ?
	- assez coûteux en pratique...
- Réutiliser des prototypes (sous format $(i,h,w)$ plutôt qu'en format vectoriel) trouvés par un autre `ProtoPNet`
- Tester sur d'autres datasets ?

#### Cas actuel
- Un backbone: VGG19
	- plus deux add-ons layers random init
- Vérifier la transférabilité entre les prototypes trouvés pour deux modèles différents, possiblement avec des architectures différentes

- Faire un premier entraînement sur une architecture faible mais efficace, afin d'obtenir un bon set de prototypes à réutiliser dans l'entraînement d'architectures plus massives. 
--> proche des concepts de teacher-learner (Knowledge Distillation)

>[!tip]
>always verify gradients flow

