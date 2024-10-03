---
tags: 
created date: 30-09-2024 13:33
modified date: 30-09-2024 16:30
---
# Construction de codes quantiques

## Codes linéaires classiques

On définit les codes linéaires classiques sur $\mathbb{Z}_{2}^{n} = \mathbb{F}_{2}^{n}$, où $\mathbb{Z}_{2} = \mathbb{F}_{2} = \{ 0, 1 \}$.

**Définition:** Un code linéaire classique $C$ (sous-espace vectoriel de $\mathbb{Z}_{2}^{n}$) qui encode $k$ bits en $n$ bits est décrit par une matrice *génératrice* $G \in \text{ Mat}_{\mathbb{Z}_{2}} (n,k)$. On nomme cela un $[n,k]$-code.

**Exemple:** Soit un code de répétition $0 \to 000$, $1 \to 111$, $G = \begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix}$, $G_{0} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$, $G_{1} = \begin{pmatrix} 1 \\ 1 \\ 1 \end{pmatrix}$. On a un $[3, 1]$-code.

**Exemple:** Soit un $[6,2]$-code. 

$$
G = \begin{pmatrix}
1 & 0 \\
1 & 0 \\
1 & 0 \\
0 & 1 \\
0 & 1 \\
0 & 1
\end{pmatrix}
$$
$$
\begin{pmatrix}
0 \\
0
\end{pmatrix} \to \begin{pmatrix}
0 \\
0 \\
0 \\
0 \\
0 \\
0
\end{pmatrix}, \ \begin{pmatrix}
0 \\
1
\end{pmatrix} \to \begin{pmatrix}
0 \\
0 \\
0 \\
1 \\
1 \\
1
\end{pmatrix}, \ \begin{pmatrix}
1 \\
0
\end{pmatrix} \to G\begin{pmatrix}
 1 \\
0
\end{pmatrix} \to \begin{pmatrix}
1 \\
1 \\
1 \\
0 \\
0 \\
0
\end{pmatrix}, \ \begin{pmatrix}
1 \\
1
\end{pmatrix} \to G \begin{pmatrix}
1 \\
1
\end{pmatrix} \to \begin{pmatrix}
1 \\
1 \\
1 \\
1 \\
1 \\
1
\end{pmatrix}
$$

L'ensemble des mots de code possibles pour le code correspond à l'espace engendré par les colonnes de $G$. Donc, à la fin, pour que tous les messages sont encodés de manière unique, nous exigeons que les colonnes de $G$ soient linéairement indépendantes.

Un code général qui encode $k$ bits en $n$ bits a besoin de spécifier $2^{k}$ mots de code de longueur $n$, donc $n 2^{k}$ bits d'information pour décrire le code. Avec un code linéaire, on a besoin de $nk$ bits.

**Définition:** Un $[n,k]$-code est décrit par les vecteurs $x \in \mathbb{Z}_{2}^{n}$ tel que $Hx=0$, avec $M \in \text{ Mat}_{\mathbb{Z}_{2}}(n-k,n)$. $M$ est la matrice de contrôle de parité. 

$$
\{ x \in \mathbb{Z}_{2}^{n} | Hx = 0 \} = \text{Ker}H
$$

Un code qui encode $k$ bits à $2^{k}$ mots de code possible est donc $\text{ dim}_{\mathbb{Z}_{2}}\text{Ker}H = k$, c'est-à-dire les rangées sont linéairement indépendantes.

Si $G$ est une matrice génératrice, soit $y_{1}, \dots, y_{n-k}$ des vecteurs linéairement indépendants et orthogonaux aux colonnes de $G$. On construit $H$ avec des rangées données par $y_{1},\dots,y_{n-k}$.

**Exemple:** Soit $G = \begin{pmatrix}1 \\ 1 \\ 1\end{pmatrix}$, $[3,1]$-code, $H \in \text{Mat}(2,3)$.

$$
y_{1} = \begin{pmatrix}
0 \\
1 \\
1
\end{pmatrix}, \ y_{2} = \begin{pmatrix}
1 \\
1 \\
0
\end{pmatrix} \implies H = \begin{pmatrix}
0 & 1 & 1 \\
1 & 1 & 0
\end{pmatrix}
$$

Si $H$ est une matrice de contrôle de parité, soit $y_{1},\dots,y_{k}$ des vecteurs générateurs du $\text{Ker}H$, la matrice $G$ a des colonnes $y_{1}, \dots, y_{k}$.

**Exemple:** $H = \begin{pmatrix}0 & 1 & 1 \\ 1 & 0 & 0 \end{pmatrix}$

$$
Hx=0 \iff \begin{pmatrix}
0 & 1 & 1 \\
1 & 1 & 0
\end{pmatrix} \begin{pmatrix}
x_{1} \\
x_{2} \\
x_{3}
\end{pmatrix} = \begin{pmatrix}
x_{2} + x_{3} \\
x_{1} + x_{2}
\end{pmatrix} = 0
$$

Donc, $x=\begin{pmatrix}1 \\ 1 \\ 1\end{pmatrix}$ et $G = \begin{pmatrix}1 \\ 1 \\ 1\end{pmatrix}$.

Supposons qu'on encode $x$ par $y = Gx$, et qu'une erreur se produit $y' = y + e$ (dans $\mathbb{Z}_{2}^{n}$). On applique $H$:

$$
Hy' = H(y+e) = HGx + He = He
$$

Soit $\{ e_{1}, \dots, e_{n} \}$ la base canonique de $\mathbb{Z}_{2}^{n}$. Supposons qu'il y a au plus une erreur. Donc, 

$$
Hy' = 0 \text{ si pas d'erreur et } e_{j} \text{ si une erreur sur le bit } j
$$

Alors, on corrige le bit $j$.

**Définition:** La distance de Hamming pour $x, y \in \mathbb{Z}_{2}^{N}$ est donnée par 

$$
d(x,y) = \# \{ x_{j} \neq y_{j} | j=1,\dots,n \}
$$

Par exemple, $d\begin{pmatrix}1 & 0 \\ 1 & 1 \\ 0 & 1\end{pmatrix} = 2$.

**Définition:** Le poids de Hamming de $x \in \mathbb{Z}_{2}^{n}$ est

$$
\begin{align}
wt(x) &= d(x, \vec{0}) \\ \\
d(x,y) &= wt(x+y)
\end{align}
$$

Si la probabilité d'erreur dans un bit est inférieure à $\frac{1}{2}$, le mot de code le plus probable qui est encodé dans $y' = y + e$ si $y = Gx$ est le mode de code $y$ qui minimise $wt(e) = d(y,y')$.

**Définition:** Soit $C$ un code dans $\mathbb{Z}_{2}^{n}$. La distance de $C$ est

$$
d(C) = \text{ min}_{x,y \in C, x \neq y} d(x,y) = \text{ min}_{x \in C, x \neq 0} wt(x)
$$

**Définition:** On dit qu'un code linéaire $C$ avec $d=d(C)$ est un $[n,k,d]$-code.

Soit $C$ un code avec $d(C) \geq 2t+1$, $t \in \mathbb{Z}_{\geq_{0}}$ celui-ci peut corriger des erreurs sur $t$ qubits avec un décodage de $y'$ pour $y$ tel que $d(y, y') \leq t$ qui est unique. Soit $H$ une matrice de contrôle de parité dans laquelle tout ensemble de $d-1$ colonnes est linéairement indépendants, mais il existe un ensemble de $d$ colonnes linéairement indépendants. Alors, $d(C) = d$.

### Codes de Hamming

Soit $r \geq 2$ et $H$ la matrice avec $2^{r}-1$ colonnes formée pour tous les vecteurs de longueur $r$ qui ne sont pas $\vec{0}$. Ces codes sont des $[2^{r}-1, 2^{r}-r-1]$-codes.

**Exemples:** $r=3$

$$
H = \begin{pmatrix}
0 & 0 & 0 & 1 & 1 & 1 & 1 \\
0 & 1 & 1 & 0 & 0 & 1 & 1 \\
1 & 0 & 1 & 0 & 1 & 0 & 1
\end{pmatrix}
$$

$d(C) = 3 = 2*1 +1$, on peut corriger toute erreur à 1 bit. $Hy' = He_{j}$ est la représentation binaire de la position de l'erreur. $[2^{r}-1, 2^{r}-r-1, 3]$.

**Théorème (Borne Gilbert-Varshamov):** Pour $n$ suffisamment grand, il existe un $[n, k]$-code capable de corriger des erreurs à $t$ bits pour $k$ tel que

$$
\frac{k}{n} \geq 1 - \mathcal{H}\left( \frac{2t}{n} \right)
$$

avec $\mathcal{H}(x) = -x\log (x) - (1-x) \log(1-x)$ l'entropie binaire de Shannon.

Soit $C$ un $[n, k]$-code avec une matrice génératrice $G$ et une matrice de contrôle de parité $H$. On définit le dual de $C$ comme le code $C^{\perp}$, une matrice génératrice $H^{T}$ et sa matrice de contrôle de parité est $G^{T}$.

## Codes quantiques de Calderbank-Shor-Steane

Soit $C_{1}$ un $[n,k_{1}]$-code et $C_{2}$ un $[n,k_{2}]$-code tel que $C_{2} \subset C_{1}$ et les codes $C_{1}$ et $C_{2}^{\perp}$ corrigeant $t$ erreurs. On va construire un $[n, k_{1}-k_{2}]$-code quantique que nous notons $\text{CSS}(C_{1}, C_{2})$ qui est capable de corriger des erreurs à $t$ qubits: *Le code CSS de $C_{1}$ sur $C_{2}$*.

$$
\frac{C_{1}}{C_{2}} = \{ x+C_{2}:x \in C_{1} \}, \ x+C_{2} = \{ x+y | y \in C_{2} \}
$$

Soit $x \in C_{1}$ un mot de code. On définit

$$
\ket{x+C_{2}} := \frac{1}{\sqrt{ \lvert c_{2} \rvert  }} \sum_{y \in C_{2}} \ket{x + y}
$$

Attention, $\ket{x+y} \neq \ket{x} + \ket{y}$, car $\ket{x+y} \in \mathbb{Z}_{2}^{n}$ et $\ket{x}+\ket{y}$ est une somme sur l'espace d'Hilbert. On a donc que

$$
x + C_{2} = x' + C_{2} \iff x-x' \in C_{2} \iff \exists c \in C_{2} \text{ t.q } x-x'=c \text{ et } x=x'+c
$$

On veut montrer que $\ket{x+C_{2}} = \ket{x'+C_{2}}$.

$$
\begin{align}
\ket{x'+C_{2}} &= \frac{1}{\sqrt{ \lvert c_{2} \rvert  }} \sum_{y \in C_{2}} \ket{x+y} \\
&= \frac{1}{\sqrt{ \lvert c_{2} \rvert  }} \sum_{y \in C_{2}} \ket{x'+\underbrace{ c+y }_{ \in C_{2} }} \\
&= \frac{1}{\sqrt{ \lvert c_{2} \rvert  }} \sum_{y' \in C_{2}} \ket{x' + y'} \\
&= \ket{x' + C_{2}}
\end{align}
$$

De plus, 

$$
\begin{align}
\braket{ x+C_{2} | x+C_{2} } &= \frac{1}{\lvert c_{2} \rvert } \sum_{y, y' \in C_{2}} \braket{ x+y | x+y' } \\
&= \frac{1}{\lvert c_{2} \rvert } \sum_{y,y' \in C_{2}} \braket{ y | y' } \\
&= \frac{1}{\lvert c_{2} \rvert } \sum_{y \in C_{2}} \braket{ y | y } \\
&= \frac{1}{\lvert c_{2} \rvert } \sum_{y \in C_{2}} 1 \\
&= 1
\end{align}
$$

Si $x+C_{2} \neq x' +C_{2}$, il existe $c \notin C_{2}$ tel que $x'=x+C$.

$$
\begin{align}
x+C_{2} &= x'+C \iff \exists c \in C_{2} \subset C_{1} x'=x+c \\
x+C_{2} &= x'+C_{2} \iff \exists c \in C_{1}, c \notin C_{2} x'=x+c 
\end{align}
$$

$$
\begin{align}
\braket{ x+C_{2} | x'+C_{2} } &= \frac{1}{\lvert c_{2} \rvert } \sum_{y,y' \in C_{2}} \braket{ x+y | x'+y' } \\
&= \frac{1}{\lvert c_{2} \rvert } \sum_{y,y' \in C_{2}} \braket{ x+y | x+c+y' } \\
&= \frac{1}{\lvert c_{2} \rvert } \sum_{y,y' \in C_{2}} \braket{ \underbrace{ y }_{ \in C_{2} } |\underbrace{  c+y' }_{ \notin C_{2} } } \\
&= 0
\end{align}
$$

Le code CSS$(C_{1},C_{2})$ est le code avec une base $\{ \ket{x+C_{2} | x \in C_{1} } \}$. $\text{dim}_{\mathbb{C}} \text{CSS}(C_{1},C_{2}) = \frac{\lvert C_{1} \rvert}{\lvert C_{2} \rvert} = \text{dim}_{\mathbb{Z}_{2}} \frac{C_{1}}{C_{2}} = 2^{k_{1}-k_{2}}$.

Donc, CSS$(C_{1},C_{2})$ est un $[n,k_{1}-k_{2}]$-code. Soit $e_{1}$ un vecteur avec 1 dans la coordonnée dans laquelle il y a un bit flip, et $e_{2}$ un vecteur avec 1 dans la coordonnée dans laquelle il y a un phase flip. Si l'état original est $\ket{x+C_{2}} = \frac{1}{\sqrt{ \lvert C_{2} \rvert }} \sum_{y \in C_{2}} \ket{x+y}$, l'état corrompu est $\frac{1}{\sqrt{ \lvert C_{2} \rvert }} \sum_{y \in C_{2}} (-1)^{(x+y)e_{2}} \ket{x+y+e_{1}}$. On va introduire des qubits auxiliaires pour sauvegarder le syndrome d'erreur de $C_{1}$ qui partent de l'état $\ket{0}$. Il est possible de faire

$$
\ket{z} \ket{0} \to \ket{z} \ket{H_{\perp}z}
$$

où $H_{\perp}$ est la matrice contrôle de parité de $C_{1}$. 

**Exemple:** $H = \begin{pmatrix}1 & 1 & 0 \\ 0 & 1 & 1\end{pmatrix}$. 

On a que

$$
\begin{align}
\ket{101}\ket{00} &\to \ket{101}\ket{11}
\ket{00} \to \ket{10} \to \ket{11}
\end{align}
$$

$$
\begin{pmatrix}
1 & 1 & 0 \\
0 & 1 & 1
\end{pmatrix}
\begin{pmatrix}
1 \\
0 \\
1
\end{pmatrix} = \begin{pmatrix}
1 \\
1
\end{pmatrix}
$$

$$
\frac{1}{\sqrt{ \lvert C_{2} \rvert  }} \sum_{y \in C_{2}} (-1)^{(x+y)e_{2}} \ket{x+y+e_{1}} \to \frac{1}{\sqrt{ \lvert C_{2} \rvert  }} \sum_{y \in C_{2}} (-1)^{(x+y)e_{2}} \ket{x+y+e_{1}} \ket{He_{1}}
$$

On mesure le qubit auxiliaire pour obtenir l'erreur $e_{1}$ et on le corrige

$$
\frac{1}{\sqrt{ \lvert C_{2} \rvert  }} \sum_{y \in C_{2}} (-1)^{(x+y)e_{2}}\ket{x+y}
$$

On applique $H^{\otimes n}$.

$$
\frac{1}{\sqrt{ \lvert C_{2} \rvert 2^{n} }} \sum_{Z} \sum_{y \in C_{2}} (-1)^{(x+y)(e_{2}+Z)} \ket{Z}
$$

En prenant $z' = e_{2}+z$,

$$
\begin{align}
&= \frac{1}{\sqrt{ \lvert C_{2} \rvert 2^{n} }} \sum_{z'} \sum_{y \in C_{2}} (-1)^{(x+y)z'} \ket{z'+e_{2}} \\
&= \frac{1}{\sqrt{ \frac{2^{n}}{\lvert C_{2} \rvert } }} \sum_{z' \in C_{2}^{\perp}} (-1)^{xz'} \ket{z'+e_{2}}
\end{align}
$$

On mesure les qubits auxiliaires ajoutés pour détecter et corriger. Finalement, on applique $H^{\otimes n}$ pour obtenir $\ket{x+C_{2}}$.