# Deep Neural Network Uncertainty Runtime Monitoring for Robust & Safe AI-based Automated Navigation
*2023-12-11*

## Automated systems in the age of deep learning
Robots can now navigate without human intervention

Architecture:
+ Navigation software pipeline/stack
	+ Detection
	+ Tracking
	+ Prediction
	+ Planning
	+ Control
- Learning-based monolithic

-> Automated navigation is difficult
Neural networks vulnerable to _distribution shift_ + have an erroneous confidence representation
No formal specification & verification of their behavior

## DNN Uncertainty
- show label and probability
- show variance of regression

## Learning-based systemes challenges
- Deal with the unknown
- Increase the amount of information passed between components
- Ensure safety
-> EU guidelines

# Key Research Questions
1. Is DNN predictive uncertainty a reliable and feasible measure for detecting distribution shifts ?
2. ...
3. ...

## Distribution shift detection problem
-> Build a confidence score $s(x)$ such that a monitoring function $\Omega$ uses a threshold $\tau$  to tell if a sample is good or not

## OoD detection with post-hoc methods
- Outputbased methods
- Feature processing
- Distance-based methods
- Density based methods

## Improve detection
- Use the uncertainty from intermediate hidden representations

# Uncertainty-aware navigation
Uncertainty propagation does not bring benefits by default 

# Conclusion
1. Uncertainty from intermediate DNN representations can be more reliable than output uncertainty (for the distribution shift detection)

# Future Work
1. Uncertainty estimation
	1. Aleatoric and epistemic uncertainty
2. Embedding uncertainty-aware DNNs
	1. What is the effect of quantization and pruning on the uncertainty estimates ?
3. Distribution shift detection with post-hoc methods
	1. Is there a relationship between LaREx, ASH, DICE, and ReAct?
4. Automated navigation safety