
**Théorème (Conditions de correction d'erreur pour les codes stabilisateurs):** Soit $C(S)$ un $[n,k]$-code stabilisateur avec $S < G_{n}$ et $-I \notin S$. Soit $\{ E_{j} \}_{j}$ tel que $E_{j}^{\dagger}E_{k} \notin N(S) \setminus S \ \forall \ j,k$. Alors, $C(S)$ peut corriger les erreurs $\{ E_{j} \}_{j}$.

**Preuve:**

Soit $P$ le projecteur sur $C(S)$. On a que $P=V_{S}$. On a deux cas: $E_{j}^{\dagger}E_{k} \in S$ ou $E_{j}^{\dagger}E_{k} \in G_{n} \setminus N(S)$.

*Rajouter le dessin.*

*Cas 1*: $E_{j}^{\dagger}E_{k} \in S$.

On sait que $P=\ket{0}_{L}\bra{0}_{L} + \ket{1}_{L}\bra{1}_{L}$.

$$
\begin{align}
E_{j}^{\dagger}E_{k}P &= E_{j}^{\dagger}E_{k} (\ket{0}_{L}\bra{0}_{L} + \ket{1}_{L}\bra{1}_{L}) = P \\
&\implies PE_{j}^{\dagger}E_{k}P = P \\
&\implies \alpha = \begin{pmatrix}
1  & \dots  & 1 \\
\vdots &  & \vdots \\
1 & \dots & 1
\end{pmatrix}
\end{align}
$$

où $\alpha$ est hermitien.

*Cas 2:* $E_{j}^{\dagger}E_{k} \notin N(S) = Z(S)$.

$E_{j}^{\dagger}E_{k} \notin G_{n}$. Donc, $\exists g_{1} \in S$ tel que $E_{j}^{\dagger}E_{k}g_{1} = -g_{1} E_{j}^{\dagger}E_{k}$. 

On complète pour obtenir un ensemble générateur de $S$.

$$
\braket{ g_{1}, \dots , g_{n-k} } = S
$$

Donc, $P = \frac{1}{2^{n-k}}\prod_{j=1}^{n-k} (I+g_{j})$.

$$
\begin{align}
E_{j}^{\dagger}E_{k}P &= E_{j}^{\dagger}E_{k} (I+g_{1}) \frac{1}{2^{n-k}} \prod_{j=2}^{n-k} (I+g_{j}) \\
&= (I-g_{1})E_{j}^{\dagger}E_{k} \frac{1}{2^{n-k}} \prod_{j=2}^{n-k} (I+g_{j})
\end{align}
$$

Alors,

$$
 \begin{align}
PE_{j}^{\dagger}E_{k}P = \frac{1}{2^{n-k}}\prod_{j=2}^{n-k} (I+g_{j}) (I+g_{1})(I-g_{1})E_{j}^{\dagger}E_{k} \frac{1}{2^{n-k}}\prod_{j=2}^{n-k} (I+g_{j})
\end{align}
$$

Comme $(I+g_{1})(I-g_{1})=I+g_{1}-g_{1}-g_{1}^{2} = 0 \ \forall \ j,n$, alors on a que $PE_{j}^{\dagger}E_{k}P = 0$ et donc que

$$
\alpha = \begin{pmatrix}
0 & \dots & 0 \\
\vdots &  & \vdots \\
0 & \dots & 0
\end{pmatrix}
$$

qui est une matrice hermitienne. $\square$

Si $S = \braket{ g_{1}, \dots, g_{n-k} }$ qui corrige $\{ E_{j} \}_{j}$, on mesure $g_{1}, \dots, g_{n-k}$ et on obtient $\beta_{1}, \dots, \beta_{n-k}$. Si $E_{j}$ se produit, le syndrôme est décrit par les $\rho$ tel que 

$$
E_{j}g_{l}E_{j}^{\dagger} = \beta_{l}g_{l} \ \forall \ l
$$

et on corrige en appliquant $E_{j}^{\dagger}$.

## Exemples

### Code bit flip à trois qubits

Pour le code de répétition, $S = \braket{ Z_{1}Z_{2},Z_{2}Z_{3} }$, $\{ X_{1},X_{2},X_{3} \}$.

$$
\begin{align}
X_{1}Z_{1}Z_{2}X_{1} = - Z_{1}Z_{2} \\
X_{1}Z_{2}Z_{3}X_{1} = + Z_{2}Z_{3} \\
X_{2}Z_{1}Z_{2}X_{2} = - Z_{1}Z_{2} \\
X_{2} Z_{2} Z_{3} X_{2} = - Z_{2} Z_{3} \\
X_{3} Z_{1} Z_{1} X_{3} = + Z_{1}Z_{2} \\
X_{3} Z_{2} Z_{3} X_{3} = - Z_{2} Z_{3}
\end{align}
$$
### Code de Shor à 9 qubits

$$
\begin{align}
\ket{0}_{L } &= \frac{1}{2\sqrt{ 2 }} (\ket{000}+\ket{111})^{\otimes 3} \\
\ket{1}_{L} &= \frac{1}{2\sqrt{ 2 }} (\ket{000}-\ket{111})^{\otimes 3}
\end{align}
$$

$$
\begin{align}
g_{1} = Z_{1}Z_{2} \\
g_{2} = Z_{2}Z_{3} \\
g_{3} = Z_{4}Z_{5} \\
g_{4} = Z_{5}Z_{6} \\
g_{5} = Z_{7} Z_{8} \\
g_{6} = Z_{8}Z_{9} \\
g_{7} = X_{1}X_{2}X_{3}X_{4}X_{5}X_{6} \\
g_{8} = X_{4}X_{5}X_{6}X_{7}X_{8}X_{9}
\end{align}
$$

$$
\begin{align}
\bar{X} = Z_{1}Z_{2}Z_{3}Z_{4}Z_{5}Z_{6}Z_{7}Z_{8}Z_{9} \\
\bar{Z} = X_{1}X_{2}X_{3}X_{4}X_{5}X_{6}X_{7}X_{8}X_{9}
\end{align}
$$

$$
\bar{X} \cdot \bar{Z} = - \bar{Z} \cdot \bar{X}
$$

### Code à 5 qubits

$$
\begin{align}
g_{1} = XZZXI \\
g_{2} = IXZZX \\
g_{3} = XIXZZ \\
g_{4} = ZXIXZ
\end{align}
$$

On a que $S = \braket{ g_{1}, \dots, g_{4} } < G_{S}$ et $\text{dim}V_{S} = 2^{1}$.

$$
\begin{align}
\bar{Z} = ZZZZZ \\
\bar{X} = XXXXX
\end{align}
$$

$$
\braket{ g_{1}, \dots, g_{n-k}, \bar{Z}_{1}, \dots, \bar{Z}_{n} }
$$

Lors du processus de correction d'erreur, la topologie de l'ordinateur quantique peut être un problème. En effet, si tous les qubits ne sont pas connectés ensemble, alors des portes SWAP devront être utilisées afin d'appliquer les portes souhaitées et de bien corriger les erreurs. Comment est-ce que cela nuit à la correction d'erreur?

*Rajouter le dessin.*

### Codes de surface

Les codes de surface permettent d'appliquer des portes à 2 qubits localement. Le coût à payer est un plus grand nombre de qubits physiques et un plus grand nombre de portes à appliquer.



$$
 S = \braket{ Z_{1}Z_{3}Z_{4}Z_{6}, Z_{2}Z_{4}Z_{5}Z_{7}, \dots, X_{1}X_{3}, X_{1}X_{2}X_{4}, \dots }
$$

$S$ a 12 générateurs, donc $\text{dim}V_{S} = 2^{0} = 1$.

