Paper: https://prl-theworkshop.github.io/prl2021/papers/PRL2021_paper_7.pdf

## Contexte
- Trouver quelles actions effectuer pour maximiser ses récompenses (dans un environnement)
- Hypothèse 1: On dispose d'un modèle qui décrit l'ensemble des états et les effets des actions
	- Note: les effets sont non-déterministes
- Une solution au problème de planification est une **politique**, i.e., une fonction *état -> action*
- Hypothèse 2: le modèle est trop grand pour calculer une politique explicite
	- On utilise des politiques représentées par des réseaux de neurones
- Problème: comment s'assurer que la politique ne va pas provoquer une catastrophe !?

## Le modèle
Tuple *<V,L,O>*
- *V*: ensemble des variables d'états
- _L_: ensemble de labels/étiquettes (actions)
- _O_: ensemble des opérateurs

Un opérateur O est un tuple *<g,l,u>*
- *g* est une condition sur l'état (combinaison de contraintes linéaires sur V)
- *l* est l'action
- *u* est une fonction _update_

Condition initiale $\phi_0$
Condition de sûreté $\phi_u$
Politique: $\pi$: état -> label

Question: si on applique $\pi$ depuis un état $s^0 \models \phi_0$ peut-on atteindre un état non sûr _l_ dangereux $s^u \models \phi_u$ ?

### Vérifier l'atteignabilité grâce à l'abstraction

### Traduction SMT