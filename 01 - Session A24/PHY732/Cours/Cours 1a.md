---
tags: []
created date: 26-08-2024 10:36
modified date: 08-09-2024 16:26
---
**Résumé:**
- Définition des matrices densités
- Propriétés des matrices densités (états purs, états mixtes, évolution temporelle, ...)
- Superposition et mélange d'états

# Matrice densité

## Ensemble d'états quantiques

Soit $\hat{A}$ une observable avec $\hat{A}\ket{\mu} = \lambda_{n} \ket{\mu_{n}}$, $n=1,2$.

$$
\begin{array}{c|c|c}
 & \text{Superposition} & \text{Mélange d'états} \\
\hline
\text{Système} & \ket{\psi} = c_{1} \ket{\mu_{1}} + c_{2} \ket{\mu_{2}}  & \{ \ket{\mu_{1}} , \ket{\mu_{2}} , \ket{\mu_{1}} , \ket{\mu_{1}}, \ket{\mu_{2}}, \dots \} \\
\text{Sélection d'état} & \ket{\psi} \text{ avec } \mathbb{P} = 1  & \ket{\mu_{1}} \text{ avec } \mathbb{P} = p_{1} \text{ et } \ket{\mu_{2}} \text{ avec } \mathbb{P} = p_{2} \\
\text{Mesure} & \lambda_{1} \text{ avec } \mathbb{P} = \lvert c_{1} \rvert^{2} \text{ et } \lambda_{2} \text{ avec } \mathbb{P} = \lvert c_{2} \rvert^{2}  &  \lambda_{1} \text{ avec } \mathbb{P} = 1 \text{ et } \lambda_{1} \text{ avec } \mathbb{P} = 1
\end{array}
$$

- **Superposition:**

Soit $\hat{B}$ une autre observable avec $\hat{B} \ket{v_{m}} = \sigma_{m} \ket{v_{m}}$, $m = 1, 2$.

$$
\begin{align}
P_{\ket{\psi}}(\sigma_{m}) &=\lvert \braket{ v_{m} | \psi }  \rvert ^2 \\
&= \braket{ v_{m} | \psi } \braket{ \psi | v_{m} } \\
&= \lvert c_{1} \rvert ^2 \lvert \braket{ v_{m} | \mu_{1} } \rvert ^2 + \lvert c_{2} \rvert ^2 \lvert \braket{  v_{m} | \mu_{2}  } \rvert ^2 + \underbrace{ 2 \mathrm{Re}( c_{1} c_{2}^{*} \braket{ v_{m} | \mu_{1} } \braket{ v_{m} | \mu_{2} }^{*} ) }_{ \text{ Terme d'interférence } }
\end{align}
$$

- **Mélange d'états (mélange statistique):**

	- $\mathbb{P} ( \ket{\mu_{n}} ) = \lvert c_{n} \rvert^{2}$, $n = 1, 2$
	- $\mathbb{P}_{\ket{\mu_{n}}}( \sigma_{m} ) = \lvert \braket{ v_{m} | \mu_{n} } \rvert^{2}$
	- $\mathbb{P}(\sigma_{m}) = \sum_{n=1}^2 \mathbb{P}(\ket{\mu_{n}}) P_{\ket{\mu_{n}}} (\sigma_{m}) = \lvert c_{1} \rvert^{2} \lvert \braket{ v_{m} | \mu_{1} } \rvert^{2}  + \lvert c_{2} \rvert^{2} \lvert \braket{ v_{m} | \mu_{2} } \rvert^{2}$

**Définition (matrice densité):** Soit $\ket{\psi}$ un état quantique. Son opérateur (matrice) densité est défini par

$$
\rho := \ket{\psi} \bra{\psi} 
$$

Soit $\hat{A}$ une observable tel que $\hat{A} \ket{\mu_{n}}= \lambda_n \ket{\mu_{n}}$, $n \geq 1$, alors

- $\ket{\psi}=\sum_{j} c_{j} \ket{\mu_{j}}$, où $c_{j}=\braket{ \mu_{j} | \psi }$
- $\rho_{ij} = \braket{ \mu_{i}| \rho | \mu_{j} } = c_{i}c_{j}^*$
- $$
\ket{\psi} = \begin{pmatrix}
c_{1} \\
c_{2} \\
\vdots \\
c_{n} \\
\end{pmatrix}, \quad 
\rho = \begin{pmatrix}
c_1 c_1^{*} & c_{1} c_{2}^{*} & \dots & c_{1} c_{n}^{*} \\
c_{2} c_{1}^{*} & \ddots &  & \vdots \\
\vdots &  & \ddots & \vdots \\
c_{n} c_{1}^{*} & \dots & \dots & c_{n} c_{n}^{*}
\end{pmatrix}
$$
**Propriétés:**

1. $\rho^{\dagger} = (\ket{\psi}\bra{\psi})^{\dagger} = \bra{\psi}^{\dagger} \ket{\psi}^{\dagger} = \ket{\psi}\bra{\psi} = \rho$
2. $\rho^2 = \ket{\psi}\bra{\psi} \ket{\psi}\bra{\psi} = \ket{\psi} \bra{\psi} = \rho$
3. Si $\ket{\psi'} = e^{ i \theta } \ket{\psi}$, alors $\rho' = e^{ i \theta } \ket{\psi} \bra{\psi} e^{ -i \theta } = \ket{\psi} \bra{\psi} = \rho$
4. $\mathbb{1} = \braket{ \psi | \psi } = \sum_{j} \lvert c_{j} \rvert^{2} = \sum_{j} c_{j} c_{j}^{\dagger} = \mathrm{Tr}(\rho)$
5. $$ 
\begin{align}
\braket{ \psi | \hat{A} | \psi } &= \braket{ \psi | \left( \sum_{i} \ket{\mu_{i}} \bra{\mu_{i}} \hat{A} \sum_{j} \ket{\mu_{j}} \bra{\mu_{j}} \right)  | \psi } \\
&= \sum_{i, j} \braket{ \psi | \mu_{i} } \braket{ \mu_{i} | \hat{A} | \mu_{j} } \braket{ \mu_{j} | \psi } \\
&= \sum_{i, j} \braket{ \mu_{j} | \psi } \braket{ \psi | \mu_{i} } \braket{ \mu_{i} | \hat{A} | \mu_{j} } \\
&= \sum_{i, j} \braket{ \mu_{j} | \rho | \mu_{j} } \braket{ \mu_{i} | \hat{A} | \mu_{j} } \\
&= \sum_{j} \braket{ \mu_{j} | \rho \hat{A} | \mu_{j} } \\
&= \mathrm{Tr}(\rho \hat{A}) \\
\end{align}
$$

**Évolution temporelle:**

Soit l'évolution temporelle $i \hbar \frac{ \partial }{ \partial t } \ket{\psi(t)} =  \hat{H} \ket{\psi(t)}$, $\rho(t) = \ket{\psi(t)} \bra{\psi(t)}$. Sachant que $\hat{H}^{\dagger} = \hat{H}$ comme $\hat{H}$ est hermitien, alors

$$
\begin{align}
\frac{ \partial }{ \partial t } \rho(t) &= \left( \frac{ \partial }{ \partial dt } \ket{\psi(t)} \right) \bra{\psi(t)} + \ket{\psi(t)} \left( \frac{ \partial  }{ \partial t } \bra{\psi(t)}  \right) \\
&= \frac{1}{i \hbar} \hat{H} \ket{\psi(t)} \bra{\psi(t)} - \frac{1}{i \hbar} \ket{\psi(t)} \bra{\psi(t)} \hat{H} \\
&= \frac{1}{i \hbar} [\bar{H}, \rho(t)] \\
\end{align}
$$

**Mélange statistique:**

Soit $\{\ket{\psi_{k}}\}_{k=1}^N$ un mélange statistique dans lequel $\ket{\psi_{k}}$ a une probabilité $p_{k}$ d'être sélectionné.

$$
\begin{align}
\mathbb{P}(\lambda_{n}) &= \sum_{k} p_{k} \mathbb{P}_{\ket{\psi_{k}}}(\lambda_{n}) \\
&= \sum_{k} p_{k} \mathrm{Tr} (p_{k} \hat{P_{n}}) \\
&= \mathrm{Tr}\left( \sum_{k} p_{k} \rho_{k} \hat{P}_{n} \right)
\end{align}
$$

 La matrice densité d'un mélange statistique $\{\ket{\psi_{k}}, p_{k} \}_{k=1}^N$ (état mixte) est 

$$
\rho = \sum_{k} p_{k} \rho_{k}
$$

On a que, pour $\hat{A} = \sum_{n} \lambda_{n} \ket{\mu_{n}} \bra{\mu_{n}}$:

- $\mathrm{Tr}(\rho) = \mathrm{Tr}\left( \sum_{k}p_{k}\rho_{k} \right) = \sum_{k} p_{k} \mathrm{Tr} (\rho_{k}) = \sum_{k} p_{k} = 1$
- $$
\begin{align}
 <\hat{A}> = \sum_{n} \lambda_{n} \mathbb{P}_{\rho} (\lambda_{n}) &= \sum_{n} \lambda_{n} \mathrm{Tr} (\rho \hat{P}_{n}) \\
&= \mathrm{Tr} \left( \sum_{n} \lambda_{n} \rho \hat{P}_{n} \right) \\
&=\mathrm{Tr} \left( \rho \sum_{n} \lambda_{n} \hat{P}_{n} \right) \\
&= \mathrm{Tr} (\rho \hat{A}) \\
\end{align}
$$