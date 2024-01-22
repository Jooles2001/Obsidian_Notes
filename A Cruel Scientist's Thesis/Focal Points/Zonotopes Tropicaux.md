**Tristan Le Gall**
(*Au tableau uniquement*)
### Notation
$$\mathcal{R}^d:(x_1,\dots,x_d)$$
$$x_1 = \alpha_{11}\varepsilon_1 + \alpha_{12}\varepsilon_2 + \dots + \alpha_{1n}\varepsilon_n$$
$$\vdots$$
$$x_d = \alpha_{d1}\varepsilon_1 + \alpha_{d2}\varepsilon_2 + \dots + \alpha_{dn}\varepsilon_n$$
$$[X]_d = M [\varepsilon]_n \quad\quad\quad \varepsilon_i \in [-1,1]$$
$$AX = [AxM]\varepsilon = M'\varepsilon$$ 
La fonction `ReLU` n'est *pas* linéaire.
$$\texttt{ReLU}(x) = \max(0,x)$$
On peut ==approximer une fonction non-linéaire par un zonotope==, mais on introduit un nouveau symbole de bruit.

### Exemple
$$x = [a_{min}, a_{max}]\varepsilon + [b_{min}, b_{max}]$$
On va donc à la place utiliser ceci:
$$x = \max(0, \bar{a}\varepsilon + \bar{b})$$
### Algèbre Tropical:
$$ a \oplus b = \max(a,b) \quad\quad\quad a \otimes b = a + b$$

Forme la plus générale: en forme de \\\_\_/
$$x = \max(m,  a\varepsilon + b,  c\varepsilon + d)$$$$a_{\max} \leq 0 \leq c_{\min}$$

On cherche à approximer des fonctions avec ces zonotopes 
--> résultats pour l'instant: pas tant plus précis que les options existantes, et beaucoup plus de temps de calcul


