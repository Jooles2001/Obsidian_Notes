
Deductive Verification
S a program (statement)
P a property (pre-condition)
Q a property (post-condition)

m, m' memory states

S *executable* programming language
\[\[S]] : m --> m   registers, references (aliasing), dynamic allocation, ...

P *logical* programming languages
\[\[P]] : m --> Prop
	contains (some) code expressions
	concise specifications wanted
	expressive power vs proof automation

Property user language
$P,Q =$ 
	| ... // Pure (1st order) formulae
	| ... // Memory related atoms

Code annotations:
```
//@ requires \separated(x,y);
//@ ensures *x == \old(*y*)+1;
function F(x,y) { *x = *y +1; }
```

### Proving Triples SMT solvers
Ground sematics

Translation (compilers):
{P} S {Q} = $\forall m . [[P]](m) ==>$

Transformation rules & Lemmas:
$$\frac{\{P_1\} S_1 \{Q_1\} \quad \{P_2\} S_2 \{Q_2\}}{\{P\} S \{Q\}}$$
### Tools & Program Logics
Boogie, Frama-C, Spark, Why3
Verifast, Gillian
VST
...
--> SMT Solvers do not use Separation Logic !
#### Hoare Logic with References

#### Separation Logic
-> Syntactic proof