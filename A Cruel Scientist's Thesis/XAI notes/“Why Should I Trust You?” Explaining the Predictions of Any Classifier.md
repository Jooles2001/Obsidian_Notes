*Ribeiro et al*

arXiv paper : https://arxiv.org/pdf/1602.04938.pdf

Better explained here:
https://towardsdatascience.com/understanding-how-lime-explains-predictions-d404e5d1829c
And here:
https://www.oreilly.com/content/introduction-to-local-interpretable-model-agnostic-explanations-lime/

Code available here: https://github.com/marcotcr/lime
# Desired Characteristics
+ Interpretability
	+ What are the features significantly influencing the prediction, how do they do it
	+ Who is the target audience ?
+ Local Fidelity
	+ _not_ global fidelity (unless the explanations **is** the model itself)
	+ it must correspond to how the model behaves in the vicinity of the instance being predicted
+ Model-agnostic
	+ should work not only on inherently interpretable models
+ Global perspective
	+ Must be able to _explain_ the model

# Local Interpretable Model-Agnostic Explanations (LIME)
--> identify an interpretable model over the _interpretable representation_ that is locally faithful to the classifier

Compute the local-surrogate $g$ that minimizes complexity and maximizes faithfulness to the original model (trade-off between the two)

Model-agnostic: local exploration by sampling