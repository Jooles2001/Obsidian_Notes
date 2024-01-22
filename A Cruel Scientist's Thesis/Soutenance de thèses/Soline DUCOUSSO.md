*2023-12-14*
# Moving code analysis from safety to security: the attacker model

**Security properties**: integrity, confidentiality, privacy

Vulnerabilities: Flawed specification, programming error, incorrect library assumptions
--> attacks: execution disruption, system observation

Historical Example - Hardware Fault Injection Attacks
- Laser, ondes electromagnetiques

Motivating Example - Data fault
+ change the value of a variable to influence conditional branches

Fault Models
+ Data faults
+ Control-flow
+ Instruction modification

The attacker can simultaneously launch different types of attacks !!

## Program Analysis Techniques
Formal methods
Symbolic execution

Real attackers:
+ various attack vectors
+ side channels
+ multiple actions in one attack

## Goal
*Devise a technique to automatically and efficiently reason about the impact of an advanced attacker

Mutant generation: analyse weakly different versions of the same initial program
Forking technique: check for each branch what would happen in normal situations, and attacked situations
==> scalability issues for both

# Adversarial Reachability

+ Hardware attacks
+ Software-implemented hardware attacks

## Model of an advanced attacker
1.  a set of attacker actions
2.  a maximum number of actions
3.  a goal expressed as a location reachability query

Expressing faults
--
(A) Independent faults: extra adversarial transition corrupting the state independently of the execution

(B) Semantic faults: adversarial transition modify the semantic of a legitimate instruction

Adversarial reachability = extended transition system + location reachability

# Forkless Adversarial Symbolic Execution

## Symbolic Execution
* symbolic inputs
* follow each path, compute its path predicate
* assess reachability with a SMT solver
* Get model for symbolic inputs
* Properties: correct and k-complete

-> Path explosion !
-> Constraint solving !

Forking technique :
* covers all adversarial behaviors
* |path| exponential with |fault injection points|

## FASE
* covers all behaviours
* no extra paths but harder "equations" and complex queries

==> Much faster than Forking !

## Optimizations Overview
Early Detection of Fault Saturation
+ on va chercher à allouer un budget max d'attaques et donc de ne pas surévaluer l'analyse
Injection On Demand
+ on va chercher à retroactivement rajouter des attaques si le chemin n'en contient pas assez

### Implementation
--> Binsec

### Research Questions
RQ1: correctness and k-completeness ?
RQ2: evaluation for arbitrary data faultd
RQ3: evaluation for other fault models
RQ4: evaluation of forkless faults in instrumentation
Case study of WooKey bootloader


# Limitations
Micro-architecure modelisation is difficult at program level
In the approach:
Adversarial Reachability
* hidden registers
* prefetch buffer
FASE
* Faults on load and write operations
* no multi-effect faults
* only transient faults -> no permanent faults (the fault disappears after the attack)
* no support for general instruction modifications
BINSEC
* no efficient symbolic algorithm for faults on addresses

# Futur perspectives
Lifting limitiations
* speculative execution inducing faults
* proof instead of bounded verification

Design hybrid forking/forkless injection techniques and heuristics
* characterization forking/forkless gain per injection point
* heuristics
* related to the path merging problem in symbolic execution

Algorithm to find the minimal attacker in a situation


