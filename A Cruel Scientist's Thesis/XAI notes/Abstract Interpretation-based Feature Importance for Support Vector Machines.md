Paper: https://caterinaurban.github.io/pdf/vmcai2024.pdf

**Contributions**
- approximate the predictive model
	- is formally correct
	- does not depend on dataset or model accuracy
	- fast to compute
	- supports both linear and nonlinear (polynomial and radial basis) kernels
- the approach is _sound by design_
	- individually fair abstract representation of a SVM => the SVM is actually fair
	- there are cases where the SVM is fair but the verification of its abstract representation fails
	-> the fraction of successful fairness verifications over a test dataset turns out to be a ==lower bound== on the real individual fairness of a SVM.
- generate counterexamples wen the abstraction is unable to prove individual fairness
	-> The fraction of successful counterexample searches over a test dataset yields an ==upper bound== on the real individual fairness of a SVM.
	
==>improves (already existing) SAVer [[Robustness Verification of Support Vector Machines]]

**Related Work**
- PFI is a global, model-agnostic, performance-based measure
- LIME and SHAP are local, model-agnostic, effect-based measure
-> AFI is global and local, effect-based and dataset independent measure
-> AFI is based on a formally correct-by-construction approximation of the underlying predictive
model


# 3.2
Page 10, il est écrit:
> Note that if, for some $i ∈ [1, k]$, either $a_{i,f} = ⊥^{CP}$ or $a_{i,t} = ⊥^{CP}$, then $\hat{γ}_i(a) = ∅$.

Remarque: je ne suis pas d'accord, il y a une faute de frappe ici ou une faute de raisonnement. Rappelons la définition de $\gamma$ dans ce domaine abstrait:
$$
∀z ∈ \mathbb{R},\quad \gamma^{CP}(z) ≜ z, \quad \gamma^{CP}(⊥^{CP}) ≜ ∅, \quad \gamma^{CP}(⊤^{CP}) ≜ \mathbb{R}.
$$$$\hat{γ}_i(a) ≜ \{x ∈ \mathbb{R}^k | x_i ∈ γ^{CP}(a_{i,t}), ∀j \neq i. x_j ∈ γ^{CP}(a_{i,f})\}$$
Correction:
> Note that if, for some $i ∈ [1, k]$, either $a_{j\neq i,f} = ⊥^{CP}$ or $a_{i,t} = ⊥^{CP}$, then $\hat{γ}_i(a) = ∅$.

# Core Concept

(The authors) implemented in SAVer (their) OH abstraction for categorical features on top of the interval and RAF abstract domains for numerical features


# Not understood
- example 3.10
	- why do we add the intervals at the very end ??
- 