---
title : "de Rham上同调"
description : "An introduction"
weight : 1
---

> 在代数拓扑中，同调群是一个重要的刻画空间的拓扑不变量。而由[Stokes公式]({{< ref "Notes/微分流形杂谈.md#Stokes_formula" >}})$\int_Md\omega=\int_{\partial M}\omega$可知，对空间求边缘其实际上和对微分形式求外微分是一种对偶的操作，也就是说，可以不用同调群中求边缘的方法，应用[几何与组合]({{< ref "Notes/differential-geometry-in-physics.md" >}})去研究，而是通过研究对微分形式的外微分，应用分析的方法的去研究。后者即是上同调群(Cohomology，co其实际上都是一种对偶的意思，更常见的翻译是“余”)。

- [1. de Rham上同调群](#1-de-rham上同调群)


### 1. de Rham上同调群

首先定义闭与恰当形式。设$\mathcal{M}$是一个光滑流形，$\omega\in\Omega^k(\mathcal{M})$是$\mathcal{M}$上的一个$k$次光滑微分形式。(1)若$d\omega=0$，则称$\omega$是闭微分形式(closed form);(2)若存在$\eta\in \Omega^{k-1}(M)$使得$\omega=d\eta$，则称$\omega$是恰当形式(exact form).

> I will try my best to write in English below regarding as a challenge for me, and it is more convenient for me actually.

And we note the set of all k-closed form on $\mathcal{M}$ as $Z^k(M)$, and all the k-exact form as $B^k(M)$.

Obviously, 
* when $k>m=dimM$,there is not such thing in Z and B, i.e.$Z^k(M)=B^k(M)=\{0\}$.

* When $k=0$, $B^0(M)={0} $ since there is no '-1-form'.And 
$$
  Z^0(M)=\{f\in C^\infty(M)|df=0 \}\simeq \mathbb{R}^K,
$$
where $K$ is the # of connected component.

* When $k=m$, $Z^m(M)=\Omega^m(M) $