---
title : "de Rham上同调"
description : "An introduction"
weight : 1
---

> 在代数拓扑中，同调群是一个重要的刻画空间的拓扑不变量。而由[Stokes公式]({{< ref "Notes/微分流形杂谈.md#Stokes_formula" >}})$\int_Md\omega=\int_{\partial M}\omega$可知，对空间求边缘其实际上和对微分形式求外微分是一种对偶的操作，也就是说，可以不用同调群中求边缘的方法，应用[几何与组合]({{< ref "Notes/differential-geometry-in-physics.md" >}})去研究，而是通过研究对微分形式的外微分，应用分析的方法的去研究。后者即是上同调群(Cohomology，co其实际上都是一种对偶的意思，更常见的翻译是“余”)。

- [1. de Rham上同调群](#1-de-rham上同调群)
- [2.Mayer-Vietoris sequence](#2mayer-vietoris-sequence)


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






### 2.Mayer-Vietoris sequence

> 一种计算特定上同调群的工具

* Exact sequence
  
  Let $(\mathcal{A},d) $ is a cochain complex, i.e.
  $$
    \dots\rightarrow A^{k-1}\xrightarrow{d_{k-1}}A^{k}\xrightarrow{d_k}A^{k+1}\xrightarrow{d_{k+1}}A^{k+2}\rightarrow\dots
  $$
  where $A^k $ is linear space. $d_{k}:A^k\rightarrow A^{k+1} $ is linear map,and it satisfies 
  $$
    d_{k+1}\circ d_k=0 ,\forall k
  $$
  So it is obvious that $Im(d_{k})\subset Ker(d_{k+1}) $.And we can define the cohomology group like de Rham one:
  $$
    H^k(\mathcal{A},d)=Ker(d_k)/Im(d_{k-1})
  $$
  We call $(\mathcal{A},d) $ is __exact sequence__ if 
  $$
    H^k(\mathcal{A},d) =0,\forall k \Leftrightarrow Ker(d_k)=Im(d_{k-1})
  $$

* Special cases:
    * Starting from 0:
    $$
      0\xrightarrow{d_0} A^1\xrightarrow{d_1} A^2\xrightarrow{d_2}A^3\rightarrow \dots
    $$
        then $d_1 $ is injection since $Ker(d_1)=Im(d_0)=0 $.
        > Note that it is linear map, so there has to be a 0 and only a 0.
    * Ending with 0:
    $$
      \dots\xrightarrow{d_0} A^1\xrightarrow{d_1} A^2\xrightarrow{d_2}A^3\xrightarrow{d_3} 0
    $$
        then $d_2 $ is surjection since $Im(d_2)=Ker(d_3)=A^3 $.

    * Very short exact sequence:
    $$
      0\rightarrow A^1\xrightarrow{\alpha} A^2\rightarrow 0
    $$
        $\alpha $ is injection since $Ker(\alpha)=0 $ and $\alpha $ is surjection since $Im(\alpha)=A^2 $, which means that $\alpha $ is bijection and in fact isomorphism.

    * __Short exact sequence__:
    $$
       0\xrightarrow{d_0} A^1\xrightarrow{d_1} A^2\xrightarrow{d_2}A^3\rightarrow 0
    $$
        we have known that $d_1 $ is injection and $d_2 $ is surjection,and by the isomorphism theorem:
        $$
          A^2 \simeq ker(d_2)\oplus Im(d_2) \simeq Im(d_1)\oplus Im(d_2)\simeq A^1\oplus A^3
        $$


___
___
___
___