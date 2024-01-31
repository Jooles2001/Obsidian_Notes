Paper: https://caterinaurban.github.io/pdf/vmcai2024.pdf

**Contributions**
- approximate the predictive model
	- is formally correct
	- does not depend on dataset or model accuracy
	- fast to compute
	- supports both linear and nonlinear (polynomial and radial basis) kernels
- the approach is _sound by design_
	- individually fair abstract representation of a SVM => the SVM is actually fair
	- there are cases where the SVM is fair but the verification of its abstract representation fails
	-> the fraction of successful fairness verifications over a test dataset turns out to be a ==lower bound== on the real individual fairness of a SVM.
- generate counterexamples wen the abstraction is unable to prove individual fairness
	-> The fraction of successful counterexample searches over a test dataset yields an ==upper bound== on the real individual fairness of a SVM.
	
==>improves (already existing) SAVer



