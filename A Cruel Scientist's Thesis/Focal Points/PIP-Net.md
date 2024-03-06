# Patch-Based Intuitive Prototypes for Interpretable Image Classification
_Meike Nauta et al._
_Presented at CVPR_
Paper: https://openaccess.thecvf.com/content/CVPR2023/papers/Nauta_PIP-Net_Patch-Based_Intuitive_Prototypes_for_Interpretable_Image_Classification_CVPR_2023_paper.pdf

### Introduction
- identify semantically meaningful components while only having access to image-level class labels not relying on additional part annotations
+ when no relevant prototypes are present in the image, with _e.g._ out-of-distribution data, PIP-Net will abstain from a decision.
- there exists a semantic gap between the similarity at image-level and latent representation
-> adversarial images for example


### Key Idea
Take the "same" architecture as ProtoPNet, but this time, reduce the semantic gap
How ? By using contrastive learning :
Force the CNN to evaluate the prototypes at the same place for similar images (pairs of very close images) -> Alignment Loss $\mathcal{L}_A$ in the paper
This approach alone is not sufficient to stop the network from:
- learning constant features
- maximizing one prototype

-> add an extra constraint (loss $\mathcal{L}_T$) per batch :
count the amount of times a prototype is "seen" by the classifier and force the network to "see" each prototype at least X times per batch (X is 10 in the paper, for a batch of 128 samples)

Finally, add a classic negative log-likelihood loss term $\mathcal{L}_C$
-> assert that the prototypes learnt are _actually_ useful

### Is it a case-based reasoning network ?
- currently "no", since it does not project the latent space representation prototypes onto a projection space (with prototypes from the training set), and therefore the decision is not based on the closest prototypes seen
- could become if the prototype layer is combined with a $L_2$ distance projection layer in the network.





