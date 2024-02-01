Paper: https://arxiv.org/pdf/1705.05598.pdf


=> Compelling **conclusion** from the paper:
> Understanding and explaining nonlinear methods is an important challenge in machine learning.
Algorithms for visualizing nonlinear models have emerged but theoretical contributions are scarce.
We have shown that the direction of the model gradient does not necessarily provide an estimate for
the signal in the data. Instead it reflects the relation between the signal direction and the distracting
noise contributions ( Fig. 2). This implies that popular explanation approaches for neural networks
(DeConvNet, Guided BackProp, LRP) do not provide the correct explanation, even for a simple
linear model. Our reasoning can be extended to nonlinear models. We have proposed an objective
function for neuron-wise explanations. This can be optimized to correct the signal visualizations
(PatternNet) and the decomposition methods (PatternAttribution) by taking the data distribution into
account. We have demonstrated that our methods constitute a theoretical, qualitative and quantitative improvement towards understanding deep neural networks.