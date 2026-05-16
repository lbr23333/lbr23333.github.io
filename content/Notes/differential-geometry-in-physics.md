---
title : "topology and differetial geometry in physics"
description : "Note on lecture"
weight : 1
---
- [😩A really brief introduction of Symplectic geometry application in mechanics](#a-really-brief-introduction-of-symplectic-geometry-application-in-mechanics)
- [😭A really brief introduction of Homology and de Rham Cohomology](#a-really-brief-introduction-of-homology-and-de-rham-cohomology)
  - [0.一些Preliminaries和符号规定](#0一些preliminaries和符号规定)
  - [1.单纯形和复形](#1单纯形和复形)


### 😩A really brief introduction of Symplectic geometry application in mechanics

### 😭A really brief introduction of Homology and de Rham Cohomology

一些基础的内容在另一个Note中可以看到，所必须的是关于[微分形式]({{< ref "Notes/微分流形杂谈.md#differetial_form" >}})的部分。

#### 0.一些Preliminaries和符号规定

* 外微分的幂零性:$d^2=0$。其证明是很显然的，考虑到$d^2\omega=\frac{\partial^2\omega}{\partial x^i\partial x^j}dx^i\wedge dx^j\wedge dx^{\mu_1}\dots\wedge dx^{\mu_k}$中偏导数是对称而楔积是反对称的，所以为0.
* 称$\omega$为闭形式，如果$d\omega=0$.
* 称$\omega$为恰当形式，如果存在$\alpha$使得$\omega=d\alpha$.🥸
* 

#### 1.单纯形和复形

流形M上，r阶闭形式的全体组成了$Ker(d_r)$，而r阶恰当形式的全体为$Im(d_{r-1})$.于是外微分的幂零性就等价于$Im(d_{r-1})\subset Ker(d_r)$.

