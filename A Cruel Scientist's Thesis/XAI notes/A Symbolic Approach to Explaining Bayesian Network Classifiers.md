Paper: https://arxiv.org/pdf/1805.03364.pdf
Related video by the authors: https://www.youtube.com/watch?v=6JFTkmPMfmI
And another: https://www.youtube.com/watch?v=Rt_cF8zM8fM


_minimum-cardinality explanations_: 
> which of the positive test results are the culprits for the classifier's decision, i.e., a minimal subset of the positive results that is sufficient for the current decision

_prime-implicant explanations_: 
> smallest subset of features that renders the remaining features irrelevant to the current decision? In other words, which subset of features—when fixed—would allow us to arbitrarily toggle the values of other features, while maintaining the classifier’s decision?


**Bayesian Network Classifiers --> Ordered Decision Diagram (ODD)

$f(X)$ is the classifier's ==decision function== if and only if,
$$
f(x) = \begin{array}{r@{}l}
      1 & \text{if } Pr(c|x)\geq T \\
      0 & \text{otherwise. } \\
\end{array}
$$
A decision function $f(X)$ is ==monotone== if, and only if,
$$
x^\star \subseteq^1 x \text{ only if } f(x^\star) \leq f(x)
$$
where $x^\star \subseteq^1 x$ means the features set to $1$ in $x^\star$ is a subset of those set to $1$ in $x$.

An OBDD is a _tractable_ representation of a function $f(X)$

### Reasoning
Observing features $Y \subset X$ leads to another naive Bayes classifier, with features $X \setminus Y$ and an adjusted class prior.

The authors construct a decision tree over features $X$ by merging nodes (found by observing a partial instanciation $y$) that are equivalent classifiers (equivalent decision function)

A second algorithm is devised to compile a latent-tree classifier into an ODD by iteratively creating a new latent-tree, all features outside of a given node $R$ are observed, and observing all features under $C$, a child of $R$.

---
### MC Explanations

The authors write $x ≤^1 x^\star$ to mean: the count of 1-features in $x$ is no greater than their count in $x^\star$


**Definition**
> An *MC-explanation* of a ==positive== instance $x$ is another positive instance $x^\star$ such that $x^\star \subseteq^1 x$ and there is no other positive instance $x' \subseteq^1 x$ where $x' <^1 x^\star$.
> 
> An *MC-explanation* of a ==negative== instance $x$ is another negative instance $x^\star$ such that $x^\star \subseteq^0 x$ and there is no other negative instance $x' \subseteq^0 x$ where $x' <^0 x^\star$.

* Which positive features are responsible for a _yes_ decision ?
* Which negative features are responsible for a _no_ decision ?

**Definition**
> For $i \in \{0, 1\}$, the $i$-minimization of decision function $f (X)$ is another decision function $f^i(X)$ defined as follows: 
> $f^i(x) = 1$ iff *(a)* $f (x) = 1$ and *(b)* $x \leq^i x^⋆$ for every $f (x^\star) = 1$.

The set of computed explanations is encoded by another decision function $g(X)$. In particular, $g(x^⋆) = 1$ iff $x^⋆$ is an **MC-explanation** of decision $f (x)$.

### PI Explanations
* Which features (**+** or **-**) make the other features irrelevant ?