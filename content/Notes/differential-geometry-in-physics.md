---
title : "topology and differetial geometry in physics"
description : "Note on lecture"
weight : 1
---

> 原本以为是很严谨的，没想到是和物理系中其他课一样的草率。不过如果视作motivation去进一步学习，那便是极佳的。

- [😩A really brief introduction of Symplectic geometry application in mechanics](#a-really-brief-introduction-of-symplectic-geometry-application-in-mechanics)
- [😭A really brief introduction of Homology and de Rham Cohomology](#a-really-brief-introduction-of-homology-and-de-rham-cohomology)
  - [0.一些Preliminaries和符号规定](#0一些preliminaries和符号规定)
  - [1.基础概念](#1基础概念)
  - [2.同调群](#2同调群)
- [HOMOTOPY GROUPS](#homotopy-groups)
  - [映射空间与同伦群](#映射空间与同伦群)


### 😩A really brief introduction of Symplectic geometry application in mechanics

待施工

### 😭A really brief introduction of Homology and de Rham Cohomology

一些基础的内容在另一个Note中可以看到，所必须的是关于[微分形式]({{< ref "Notes/微分流形杂谈.md#differetial_form" >}})的部分。

#### 0.一些Preliminaries和符号规定

* 外微分的幂零性:$d^2=0$。其证明是很显然的，考虑到$d^2\omega=\frac{\partial^2\omega}{\partial x^i\partial x^j}dx^i\wedge dx^j\wedge dx^{\mu_1}\dots\wedge dx^{\mu_k}$中偏导数是对称而楔积是反对称的，所以为0.
* 称$\omega$为闭形式，如果$d\omega=0$.
* 称$\omega$为恰当形式，如果存在$\alpha$使得$\omega=d\alpha$.
* 

#### 1.基础概念

设$0\le r\le m,p_0,p_1,\dots p_r$是$\mathbb{R}^{r+1}$中r+1个几何独立的点，所谓的几何独立是指他们不全都位于任何一个(r-1)维的超平面上。那么称
$$
  \{x\in\mathbb{R}^m|x=\sum_{i=0}^{r}c_ip_i,c_i\ge0,\sum_{i=0}^r c_r=0 \}
$$
为一个r-单纯形，记作$\sigma=<p_0p_1\dots p_r>$.

例如，$\sigma^0=<p_0>$就是一个单点$p_0$.同理,$\sigma^1,\sigma^2,\sigma^3$就分别是线段，三角形和四面体。

在$\sigma^r$中任取q+1个点构成$\sigma^q$，称之为$\sigma^r$的一个q-面.且若$\sigma^q\ne\sigma^r$，则称之为$\sigma^r$的一个真面，记作$\sigma^q<\sigma^r$.

$K$是$\mathbb{R}^m$中有限多个单形的集合，$K$是一个单纯复形，如果
* 对于K中的任意单形$\sigma$,$\sigma'<\sigma\Rightarrow\sigma'\in K$
* 对于K中有交的单形$\sigma,\sigma'$，其交$\sigma\cap\sigma'$为$\sigma,\sigma'$的公共边，即$\sigma\cap\sigma'<\sigma,\sigma\cap\sigma'<\sigma'$.

复形K的全体单形的全体点构成点空间$｜K｜\subset \mathbb{R}^m$成为一个多面体，而K为该多面体的一个单纯剖分，或称之为三角剖分，剖分。注意多面体允许有不同的三角剖分。

> 剖分是很重要的，它将一个复杂（或者说研究起来很复杂）的几何对象简化成了许多个三角形，而显然这个剖分是与所研究的对象同胚的。于是总是可以利用一些同胚不变量对该几何对象进行研究，这就是代数拓扑的意义。

定向的单形，$r\ge1$的单形总是可以引入两种不同的定向，如
$$
  \begin{align*}
    \sigma^1&=(p_0p_1)=-(p_1p_0)
    \\
    \sigma^2&=(p_0p_1p_2)=(p_1p_2p_3)=\dots=-(p_1p_0p_3)=\dots
  \end{align*}
$$

如果复形K有$I_r$个r定向单形$\sigma^r_i,1\le i\le I_r$,定义复形的一个r-链为
$$
  c_r=\sum_{i=1}^{I_r}n_i\sigma_i^r,n_i\in \mathbb{Z}
$$
显然K中所有的r-链$c_r$构成一个群$C_r(K)$，称之为链群，且有$C_r(K)\simeq\mathbb{Z}\oplus\mathbb{Z}\oplus\dots\oplus\mathbb{Z}$.

再定义边缘算子$\partial_r:C_r(K)\rightarrow C_{r-1}(K)$为:
$$
  \partial_r(p_0p_1\dots p_r)=\sum_{i=0}^r(-1)^i(p_0\dots \hat p_i\dots p_r)
$$
如$\partial_0p_0=0,\partial_1(p_0p_1)=p_1-p_0,\partial_2(p_0p_1p_2)=(p_1p_2)-(p_0p_2)+(p_0p_1)$.

于是可以构造一个链复形:
$$
  0\hookrightarrow C_n(K) \xrightarrow{\partial_n}C_{n-1}(K)\xrightarrow{\partial_{n-1}}\dots\xrightarrow{\partial_1}C_1(K)\xrightarrow{\partial_1}C_0(K)\xrightarrow{\partial_0}0
$$
对于满足$\partial_rc=0$的$c$，其全体构成$C_r(K)$的子群$Z_r(K)$，称为r-闭链，显然有$C_0(K)=Z_0(K)$.对于满足$c=\partial_{r+1}c',c'\in C_{r+1}(K)$的全体，同样构成子群$B_r(K)$,显然对于最高维的$m=dimK,B_m(K)=\emptyset$.

可以计算得到，边缘算子同样具有幂零性$\partial^2=\partial_r\partial_{r+1}=0$，也就是说“边缘的边缘为0”。

有了这些基础，就可以引入同调群。

#### 2.同调群








流形M上，r阶闭形式的全体组成了$Ker(d_r)$，而r阶恰当形式的全体为$Im(d_{r-1})$.于是外微分的幂零性就等价于$Im(d_{r-1})\subset Ker(d_r)$.这是一个很好性质

### HOMOTOPY GROUPS

引入一种新的等价关系,考虑 $\mathcal{F} $ 是从拓扑空间 $X $ 到拓扑空间 $Y $ 的连续映射集,对于 $f,g\in \mathcal{F} $ ,若在 $Y $ 中 $f(X) $ 可以连续形变到 $g(X) $ ,那么称 $f $ 同伦于 $g $ .

% #### 1.基本群
%
%考虑一个有洞的disc拓扑空间 $X $ 和一个没有洞的 $Y $ , $Y $ 中的闭合曲线总是可以连续地收缩到一点,也就是说 $Y $ 中所有的曲线都是同伦等价的,或者说,  $Y $ 中只有一个同伦类.但是在 $X $ 中,每一个同伦类由 $n\in \Z $ 所刻画, $n<0 $ 表示绕洞顺时针旋转的次数, $n>0 $ 就是绕洞逆时针.也就是说 $X $ 中有无穷多的等价类,考虑到 $\Z $ 的加法群结构, $n+m $ 就对应于先绕 $n $ 次再绕 $m $ 次的闭合曲线.同伦类的集合因此就被赋予了群结构,此即基本群(fundamental group).
%
%##### paths and loops

#### 映射空间与同伦群
在拓扑空间 $\Sigma,X $ 中分别取定**基点** $\sigma_0\in\Sigma,x_0\in X $ ,考虑所有保持基点的映射 $f:\Sigma\rightarrow X $ ,即 $f(\sigma_0)=x_0 $ ,所有的保持基点的连续映射构成一个映射空间 $X^\Sigma=\{f|f:\Sigma\rightarrow X,f(\sigma_0)=x_0 \} $ .
{{% mathbox type="slate" title="例子" %}}
* 显然 $X^\{1\}={f_0} $ 是一个单点集,由单个映射 $f_0(1)=x_0 $ 所构成.
* 对于 $S^0=\{ \pm 1  \} \rightarrow X $ 的 $X^{\{ S^0 \} } $ ,基点为 $f(1)=x_0 $ ,所以 $f $ 完全由 $f(-1) $ 所确定, $\forall f\in X^{ S^0  },f\xLeftrightarrow{1:1}f(-1)\in X $,也就是说 $X^{ S^0 }\simeq X $.  
* 显然,对于离散的多点集 $\Sigma=\{ \sigma_0,\sigma_1,\dots,\sigma_n \}  $ 到 $X $ 所构成的 $X^{\left\{ \Sigma \right\} } $ 有
$$
  X^{\left\{ \Sigma \right\} }\cong \underbrace{X \times \dots \times X}_n
$$
{{% /mathbox %}}

{{% mathbox type="green" title="约定" %}}
 $\cong $ 表同胚, $\simeq $ 表同伦, $\sim $ 是同调或者一般的等价关系.
{{% /mathbox %}}

由此可以定义所谓的**道路空间**和**圈空间**: $X^{[0,1]},X^{S^1} $:
$$
  X^{[0,1]}=\left\{ f|f(t)\in X;f(0)=x_0 \right\} 
  \\
  X^{S^1}=\left\{ f|f(t)\in X;f(0)=f(1)=x_0 \right\} 
$$
另外,保基映射 $f:\Sigma_2\rightarrow \Sigma_1,g:X_1\rightarrow X_2 $  诱导了   $g^f:X_1^{\Sigma_1}\rightarrow X_2^{\Sigma_2} $ ,其中 $g^f(h)=g\circ h\circ f ,\forall h\in X_1^{\Sigma_1}$ 
>  $\Sigma_2\xrightarrow{f}\Sigma_1\xrightarrow{h}X_1\xrightarrow{g}X_2 $

{{% mathbox type="blue" title=" $g^f $ 的结合性" %}}
具有某种结合性,也就说,对于另外两个保基映射 $f':\Sigma_3\rightarrow \Sigma_2,g':X_2\rightarrow X_3 $ ,那么
$$
  {g'}^{f'}\circ g^f=(g'\circ g)^{f\circ f'}:X_1^{\Sigma_1}\rightarrow X_3^{\Sigma_3}
$$
根据连续函数的复合的结合律可以很容易得到.实际上,也就是将
$$
  \Sigma_2\xrightarrow{f}\Sigma_1\xrightarrow{h}X_1\xrightarrow{g}X_2 
$$
增长到了
$$
  \Sigma_3\xrightarrow{f'}
  \Sigma_2\xrightarrow{f}\Sigma_1\xrightarrow{h}X_1\xrightarrow{g}X_2 
  \xrightarrow{g'}X_3 
$$
{{% /mathbox %}}
根据该性质, $f_t,g_t $ 分别是两个伦移,那么 $H(\cdot,t)={g_t}^{f_t}:X_1^{\Sigma_1}\rightarrow X_2^{\Sigma_2} $ 就给出了从 $g_0^{f_0} $ 到 $g_1^{f_1} $ 的伦移,因为连续函数的复合还是连续函数.

{{% mathbox type="blue" title="同伦复合" %}}
若 $\Sigma_1\simeq\Sigma_2,X_1\simeq X_2 $ ,那么 $X_1^{\Sigma_1}\simeq X_2^{\Sigma_2} $ 

根据同伦的定义,存在一些复合为 $\mathbb{1} $的函数,再结合上命题就很容易证明. 

推论: 道路空间总是可缩的,即 $X^{[0,1]} \simeq X^{\left\{ 1 \right\} }\simeq \left\{ f_0 \right\}  $ .这在直观上也是很显然的.
{{% /mathbox %}}

{{% mathbox type="blue" title="" %}}
给定拓扑空间 $X_j,Y_j $ 及连续保基映射 $f_j:X_j\rightarrow Y_j $ ,存在 $\vee_{i}f_j:\vee_j X_j\rightarrow \vee_j Y_j $,具有如下性质
* 若 $g_j:Y_j\rightarrow Z_j $ 是连续保基映射,那么
$$
  \left(\bigvee_j g_j\right )\circ \left(\bigvee_j f_j\right )=\bigvee_j (g_j\circ f_j)
$$
* 若 $f_j\simeq g_j:X_j\rightarrow Y_j  $  是同伦等价的映射,那么
$$
  \bigvee_j f_j\simeq \bigvee_j g_j:\bigvee_j X_j\rightarrow \bigvee_j Y_j
$$
{{% /mathbox %}}
> 直观上,可以将 $\bigvee_j X_j $ 理解成一朵花🌸,不同的 $X_j $ 就是各个花瓣,对其做楔和也就是将其粘到一起,只在中心一点相交. $f_j $ 的保基性使得其基点只能取为花的中心(也即交点 $x_0,y_0 $ ),否则会导致函数多值.这样的视角下,后面两个性质就几乎是显然的了.

给出显式的表达, $F=\bigvee f_j:\bigvee X_j\rightarrow \bigvee Y_j $ 自然地定义为
$$
  F([x])=\left( \bigvee _j f_j \right) ([x])=[f_k(x)],x\in X_k,k\in J
$$

可以证明该定义的良定性,即与 $[x] $ 的代表元选取无关,实际上楔和中所诱导的等价类也只有两种,即交点和非交点:
* 对于各个交点 $x=\mathring{x_k} $ ,选择任意的 $\mathring{x}_j,j\in J $ ,其都被 $F $ 映射到 $\bigvee_j  Y_j $ 中的交点处,所以与代表元选取无关.
* 对于 $x\in X_k/\left\{ \mathring{x}_k \right\}  $ ,显然 $[x]=\left\{ x \right\}  $ 只有一个元素,自然良定.

那么,令 $G=\bigvee g_j:\bigvee Y_j\rightarrow \bigvee Z_j $ ,当 $x\in X_k $ , $f_k(x)\in Y_k $ 时,有
$$
  G\circ F([x])=G([f_k(x)])=[g_k\circ f_k(x)]
  \\
  =\left( \bigvee(gj\circ f_j) \right) ([x])
$$
于是我们证明了第一个性质.对于第二条: 设 $f_j\simeq g_j $ ,有伦移
$$
  H_j:X_j\times [0,1]\rightarrow Y_j
$$
定义
$$
  H(\cdot,t)=\bigvee_j H_j(\cdot,t):\bigvee_j X_j\rightarrow \bigvee_j Y_j
$$
提供了 $\bigvee f_j $ 到 $\bigvee g_j $ 的伦移,自然就是第二条结论.

由上命题,可以得到一个推论:若 $X_j\simeq Y_j,\forall j\in J $ ,则 $\bigvee X_j \simeq \bigvee Y_j $.由同伦的定义和上命题第一条任意证明.于是: $Y\simeq \left\{ \mathring{y} \right\}  $是可缩空间,那么 $X\vee Y\simeq X\vee \left\{ \mathring{y} \right\} \cong X $ .

完全同理地,可以得到归纳积的相关同伦性质.
先简单回顾归纳积的定义
$$
  X\wedge Y:=(X\times Y)/(X\vee Y)
$$
例如
* 对于单点集 $\left\{ \mathring{y} \right\}  $ 和以 $\mathring{x} $ 为基点的空间X,前面已经知道了
$$
  X\vee \left\{ \mathring{y} \right\}\cong \left( X\times \left\{ \mathring{y} \right\} \right) \cup \left( \left\{ \mathring{x} \right\} \times \left\{ \mathring{y} \right\}\right) 
  \\
  =X\times \left\{ \mathring{y} \right\}
$$
于是
$$
  X\wedge\left\{ \mathring{y} \right\}=(X\times \left\{ \mathring{y} \right\})/(X\vee \left\{ \mathring{y} \right\})
  \\
  \cong (X\times \left\{ \mathring{y} \right\})/(X\times \left\{ \mathring{y} \right\})
  \\
  =\left\{ \mathring{x} \right\}\times\left\{ \mathring{y} \right\}=\left\{ (\mathring{x}, \mathring{y}) \right\}
$$
也就是说 $X\wedge\left\{ \mathring{y} \right\} $ 同胚于一个单点集.

* 对于 $X\wedge S^0=X\wedge \left\{ \pm 1 \right\}  $ ,可以类似处理.不妨选取 $x_0,+1 $ 为基点,那么
$$
  X\vee S^0=(X\times \left\{ + 1 \right\} )\cup (\left\{ \mathring{x}\times S^0 \right\} )
$$
于是
$$
  \begin{align*}
    X\wedge S^0&=(X\times S^0)/(X\vee S^0)
    \\ &=X\times \left\{ -1 \right\} \cong X
  \end{align*}
$$
> 这里最后一步的商细节如下:
>
> 首先考虑 
$$
  X\times S^0=(X\times \left\{ +1 \right\} )\cup (X\times \left\{ -1 \right\} ) =X_{top} \cup X_{down}
$$
> 于是 $(X\times S^0)/(X\times\left\{  +1 \right\} )\cong (\left\{ \mathring{x} \right\} \times \left\{ +1 \right\} )\cup (X\times \left\{ -1 \right\} ) $ .
> 再模去 $\left\{ \mathring{x} \right\} \times \left\{ \pm 1 \right\}  $ 也就是得到
$$
  (\left\{ \mathring{x} \right\} \times \left\{ +1 \right\} )\cup (X_{down}/\left\{ (\mathring{x},-1) \right\}  )\cong X_{down}
$$
可知在 Smash Product 中, $S^0 $ 是类似单位元的东西.


*  $X\wedge S^1 $ :
  
    可以想象类似 $T^2 $ 的东西,
    ![picsol1](/images/Topology/picsol1.png)
    应用图解法可以得到




{{% mathbox type="blue" title="归纳积" %}}

{{% /mathbox %}}




___
___
___
___