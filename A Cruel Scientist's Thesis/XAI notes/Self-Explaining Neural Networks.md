https://arxiv.org/pdf/1806.07538.pdf

a **self-explaining prediction model** has the form:
$$f (x) = g(\theta_1(x)h_1(x), . . . , \theta_k(x)h_k(x))$$
where:
P1) $g$ is monotone and completely additively separable
P2) For every $z_i := \theta_i(x)h_i(x)$, $g$ satisfies $\partial g\partial z_i \geq 0$
P3) $\theta$ is locally difference bounded by $h$
P4) $h_i(x)$ is an interpretable representation of $x$
P5) $k$ is small.

In that case, for a given input $x$, we define the explanation of $f(x)$ to be the set $E_f(x) ≡\{(h_i(x), \theta_i(x))\}^k_{i=1}$ of basis concepts and their influence scores.

When $\theta(x)$ is realized with a neural network, we refer to $f$ as a self-explaining neural network (SENN)

The final loss:
$$L_y (f (x), y) + λL_θ (f ) + ξL_h(x, \hat{x})$$

![[Pasted image 20240103162800.png]]

