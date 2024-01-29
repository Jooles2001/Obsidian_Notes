Paper: https://openreview.net/pdf?id=3FJaFElIVN
Paper: https://arxiv.org/pdf/2311.15722.pdf

LIME has two main problems: 
- its sampling neighborhood is non-local and biased towards the reference
- poor local fidelity and sensitivity 

=> for two random seeds, the explanation can be very different for LIME

> An explanation cannot be considered as local if the samples themselves are non-local, leading to a lack of local fidelity in the explanation. 

> GLIME—a local explanation framework that generalizes LIME and five other methods: KernelSHAP [19 ], SmoothGrad , Gradient , DLIME , and ALIME. Through a flexible sample distribution design, GLIME produces explanations that are more stable and faithful. Addressing LIME’s instability issue, within GLIME, we derive an equivalent form of LIME, denoted as GLIME-BINOMIAL, by integrating the weighting function into the sampling distribution. GLIME-BINOMIAL ensures exponential convergence acceleration compared to LIME when the regularization term is presented. Consequently, GLIME-BINOMIAL demonstrates improved stability compared to LIME while preserving superior local fidelity. Furthermore, GLIME enhances both local fidelity and stability by sampling from a local distribution independent of any specific reference point.

