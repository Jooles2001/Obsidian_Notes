Include images

Explain the motivation of our experiment 
- why do we do that 

Explain why statically attack & explain the images of the dataset rather than "on-the-fly"
- runtime
	- execution time explosion
- consequences
- determinism (or lack thereof)
- problems encountered with biased data


Why & how do we split the dataset initially ?

-> Use _pretrained_ ResNet18 rather than toy-model(s)
* for classifier AND detector

Toy model out of scope, want to have "realistic" models & results, compare ourselves with the international community, close to SotA models

Detector agnostic to model ? dataset ? explanation model ?

Multiple detectors/binary classifiers ? N * k where k is the number of explanation models ?


Good habits
- use alarms to allocate a certain amount of time to each task (or type of task)
- precise tensor shape in comments in the code

