***Julien Girard-Satabin,** Michele Alberti, François Bobo, Zakaria Chihani


Difficultés récentes:
* robustesse locale
* propriétés fonctionnelles
* respect de la vie privée
* équité

Spécialisations:
1. Par propriétés: *difficultés mentionnées en haut*
2. Par technique: SMT, programmation par contrainte

#### Why3
Modélisation unifiée (`WhyML`), parser, générateur d'obligation de preuves, $\dots$

#### CAISAR
Programmes sous différents formats (ONNX, NNnet, OVO)

##### ACAS
* 5 entrées: $\rho, \theta, \phi, v_{own}, v_{int}$
* 5 sorties: COC, SL, SR, WL, WR

$\phi_3$ : "Si l'intrus est juste devant l'appareil, Clear-Of-Conflict ne doit pas avoir le score maximal"

##### Spécification
```
theory ...
	predicate ...
[...]
constant nn
predicate 
	forall
goal 
	forall
end
```

#### Additions
1. gestion des ensembles d'apprentissage, propriétés non "réellement" universelles
2. support de huit "prouveurs" dédiés : SMT ; interprétation abstraite, test métamorphique
3. traducteur du flot de contrôle du programme (réseaux de neurones, SVM, arbres) vers une représentation intermédiaire et du SMTLIB "classique"
4. moteur d'interprétation pour faciliter la décharge de preuve aux prouveurs

#### Travaux en cours
1. sémantique de preuves différentes
2. granularité dans les tactiques
3. propagation des résultats de vérification d'un programme vers un autre
4. explications de décisions
5. spécifier (et prouver) les données

Site web : https://caisar-platform.com/
Rapport technique: https://hal.science/hal-XXXXX


