Paper: https://www.researchgate.net/profile/Avi-Rosenfeld/publication/349111351_Better_Metrics_for_Evaluating_Explainable_Artificial_Intelligence_Blue_Sky_Ideas_Track/links/6021333a92851c4ed5580e7e/Better-Metrics-for-Evaluating-Explainable-Artificial-Intelligence-Blue-Sky-Ideas-Track.pdf
Paper: https://dl.acm.org/doi/pdf/10.5555/3463952.3463962

# Abstract
This paper presents objective metrics for how explainable artificial intelligence (XAI) can be quantified. Through an overview of current trends, we show that many explanations are generated post-hoc and independent of the agent's logical process, which in turn creates explanations with limited meaning as they lack transparency and fidelity. While user studies are a known basis for evaluating XAI, studies that do not consider objective metrics for evaluating XAI may have limited meaning and may suffer from confirmation bias, particularly if they use low fidelity explanations unnecessarily. To avoid this issue, this paper suggests a paradigm shift in evaluating XAI that focuses on metrics that quantify the explanation itself and its appropriateness given the XAI goal. We suggest four such metrics based on performance differences, D, between the explanation's logic and the agent's actual performance, the number of rules, R, outputted by the explanation, the number of features, F, used to generate that explanation, and the stability, S, of the explanation. We believe that user studies that focus on these metrics in their evaluations are inherently more valid and should be integrated in future XAI research.

## Notation
* ***D***, the performance difference between the agent’s model and the performance of the logic presented as an explanation
* ***R***, the number of rules in the agent’s explanation
* ***F***, the number of features used to construct the explanation
* ***S***, the stability of the agent’s explanation

## Motivation
The authors claim that *"existing user studies that evaluate explanations generated post-hoc with a separate logic and low fidelity to validate legal, ethics or safety concerns are inherently flawed."*
==>
If the post-hoc explanation is based on a fundamentally different logic than the one used by the agent, then what is being evaluated? If they contain the same logic, then why not use that model instead of the black-box model ? 
[[Stop Explaining Black Box Machine Learning Models for High Stakes Decisions and Use Interpretable Models Instead]]


## Proposed metrics
***D*** quantifies the change of agent performance, $\delta$, between the black box model, and the best observed transparent model. 

Even if a user is happy with an explanation, 𝛿 helps measure if the trade-off between this explanation and one with
transparency was warranted by comparing the performance, $𝑃_𝑡$ of the transparent model and the performance, $𝑃_𝑏 − 𝛿$, of the black
box model.

---
***R*** quantifies explanations based on their simplicity – the fewer rules in the explanation, the better. This metric is built upon an assumption that simpler explanations should be preferred as per Occam's Razor
==> Use of a penalty metric : $\lambda * \mathcal{L}$   where 
$$
\mathcal{L} =
\begin{cases}
       size(m) - c & \text{if }  (size(m) - c) > 0 \\
      0 & \text{otherwise. } \\
\end{cases}$$
* $size(m)$ is the number of rules
* $c=1$ is the number of rules allowed before penalization
* $\lambda$ the penalty factor

---
***F*** focuses on the number of features inputted by agent to create its explanation.
Similarly, use a penalty metric : $\lambda * \mathcal{L}$
--> $size(m)$ is instead the number of features used to create an explanation

_How to differ **R** from **F** when rules $\approx$ features ?_
For example, image processing typically currently focuses on pixels inputs, but some constructed image features such as edges are inherently more interpretable and might be considered as a single feature for purposes of these metrics.

---
***S*** quantifies the stability of the agent’s explanation

The authors suggest "boostrapping the data and then observing its impact on the outputted agent explanations. The similarity between the bootstraps’ explanations can be quantified using Jaccard and/or Tanimoto similarity measures. $[$They$]$ stress that only small perturbations should be used by the bootstraps such that the class labels are not changed and small amounts of resampling noise are used to check that the explanations are stable and thus general."