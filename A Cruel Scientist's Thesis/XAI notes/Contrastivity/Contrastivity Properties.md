From  [[From Anecdotal Evidence to Quantitative Evaluation Methods - A systematic Review]]
## Target Sensitivity
Captures “the intuition that class-specific features highlighted by
an explanation should differ between classes”
- So far only evaluated on heat-maps
- Some attribution methods can converge to class-insensitive explanations
- Visual inspections favor plausible heatmaps
	- high similarity between edge detectors for image data and explanatory saliency maps
-> A different prediction should then also lead to a different explanation
-> The authors of [[Interpretable and Fine-Grained Visual Explanations for Convolutional Neural Networks]] argue that explanations should be empty for targets for which there is no evidence in the input sample (e.g. a class that is visually not present in an image). 

---
## Target Discriminativeness
Implies good “informativeness for a downstream prediction task”

To evaluate the target-discriminativeness, either an external classifier is trained on predicting the right target given the explanation, or a cluster method is applied on the explanations.
- The performance of the classifier or clustering method is evaluated against ground-truth targets

Alternatively, the authors of [[LEARNING HOW TO EXPLAIN NEURAL NETWORKS PATTERNNET AND PATTERNATTRIBUTION]] evaluate **Target Discriminativeness** by evaluating how much of the target can be reconstructed when the explanation is *removed* from the input.

---
## Data Randomization Check

- introduced by the authors of [[Sanity Checks for Saliency Maps]]
-> sanity check for the "sensitivity of an explanation method to the relationship between instances and labels"
+ model-agnostic
- explanations explain the mapping between input and output that the predictive model has learned.
- Interesting results from [[Understanding Deep Learning (Still) Requires Rethinking Generalization]]
-> for a given test sample, the explanation of a model trained on randomized data should be different from an explanation of a model trained on the original dataset.