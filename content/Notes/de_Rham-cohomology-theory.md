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
    \begin{equation} 
      \dots\rightarrow A^{k-1}\xrightarrow{d_{k-1}}A^{k}\xrightarrow{d_k}A^{k+1}\xrightarrow{d_{k+1}}A^{k+2}\rightarrow\dots
    \end{equation}
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

And then we can introduce the short exact sequence of complex. Let $\mathcal{A,B,C} $ are cochain complexes, and $\forall k $
$$
  0\rightarrow A^k\rightarrow B^k \rightarrow C^k \rightarrow 0 
$$
is short exact sequence, then we say $\mathcal{A,B,C} $ form a short exact sequence of complex, and note it as'$0\rightarrow \mathcal{A}\rightarrow\mathcal{B}\rightarrow\mathcal{C}\rightarrow 0 $'. In a simple way, it is a huge grid, in which every line is '$0\rightarrow A^k\rightarrow B^k \rightarrow C^k \rightarrow 0  $' and every row is a cochain sequence. There is a principle in the homological Algebra that if by this such complex short exact sequence, we can construct a long exact sequence of homological groups as 
$$
  \dots\rightarrow H^{k-1}(\mathcal{C})\rightarrow H^{k}(\mathcal{A})\rightarrow H^{k}(\mathcal{B})\rightarrow H^{k}(\mathcal{C})\rightarrow H^{k+1}(\mathcal{A})\rightarrow\dots
$$
What we will deal with next is just getting the specific expression of the maps between the groups.Let  $M $ be a smooth manifold  and $M=U\cup V $,where $U,V $ are open set. then we get 4 de Rham cochain complexes:
$$
  \begin{align*}
   &\Omega^*(M):0\rightarrow\Omega^0(M)\rightarrow\Omega^1(M)\rightarrow\Omega^2(M)\rightarrow\dots
    \\
    &\Omega^*(U):0\rightarrow\Omega^0(U)\rightarrow\Omega^1(U)\rightarrow\Omega^2(U)\rightarrow\dots
    \\
    &\Omega^*(V):0\rightarrow\Omega^0(V)\rightarrow\Omega^1(V)\rightarrow\Omega^2(V)\rightarrow\dots
    \\
    &\Omega^*(U\cup V):0\rightarrow\Omega^0(U\cup V)\rightarrow\Omega^1(U\cup V)\rightarrow\Omega^2(U\cup V)\rightarrow\dots
  \end{align*}
$$
In fact, these cochain complexes form a complex short exact sequence:
$$
  0\rightarrow\Omega^*(M)\rightarrow \Omega^*(U)\oplus\Omega^*(V)\rightarrow
  \Omega^*(U\cap V)\rightarrow 0
$$
where we consider inclusion map:
$$
  \begin{align*}
    &\iota_1:U\rightarrow W  &\iota_2:V\rightarrow W
    \\& j_1:U\cap V\rightarrow U  & j_2:U\cap V\rightarrow V
  \end{align*}
$$
which induce the linear maps between cochain complexes:
$$
  \alpha_k:\Omega^k(M)\rightarrow \Omega^*(U)\oplus\Omega^*(V)
  \\ \alpha_k(\omega)=(\iota_1^*\omega,\iota_2^*\omega)
$$
and
$$
  \beta_k:\Omega^*(U)\oplus\Omega^*(V)\rightarrow \Omega^*(U\cap V)
  \\ \beta_k(\omega_1,\omega_2)=j_1^*\omega_1-j_2^*\omega_2
$$
By the definition of the inclusion map, it is obvious that $\alpha_k $ is injection, $\beta_k $ is surjection. And we need  $\beta_k\circ\alpha_k =0 $:
$$
  \beta_k\circ\alpha_k(\omega)=j_1^*\iota_1^*\omega-j_2^*\iota_2^*\omega
$$
Note that $\iota^* $ and $j_1^* $ are some kind of simple way of $(d\iota)^* $ and $(j)^* $, it is mathematician who like to do this （

So 
$$
  j_1^*\iota_1^*\omega-j_2^*\iota_2^*\omega(v_1,\dots,v_2)=\omega((\iota_1j_1-\iota_2j_2)v_1,\dots)
$$
By Observation, we know that 
$$
  (\iota_1j_1-\iota_2j_2)v_i=0,\forall v_i\in T_pM,\forall p\in M
$$
then 
$$
  \beta_k\circ\alpha_k(\omega)=j_1^*\iota_1^*\omega-j_2^*\iota_2^*\omega=0
$$
___
In fact, it is obvious that $\beta_k $ is surjection, in which there is some problem leading to the same trick in constructing M-V sequence: 

We can trivially think that, 
$$
  \beta_k:\Omega^*(U)\oplus\Omega^*(V)\rightarrow \Omega^*(U\cap V)
  \\ \beta_k(\omega_1,\omega_2)=j_1^*\omega_1-j_2^*\omega_2
$$
then $\forall \eta \in \Omega^*(U\cap V)$, we can always choose $\omega_2=0 $ and let $\omega_1|_{U\cap V}=\eta $, and claim that we have finish the proof.But the $\omega_1|_{U\cap V} $ is the bug, we can't even make sure that it is smooth. So we can take P.O.U {$\rho_U,\rho_V $} of $U,V $, where $supp(\rho_U) \subset U,supp(\rho_V) \subset V  $. Although $\rho_U\eta $ may still not be continuous on $U $, it must be continuous on $V $ since we avoid some problem on the boundary, i.e. we choose
$$
  \omega_1=\begin{cases}
    \rho_V\eta \text{ on } U\cap V 
    \\ 0 \text{ on } U-V
  \end{cases}
$$
And we get $\omega_2=-\rho_U \eta $ on $V $, then we have 
$$
  \forall \eta\in \Omega^*(U)\oplus\Omega^*(V), \exist j_1^*\omega_1-j_2^*\omega_2=\eta ,
$$
i.e. $\beta_k $ is surjection.

As I say at the beginning, this trick we will meet again before long.
> 也就是说我们总得考虑边界上极坏的情况，而这个情况又总可以取为另一边的0，所以交换一下就都完美解决了
___
___
___