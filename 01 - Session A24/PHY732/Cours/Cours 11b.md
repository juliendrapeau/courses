# Concaténation

![|500](Attachements/Pasted%20image%2020241128090430.png)

|               | Composantes<br>physiques<br> | Composantes<br>encodées<br> | Composantes<br>réencodées | ... | Concaténation<br>à niveau k<br> |
| ------------- | ---------------------------- | --------------------------- | ------------------------- | --- | ------------------------------- |
| Taux d'erreur | $p$                          | $cp^{2}$                    | $c(cp^{2})^{2}=O(p^{4})$  | ... | $\frac{(cp)^{2k}}{c}$           |

Ainsi, un code concaténé à un niveau $k$ possède un taux d'erreur $\frac{(cp)^{2k}}{c}$. Si $p < p_{th} \equiv \frac{1}{c}$, on a une suppression d'erreur. Par exemple, pour le code de Steane, $p_{th} \sim 10^{-4} - 10^{-6}$.

Supposons un circuit idéal $C$ avec $q(n)$ portes ($p<p_{th}$). Comment peut-on simuler $C$ avec une probabilité d'échec $\varepsilon$? On cherche ici à montrer que la probabilité d'échec par porte est de $\frac{\varepsilon}{q(n)}$  dans le pire des cas.

$$
\begin{align}
\frac{(cp)^{2k}}{c} &\leq \frac{\varepsilon}{q(n)} \\
\frac{1}{(cp)^{2k}} &\geq \frac{q(n)}{\varepsilon} \\
2^{k} &\geq \frac{\log\left( \frac{q(n)}{c\varepsilon} \right)}{\log\left( \frac{1}{cp} \right)} \\
2^{k} &\geq O\left( \log\left( \frac{q(n)}{\varepsilon} \right) \right)
\end{align}
$$

Porte encodée - niveau 1: $d$ opérations
Porte encodée - niveau 2: $d^{2}$ opérations
...
Porte encodée - niveau k: $d^{k}$ opérations

On a donc que $d^{k} = O(\text{poly}(\log(q(n)\varepsilon)))$ opérations.

**Théorème (Théorème de seuil pour le calcul quantique):** La simulation tolérante aux fautes d'un circuit idéal $C$ comportant $q(n)$ portes avec une probabilité d'échec $\varepsilon$ requiert $O\left( \text{poly}\left( \log\left( \frac{q(n)}{\varepsilon} \right) \right) q(n) \right)$ opérations, à condition que chaque opération élémentaire échoue avec probabilité $p < p_{th}$.

# Complexité du calcul quantique

Pourquoi est-ce que le calcul quantique est difficile à simuler classiquement?

**Définition:** La satisfiabilité booléenne (SAT) est:

- Variables: $x_{i} \in \{ 0,1 \}, i=1,\dots,n$
- Négation: $\neg x_{i} = \bar{x}_{i}$
- Clauses disjonctives ("ou" logique): $c_{j} = (x_{p} \lor x_{q} \lor x_{r})$
- Formule (conjonction ("et" logique) de clauses): $F = c_{i} \land c_{j} \land \dots = \land_{j=1}^{m}c_{j}$

Existe-t-elle une assignation $\vec{x}$ qui satisfait $F$?

**Exemple:** 3SAT

| $x_{1}$ | $x_{2}$ | $x_{3}$ | $(x_{1}\lor x_{2}\lor x_{3})$ |
| ------- | ------- | ------- | ----------------------------- |
| 0       | 0       | 0       | 0                             |
| 0       | 0       | 1       | 1                             |
| 0       | 1       | 0       | 1                             |
| 0       | 1       | 1       | 1                             |
| 1       | 0       | 0       | 1                             |
| 1       | 0       | 1       | 1                             |
| 1       | 1       | 0       | 1                             |
| 1       | 1       | 1       | 1                             |

*Rajouter le dessin du circuit classique.*
*Rajouter le dessin du circuit quantique.*

La question de satisfiabilité se transforme:

$$
\exists \vec{x} F(\vec{x}) =^{?} 1 \iff \lvert \braket{ \vec{0} | U | \vec{0} } \rvert^{2} <^{?} 1
$$

Cela équivaut à dire que $\lvert \bra{ \vec{0} | U | 0\dots01 } \rvert^{2} >^{?} 0$. Or, comme la probabilité de mesurer une solution (dans le pire des cas où il n'y a qu'une solution) est de $O\left( \frac{1}{2^{n}} \right)$, alors il faut prendre un nombre exponentiel de mesures.

*Rajouter le dessin du circuit.* 

$$
\braket{ \vec{b} | U | \vec{a} } = \frac{1}{\sqrt{ 2^{n} }} \sum_{\vec{x}:\vec{B}(\vec{x})=\vec{b}} (-1)^{\varphi(\vec{x})}
$$
où $n$ est le nombre de portes $H$.

$$
\varphi(\vec{x}) = \sum_{\text{Portes H}} (\text{Valeurs à l'entrée}) \times (\text{Valeur à la sortie})
$$


$$
\begin{align}
\#(0) = \lvert \{ \vec{x} : \vec{B}(\vec{x}) =\vec{b} \text{ et } \varphi(\vec{x})=0 \} \rvert
\#(1) = \lvert \{ \vec{x} : \vec{B}(\vec{x}) =\vec{b} \text{ et } \varphi(\vec{x})=1 \} \rvert
\end{align}
$$

Donc,

$$
\braket{ \vec{b} | U | \vec{a} } = \frac{1}{\sqrt{ 2^{n} }} (\#(0) - \#(1))
$$
Problème de comptage!

SAT: NP
\#(0)/\#SAT: \#P
\#(0) - \#(1): GapP

$BQP \subseteq PP$

$P^{\#P} $