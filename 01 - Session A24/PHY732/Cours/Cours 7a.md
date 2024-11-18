---
tags: 
created date: 07-10-2024 13:32
modified date: 11-11-2024 13:33
---
**Example:** Soit
$$
\mathbb{Z}_{2} \times \mathbb{Z}_{2} = \{ (0,0), (0,1), (1,0), (1,1) \}
$$

Un sous-groupe de ce groupe est $G = \{ (0,0), (0,1) \}$. Soit l'homomorphisme

$$
\begin{align}
f: \mathbb{Z}_{2} \times \mathbb{Z}_{2} &\to Z_{2} \\
(0,0) &\to 0 \\
(0,1) &\to 0
\end{align}
$$

1. $f((0,0)+(0,1)) = f(0,1) = 0$
2. $f(0,0)+f(0,1)=0+0=0$

Il s'agit bien d'un homomorphisme comme

1. $f((a,b)+(c,d)) = f(a+c,b+d) = a+c$
2. $f(a,b)+f(c,d) = a+c$ 

On remarque que
$$
\begin{align}
\text{Ker}f &= \{ (a,b) | f(a,b)=0 \} \\
&= \{ (a,b) | a=0 \} \\
&= \{ (0,b) \}
\end{align}
$$

Donc, on peut trouver des homomorphismes entre deux groupes en calculant le noyau.

Soit

| $\cdot$ | I   | X   | Y   | Z   |
| :-----: | --- | --- | --- | --- |
|    I    | I   | X   | Y   | Z   |
|    X    | X   | I   | iZ  | -iY |
|    Y    | Y   | -iZ | I   | iX  |
|    Z    | Z   | iY  | -iX | I   |

On définit le groupe $G_{1} = \{ \pm I, \pm iI, \pm X, \pm iX, \pm Y, \pm iY, \pm Z, \pm iZ  \}$. On le nomme le *groupe de Pauli à 1 qubit*. On a que $G_{2} = \{ P \otimes Q | P,Q \in G_{1} \}$ pour deux qubits. Le *groupe de Pauli à n qubits* est définit comme $G_{n} = \{ P_{1} \otimes \dots \otimes P_{n} | P_{j} \in G_{1} \}$.

Soit un groupe $H = \{I, X \}$. On trouve avec ce groupe que $X(-iY)=Z$, $(-iY)X = -i(-i)Z = -Z$, $Z(-iY)=-i(-i)X=-X$. On peut générer alors

$$
H' = \{ I, X, Z, -iY, -Z, -X, \dots \} = G_{1}
$$

**Définition:** Soit $G$ un groupe et $a \in G$, le *sous-groupe engendré* par $a$ est

$$
\braket{ a } = \{ a^{n} : n \in \mathbb{Z} \}
$$

On a en particulier que $a^{0} = e_{G}$. Comme $n \in \mathbb{Z}$, alors on a que $\braket{ a^{-1} } = \braket{ a } \neq \braket{ a^{2} }$. Par exemple, $\braket{ X } = H = \{ I, X \}$.

**Définition:** Soit $S$ un sous-ensemble d'un groupe $G$. Un *mot* sur $S$ est un élément $w \in G$ de la forme $w = x_{1}^{l_{1}} \dots x_{n}^{l_{n}}$, pour $x_{j} \in S$, $l_{j} \in \{ \pm 1 \}$, $n \geq 1$.

**Théorème:** Soit $S$ un sous-ensemble d'un groupe $G$. Alors,

$$
\braket{ S } = \{ \text{mots sur } S \}
$$

Par exemple, $\braket{ X,Z } = H' = \dots$

**Notation:** Si $S=\{ x_{1}, \dots , x_{n} \}$, $\braket{ S } = \braket{ x_{1}, \dots, x_{n} }$. Les $x_{j}$ sont les générateurs de $\braket{ S }$.

**Définition:** On dit que $x_{1}, \dots, x_{n} \in G$ sont *indépendants* si $\ \forall \ j=1,\dots,n$

$$
\braket{ x_{1},\dots,x_{j-1},x_{j+1},\dots,x_{n} } \subsetneq \braket{ x_{1},\dots,x_{n} }
$$

Si $P \in G_{1}$, et $\ket{\psi}$ un état à un qubit, $P\ket{\psi}$ est un état à un qubit.

**Définition:** Soit $G$ un groupe et $X \neq \emptyset$ un ensemble. Une action de $G$ sur $X$ est une fonction

$$
\begin{align}
\cdot : G \times X &\to X \\
(g,x) &\to g \cdot x
\end{align}
$$

tel que

1. $e_{G} \cdot x = x \ \forall \ x \in X$
2. $h \cdot (g \cdot x) = (h * g) \cdot x \ \forall \ h,g \in G, \ \forall \ x \in X$

Soit $P,Q \in G_{1}$ et $\ket{\psi}$ un état à un qubit.

$$
\begin{align}
P \cdot (Q \cdot \ket{\psi}) &= P \cdot (Q \ket{\psi}) = P(Q\ket{\psi}) \\
PQ \cdot \ket{\psi} &= (PQ)\ket{\psi}
\end{align}
$$

On a que $A \subsetneq A \subset B, A \neq B$.

Soit $\ket{\psi} = \frac{1}{\sqrt{ 2 }} (\ket{00} + \ket{11}$ et $G_{2}$. On a que $X_{1}X_{2}\ket{\psi}=\ket{\psi}$ et $Z_{1}Z_{2}\ket{\psi}=\ket{\psi}$.

**Définition:** Supposons que le groupe $G$ à une action sur $X$ et $x \in X$. Le *stabilisateur* de $x$ est

$$
\text{stab}(x) = \{ g \in G | g \cdot x = x \}
$$
On a que $e_{G} \cdot x = x \implies e_{G} \in \text{stab}(x) \neq \emptyset$. Soit $g, g' \in \text{stab}(x)$, $g \cdot x =x$ et $g' \cdot x = x$.

$$
(g * g') \cdot x = g \cdot (g' \cdot x) = g \cdot x = x
$$

Cela implique que $g*g' \in \text{stab}(x)$.

Soit $g \in \text{stab}(x)$ et $g^{-1} \in G$.

$$
\begin{align}
g \cdot x = x & \implies g^{-1} \cdot (g \cdot x) = g^{-1} \cdot x \\
&\implies (g^{-1}*g) \cdot x = g^{-1} \cdot x \\
& \implies e_{G} \cdot x = g^{-1} \cdot x \\
&\implies x = g^{-1} \cdot x
\end{align}
$$

Donc, $g^{-1} \in \text{stab}(x)$. Ainsi, $\text{stab}(x)$ est un sous-groupe de $G$.

**Exemple:** Soit $\ket{\psi} = \frac{1}{\sqrt{ 2 }} (\ket{00} + \ket{11})$, $X_{1}X_{2}\ket{\psi}=\ket{\psi}$, $Z_{1}Z_{2} \ket{\psi}= \ket{\psi}$. Celui implique que $\{ X_{1}X_{2}, Z_{1}Z_{2} \} \subset \text{stab}(\ket{\psi})$ et que $\braket{ X_{1}X_{2}, Z_{1}Z_{2} } = \text{stab}(\ket{\psi})$.

**Définition:** Soit $S$ un sous-ensemble d'un groupe $G$. Le *centralisateur* est

$$
C_{G}(S) = \{ g \in G | gs=sg \ \forall \  s \in S \}
$$

Le *normalisateur* est

$$
N_{G}(S) = \{ g \in G | gSg^{-1} = S \} \neq \emptyset
$$

Donc, le centralisateur d'un sous-groupe est l'ensemble des éléments du groupe qui commutent avec tous les éléments du sous-groupe.

On a que $gSg^{-1} = \{ gsg^{-1} | s \in S \}$. De plus, $e_{G} \in C_{G}(S)$, $eSe = \{ ese | s \in S \} = \{ s|s \in S \} = S$. $e_{G} \in N_{G}(S)$.

Soit $g, g' \in C_{G}(S)$, $gs=sg$, $g's=sg' \ \forall \ s \in S$.

$$
gg's = gsg' = sgg' \implies gg' \in C_{G}(S)
$$

Soit $g_{1}, g_{2} \in N_{G}(S)$, $g_{1}Sg_{1}^{-1} = S$, $g_{2}Sg_{2}^{-1} = S$.

$$
\begin{align}
(g_{1}g_{2})S(g_{1}g_{2})^{-1} &= g_{1}g_{2} S g_{2}^{-1}g_{1}^{-1} \\
&= g_{1}Sg_{1}^{-1} \\
&= S
\end{align}
$$

Car $g_{2}^{-1}(g_{1}^{-1}g_{1})g_{2}=g_{2}^{-1}eg_{2}=g_{2}^{-1}g_{2}=e$ et $g_{2}^{-1}g_{1}^{-1}=(g_{1}g_{2})^{-1}$. Cela implique alors que $g_{1}g_{2} \in N_{G}(S)$.

Soit $g \in C_{G}(S)$. $\forall \ s \in S$, on a que

$$
\begin{align}
gs&=sg \\
\implies g^{-1}gs&=g^{-1}sg \\
\implies s &= g^{-1}sg \\
\implies sg^{-1} &= g^{-1}sgg^{-1} \\
\implies sg^{-1} &= g^{-1}s
\end{align}
$$

Ainsi, $g^{-1} \in C_{G}(S)$. Soit $g \in N_{G}(S)$. Alors,

$$
\begin{align}
\implies gSg^{-1} &= S \\
\implies g^{-1}gSg^{-1} &= g^{-1}S \\
\implies Sg^{-1}g &= g^{-1}Sg \\
S=g^{-1}Sg
\end{align}
$$
Ainsi, $g^{-1} \in N_{G}(S)$.

**Exemple:** Soit $G_{n}$. Le groupe de Clifford est

$$
C_{n} = N(G_{n}) = \{ U : UPU^{\dagger} \in G_{n} \ \forall \ P \in G_{n} \}
$$

On a que $gSg^{-1} = S$. $\{ gsg^{-1} | s \in S \} = \{  s' \in S \}$. $s' = gsg^{-1} \in S$.

**Exemple:** $GL_{n}(\mathbb{C}) = \{ M | \text{ matrice complexe inversible } n\times n \}$.

$$
C_{GL_{n}(\mathbb{C})}(GL_{n}(\mathbb{C})) = \{ \text{diag}(\lambda_{1}, \dots, \lambda_{n}) | \lambda_{j} \neq 0 \in \mathbb{C} \}
$$

**Exemple:** $SL_{n}(\mathbb{C}) = \{ M \in GL_{n}(\mathbb{C}) | \det(M)=1 \}$. Soit $X \in SL_{n}(\mathbb{C})$, $A \in GL_{n}(\mathbb{C})$, alors

$$
\det(A^{-1}XA) = \det(A)^{-1}\det (X) \det(A) = \det(X) = 1
$$

Cela implique $N_{GL_{n}(\mathbb{C})}(SL_{n}(\mathbb{C})) = SL_{n}(\mathbb{C})$.

**Définition:** Un sous-groupe $H$ d'un groupe $G$ est *normal* si $N_{G}(H)=H$. On dit que $H$ est un sous-groupe abélien si $C_{G}(H)=H$.

Si $G$ est un groupe abélien, $C_{G}(G)=G$, et soit $H$ un sous-groupe.

$$
N_{G}(H) = \{ g \in G | gHg^{-1}=H \} = \{ g \in G | gg^{-1}H=H \} = \{  g \in G | H=H \} = G
$$

$$
\begin{align}
gHg^{-1} = H &\implies \{ ghg^{-1} | h \in H \} = \{  h' \in H \} \\
& \implies \{ h | h \in H \} = \{ h' \in H \}
\end{align}
$$

**Définition:** Soit $H$ un sous-groupe de $G$. Le *groupe quotient* est défini par

$$
\frac{G}{H} = \{ gH | g \in G \}
$$

Celui-ci est l'ensemble des classes résiduelles.

**Théorème:** Si $H \triangleleft G$ est un sous-groupe normal, alors $\frac{G}{H}$ est un groupe avec $gH \cdot g'H = (gg')H$.

# Codes stabilisateurs
## Formalisme des stabilisateurs

Le groupe $G_{n}$ a une action sur l'espace d'Hilbert à n-qubits. Soit $S < G_{n}$ un sous-groupe.

$$
V_{s} = \{ \ket{\psi} \in \mathcal{H}_{n} | P\ket{\psi} = \ket{\psi} \ \forall \  P \in S \}
$$

Donc, $S = \text{stab}(V_{s})$. Soit $\ket{\psi}, \ket{\varphi} \in V_{s}$.

$$
P(\alpha \ket{\psi} + \beta \ket{\varphi}) = \alpha P\ket{\psi} + \beta P \ket{\varphi} = \alpha \ket{\psi} + \beta \ket{\varphi}
$$

Cela implique que $V_{s}$ est une espace vectoriel.

**Exemple:** Soit $\mathcal{H}_{3}$ et $G_{3}$.

$$
\begin{align}
S &= \{ I, Z_{1}Z_{2}, Z_{2}Z_{3}, Z_{1}Z_{3} \} < G_{3} \\
V_{Z_{1}Z_{2}} &= \text{span}\{ \ket{000}, \ket{001}, \ket{110}, \ket{111} \} \\
V_{Z_{2}Z_{3}} &= \text{span}\{ \ket{000}, \ket{100}, \ket{011}, \ket{111} \} \\
V_{Z_{1}Z_{3}} &= \text{span}\{ \ket{000}, \ket{010}, \ket{101}, \ket{111} \} \\
V_{S} &= \text{span}\{ \ket{000}, \ket{111} \}
\end{align}
$$
