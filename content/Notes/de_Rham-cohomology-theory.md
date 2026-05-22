---
title : "de Rham上同调"
description : "An introduction"
weight : 1
---

> 在代数拓扑中，同调群是一个重要的刻画空间的拓扑不变量。而由[Stokes公式]({{< ref "Notes/微分流形杂谈.md#Stokes_formula" >}})$\int_Md\omega=\int_{\partial M}\omega$可知，对空间求边缘其实际上和对微分形式求外微分是一种对偶的操作，也就是说，可以不用同调群中求边缘的方法，应用[几何与组合]({{< ref "Notes/differential-geometry-in-physics.md" >}})去研究，而是通过研究对微分形式的外微分，应用分析的方法的去研究。后者即是上同调群(Cohomology，co其实际上都是一种对偶的意思，更常见的翻译是“余”)。

- [1. de Rham上同调群](#1-de-rham上同调群)
- [2.Mayer-Vietoris sequence](#2mayer-vietoris-sequence)
- [3.Compact support set de Rham cohomology group](#3compact-support-set-de-rham-cohomology-group)
- [4.The highest rank de Rham cohomology group](#4the-highest-rank-de-rham-cohomology-group)
- [5.Map degree theory and its application](#5map-degree-theory-and-its-application)


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
> 也就是说我们总得考虑边界上极坏的情况，而这个情况又总可以取为另一边的0，所以交换一下就都完美解决了.
___

### 3.Compact support set de Rham cohomology group

___

### 4.The highest rank de Rham cohomology group

In this section, we will prove some theorems about the highest-rank de Rham cohomology group.

1. Let $M $ be a connected oriented smooth manifold with m-dimension, then the map $\int_M:H^m_c(M)\rightarrow \R $ is linear isomorphism.(i.e. $H^m_c(M)\simeq \R $)
   
2. Let $M $ be a connected orientable smooth manifold with m-dimension, then $H^m_{dR}\simeq \R $.

3. Let $M $ be a non-connected orientable smooth manifold with m-dimension, then $H^m_{dR}=0 $.
   pf.There always exists exhausted function which divides M into local countable covering $\{V_k\}$, which satisfy:
   * each $V_k $ is connected and precompact.
   * $\forall k $,$\exist j>k $ s.t. $V_k\cap V_j\ne 0 $.(In fact, by the definition of exhausted function, $V_k\cap V_j\ne 0 \iff j=k-1,k,k+1$)

    Suppose $\omega $ is any smooth n-form on M, then we can take P.O.U of $\{V_k\} $ as $\{\rho_k\}$ and for each $i $ there is a $\theta_i\in \Omega^{n}_c(M) $ supported on $V_i\cap V_{i+1} $ ,satisfying $\int_M \theta_i =1 $ .Then $\omega_i=\rho_i \omega \in \Omega^n_c(V_i) $, let $c_1=\int_{V_1} \omega_1 $, so $\omega_1-c_1\theta_1 $ is compactly supported on $V_1 $ and $\int_{V_1}(\omega_1-c_1\theta_1)=0 $. By thm1, we know that there exists $\eta_1$ s.t.$d\eta_1=\omega_1-c_1\theta_1 $. In the same way, we can choose $c_2\in\R $ such that 
    $$
      \int_{V_2}(\omega_2+c_1\theta_1-c_2\theta_2)=0 
      \\
      \exist \eta_2 ~~s.t.~~d\eta_2=\omega_2+c_1\theta_1-c_2\theta_2
    $$
    Continuing this way, We get $d\eta_j=\omega_j+c_{j-1}\theta_{j-1}-c_j\theta_j $.Set $\eta=\sum_i \eta_i $, it is well-defined since the local countable of the $\{V_k\} $.And 
    $$
      d\eta= d\sum_{i=1}^\infty \eta_i=\sum_{i=1}^\infty \omega_i=\sum_{i=1}^\infty\rho_i \omega=\omega
    $$
    So we find that $\omega\in B^m_{dR}(M),\forall \omega\in \Omega^m(M) $, i.e. $ H^m_{dR}=0 $.
___

### 5.Map degree theory and its application

Let $M,N $ be connected oriented manifolds with $m$-dimension, and $f:M\rightarrow N $ is a proper smooth map. Since we have known that the highest-level $H^m_c(M)\simeq H^m_c(N) \simeq \R $, the map
$$
  f^*:H^m_c(M)\to H^m_c(N)(i.e.\R\rightarrow \R)
$$
is a linear map. So there is a constant depending only on $f $:
$$
  \int_M f^*\omega= deg(f)\int_N \omega.
$$
The $deg(f) $ is the map degree.

> a map between topological spaces is called proper if inverse images of compact subsets are compact.

Consider the parameter-changing formula, we have

>Thm:  Map degree is integer and
$$
  deg(f)=\sum_{i=1}^k\sigma_i, \sigma_i=\begin{cases}
    1,\text{ if f is keeping oriented}
    \\ -1,\text{ if f is inversing oriented.}
  \end{cases}
$$

In particular, the antipodal map
$$
  f:S^m\rightarrow S^m,p\mapsto f(p)=-p
$$
and we know that it is orientation-preserving when $m $ is odd and orientation- inverse when $m $ is even. So
$$
  deg(f)=\begin{cases}
    &1,     &\text{m is odd};
    \\& -1, &\text{m is even}.
  \end{cases}
$$

>Thm:Let $M,N,P $ be connected oriented manifolds with the same dimensions:
>* If $f:M\rightarrow N $ and $g:N\rightarrow P $ are proper maps, then $g\circ f $ is also proper and
$$
  deg(g\circ f)=deg(f)deg(g)
$$
>* If $f $ and $g $ are proper and homotopic, them
$$
  deg(f)= deg(g)
$$

With the Whitney approximate thm, there always exists a smooth $g $ homotopic to $f $, with $deg(f)=deg(g) $.Conversely, the degrees cna be used to describe whether 2 maps are homotopic:

> Hopf map degree theory:
>
> Let $M $ is a connected oriented __compact__ manifold with $m $-dimension, then the continuous map $f,g:M\rightarrow S^m $ are homotopic if and only if $deg(f)=deg(g) $.

This shows that the map degree is the **only** homotopic invariance in continuous map space $C(M,S^m) $, but I will not prove this thm here.

And we can get map degree by the local information:
> Let $M,N $ be connected oriented manifolds. If the proper smooth map $f:M\rightarrow N $ is not surjection, then $deg(f)=0 $.

pf. consider that the proper map is closed map(closed set $\to $ closed set), then if $q\notin f(M) $, there exists open nbhd $\tilde{U} $ of $q $, s.t.$\tilde{U}\cap f(M)=0 $. Take a $m $-form $\omega $ supported on $\tilde{U} $ s.t. $\int_M \omega=1 $.And $\int_M f^*\omega =0 $ since there is no pre-image in $M $.So the map degree $deg(f)=0 $.

It is kind of counterintuitive, but recall the map degree is the **only** homotopic invariance in continuous map space. You(in fact it is me) will feel comfortable.

Consider $f $ is surjection and proper. Let $q\in N $ is a regular value of $f $. Then $f^{-1}(q)=\{p_1,\dots,p_k\} $ is a finite set, and there exists nbhd $\tilde{U} $ of $q $ and nbhd $\{U_i\} $ of $p_i $  s.t.
* for $i\ne j $,$U_i\cap U_j= \emptyset $
* $f^{-1}(\tilde{U})=\cup_{i=1}^k U_i$
* f is diffeomorphism between $\tilde{U} $ and any $U_i $.

And we can choose the charts $U_i,\tilde{U} $, which are small enough s.t. they are respectively connected and oriented charts. Let
$$
  \sigma_i=\begin{cases}
    &1 ,& f:U_i\rightarrow \tilde{U} \text{ is orientation-preserving}
    \\&-1,& f:U_i\rightarrow \tilde{U}\text{ is orientation-inverse}
  \end{cases}
$$
Take $\omega\in \Omega^m_c(\tilde{U}) $ s.t. $\int_N \omega=1 $. Then $supp (f^*\omega) \subset \cup_{i=1}^k U_i$, and
$$
  \int_M f^*\omega =\sum_{i=1}^k\int_{U_i}f^* \omega=\sum_{i=1}^k\sigma_i\int_{\tilde{U}}\omega=\sum_{i=1}^k\sigma_i
$$ 

Then we have proved:
> the map degree of $f$ has to be integer, and 
$$
  deg(f)=\sum_{i=1}^k\sigma_i
$$ 

Consider 
$$
  f:\mathbb{C}\rightarrow \mathbb{C},w\mapsto w^k
$$
Since $f $ is always orientation-preserving adn there are k regular pre-images when $w\ne 0 $, we know that $deg(f)=k $.And we can use this to prove the Algebra foundational theorem:

Consider polynomial $P(z)=z^k+a_{k-1}z^{k-1}+\dots+a_1z+a_0 $, and $S^2 $ is the compactiftion of $\mathbb{C} $, in where we take North pole $N $ as $\infty $. Then we consider the homotopy between $P(z) $ and $z^k $:
$$
  F:S^2\times [0,1] \rightarrow S^2
  \\
  F(z,t)=z^k+t(a_{k-1}z^{k-1}+\dots+a_1z+a_0)
$$
Since the homotopic invariance of the map degree, we know that
$$
  deg(P(z))=deg(z^k)
$$
If there is not any solution of $P(z) $, i.e. $P(z) $ is not surjection at least $0\notin P(S^2) $. With the theorem we have proved, $deg(P(z))=0 $.Contradiction!

So there is at least 1 solution, then we use the local method.

If $0 $ is a regular value, i.e. there is not multiple root. Take a $\omega\in \Omega^k_c(S^2) $ s.t. $\int_{S^2}\omega=1 $ , its nbhd $U $ and nbhd of 0-pre-images $\{U_i\} $:
$$
  \int_{S^2}P^*\omega=\sum_{i=1}^k\int_{U_i}P^*\omega=\sum_{i=1}^k\sigma_i\int_U\omega=\sum_{i=1}^k\sigma_i=k
$$
where $\sigma_i=1 $ since $P $ is orientation-preserving.

 If $w $ is  one of the solutions, $w $ is a $m $-multiple root.Then $0 $ is not a regular value now. Near the $w $, $P(z)\sim (z-w)^m $ and its nbhd is $U_1 $. so
$$
  \int_{S^2} P^*\omega=\int_{U_1}P^*\omega +else=m\int_U\omega+else
$$
Consider $P(z)=P(\rho e^{i\theta})=\rho^m e^{im\theta} $, so 
$$
  \begin{align*}
   r\rightarrow  r^m,\theta\rightarrow m\theta
  \end{align*}
$$
but $r=1 $, then the integral is 
$$
  \int_0^{\theta}\int_0^1f(r,\theta)\rightarrow \int_0^{m\theta}\int_0^1f(r,\theta)=m\int_0^{\theta}\int_0^1f(r,\theta)
$$

we can see that, even though there is a multiple root, it dose not change the map degree. 

In fact, with the Sard thm, we can always take a regular value by take a perturbation and avoid the critical value, and we have k good pre-images.

SO we have proved the Algebra foundational theorem.

And we can use the property of map degree to prove the Hairy ball thm:

> There is nowhere vanishing smooth vector field on $S^{2n} $.
> nowhere vanishing是处处非0，但是我不知道这样翻译对不对

Set X is the nowhere vanishing vector field on $S^{2n}\in \R^{2n+1} $, and we can set $|X_p|=1 ,\forall p\in S^{2n}$ by the metric structure on Euclidean space. Consider the map:
$$
  F: S^{2n}\times [0,1]\rightarrow S^{2n},F(p,t)=p \cos(t\pi)+X_p\sin(t\pi)
$$
It is obvious that $F(\cdot,0)=Id_{S^{2n}} $ and $F(\cdot,1): p\mapsto -p $, which are homotopical. But $deg(F(\cdot,1))=-1 $ and $deg(Id_{S^{2n}})=1$. Contradiction! 

