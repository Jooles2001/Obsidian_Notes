https://towardsdatascience.com/from-shapley-to-shap-understanding-the-math-e7155414213b
(very good videos inside that blog post as well)

comes from game theory
want to evaluate the contribution of each "player" to a team, with regards to the final result/score

$$\phi_i = \sum_{S\subseteq\{1, \dots, p\}\setminus\{i\}}\frac{|S|!(p-|S|-1)!}{p!}[val(S \cup \{i\}) - val(S)]$$
$|S|! \Rightarrow$ number of ways players can join $S$ before player $i$
$(p-|S|-1)! \Rightarrow$ number of ways players can join coalition after player $i$ joins
$p! \Rightarrow$ number of ways to form coalition of $p$ players

This fraction represents the weight of the marginal contribution