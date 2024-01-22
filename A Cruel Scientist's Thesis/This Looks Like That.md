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