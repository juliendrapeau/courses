---
tags: 
created date: 06-11-2024 15:41
modified date: 11-11-2024 13:33
---
## Rappel

- $G_{3} = \text{Groupe Pauli à 3 qubits}$
- $S = \braket{ Z_{1}Z_{2}, Z_{2}Z_{3} } = \{ Z_{1}Z_{2}, Z_{2}Z_{3}, Z_{1}Z_{2}, I \} < G_{3}$
- 
$$
\begin{align}
V_{s} &= \{ \ket{\psi} \in C^{\otimes_{n}} \mid g\ket{\psi} = \ket{\psi} \ \forall \ g \in S \} \\
&= \{ \ket{\psi} \mid Z_{1}Z_{2}\ket{\psi} = \ket{\psi} \text{ et } Z_{2}Z_{3}\ket{\psi} = \ket{\psi} \} \\
&= \text{Span}\{ \ket{000}, \ket{111} \}
\end{align}
$$
- $H = \{ I, -X, -I, X \} < G_{1}$
- $H'=\{ -I, I \} < G_{1}$
- On a que $-I \ket{\psi} = \ket{\psi} \iff \ket{\psi} \cdot \vec{0}$, qui n'est pas un vecteur physique. On est intéressé par les sous-groupes de $G_{n}$ dans lesquels $-I^{\otimes n} \in S$.

## Formalisme des stabilisateurs (suite)

**Propriété 1:** Si $S < G_{n}$, alors $-I \notin S \implies \pm iI \notin S$

**Preuve:** On a que $P \implies Q$, alors prouvons que $\neg Q \implies \neg P$. On a que $Q = +iI \not\in S \land -iI \not\in S$ et que $\neg Q = +iI \in S \lor -iI \in S$.

1. $+iI \in S \implies (iI)(iI) \in S \implies -I \in S = \neg P$
2. $-iI \in S \implies (-iI)(-iI) \in S \implies -I \in S = \neg P$

Donc, on a que 
$$
+iI \in S \text{ ou } -iI \in S \implies -I \in S \implies -I \not\in S \implies \pm iI \not\in S
$$
**Propriété 2:** Si $M,N \in G_{n}$, soit $[M,N] = 0$ ou $\{ M,N \} = 0$. Si $0=\{ M,N \} = MN+MN$, alors $MN=-NM$. Supposons que $S < G_{n}$ tel que $V_{s} \neq \{ \vec{0} \}$, il existe $\ket{\psi} \in V_{s}$ tel que $\ket{\psi} \neq \vec{0}$. Donc, si $M,N \in S$,

$$
\ket{\psi} = MN \ket{\psi} = -NM \ket{\psi} = -\ket{\psi}
$$

Contradiction, donc $\{ M,N \}$ ne peut être nul.

**Propriété 3:** Si $S < G_{n}$ tel que $V_{s} \neq \{ \vec{0} \}$,

1. $-I \notin S \ (\implies \pm iI \notin S)$
2. $S$ est commutatif (abélien)

**Propriété 4:** Si $S = \braket{ g_{1}, \dots, g_{k} }$, alors $S$ est abélien $\iff g_{i}g_{j}=g_{j}g_{i} \in S$.

**Preuve:** 

- $\implies$: Ok.
- $\impliedby$: *À rajouter*

**Exemple (Code de Steane):** 

$$
\begin{align}
\ket{0 \cdot C_{2}} &= \frac{1}{\sqrt{ 8 }} (\ket{1111111} + \ket{1010101} + \ket{0110011} + \ket{1100110} \\
&+ \ket{0001111} + \ket{1011010} + \ket{0111100} + \ket{1101001}) \\
\ket{1 \cdot C_{2}} &= \frac{1}{\sqrt{ 8 }} (\dots)
\end{align}
$$
Les générateurs du stabilisateur $S = \braket{ g_{1}, \dots, g_{6} }$ du code de Steane sont:

$$
\begin{align}
g_{1} &= IIIXXXX \\
g_{2} &= IXXIIII \\
g_{3} &= XIXIXIX \\
g_{4} &= IIIZZZZ \\
g_{5} &= IZZIIII \\
g_{6} &= ZIZIZIZ
\end{align}
$$

On a que $V_{s} = \text{Span}\{ \ket{0 \cdot C_{2}}, \ket{1 \cdot C_{2}} \}$. La matrice contrôle parité est

$$
H = \begin{pmatrix}
0 & 0 & 0 & 1 & 1 & 1 & 1 \\
0 & 1 & 1 & 0 & 0 & 1 & 1 \\
1 & 0 & 1 & 0 & 1 & 0 & 1
\end{pmatrix}
$$

Soit $S = \braket{ g_{1}, \dots, g_{k} } < G_{n}$. On construit sa matrice contrôle $M_{s} \in \text{Mat}_{\mathbb{Z}_{2}}(k, 2n)$.

$$
\begin{align}
\begin{matrix}
g_{1} = I_{1} X_{2} Y_{3} Z_{4} \to
\end{matrix}
\begin{pmatrix}

\end{pmatrix}
\end{align}
$$


*Rajouter le produit intérieur symplectique!!*

*Voir les notes de Ben.*