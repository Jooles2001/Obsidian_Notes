Paper: https://arxiv.org/pdf/1806.10574.pdf

---
_This_ Looks Like _That_
--
### The architecture
![[Pasted image 20240122103408.png]]

### The parameters

The network learns $m$ prototypes $P = \{\mathbf{p}_j \}^m_{j=1}$, whose shape is $H_1 × W_1 × D$ with $H_1 ≤ H$ and $W_1 ≤ W$ . In (their) experiments, (they) used $H_1 = W_1 = 1$.  

> ==>The depth of each prototype is the same as that of the convolutional output but the height and the width of each prototype is smaller than those of the whole convolutional output, each prototype will be used to represent some prototypical activation pattern in a *patch* of the convolutional output
> ==>Each prototype $\mathbf{p}_j$ can be understood as the latent representation of some prototypical *part*

---
> Given a convolutional output $z = f (x)$, the j-th prototype unit $g_{\mathbf{p}_j}$ in the prototype layer $g_\mathbf{p}$ computes the squared $L^2$ distances between the $j$-th prototype $\mathbf{p}_j$ and all patches of $\mathbf{z}$ that have the same shape as $\mathbf{p}_j$ , and inverts the distances into **similarity scores**.

> The activation map of similarity scores produced by each prototype unit $g_{\mathbf{p}_j}$ is then reduced using global $\texttt{max pooling}$ to a single similarity score, which can be understood as how strongly a prototypical part is present in *some* patch of the input image.

The prototype unit $g_{\mathbf{p}_j}$ computes 
$$g_{\mathbf{p}_j} = max_{\tilde{\mathbf{z}}\in patches(\mathbf{z})} \log (\frac{(\|\tilde{\mathbf{z}} − \mathbf{p}_j \|^2_2 + 1)}{(\|\tilde{\mathbf{z}} − \mathbf{p}_j \|^2_2 + \epsilon))}
$$

The function $g_{\mathbf{p}_j}$ is *monotonically decreasing* with respect to $\|\tilde{\mathbf{z}} − \mathbf{p}_j \|^2_2$ (if $\tilde{\mathbf{z}}$ is the closest latent patch to $\mathbf{p}_j$ )
> ==> if the output of the $j$-th prototype unit $g_{\mathbf{p}_j}$ is large, then there is a patch in the convolutional output that is (in 2-norm) very close to the $j$-th prototype in the latent space, and this in turn means that there is a patch in the input image that has a similar concept to what the $j$-th prototype represents.

In (their) ProtoPNet, (they) allocate a pre-determined number of prototypes $m_k$ for each class $k ∈ \{1, ..., K\}$ 
($K=10$ per class by default), so that every class will be represented by some prototypes in the final model. 

---
## Training algorithm

Optimization problem:
$$
\min_{\mathbf{P}, w_{conv}}\frac{1}{n}\sum_{i=1}^n\text{CrsEnt}(h \circ g_{\mathbf{p}} \circ f(\mathbf{x}_\mathbf{i}), \mathbf{y}_\mathbf{i}) + \lambda_1\text{Clst} + \lambda_2\text{Sep}
$$
-> The cross entropy loss penalizes mis-classification on the training data


With the following sub-loss problems:
$$
\text{Clst}=\frac{1}{n}\sum_{i=1}^n\min_{j:\mathbf{p}_j\in\mathbf{P}_{y_i}}\min_{\mathbf{z}\in\text{patches}(f(\mathbf{x}_i))}\|\mathbf{z} − \mathbf{p}_j \|^2_2
$$
-> The minimization of the cluster cost (Clst) encourages each training image to have some latent patch that is close to at least one prototype of its own class


$$
\text{Sep} = -\frac{1}{n}\sum_{i=1}^n\min_{j:\mathbf{p}_j\notin\mathbf{P}_{y_i}}\min_{\mathbf{z}\in\text{patches}(f(\mathbf{x}_i))}\|\mathbf{z} − \mathbf{p}_j \|^2_2
$$
-> The minimization of the separation cost (Sep) encourages every latent patch of a training image to stay away from the prototypes not of its own class.

> Note: the last layer $h$ is fixed at this stage, with $w_h^{(k,j)}=1$ for all $j$ such that $\mathbf{p}_j \in \mathbf{P}_k$ and 
> $w_h^{(k,j)}=-0.5$ for all $j$ such that $\mathbf{p}_j \notin \mathbf{P}_k$

#### Projection of prototypes
The update that is operated is the following:
$$
\mathbf{p}_j \leftarrow \min_{\mathbf{z}\in\mathcal{Z}_j}\|\mathbf{z} − \mathbf{p}_j \|^2_2
\quad; \quad
\mathcal{Z}_j=\{\tilde{\mathbf{z}}:\tilde{\mathbf{z}} \in \text{patches}(f(\mathbf{x}_i)),  \forall i \text{  s.t.  } y_i=k\}
$$

#### Convex optimization of last layer
Goal:   have $w_h^{(k,j)}\approx0$ for all $j$ such that $\mathbf{p}_j \notin \mathbf{P}_k$ 
The convex optimization problem solved is :
$$
\min_{w_h}\frac{1}{n}\sum_{i=1}^n\text{CrsEnt}(h \circ g_{\mathbf{p}} \circ f(\mathbf{x}_\mathbf{i}), \mathbf{y}_\mathbf{i}) + \lambda\sum_{k=1}^K\sum_{j:\mathbf{p}_j\notin\mathbf{P}_k}|w_h^{(k,j)}|
$$
> Note: at this stage, all the convolutional and prototype layers are fixed