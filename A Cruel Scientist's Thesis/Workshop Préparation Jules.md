
Way too much time spent on the background context !!!!
-> should not be more than 1/3 of the time, was a little more than 1/2
-> spent too much time explaining why AI is everywhere
-> " " " what adversarial attacks are, with too many examples
-> gave the (mathematical, for some) definition of adversarial attacks when it was clearly not needed or reused
-> gave the definition of Integrated Gradients, GradCAM (went back and forth) and did not use those XAI methods
-> in the midst of these unnecessary definitions, I do not ever formally define Saliency method

Now, feedback on the first part of the "core" of the presentation:
- slide 12: not properly explained how the _explanation_ helps truly distinguish between original and adversarial
- slide 13: unnecessary to display the classification model and the adversarial detection model as distinct mixtures of a CNN and a FC layer. I need to personally change that
-> I could already introduce the notion that we could attack the detector, but that instead of attacking the model, of which we do not have any info, we could attack the saliency map produced.
- slides 15-17: a lot to unpack here
	- unnecessary ticks
	- no labels to explain what we are looking at
	- too high $\epsilon$ for CIFAR10
	- what is exactly being expressed in slide 16 ?
	-> show with/without rescaling the noise vector values to $[0, 1]$
	- serious need for explaining and quantitatively measure the $L_2$ distance between the saliency maps

Going into feedback of the ReLU part:
- stop using the word "facet" and use "linear regions" instead 
 