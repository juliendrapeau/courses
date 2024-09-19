---
tags: 
created date: 05-09-2024 08:39
modified date: 08-09-2024 16:26
---
## Propriétés générales des matrices densités

**Définition:** 
- Un état $\ket{\psi}$ est un *état pur*.
- Un mélange statistique $\{ \ket{\psi_{k}}, p_{k} \}_{k=1}^N$ est un *état mixte*.

**Évolution:**

- Pour un état pur $\ket{\psi'} = U \ket{\psi}$, on a que

$$
\begin{align}
\rho' &= \ket{\psi'} \bra{\psi'}  \\
&= U \ket{\psi} \bra{\psi} U^{\dagger} \\
&= U \rho U^{\dagger}
\end{align}
$$
- Pour un état mixte $\rho = \sum_{k} p_{k} \rho_{k}$, où $\rho_{k} = \ket{\psi_{k}} \bra{\psi_{k}}$ et $\ket{\psi_{k}'}= U \ket{\psi_{k}}$, on a que

$$
\begin{align}
\rho' &= \sum_{k} p_{k} U \rho_{k} U^{\dagger} \\
&= U \left( \sum p_{k} \rho_{k} \right) U^{\dagger} \\
&= U \rho U^{\dagger}
\end{align}
$$

Pour distinguer les états purs des états mixtes, on peut étudier $\rho^{2}$. Pour un état pur, $\rho_{k}^{2} = \rho_{k}$, alors $\mathrm{Tr}(\rho_{k}^2) = \mathrm{Tr}(\rho_{k}) = 1$. Pour un état mixte, $\rho^{2} = \sum_{k} p_{k}^2 \rho_{k}^2 = \sum_{k} p_{k}^2 \rho_{k}$, alors $\mathrm{Tr}(\rho_{k}^2) = \dots < 1$.

*Il manque de quoi je pense?*

**Théorème:** Un opérateur $\rho$ est l'opérateur densité d'un mélange $\{ \psi_{k}, \rho_{k} \}_{k=1}^N$ si et seulement si

1. $\mathrm{Tr}(\rho) = 1$
2. $\underbrace{ \braket{ \phi | \rho | \phi }  }_{ \text{ Opérateur positif } }\geq 0 \quad \forall \ket{\phi}$

Un opérateur positif semi-défini si toutes les valeurs propres sont non-négatives. *La formulation $\{ \psi_{k}, \rho_{k} \}_{k=1}^N$ implique que l'opérateur doit être hermitien.

**Preuve:** 

$\implies$ Si $\rho = \sum_{k} p_{k} \rho_{k}$, $\rho_{k} = \ket{\psi_{k}} \bra{\psi_{k}}$, $\mathrm{Tr}(\rho) = 1$. Alors,

$$
\begin{align}
\braket{ \phi | \rho | \phi } &= \sum_{k} p_{k} \braket{ \phi | \psi_{k} } \braket{ \psi_{k} | \phi }  \\
&= \sum_{k} p_{k} \lvert \braket{ \phi | \psi_{k} }  \rvert^{2}  \\
&= \geq
\end{align}
$$

$\impliedby$ Si $\rho$ est tel que $\braket{ \psi | \rho | \psi } \geq 0 \quad \forall \ket{\psi}$, $\rho = \sum_{j} \lambda_{j} \ket{j} \bra{j}$ est sa décomposition spectrale et $\braket{ j | \rho | j } = \lambda_{j} \geq 0$ et donc $1 = \mathrm{Tr}(\rho) = \sum_{j} \lambda_{j}$. Alors, $\rho$ est la matrice densité de l'état mixte $\{ \ket{j}, \lambda_{j} \}_{j}$. 

Les mesures quantiques sont décrites par une collection d'opérateurs de mesure $\{ M_{m} \}_{m}$. Ce sont des opérateurs agissant sur l'espace d'état du système mesuré. L'indice *m* fait référence aux résultats de mesure qui peuvent se produire dans l'expérience. Si l'état du système quantique est $\ket{\psi}$ immédiatement avant la mesure, alors la probabilité que le résultat *m* se produise est donné par

$$
\mathbb{P}_{\ket{\psi} }(m) = \braket{ \psi | M_{m}^{\dagger} M_{m} | \psi }
$$

et l'état du système après la mesure est

$$
\frac{M_{m}\ket{\psi} }{\sqrt{ \braket{ \psi | M_{m}^{\dagger}M_{m} | \psi }  }}
$$
On a que $1 = \sum_{m} \braket{ \psi | M_{m}^{\dagger}M_{m} | \psi } \implies \sum_{m} M_{m}^{\dagger}M_{m} = \mathbb{1}$. $\square$

**Exemple:** Si $\ket{\psi} = \alpha \ket{0} + \beta \ket{1}$, $M_{0} = \ket{0} \bra{0}$, $M_{1} = \ket{1} \bra{1}$, alors

$$
\begin{align}
\mathbb{P}_{\ket{\psi}}(0) &= \braket{ \psi | M_{0}^{\dagger}M_{m} | \psi } = \braket{ \psi | M_{0} | \psi } = \lvert \alpha \rvert^{2} \\
\mathbb{P}_{\ket{\psi} }(1) &= \lvert \beta \rvert^{2} 
\end{align}
$$

$$
m = 0 \implies \frac{M_{0} \ket{\psi} }{\lvert \alpha \rvert } = \frac{\alpha \ket{0} }{\lvert \alpha \rvert }
$$

Une *mesure projective* est décrite par un observable $M$ dans l'espace d'état. L'observable à une décomposition spectrale

$$
M = \sum_{m} m \hat{P}_{m} = \sum_{m} m \ket{m} \bra{m}
$$
$$
\mathbb{P}_{\ket{\psi}}(m) = \braket{ \psi | \hat{P}_{m} | \psi }
$$
Après la mesure, l'état collapse dans l'état

$$
\frac{\hat{P}_{m} \ket{\psi} }{\sqrt{ \braket{ \psi | \hat{P}_{m} | \psi }  }}
$$

**Postulats de la mécanique quantique:**

$$
\begin{array}{|c|c|c|}
\text{ Postulats } & \text{ Vecteur d'état } & \text{ Matrice densité } \\
\hline \\
1.\text{ Description } & \ket{\psi}  & \rho \\
2. \text{ Évolution unitaire } & \ket{\psi'} = U \ket{\psi}  & \rho' = U\rho U^{\dagger} \\
 & \frac{ \partial }{ \partial t } \ket{\psi(t)}  = i \hbar \hat{H}(t) \ket{\psi(t)} & \frac{ \partial }{ \partial t } \rho (t) = \frac{1}{i\hbar} [\bar{H}(t), \rho(t)] \\
3. \text{ Mesure } & \hat{A} \ket{\lambda_{n}} = \lambda_{n} \ket{\mu_{n}}  & \mathbb{P}_{\rho}(\lambda_{n}) = \mathrm{Tr}(\rho \hat{A}) \\
 & \mathbb{P}_{\ket{\psi} }(\lambda_{n}) = \lvert \braket{ \mu_{n} | \psi }  \rvert^{2}  & \text{ Valeur moyenne } = \mathrm{Tr}(\rho \hat{P}_{n}) \\
 & \braket{ \psi | \hat{A} | \psi } = \sum_{n} \lambda_{n} \mathbb{P}_{\ket{\psi} } (\lambda_{n}) & \hat{P}_{n} = \ket{\mu_{n}} \bra{\mu_{n}} \\
 4. \text{ Normalisation } & \ket{\psi} \to \frac{M_{M} \ket{\psi} }{\sqrt{ \braket{ \psi | M_{m}^{\dagger}M_{m} | \psi }  }} & \rho \to \frac{M_{m} \rho M_{m}^{\dagger}}{\mathrm{Tr}(M_{m}^{\dagger}M_{m}\rho)} \\
 &  &  \sum_{m} M_{m}^{\dagger}M_{m} = \mathbb{1} \\
5. \text{ Système composé } & \ket{\psi_{1}} \otimes \ket{\psi_{2}} \otimes \dots \otimes \ket{\psi_{n}} &  \rho_{1} \otimes \rho_{2} \otimes  \dots \otimes \rho_{n}  
\end{array}
$$

**Exemple:**

$$
\begin{align}
\rho &= \frac{3}{4} \ket{0} \bra{0} + \frac{1}{4} \ket{1} \bra{1} \\
\rho^{2} &= \frac{9}{16} \ket{0} \bra{0} + \frac{1}{16} \ket{1} \bra{1} \\
\ket{a} &= \sqrt{ \frac{3}{4} } \ket{o} + \sqrt{ \frac{1}{4} } \ket{1} \\
\ket{b} &= \sqrt{ \frac{3}{4} } \ket{0} - \sqrt{ \frac{1}{4} } \ket{1}  \\
\rho &= \frac{1}{2} \ket{a} \bra{a}  + \frac{1}{2} \ket{b} \bra{b}   
\end{align}
$$

## Matrice densité partielle 

Considérons un système quantique constitué de deux sous-systèmes $A$ et $B$. On choisit des bases d'états orthonormées $\{ \ket{\phi_{j}^{A}} \}_{j}$ et $\{ \ket{\phi_{j}^{B}} \}_{j}$ pour les deux sous-systèmes. Donc, $\{ \ket{\psi_{j}^{A}} \otimes \ket{\psi_{j}^{B}} \}_{i, j}$ est une base pour le système entier.

Si $\rho$ est un état dans le système $A$,

$$
\mathrm{Tr}(\rho) = \sum_{j} \braket{ \phi_{j}^{A} | \rho | \phi_{j}^{A} }
$$

Si $\rho$ est un état dans le système en entier $AB$,

$$
\mathrm{Tr}(\rho) = \sum_{j} \bra{\psi_{j}^{A}} \braket{ \psi_{j}^{B} | \rho | \psi_{j}^{B} } \ket{\psi_{j}^{A}}
$$

**Définition:** La matrice densité réduite de $\rho$ est

$$
\rho^{A} = \sum_{j} \braket{ \phi_{j}^{B} | \rho | \phi_{j}^{B} } 
$$
et l'opération

$$
\mathrm{Tr}_{B}(\rho) = \sum_{j} \braket{ \phi_{j}^{B} | \rho | \phi_{j}^{B} }
$$

est la trace partielle sur le sous-espace $B$.

Si $\hat{M} = \hat{m}_{m} \otimes I_{B}$, alors

$$
\begin{align}
\braket{ \hat{M} }_{\rho} &= \mathrm{Tr}(\rho M) \\
&= \sum_{i,j} \braket{ \phi_{i}^{A} | \braket{ \phi_{j}^{B} | \rho(\hat{m}_{A} \otimes I_{B}) | \phi_{j}^{B} }  | \phi_{i}^{A} } \\
&= \sum_{i,j} \braket{ \phi_{i}^{A} | \hat{m}_{A} \braket{ \phi_{j}^{B} | \rho | \phi_{j}^{B} }  | \phi_{i}^{A} } \\
&= \sum_{j} \braket{ \phi_{j}^{A} | \hat{m}_{A} \rho^{A} | \phi_{j}^{A} } \\
&= \mathrm{Tr}_{A}(\hat{m}_{A} \rho^{A})
\end{align}
$$

$$
\rho =\overbrace{  \begin{pmatrix}
a & b & c & d \\
e & f & g & h \\
i & j & k & l \\
m & n & o & p
\end{pmatrix}S }^{ \ket{0_{A}0_{B}} \quad\ket{0_{A}1_{B}} \quad \ket{1_{A}0_{B}} \quad \ket{1_{A}1_{B}} }
= a \ket{00} \bra{00} + b \ket{01} \bra{00} + \dots 
$$

$$
\begin{align}
\braket{ 0_{B} | 0_{A} 0_{B}  } &= \ket{0_{A}} \braket{ 0_{B} | 0_{B} } = \ket{0_{A}} \\
\braket{ 1_{A} | 1_{A}0_{B} } &= \ket{0_{B}}  \\
\braket{ 0_{B} | 0_{A}1_{B} } &= \ket{0} \braket{ 0_{B} | 1_{B} } = 0  
\end{align}
$$

$$
\begin{align}
\mathrm{Tr}_{B}(\rho) &= \braket{ 0_{B} | \rho | 0_{B} } + \braket{ 1_{B} | \rho | 1_{B} }  \\
&= \braket{ 0_{B} | (a \ket{0_{A}0_{B}} \bra{0_{A}0_{B}} + b \ket{0_{A}1_{B}} \bra{0_{A}0_{B}} + \dots) | 0_{B} }+ \braket{ 1_{B} | \rho | 1_{B} } \\
&= a \ket{0_{A}} \bra{0_{A}} + c \ket{1_{A}} \bra{0_{A}} + \dots \\
&= \begin{pmatrix}
a & c \\
j & k
\end{pmatrix}+ \begin{pmatrix}
f & h \\
n & p
\end{pmatrix} \\
&= \begin{pmatrix}
a + f & c + h \\
j + n & k + p
\end{pmatrix}
\end{align}
$$

$$
\begin{align}
\mathrm{Tr}_{A}(\rho) &= \braket{ 0_{A} | \rho | 0_{A} } + \braket{ 1_{A} | \rho | 1_{A} }  \\
&= \begin{pmatrix}
a & b \\
e & f
\end{pmatrix} + \begin{pmatrix}
k & l \\
o & p
\end{pmatrix} \\
&= \begin{pmatrix}
a+k & b+l \\
e+o & f+p
\end{pmatrix}
\end{align}
$$

**Exemple:** Soit l'état $\ket{\psi} = \frac{1}{\sqrt{ 2 }} (\ket{00}+\ket{01})$. Alors,

$$
\rho = \frac{1}{2} (\ket{00} \bra{00} + \ket{00} \bra{01} + \ket{01} \bra{00} + \ket{01} \bra{01} ) = \frac{1}{2} \begin{pmatrix}
1 & 1 & 0 & 0 \\
1 & 1 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$
$$
\mathrm{Tr}_{B}(\rho) = \frac{1}{2} \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} + \frac{1}{2} \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} = \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} = \ket{0} \bra{0} 
$$
$$
\mathrm{Tr}_{A}(\rho) = \frac{1}{2} \begin{pmatrix}
1 & 1 \\
1 & 1
\end{pmatrix} = \begin{pmatrix}
\frac{1}{2} & \frac{1}{2} \\
\frac{1}{2} & \frac{1}{2}
\end{pmatrix} = \rho^{B} = U \begin{pmatrix}
1 & 0 \\
0 & 0
\end{pmatrix} U^{\dagger}
$$

$$
\det(\rho^{B} - \lambda \mathbb{1}) = \det \begin{pmatrix}
\frac{1}{2} - \lambda & \frac{1}{2} \\
\frac{1}{2} & \frac{1}{2} - \lambda
\end{pmatrix}
= \left( \frac{1}{2} - \lambda \right)\left( \frac{1}{2}-\lambda \right)-\frac{1}{4} = \lambda (\lambda - 1)
$$
*Fini?*