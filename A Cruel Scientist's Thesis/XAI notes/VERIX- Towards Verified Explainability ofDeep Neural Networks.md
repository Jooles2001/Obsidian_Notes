https://arxiv.org/pdf/2212.01051.pdf

### Optimal robust explanations
Find input space $A$ such that, when perturbing $B = \Theta(X) \setminus A$, the prediction of the new samples is close to the prediction of $x$

Formula in the paper:
$$
\forall x^{B'}. \|x^B - x^{B'}\| \leq \epsilon \Rightarrow \| f(x) - f(x') \| \leq \delta
$$
Here, $x^B$ refers to the _irrelevant_ features
Then, is defined an _optimal_ explanation $x^A$ such that, for any perturbation $x^{A'}$, the prediction is out of bounds (greater than $\delta$ )
- $x^A$ is $\epsilon$-robust if _no_ feature is relevant (can move the decision)
- $A = \Theta(X)$ if any perturbation changes the decision
### Counterfactuals along decision boundary

During the process of producing an explanation, the equivalent of _counterfactuals_ are produced: minor perturbations to the _irrelevant features_ ($x^{B'}$) along with _one_ change in the set of features $x^A$ induces a difference in prediction.

