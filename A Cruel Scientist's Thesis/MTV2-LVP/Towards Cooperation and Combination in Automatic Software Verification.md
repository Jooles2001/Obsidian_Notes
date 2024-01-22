*Dirk Beyer - LMU Munich*

Scope:
	C Program -> Verification Tool -> boolean + witness

Competitions in Software Verification and Testing:
	- RERS
	- SV-COMP
	- Test-Comp
	- VerifyThis

Example: CPAChecker 

#### Motivation for Cooperative Verification:
* Introduce a new level
* Current tools should become "low level" components
* Construct combinations
* Common Interface to be developed!
* Success: SAT, SMT

#### Definition of Cooperative Verification
An approach is called **cooperative verification**, if
- identifiable *actors* pass information of 
- identifiable *artifacts* towards the common objective of
- solving a *verification* problem,
where at least two of these actors are *analyzers*.


#### Correctness Witness
Program P, specification $\varphi$ , proof $\pi$

Verifier : proves that P implies $\varphi$ by $\pi$
Validator: proves that P implies $\varphi$ given witness by $\pi'$


Many validators exist for C today


#### Template
```
p = ... //program
s = ...  //specification
witness = ...
verifier = ...
validator = ...
result = verifier.verify(p,s)
if result then
	result = validator.validate(p,s,witness)
return (result,witness)
```

#### From Components: Construct Iteractive Verifiers
-> Turn a witness validator into an interactive verifier
-> Turn an automatic verifier into an interactive verifier
-> Annotating in ACSL is more human-readable than witness automata
-> Works for a wide range of automatic verifiers/validators

#### Component Framework: Constructing Validators
-> Turn an interactive verifier (`Frama-C`) into a validator
-> Turn an automatic verifier into a validator
