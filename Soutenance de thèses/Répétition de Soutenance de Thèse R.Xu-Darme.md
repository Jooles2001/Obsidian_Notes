*22/09/2023*
*Romain Xu-Darme*
# Algorithms and evaluation metrics for improving trust in machine learning: application to visual object recognition

#### Visual object recognition
* Object classification: classifies the object into a set of predetermined classes
* Localisation
* Segmentation

#### Traditional programming vs machine learning

#### Trust
The belief (by the trustor) in the ability (of the trustee) to achieve something
* Why ?
	* ML systems are everywhere
	* They **can** (and **will**) fail
	* Are use for decision-making *instead* of decision-suport
	* Regulated (GDPR, AI Act)
* How ?
	* User empowerment: provide relevant and faithful information about the system
	* Purpose of the thesis

#### What kind of information ?
Uncertainty estimation
-> The model should be able to indicated when it is not sure of its decision

Two sources of uncertainty:
* Aleatoric uncertainty: inherent randomness in data distribution
* Epistemic uncertainty: lack of representativeness of the training data
	* Operational domain / Out-of-distribution detection
	* Out-of-distribution detection in latent space

**Interpretability:**
> Degree of adequacy between the mental model of the user and how the algorithm is actually working

--> Increases with transparency and explainability
* Transparency
	* Simulatability => I can reproduce the operations
	* Decomposability => I can understand the purpose of the operations
* Explainability
	* XAI => I can interact with the model to extract knowledge
### Explainable AI (XAI) taxonomy

# Improving Trust
### Difficulty in nature of the data
High dimensional data + no clear semantic value of pixels =>
* No simulability, no decomposability
* No clear 

Complex models for complex problems:
* DCNNs
* Transformers
Hinders interpretability:
* simply explaining something complex requires compromises
* (post-hoc) explanations follow (conflicting) properties


## Solution 1: Increase transparency
* Extract semantic information
* Attribute: relation between semantic variable and the image
* Attribute extraction: detection + property association

## Solution 2: Use good explanation methods

# PARTICUL : Part Identification with Confidence measure using Unsupervised Learning
#### Core concepts
* Locality: each detector *should* focus on a small part of the image
* Unicity: detectors *should* focus on different regions of the image
* Clustering: detectors *should* focus on contiguous regions of the image

--> PARTICUL-based classification on-par with State-of-the-Art methods

> **Hypothesis :**
> Out-of-distribution data can be detected through the absence of all parts
 

# Evaluating Explainable AI models
### Explaining image classifiers using feature importance
A large (and growing) ecosystem:
* Model-agnostic
* Model-specific

Properties of explanations (12 identified)
* Correctness
* Consistency
* Compactness
* Confidence
* $\dots$

What are the limitations of current evaluation metrics ?
For a given property, is there a consensus among metrics ?
* Ranking-based method for evaluating consensus between evaluation metrics
* **Plausibility** not correlated with stability and correctness

* Explanations should not be taken at face value
* Difficult to disentangle mutual dependency between model, explanation method and evaluation metric
	* Not limited to post-hoc XAI methods

==> Two new metrics proposed and designed during the thesis (LSS, LRC) for evaluating **stability** and **correctness**

# Contributions
Many papers !!!
5 papers, 1 or 2 best paper awards
Industrial partnerships: Renault, Thales, Valeo
Numerous presentations given to share scientific progress


# Perspectives
**PARTICUL:** Going beyond unsupervised part detection
* Automatic property retrieval (*e.g.*, color)
* Improving the learning process and property implementation
* Application to other modalities
	* Signal processing
	* Object detection

**Improving the design of self-explaining models:**
* *Work in progress:* Generic Python library reimplementing popular models (`ProtoLib`)
* Improving visual similarity detection using interval propagation

**Evaluating explanation methods:**
* Going beyond sampling
* Study concensus with other properties




