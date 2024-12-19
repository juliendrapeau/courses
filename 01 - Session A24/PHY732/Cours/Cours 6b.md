---
tags: 
created date: 03-10-2024 08:37
modified date: 24-10-2024 16:44
---
Les codes linéaires $C$ sont des espaces vectorielles sur $\mathbb{Z}_{2}$: $\begin{pmatrix}1&1&1&1\end{pmatrix} \cdot \begin{pmatrix}1&1&1&1\end{pmatrix}=4=0$.

**Théorème (Borne de Gilbert-Varshamov quantique):** Pour un $n$ suffisamment grand, il existe un $[n,k]$-code quantique capable de corriger des erreurs à $t$ qubits pour $k$ tel que

$$
\frac{k}{2} \geq 1-2\mathcal{H}\left( \frac{2t}{n} \right)
$$

où $\mathcal{H}(x) = x\log (x) - (1-x)\log(1-x)$.

### Code Steane

Considérons le $[7,4,3]$-code de Hamming $C=\text{Ker}H$.

$$ H =
\begin{pmatrix}
0 & 0 & 0 & 1 & 1 & 1 & 1 \\
0 & 1 & 1 & 0 & 0 & 1 & 1 \\
1 & 0 & 1 & 0 & 1 & 0 & 1
\end{pmatrix}
$$

Définissons $C_{1}=C$, $C_{2}=C^{\perp}$ (espace vectoriel $\mathbb{Z}_{2}$).

$$
H[C_{2}] = G[C_{1}]^{\dagger} = \begin{pmatrix}
1 & 0 & 0 & 0 & 0 & 1 & 1 \\
0 & 1 & 0 & 0 & 1 & 0 & 1 \\
0 & 0 & 1 & 0 & 1 & 1 & 0 \\
0 & 0 & 0 & 1 & 1 & 1 & 1
\end{pmatrix}
$$

L'espace généré par les rangées de $H[C_{2}]$ contient celui généré par les rangées de $H[C_{1}]$. Cela implique que $C_{2} \subset C_{1}$ ($C^{\perp} \subset C$). Aussi, $C_{2}^{\perp}=(C^{\perp})^{\perp}=C=C_{1}$ implique que $d(C_{1})=d(C_{2})=3$. Alors, $C_{1}$ est un $[7,4,3]$-code. On peut corriger des erreurs à un qubit. $C_{1}$ est un $[7,4]$-code, $C_{2}$ est un $[7,3]$-code. Donc, $\text{CSS}(C_{1},C_{2})$ est un $[7,1]$-code qui peut corriger des erreurs à un qubit. Les mots de code sont

$$
\begin{align}
\ket{0+C_{2}} &= \frac{1}{\sqrt{ 8 }} [\ket{0000000}+\ket{1010101}+\ket{0110011}+\ket{1100110} \\
&+\ket{0001111}+\ket{1011010}+\ket{0111100}+\ket{1101001}]
\end{align}
$$

$$
H = H[0] = \begin{pmatrix}
0 & 0 & 0 & 1 & 1 & 1 & 1 \\
0 & 1 & 1 & 0 & 0 & 1 & 1 \\
1 & 0 & 1 & 0 & 1 & 0 & 1
\end{pmatrix}, \ x \in \frac{C_{2}}{C_{1}}, \ x = \begin{pmatrix}
1 \\
1 \\
1 \\
1 \\
1 \\
1 \\
1 \\
\end{pmatrix}
$$

$$
\ket{1+C_{2}} = \frac{1}{\sqrt{ 8 }} \sum_{y \in C_{2}} \ket{x+y}
$$

# Théorie des groupes

**Définition:** Un *groupe* est un ensemble $G \neq \emptyset$ avec une opération binaire

$$
\begin{align}
*:\ &G \times G \to G \\
& (a,b) \to a*b
\end{align}
$$

tel que

1. $(a * b) * c = a * (b * c) \ \forall \ a,b,c \in G$
2. $\exists e_{G} \in G$  tel que $a*e=e*a=a \ \forall \ a \in G$
3. $\ \forall \ a \in G \ \exists  a^{-1} \in G$ tel que $a*a^{-1}=a^{-1}*a=e$

**Exemple:**

1. $(\mathbb{Z}, +)$, $e_{\mathbb{Z}}=0$, $a^{-1}=-a$.
2. $(\mathbb{Z}_{n}, +)$, $[a]+[b]=[a+b]$ où $[a]=\{ x | a \equiv x \text{ mod } n \}$, $e_{\mathbb{Z}_{n}}=[0]$, $[a]^{-1}=[-a]$.
3. $(GL_{n}(\mathbb{C}), \cdot)$, $GL_{n}(\mathbb{C}) = \{ M \in \text{Mat}_{\mathbb{C}} (n,n) | \exists M^{-1} \}$, $e_{GL_{n}(\mathbb{C})} = I_{n}$, $M=M^{-1}$.

$G=(\{ \pm 1 \}, *)$

|  *  | +1  | -1  |
| :-: | :-: | --- |
| +1  | +1  | -1  |
| -1  | -1  | +1  |

$H=(\mathbb{Z}_{2}, +)$

|   +   | $[0]$ | $[1]$ |
| :---: | ----- | ----- |
| $[0]$ | $[0]$ | $[1]$ |
| $[1]$ | $[1]$ | $[0]$ |

 $L = (\{ A, B \}, \times)$

| $\times$ | A   | B   |
| :------: | --- | --- |
|    A     | A   | B   |
|    B     | B   | A   |

**Définition:** Soit $(G, *_{G})$ et $(H, *_{H})$ des groupes. Une fonction $f:G \to H$ est un *homomorphisme* de groupe si

$$
f(a*_{G}b) = f(a) *_{H} f(b)
$$

**Exemple:**
$$
\begin{align}
f: \{ +1,1 \} &\to \{ [0], [1] \} \\ \\

+1 &\to [0] \\
-1 &\to [1] \\ \\

f((+1)*(-1)) &= f(-1) = [1] \\
f(+1)+f(-1) &= [0]+[1] = [1] \\
\end{align}
$$

$$
\begin{align}
g: \{ +1,1 \} &\to \{ [0], [1] \} \\ \\

+1 &\to [0] \\
-1 &\to [0] \\ \\

g((+1)*(-1)) &= g(-1) = [0] \\
g(-1)&=[0] \\
\end{align}
$$

**Définition:** Soit $f:(G,*) \to (H, \circ)$ un homomorphisme de groupe.

1. $f$ est un monomorphisme si $f$ est injective.
2. $f$ est un épimorphisme si $f$ est surjective.
3. $f$ est un isomorphisme si $f$ est bijective.

**Définition:** Deux groupes $(G,*)$ et $(H, \circ)$ sont *isomorphes*, $G \cong H$, s'il existe un isomorphisme $f: G \to H$.

Par exemple, $(\{ \pm 1, * \}) \cong (\mathbb{Z}_{2}, +)$ comme $Z\ket{0}=+1 \ket{0}$ et $Z\ket{1}=-1\ket{1}$.

**Proposition:** Soit $f: (G,*) \to (H, \circ)$ un homomorphisme de groupe. Alors,

1. $f(e_{G})=e_{H}$
2. $f(a^{-1})=f(a)^{-1}$
3. $f(a^{n})=f(a)^{n} \ \forall \ n \in \mathbb{Z}$

**Preuve:**

1. On a que
$$
\begin{align}
e_{G} = e_{G}*e_{G} &\implies f(e_{G}) = f(e_{G}) \circ f(e_{G}) \\
&\implies f(e_{G})^{-1} \circ f(e_{G}) = f^{-1}(e_{G}) \circ f(e_{G}) \circ f(e_{G}) \\
&\implies e_{H} = e_{H} \circ f(e_{G}) = f(e_{G}) 
\end{align}
$$

2. $\forall \ h \in H \ \exists h^{-1} \in H \text{ t.q. } h\circ h^{-1} = h^{-1}\circ h = e_{H}$. Soit $a \in G$, $f(a) \in H$, $\exists f(a)^{-1} \in H$ t.q.

$$
\begin{align}
f(a)^{-1} \circ f(a) &= f(a) \circ f(a)^{-1} = e_{H} \\
f(a^{-1}) \circ f(a) &= f(a^{-1}*a) = f(e_{G}) = e_{H} \\
f(a) \circ f(a^{-1}) &= f(a*a^{-1}) = f(e_{G}) = e_{H}
\end{align}
$$

3. En devoir. $\square$

**Définition:** Soit $G$ ($a*b=ab$) un groupe. Un sous-ensemble $S \subset G$ est un *sous-groupe* si

1. $x \in S \implies x^{-1} \in S$
2. $x,y \in S \implies xy \in S$

Est-ce que $e_{G} \in S$? Oui!

$$
\begin{align}
x \in S &\implies x^{-1} \in S \\
x, x^{-1} \in S &\implies e_{G} = xx^{-1} \in S
\end{align}
$$

**Proposition:** Si $S$ est un sous-groupe d'un groupe $G$, alors $S$ est un groupe.

**Preuve:** 

1. 
$$
\begin{align}
S \times S \to S \\
(a,b) \to ab
\end{align}
$$

2. $a(bc)=(ab)c$.
3. $e_{G} = xx^{-1} \in S$, $ae_{G}=e_{G}a=a \ \forall \ a \in G$. $se_{G}=e_{G}s=s \ \forall \ s \in S \subset G$.
4. $x \in S, \exists x^{-1} \in S$. $\square$

**Définition:** Soit $f:(G, *) \to (H,\circ)$ un homomorphisme. On définit le *noyau* de ce groupe comme $\text{Ker}f = \{ g \in G | f(g) = e_{H} \}\neq \emptyset$.

1. $e_{G} \in \text{Ker}f$, $f(e_{G}) = e_{H}$.
2. $x \in \text{Ker}f \iff f(x) = e_{H}$, $f(x^{-1})=f(x)^{-1}=e_{H}^{-1}=e_{H} \implies x^{-1} \in \text{Ker}f$.
3. $x,y \in \text{Ker}f \implies f(x)=e_{H}, f(y)=e_{H} \implies f(x*y) = f(x)\circ f(y) = e_{H} \circ e_{H}= e_{H}$. 

$f: (G,*) \to (H, \circ)$ est un homomorphisme et donc $\text{Ker}f \subset G$ est un sous-groupe de $G$.

Soit $\mathbb{Z}_{2} \times \mathbb{Z}_{2} = \{ (a,b): a,b \in \mathbb{Z}_{2} \}$

$$
\begin{align}
*: &(\mathbb{Z}_{2} \times \mathbb{Z}_{2}) \times (\mathbb{Z}_{2} \times \mathbb{Z}_{2}) \to \mathbb{Z}_{2} \times \mathbb{Z}_{2} \\
&([a],[b]), ([c],[d]) \to ([a],[b])*([c],[d])=([a+c],[b+d])
\end{align}
$$

**Définition:** Soit des groupes $(G,*)$ et $(H, \circ)$. Un *groupe produit* $G \times H$ est un groupe avec $(g,h) \cdot (g',h') = (g*g', h \circ h')$. On a alors que $e_{G \times H} = (e_{G}, e_{H})$ et $(g,h)^{-1}=(g^{-1},h^{-1})$.

Soit $\tilde{G} = \{ (g,e_{H}): g \in G \} \subset G \times H$. On a que

$e_{\tilde{G}}=(e_{G}, e_{H})=e_{G \times H}$, $(g, e_{H}) \cdot (g', e_{H}) = (g * g', e_{H} \circ e_{H}) = (g*g', e_{H}) \in \tilde{G}$.
$(g, e_{H})^{-1} = (g^{-1},e_{H}^{-1} = (g^{-1}, e_{H}) \in \tilde{G}$.

Donc, $\tilde{G} \subset G \times H$ est un sous-groupe.

$$
\begin{align}
f&: G \times H \to \tilde{G} \\
&(g,h) \to (g, e_{H})
\end{align}
$$

$f(g,h) \cdot f(g',h')=(g,e_{H}) \cdot (g', e_{H}) = (g*g', e_{H} \circ e_{H}) = (g*g', e_{H})$
$f(g,h)=(g,e_{H})$
$f(g, e_{H})=(g,e_{H})$

$f$ n'est pas injective (pas un isomorphisme). On a par contre que

$$
\begin{align}
F&: G \to \tilde{G} \\
&g \to (g, e_{H})
\end{align}
$$

est un isomorphisme.

**Définition:** Un groupe $G$ est *abélien* si 

$$
a*b=b*a \ \forall \ a,b \in G,
$$
c'est-à-dire que tous les éléments du groupe commutent entre eux.