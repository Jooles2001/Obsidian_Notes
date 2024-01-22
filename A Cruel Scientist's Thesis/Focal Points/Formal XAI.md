*Julien Girard-Satabin*
*CEA Nano-Innov*

#### Goal
- Some (recent) papers on formal xAI
- Some interesting research directions ++
***

#### State-Of-The-Art
- Delivering trustworthy AI through formal XAI
- Deep explainable relational reinforcemen learning: a neuro-symbolic approach
- Abstract interpretation-based feature importance for SVMs
- Towards Formal XAI
- ...
- ...
- High-Precision Model-Agnostic (Anchor LIME)

***
##### Framework
Given a network $f: \mathcal{X} \rightarrow \mathcal{Y}$ 

***
##### Feature Removal

Attribution by feature removal: if we remove an important feature, prediction will change.

$\star$ $\star$ $\star$ 
With a $k$-Lipschitz network, variation on the explanation will be upper-bounded by $k$ (for variation on $x$)

Naive Approach:
Iterate through : assign random value to a feature of a sample, check if the prediction changes, and if yes, the feature is important, else it is irrelevant
* Prone to out-of-distribution assignment influencing the altered prediction


Slightly less naive approach:
Iterate through : assign random value to a feature of a sample, check if the prediction change is SAT, and if yes, the feature is important, else it is irrelevant
--> the set of relevant features is the explanation

##### VeriX
Heuristics to sort the features by their relevance + robustness queries
--> If the explanation is robust to variations then it is a good explanation (?)

###### Overapproximations
Partition input's features into bundles

###### A bridge between post-hoc explainability and inherent interpretability
Guaranteed model distillation from black-box to white-box model


### Fidelity of the Explanation
How can we use formal methods to ensure that the explanation translates properly the "actual" behaviour of the model ?
--> Partially "solved" by feature removal and formal verification
Robust explanations ?

### Validity Domain of the Explanation
Given an explanation for a prediction ($x,y,f$), how is it sensitive to variations on $x,y,f$ ?
Guarantees for a $k$-Lipschitz NN, but not enough for characterising small variations (advexs)
##### Sub-problem: Contestability
Given an explanation for a prediction ($x,y,f$), what would be the minimal variation of ($x,y,f$) such that the minimal variation of ($x,y,f$) such that the prediction would go the "good" way ?


### Scalability of the Explanation
--> Image classification

$\vdots$
$\vdots$

***
# Théorie des Observations Critiques
*Alban Grastien*

A quoi/qui servent les explication ?
Différents publics --> différents types d'explications

Propriétés des explications:
*sous-entendu: propriétés qu'elles devraient avoir, et qui sont parfois oubliées par les chercheurs et développeurs
* Monotonicité
* Il ne devrait pas exister une explication qui prouve le contraire de la sortie de l'algorithme
	* LIME peut donner la même explication pour un refus ET une acceptation de prêt


### Diagnostic à base de modèle
Identifier l'ensemble minimal de candidats pour expliquer la situation

### Hypothèse de Travail
Une explication est une abstraction des observations qui permet d'inférer le diagnostic (minimal)







