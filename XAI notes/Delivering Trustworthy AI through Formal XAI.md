*Joao Marques-Silva, Alexey Ignatiev*

#### Current problems with explanations
* The same explanation $X$ can be given to justify the prediction $c_1$ for sample $s_1$ and (a different) prediction $c_2$ for sample $s_2$
* Explanations can be too long , complicated and unnecessarily conservative
==> [[Formal XAI]] to (partially) solve these issues

Non-formal explanations require to analyze the training data (impractical), and which may not faithfully represent the input distribution (data/concept drift may be observed)

# Formal Explanations
## Defining them
### Answer "Why?" questions
+ We want the subset of features to be minimal, and such that, regardless of the values of the features not in the subset, the prediction will not change for values of the features in the subset (Occam's Razor). --> Abductive explanations (AXp)
+ *weak* AXp if subset chosen is not necessarily minimal ==> $\mathcal{F}$ is always *weak* AXp
### Answer "Why Not?" questions
>we want to find a subset of features which,  if allowed to take some other value, and when the remaining features remain unchanged given their values in **v**, then the prediction can be changed to a class other than $c$.
+ We want a subset of features that, if all others are fixed, can take another value to change the prediction --> Contrastive explanation (CXp)
+ If not necessarily CXp then _weak_ CXp ==> $\mathcal{F}$ is always *weak* CXp
### Duality of explanations
+ ==For an instance (**v**, *c*), the AXp’s are (subset-)minimal hitting sets of the CXp’s and vice-versa.==
+ AXp's can be defined _globally_ (how?)
+ AXp's are also linked with counterexamples (CEx's) --> link between explanations and adversarial examples.

## Computing Formal Explanations
+ Start with $\mathcal{S} := \mathcal{F}$
+ Iteratively try for all $i \in \mathcal{F}$ if the property $\mathbb{P}$ holds, if yes then $\mathcal{S} := \mathcal{S} \setminus \{i\}$
+ Return $\mathcal{S}$

### Tractable Explanations
AXp computation can be done in ==polynomial== time for:
+ Naive Bayes Classifier
+ Decision Trees  -->  
	+ paths that are arbitrarily large (which the explanation shortens for succintness)
	+ dependent on the number of tree nodes
	+ can also find CXp's
	+ feature _membership_ in explanations computed
+ d-DNNF ?
+ GDF (non-overlapping boolean functions)

Work in progress on **Approximate Explanations** by relaxing the requirements (allows the property to _not_ hold for some points of the feature space)
Feature membership in explanations (is _gender_ used in the decision process ?)
Enumeration of explanations

## Challenges
+ Scalability issues (especially with neural networks and bayesian networks)
	+ Automated reasoners to ease the process
+ Size of explanation can be too large
+ Constraining the feature space
+ [[Formal XAI]] beyond classification problems


Non-formal XAI not reliable in _high-risk situations_
