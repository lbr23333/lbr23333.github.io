---
title : "topology and differetial geometry in physics"
description : "Note on lecture"
weight : 1
---
- [😩A really brief introduction of Symplectic geometry application in mechanics](#a-really-brief-introduction-of-symplectic-geometry-application-in-mechanics)
- [😭A really brief introduction of Homology and de Rham Cohomology](#a-really-brief-introduction-of-homology-and-de-rham-cohomology)
  - [0.一些Preliminaries和符号规定](#0一些preliminaries和符号规定)
  - [1.基础概念](#1基础概念)
  - [2.同调群](#2同调群)


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

