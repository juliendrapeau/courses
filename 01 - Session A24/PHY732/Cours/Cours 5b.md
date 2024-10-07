---
tags: 
created date: 26-09-2024 08:33
modified date: 07-10-2024 12:59
---
# Théorie de la correction d'erreur quantique

Un code est déterminé par l'encodage

$$
\ket{0} \to \ket{0}_{L}, \ \ket{1} \to \ket{1}_{L}
$$

dans un espace d'Hilbert à N qubits ($\ket{0}_{L}, \ \ket{1}_{L} \in \mathbb{C}^{2^{n}}$). Les vecteurs $\ket{0}_{L}$ et $\ket{1}_{L}$ génère un sous-espace $C$ et un projecteur sur $C$

$$
\hat{P} = \ket{0_{L}}\bra{0_{L}} + \ket{1_{L}}\bra{1_{L}}
$$

Une fois que l'erreur est détectée, on a un syndrome d'erreur, avec lequel on peut récupérer l'erreur et envoyer l'état dans le sous-espace de code.

$$
\text{ span } \{ \ket{000}, \ket{111} \} \subset \mathbb{C}^{8}
$$

Par example, $a \ket{100} + b \ket{011} \to a \ket{000} + b \ket{111}$. Chaque syndrome différent correspond à un sous-espace non-déformé orthogonal de $\mathbb{C}^{2^N}$. Si les sous-espaces ne sont pas orthogonaux, ce n'est pas possible de différentier les syndromes. De plus, les différents sous-espaces doivent être des versions non-déformées de l'espace de code original, dans le sens où les erreurs qui mappent aux différent sous-espaces doivent transformer les mots de code orthogonaux en état orthogonaux afin de pouvoir récupérer l'erreur. 

On va faire deux suppositions:

1. Le bruit est décrit par une opération $\varepsilon$
2. Le processus de correction d'erreur est effectué par une opération $R$ qui conserve la trace et on l'appelle *opération de correction d'erreur*.

$$
R = \text{ Détection et correction }
$$

**Définition:** Pour que la correction d'erreur soit considérée comme réussie, il faut que $\forall \ \rho$ dont le support se trouve dans l'espace $C$

$$
(R \circ \varepsilon)(\rho) \propto \rho
$$

parce que $\varepsilon$ peut ne pas conserver la trace. Par contre, $R$ doit réussir avec probabilité $1$.

**Théorème (Conditions de correction d'erreur quantique):** Soit $C$ un code quantique et $\hat{P}$ le projecteur sur $C$. Supposons que $\varepsilon(\rho) = \sum_{i} E_{i} \rho E_{i}^{\dagger}$ est son opération quantique. Alors, il existe une opération quantique $R$ de correction d'erreur sur $C$ pour $\varepsilon$ tel que $(R \circ \varepsilon)(\rho) \propto \rho$ si et seulement s'il existe une matrice Hermitienne $\propto$ tel que

$$
\hat{P}E^{\dagger}_{j} E_{j} \hat{P} = \alpha_{ij} \hat{P}
$$

**Preuve:** 

- $\impliedby$: On diagonalise: $d = U\alpha U^{\dagger}$. On définit $F_{k} = \sum_{j} U_{jk} E_{j}$. Alors, les opérations $\{ F_{k} \}_{k}$ génèrent aussi $\varepsilon$. Donc,

$$
\begin{align}
\hat{P}F_{k}^{\dagger}F_{k}\hat{P} &= \sum_{ij} U_{ki}^{\dagger}U_{jl} \hat{P} E_{i}^{\dagger} E_{j} \hat{P} \\
&= \sum_{ij} U_{ki}^{\dagger} U_{jl} \alpha_{ij} \hat{P} \\
&= d_{kl} \hat{P}
\end{align}
$$

On va utiliser la décomposition polaire.

**Théorème (Décomposition polaire):** Pour une matrice $A$, il existe une matrice unitaire $U$ tel que $A = U \sqrt{ A A^{\dagger} } = \sqrt{ A A^{\dagger} }U$. On peut utiliser cela pour normaliser $A$.

On a que $F_{k} \hat{P} = U_{k} \sqrt{ \hat{P} F_{k}^{\dagger} F_{k} \hat{P} } = \sqrt{ d_{kk} } U_{k} \hat{P}$. $F_{k}$ fait tourner le sous-espace de code dans le sous-espace défini par $\hat{P}_{k} = U_{k} \hat{P} U_{k}^{\dagger} = \frac{1}{\sqrt{ d_{kk} }} F_{k}\hat{P}F_{k}^{\dagger}$. De plus,

$$
\begin{align}
\hat{P}_{l} \hat{P}_{k} &= \hat{P}_{l}^{\dagger} \hat{P}_{k} \\
&= \frac{1}{\sqrt{ d_{ll} }} U_{l} \hat{P} F_{l}^{\dagger} \frac{1}{\sqrt{ d_{kk} }} F_{k} \hat{P} U_{k}^{\dagger} \\
&= \frac{1}{\sqrt{ d_{ll} d_{kk} }} U_{l} \hat{P} F_{l}^{\dagger} F_{k} \hat{P} U_{k}^{\dagger} \\
&= \frac{d_{lk}}{\sqrt{ d_{ll}d_{kk} }} U_{l} \hat{P} U_{k}^{\dagger} \\
&= 0 \text{ si } l \neq k
\end{align}
$$

car $d$ est diagonale. Le syndrome est donné par la mesure des projecteurs $\{  P_{k} \}_{k}$ dans laquelle on en ajoute plusieurs (si nécessaire) pour compléter $\sum_{k} \hat{P}_{k}^{\dagger}\hat{P}_{k} = \sum_{k}\hat{P}_{k} = I$. La récupération se fait avec $U_{k}^{\dagger}$, c'est-à-dire $R(\rho) = \sum_{k} U_{k}^{\dagger} \hat{P}_{k} \rho P_{k} U_{k}$. Soit $\rho$ un état dans $C$.

$$
\begin{align}
U_{k}^{\dagger} \hat{P}_{k} F_{l} \sqrt{ \rho } &= U_{k}^{\dagger}\hat{P}_{k}^{\dagger} F_{l} \hat{P} \sqrt{ \rho } \\
&= \frac{1}{\sqrt{ d_{kk} }} U_{k}^{\dagger} U_{k} \hat{P} F_{k}^{\dagger} F_{l} \hat{P} \sqrt{ \rho } \\
&= \frac{d_{kl}}{\sqrt{ d_{kk} }} \hat{P}\sqrt{ \rho } \\
&= \delta_{kl} \sqrt{ d_{kk} } \hat{P}
\end{align}
$$

$$
\begin{align}
(R \circ \varepsilon)(\rho) &= \sum_{kl} U_{k}^{\dagger}\hat{P}_{k}F_{l}\rho F_{l}^{\dagger}\hat{P}_{k}U_{k} \\
&= \sum_{kl} U_{k}^{\dagger} \hat{P}_{k}F_{l}\sqrt{ \rho }\sqrt{ \rho } F_{l}^{\dagger}\hat{P}_{k}U_{k} \\
&= \sum_{kl} \delta_{kl}\sqrt{ d_{kk} } \sqrt{ \rho } \delta_{kl} \sqrt{ d_{kk} } \sqrt{ \rho } \\
&= \sum_{kl} \delta_{kl}^{2} d_{kk} \rho \\
&= \sum_{k} d_{kk} \rho  \\
&\propto \rho
\end{align}
$$

- $\implies$: $R(\sigma) = \sum_{j} R_{j} \sigma R_{j}^{\dagger}$. On définit $\varepsilon_{c}(\rho) = \varepsilon(\hat{P}\rho \hat{P})$, $\hat{P}\rho \hat{P} \in C \  \forall \ \rho$. Donc, $R(\varepsilon_{c}(\rho)) \propto \hat{P}\rho \hat{P}$ et $R(\varepsilon_{c}(\rho)) = c(\rho) \hat{P}\rho \hat{P}$ où $c(\rho)$ est une constante selon $\rho$. 

$$
\begin{align}
R(\varepsilon_{c}(p\rho + q\sigma)) &= c(p\rho + q\sigma) \hat{P} (p\rho + q\sigma)\hat{P} \\
&= c(p\rho + q\sigma) p\hat{P}\rho \hat{P} + c(p\rho + q\sigma) q \hat{P} \sigma \hat{P} \\
pR(\varepsilon_{c}(\rho)) + qR(\varepsilon_{c}(\sigma)) &= p c(\rho) \hat{P} \rho \hat{P} + q c(\sigma) \hat{P} \rho \hat{P} \\
\end{align}
$$

On a que $c(p\rho + q\sigma) = c(\rho)$. Donc, $c(\rho)$ ne dépend pas de $\rho$ (?). Alors, $R(\varepsilon_{c}(\rho)) = c\hat{P} \rho \hat{P}$. Ainsi,

$$
\sum_{ij} R_{j}E_{i} \hat{P}\rho \hat{P} E_{i}^{\dagger} R_{j}^{\dagger} = c \hat{P}\rho \hat{P} \  \forall \ \rho
$$
Il s'agit de deux opérations quantiques équivalentes. Donc, l'opération quantique avec éléments $\{ R_{j} E_{i} \hat{P} \}_{ij}$ est la même que l'opération avec élément $\{ \sqrt{ c } \hat{P} \}$. 

$$
\implies \exists c_{k,i} \in C \text{ t.q } R_{k}E_{i}\hat{P} = c_{ki} \hat{P} \  \forall  \ k,i
$$

On se retrouve avec $\hat{P}E_{i}^{\dagger} R_{k}^{\dagger} R_{k} E_{j} \hat{P} = c_{ki}^{\star} c_{kj}\hat{P}$. Mais, $R$ conserve la trace ($\sum_{k} R_{k}^{\dagger} R_{k} = I$).

$$
\begin{align}
\sum_{k} \hat{P} E_{i}^{\dagger} R_{k}^{\dagger} R_{k} E_{j}\hat{P} &= \hat{P}E_{i}^{\dagger} E_{j}\hat{P} \\
&=\sum_{k} c_{ki}^{\star} c_{kj} \hat{P} \\
&= \alpha_{ij} \hat{P}
\end{align}
$$

avec $\alpha_{ij} = \sum_{k} c_{ki}^{\star} c_{kj}$ qui est hermitien. Alors, $\hat{P} E_{i}^{\dagger} E_{j} \hat{P} = \alpha_{ij} \hat{P}$. $\square$

## Discrétisation des erreurs

**Théorème:** Soit $C$, $R$ et $\varepsilon$ comme dans le dernier théorème. Supposons que $\mathcal{F}$ est une autre opération quantique avec éléments $\{ F_{j} \}_{j}$ tel quel $F_{j} = \sum_{i} m_{ji} E_{j}$. Alors, $R$ corrige aussi le processus de bruit décrit par $\mathcal{F}$.

**Preuve:**

On a que $\hat{P}E_{i}^{\dagger}E_{j}\hat{P} = \alpha_{ij} \hat{P}$. On suppose que $\alpha$ est diagonale. L'opération de correction a des éléments $\{ U_{k}^{\dagger} \hat{P}_{k} \}_{k}$ tel que $U_{k}^{\dagger} P_{k}E_{i}\sqrt{ \rho } = \delta_{ki} \sqrt{ \alpha_{kk} } \sqrt{ \rho }$. Comme $F_{j} = \sum_{i} m_{ji} E_{i}$, 

$$
\begin{align}
U_{k}^{\dagger}\hat{P}_{k}E_{i}\sqrt{ \rho } &= \sum_{i} m_{ji} \delta_{ki} \sqrt{ \alpha_{kk} } \sqrt{ \rho } \\
&= m_{jk} \sqrt{ \alpha_{kk} }\sqrt{ \rho }
\end{align}
$$ 
Alors, on a que

$$
\begin{align}
R(\mathcal{F}(\rho)) &= \sum_{kj} U_{k}^{\dagger}\hat{P}_{k} F_{j}\rho F_{j}^{\dagger} P_{k}U_{k} \\
&= \sum_{kj} \lvert m_{jk} \rvert^{2} \alpha_{kk} \rho \\
& \propto \rho
\end{align}
$$

On appelle $\{ E_{i} \}_{i}$ l'ensemble des erreurs corrigées par le code $C$ et l'opération $R$ de correction.

**Exemple:** Pour le code de Shor, pour démontrer qu'il corrige des erreurs arbitraires à un qubit, disons décrites par des opérateurs $\{ E_{i} \}_{i}$, on a que chaque $E_{i}$ est une combinaison linéaire de $\{ I,Z,Y,Z \} = \{ \sigma_{0}, \sigma_{1}, \sigma_{2}, \sigma_{3} \}$. Donc, il est suffisant de vérifier que le code satisfait les équations

$$
\begin{align}
\hat{P} \sigma_{i}^{1} \sigma_{j}^{1} \hat{P} &= \alpha_{ij} \hat{P} \  \forall  \ i,j \\ \\
&\vdots \\
\hat{P} \sigma_{i}^{q} \sigma_{j}^{q} \hat{P} &= \alpha_{ij}^{(q)} \hat{P}
\end{align}
$$

où $\sigma^{1}$ implique sur le qubit 1. Pour être sûr que le code corrige des erreurs arbitraires dans le qubit 1. Par contre, si on est capable de corriger des erreurs de canal dépolarisant

$$
\varepsilon(\rho) = (1-p)\rho + \frac{\rho}{3} (X\rho X + Y\rho Y + Z\rho Z)
$$

on est capable de corriger des erreurs arbitraires.


On doit être capable de corriger des erreurs à partir de Paulis pour corriger n'importe quelle erreur. *Ce n'est pas vrai pour les systèmes classiques analogues*.

1. Non-clonage $\leftrightarrow$ $C$
2. Erreurs discrètes $\leftrightarrow$ Erreurs continues
3. Mesure $\leftrightarrow$ Mesure seulement l'erreur (le syndrome)