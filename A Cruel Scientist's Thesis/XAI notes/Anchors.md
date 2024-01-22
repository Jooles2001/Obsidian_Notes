Blog: https://medium.com/swlh/ultimate-guide-to-model-explainability-anchors-2deab8239f57
Paper: https://dl.acm.org/doi/pdf/10.5555/3504035.3504222
Molnar: https://christophm.github.io/interpretable-ml-book/anchors.html

### Anchors
$A$ is a set of predicates
$A(x)$ returns $1$ if all its feature predicates are `true` for instance $x$. 
$\mathcal{D}(.|A)$ denotes the conditional distribution when the rule $A$ applies.
$A$ is an _anchor_ if $A(x)=1$ and $A$ is a sufficient condition for $f(x)$ with high probability 
> How is a "high" probability determined ?

Formally, $A$ is an anchor if,
$$
\mathbb{E}_{\mathcal{D}(z|A)}[\mathbb{1}_{f(x)=f(z)}] \ge \tau, A(x)=1
$$
Where we define prec($A$) $= \mathbb{E}_{\mathcal{D}(z|A)}[\mathbb{1}_{f(x)=f(z)}]$

However, it is usually _intractable_ to compute this precision for any $\mathcal{D}$

We instead use a probabilistic value
$$
P(\text{prec}(A) \ge \tau) \ge 1 - \delta
$$

The coverage of an anchor is defined as the probability that it applies to samples from $\mathcal{D}$, i.e. 
$cov(A) = E_{\mathcal{D}(z)}[A(z)]$

And we search the anchor that has the maximum coverage
==> Optimize the following problem :
$$
\max_{A \text{  s.t. } P(\text{prec}(A) \ge \tau) \ge 1 - \delta} cov(A)
$$