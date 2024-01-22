Paper: https://arxiv.org/pdf/1705.07874.pdf
GitHub repo: https://github.com/shap/shap/
very good video: https://www.youtube.com/watch?v=VB9uV-x0gtg

Applies [[Shapley Values]] to Machine Learning models

Introduce `KernelSHAP` to quickly and statistically compute Shapley Values (using background data *which can be an extract of the training data*)

==> Surrogate model for explanation only:
$$x \approx x' \Rightarrow f(x) \approx g(x')$$
with $g$ defined as such
$$g(x') = \phi_0 + \sum_{i=1}^N\phi_ix'_i$$
(here $x'$ is a constructed data point for which )

Notes
==

Authors identify that explanation methods are actually mathematically within the same family of functions


![[Pasted image 20240105145528.png]]

**Warning**: they explain the deviation from mean prediction and not the prediction itself **!!**