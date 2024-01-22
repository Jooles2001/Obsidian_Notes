HAL paper: https://cea.hal.science/cea-04256974v1/document

### Properties
**Correctness**
> can be evaluated using parameter randomisation which assesses the "causal" relationship between the model parameters and a given explanation method.

* Area Under the Deletion Curve, Average Drop/Increase/Gain 
	--> Out-of-Distribution data
* Causal Local Explanation metric
		--> Potential instability of the model

**Stability**
> metrics hypothesize that an explanation method should produce
> similar explanations for similar inputs.

* Maximum discrepancy between explanations in the neighborhood of an input.
	--> does not take into account local model behavior
	--> penalizes correct explanation methods in favor of more stable ones

**Plausibility**
> evaluates the adequacy between an explanation and the mental model of a human user, i.e., how this user thinks the model is behaving.

* Gaze-Fixation Density Maps that capture the distribution of human attention inside each image of a dataset
* Pearson Correlation Coefficient between saliency map and "ground-truth"
	--> does not entail correctness


---
_Building a surrogate model_

$$
\forall X\in \mathcal{X}, E_{X_0}(X) = s(X_0)^T (X-X_0) + g(X_0) \in \mathbb{R}
$$
_Measuring stability_

$$
LIP(X_0) = \max_{\|X_0-\tilde{X}\|_2<\epsilon}\frac{\|s(X_0) - s(\tilde{X})\|_2}{\|X_0-\tilde{X}\|_2}
$$

> **Note:** this metric does not take into account the possible instability of the model _g_ in the neighborhood of $X_0$
	--> an unstable model will be discarded in favor of a less correct, but seemingly more stable method

_Revised stability metric_
$$
D(X_0, \tilde{X}) = |E_{X_0}(m) - E_{\tilde{X}}(m)|
$$
where $m$ is the middle point between $X_0$ and $\tilde{X}$

_Local Surrogate Stability_
$$
LSS(X_0)= \max_{\|X_0-\tilde{X}\|_2<\epsilon}\frac{D(X_0, \tilde{X})}{\|X_0-\tilde{X}\|_2}
$$
**Figure for LSS**

![[Pasted image 20240116150058.png]]

---
_Measuring correctness_
$$
CLE(X_0) = \mathbb{E}_{\|X_0-\tilde{X}\|_2<\epsilon}C(X_0,\tilde{X})
$$

where $C(X_0,\tilde{X}) = |E_{X_0}(\tilde{X}) - g(\tilde{X})|$  measures the local prediction error of the surrogate model.

> **Note:** CLE does not take into account the possible instability of the model $g$ in the neighborhood of $X_0$


_Local Relative Correctness_
$$
LRC(X_0) = \mathbb{E}_{\|X_0-\tilde{X}\|_2<\epsilon}\frac{C(X_0, \tilde{X})}{\Delta_g(X_0, \tilde{X}) + \eta^2}
$$

where $\Delta_g(X_0,\tilde{X}) = |g(X_0) - g(\tilde{X})|$  and $\eta$ a small constant for stability


![[Pasted image 20240116151027.png]]

---
## Experiments


