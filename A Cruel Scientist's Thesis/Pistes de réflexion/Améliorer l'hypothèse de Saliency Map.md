On se base sur le travail de [[On the stability, correctness and plausibility of visual explanation methods based on feature importance]]

Rappel: on a l'équation suivante
$$\forall X\in \mathcal{X}, E_{X_0}(X) = s(X_0)^T (X-X_0) + g(X_0) \in \mathbb{R}$$
Et le but est d'évaluer les différentes manières de produire $s(.)$ la fonction de _saliency map_

Hypothèse: $s(X_0) \approx \frac{dg}{dx}(X_0)$
Sauf que: par construction (et empiriquement), ce n'est pas le cas
Contre-exemple: une méthode qui normalise les gradients dans $[-1, 1]$

Potentielle nouvelle hypothèse: $s(X_0)=\lambda \otimes \frac{dg}{dx}(X_0) + \mu$     avec $\lambda, \mu \in \mathbb{R}^D$
> On pourrait considérer à un moment que $\mu = 0$ si nécessaire

On suppose avoir $X_0, X_1$
On sample $\tilde{X}_i^{(k)}$ tels que $\|\tilde{X}_i^{(k)} - X_i\|\leq\epsilon, \quad i\in \textlbrackdbl 0,1\textrbrackdbl$
On a alors,
$$
\frac{dg}{dx}(X_i) \approx \sum_{k=1}^N \frac{g(X_i) - g(\tilde{X}_i^{(k)})}{X_i - \tilde{X}_i^{(k)}} = \Delta_i
$$

Puis
$$s(X_0) = \lambda \otimes \Delta_0 + \mu$$
$$s(X_1) = \lambda \otimes \Delta_1 + \mu$$
$$\lambda = \frac{s(X_0)-s(X_1)}{X_0-X_1}$$
$$\mu=s(X_0) - \lambda\otimes\Delta_0$$


> Note: idée à développer

