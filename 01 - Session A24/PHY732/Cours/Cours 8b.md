---
tags: 
created date: 07-11-2024 08:57
modified date: 11-11-2024 13:33
---
*On a fait une révision des numéros de l'examen intra durant la première partie du cours.*

**Théorème:** Soit $S = \braket{ g, \dots, g_{n-k} } < G_{n}$ abélien, avec des générateurs indépendants, et $-I \notin S$. Alors, $\text{dim}_{\mathbb{C}}V_{s} = 2^{k}$.

**Preuve:**

$$
\begin{align}
g_{j} &= + \frac{I+g_{j}}{2} - \frac{I-g_{j}}{2} \\
I &= \frac{I+g_{j}}{2} + \frac{I-g_{j}}{2}
\end{align}
$$

Si $x = (x_{1},\dots, x_{n-k}) \in \mathbb{Z}_{2}^{n-k}$,

$$
\begin{align}
P_{S}^{x} &= \frac{1}{2^{n-k}} \prod_{j=1}^{n-k} (I+ (-1)^{x_{j}}g_{j}) \\
P_{S}^{(0, \dots, 0)} &= \frac{1}{2^{n-k}} \prod_{j=1}^{n-k} (I+g_{j})
\end{align}
$$

**Exemple:** Si $k=1$, alors $\text{dim}_{\mathbb{C}}V_{S}=2$. Dans $V_{S}$, on prend $\ket{0}_{L}$ et $\ket{1}_{L}$ orthogonaux.

**Théorème:** Soit $S = \braket{ g_{1}, \dots, g_{n-k}} < G_{n}$. Pour $j \in \{ 1, .., n-k \}$, il existe $g \in G_{n}$ tel que $gg_{i}g^{\dagger} = -g_{i}$, $gg_{j}g^{\dagger}=g_{j} \ \forall \ i\neq j$ . Pour $x \in Z_{2}^{n-k}$, $\exists g_{x} \in G_{n}$ tel que

$$
g_{x} P_{S}^{(0, \dots, 0)} g_{x}^{\dagger} = \varphi_{S}^{x}
$$

Par exemple, pour $x = (1,0,0)$, on a que $P_{S}^{x} = \frac{1}{2^{3}}(I-g_{1})(I+g_{2})(I+g_{3})$. Donc, $\exists g_{x}' \in G_{n}$ tel que

$$
\begin{align}
g_{x}'g_{1}g_{x}'^{\dagger} &= -g_{1} \\
g_{x}'g_{2}g_{x}'^{\dagger} &= g_{2} \\
g_{x}'g_{3}g_{x}'^{\dagger} &= g_{3}
\end{align}
$$

Pour $x = (0,1,0)$, $\exists g_{x}'' \in G_{n}$ tel que

$$
\begin{align}
g_{x}''g_{1}g_{x}''^{\dagger} &= g_{1} \\
g_{x}''g_{2}g_{x}''^{\dagger} &= -g_{2} \\
g_{x}''g_{3}g_{x}''^{\dagger} &= g_{3}
\end{align}
$$

Pour $x = (0,0,1)$, $\exists g_{x}''' \in G_{n}$ tel que

$$
\begin{align}
g_{x}'''g_{1}g_{x}'''^{\dagger} &= g_{1} \\
g_{x}'''g_{2}g_{x}'''^{\dagger} &= g_{2} \\
g_{x}''''g_{3}g_{x}'''^{\dagger} &= -g_{3}
\end{align}
$$

Pour $x=(x_{1},x_{2},x_{3})$, $g_{x} = (g_{x}')^{x_{1}}(g_{x}'')^{x_{2}}(g_{x}''')^{x_{3}}$.

$$
\begin{align}
g_{x} P_{S}^{(0,\dots,0)}g_{x}^{\dagger} &= g_{x} (I+g_{1})(I+g_{2})(I+g_{3})g_{x}^{\dagger} \\
&= (g_{x} + g_{x}g_{1})(I+g_{2})(g_{x}^{\dagger} + g_{3}g_{x}^{\dagger}) \\
&= \dots \\
&= I + g_{x}g_{3}g_{x}^{\dagger}+ g_{x}g_{2}g_{x}^{\dagger}+ g_{x}g_{1}g_{x}^{\dagger} + g_{x}g_{1}g_{3}g_{x}^{\dagger} + g_{x}g_{1}g_{2}g_{x}^{\dagger} + g_{x}g_{2}g_{3}g_{x}^{\dagger} + g_{x}g_{1}g_{2}g_{3}g_{x}^{\dagger}
\end{align}
$$

$$
\begin{align}
P_{S}^{x} &= (I + (-1)^{x_{1}}g_{1})(I+(-1)^{x_{2}}g_{2})(I+(-1)^{x_{3}}g_{3}) \\
&= \dots \\
&= I + (-1)^{x_{3}}g_{3} + (-1)^{x_{2}}g_{2} + (-1)^{x_{2}+x_{3}}g_{2}g_{3} + (-1)^{x_{1}}g_{1} + (-1)^{x_{1}+x_{3}}g_{1}g_{3}+(-1)^{x_{1}+x_{2}}g_{1}g_{2} + (-1)^{x_{1}+x_{2}+x_{3}}g_{1}g_{2}g_{3}
\end{align}
$$

On a que $g_{x}g_{j}g_{x}^{\dagger} = (-1)^{x_{j}}g_{j}$, où $x=e_{j}$.

$$
g_{x}g_{1}g_{2}g_{x}^{\dagger} = g_{x}g_{1}g_{x}^{\dagger}g_{x}g_{2}g_{x}^{\dagger} = (-1)^{x_{1}+x_{2}}g_{1}g_{2}
$$

$$
g_{x}P_{s}^{(0,\dots,0)}g_{x}^{\dagger} = P_{S}^{x}
$$

On a que $P_{S}^{x}P_{S}^{x'}=0$. Par exemple, pour $x=(0,1)$ et $x' = (1,1)$, on a que

$$
\begin{align} \\
P_{S}^{x} &= (I+g_{1})(I-g_{2}) \\
P_{S}^{x'} &= (I-g_{1})(I-g_{2}) \\
P_{S}^{x}P_{S}^{x'} &= \dots = 0
\end{align}
$$

En effet, si $x \neq x'$, $\exists j$ tel que $x_{j} \neq x_{j}'$, alors

$$
\begin{align}
P_{S}^{x}P_{S}^{x'} &= (I + g_{j})(I-g_{j}) \prod \dots \\
&= 0 \prod \dots \\
&= 0
\end{align}
$$

Soit $P_{S}^{(0,\dots,0)}$ le projecteur sur $V_{S}$ ($V_{S} = \{ \ket{\psi} \mid g_{j} \ket{\psi} = \ket{\psi} \ \forall \ j \}$). La dimension de $P_{S}^{x}$ est la même que de $P_{S}^{(0,\dots,0)}$. Aussi,

$$
I = \sum_{x \in \mathbb{Z}_{2}^{n-k}} P_{S}^{x}
$$
On a que $\text{dim}I = 2^{n}$ et que $x$ à $2^{n-k}$ termes. Donc, $\text{dim}P_{S}^{x}=2^{k}=\text{dim}V_{S}$.