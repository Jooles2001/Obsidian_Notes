*Louis Gauthier*

# Introduction
- ACSL: C specification language
	- ACSL specified with an _informal semantics_
	- Used in Frama-C
- Informal semantic issues
	- Ambiguity of natural language
	- Can lead to interpretation errors or even inconsistency
- Formalize the semantics (_e.g._ in Coq/Roq)
- Many formalisations of C semantics exist
- Formalisations of specification language exist too

### Some features of ACSL
- Comparing structures or unions is allowed
- Underspecified terms (divisions by zero) won't stop the execution

# C syntax
