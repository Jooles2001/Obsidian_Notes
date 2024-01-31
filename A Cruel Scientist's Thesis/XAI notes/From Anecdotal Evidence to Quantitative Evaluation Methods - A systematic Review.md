*Mike Nauta (University of Twente) et al.*
Paper: https://arxiv.org/pdf/2201.08164.pdf

Growing demand for XAI evaluation metrics
--> community has to agree on standardized evaluation metrics
--> currently, evaluation is based on "the researchers' intuition of what constitutes a good explanation"

>  **Definition**
>  An **explanation** is a presentation of (aspects of) the reasoning, functioning and/or behavior of a machine learning model in human-understandable terms.

Explanation methods should be evaluated on "how they behave on the curve from maximum interpretability to maximum completeness"

Three-level taxonomy of plausibility:
1. **application-grounded evaluation:** with (human) domain experts
2. **human-grounded evaluation**: with lay persons on simplified tasks
3. **functionally-grounded evaluation**: with computational proxy measures of interpretability

==> User-studies are unreliable, not reproducible, not comparable, and imply strong biases towards explanations that match with users' expectations rather than how the model works.

==> dissociating the evaluation of the explanation method from the performance of the model itself

==> proxy studies valid in early development : generating and experimenting process greatly outpaces human studies

## Co-12 properties
### Correctness
> indicates how truthful the explanations are compared to the “true” black box behavior (either locally or globally).

### Completeness
> the extent to which the explanation explains predictive model $f$.
> ==> should be balanced with ==compactness and correctness==
> **Reasoning-completeness:** the extent to which the explanation reveals all the mathematical operations and parameters in the system.
> **Output-completeness:** the extent to which the explanation agrees with the predictions of the original predictive model.

### Consistency
> identical inputs have identical explanations. --> explanation is _deterministic_

### Continuity
> how "smooth" the explanation function is, i.e small variations in the input induce near identical responses from the model.

### Contrastivity
> discriminativeness of an explanation ==> an explanation should explain an event, but also relative to some other event that did not occur

-> More on [[Contrastivity Properties]]
### Covariate complexity
> covariates in the explanation should be comprehensible and concepts should have an immediate human-understandable interpretation.

### Compactness
> the size of the explanation respects human cognitive capacity limitations.

### Composition
> the presentation format, organizaion, and structure of the explanation.

### Confidence
> the explanation has a measure of certainty or other probability information.
> -> confidence measure of the black box prediction
> -> likelihoud of the explanation

### Context
> the extent to which the user and their needs are taken into account.

### Coherence
> the extent to which the explanation is consistent with relevant background knowledge.

### Controllability
> to what extent a user can control correct or interact with an explanation <- explanations are social






