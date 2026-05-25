---
title : "Lie群与Lie代数"
weight : 1
description : "Lie，我从微分流形中杀出来了！"
date : "2026-05-25"
---

> ref Siqi Liu.

- [0 Preliminaries of differential manifolds](#0-preliminaries-of-differential-manifolds)
  - [0.0 符号约定](#00-符号约定)
  - [0.1 微分算子与微分微分表达式](#01-微分算子与微分微分表达式)
  - [0.2 映射与子流形](#02-映射与子流形)


### 0 Preliminaries of differential manifolds

可参见[微分几何杂谈]({{< ref "/Notes/微分流形杂谈.md" >}}).这里所补充的都是一些在微分几何中随口一提，但是在Lie群中非常重要的topics.

#### 0.0 符号约定
> 总之就是非常神秘

* 流形$M $上的全体光滑函数记作$C^\infty(M)=\mathcal{O}(M) $.若$f_1|_x=f_2|_x $，记$f_1\sim_x f_2 $构成一种等价关系，那么$\mathcal{O}(M)/\sim_x =\mathcal{O}_x(M)$称为x点的函数芽germ，由函数芽可以定义切空间。
* 流形$M $上的全体向量场记作$\mathfrak{X}(M) $，前面在微分几何中通常记作$\Gamma^\infty (M) $
* 

#### 0.1 微分算子与微分微分表达式

在微分几何中，总所周知的是，切向量就是一个特殊的一阶微分算子，特殊在没有0阶项。但其实际上要细分的话，切向量对应的是「微分表达式」(differential expression).具体来说，一个$r$-阶的微分表达式$D $ ，也就是一个线性映射，将一个光滑函数映射到$\R $：
$$
  \begin{align*}
    &D:\mathcal{O}_p(M)\rightarrow \R，\forall p\in M
    \\
    &D(f(x))=D(f(x_0)+\sum_i\frac{\partial f}{\partial x^i}|_{x=x_0}(x-x_0)^i+\dots+\mathcal{O}((x-x_0)^{r+1}))
  \end{align*}
$$
最高作用到$r$阶上.也就是对函数进行某种导数操作，由于最高求导只能求到$r$阶，所以$r+1 $阶及其之后的项在取$x=x_0 $的极限之后就都为$0 $了.

如对于$r=2 $的微分表达式，上式就是
$$
  =f(x_0)D(1)+\sum_i\frac{\partial f}{\partial x^i}|_{x=x_0}D((x-x_0)^i)\\+\frac{1}{2}\sum_{ij}\frac{\partial^2 f}{\partial x^i}|_{x=x_0}D((x-x_0)^i(x-x_0)^j)
$$
那么切向量就是满足 Leibniz律的一阶微分算子
$$
  X(f\cdot g)=X(f)\cdot g(x_0)+X(g)\cdot f(x_0)
$$
所以切向量中就没有了$D(1) $这样的项，否则不满足上式.

将定义中的$p $跑遍整个流形（也许并不一定整个流形，只要求一个区域，因为世界上总得有坏人🦹，也就是不完备的），那么就得到了一个微分算子，正如如此操作下切向量对应的就是一个向量场.

$p $处全体$r $阶微分表达式的全体记为$T_p^{(r)}(M) $，$T_p^{(\infty)}(M)=\cup_{r=0}^\infty T_p^{(r)}(M) $.

记 $\alpha=(a_1,\dots,a_m) $,$|\alpha|=a_1+\dots+a_m $,$\partial^\alpha =(\frac{\partial}{\partial x^1})^{a_1}\dots (\frac{\partial}{\partial x^1})^{a_m}$，于是$T_p^{(r)}(M) $的基就是
$$
  \{\partial^\alpha:|\alpha|\le r\}
$$
记开集$U $上全体微分算子为$D(U) $.

若存在这样一族向量场$X_1,\dots,X_m \in \mathfrak{X}(M)$使得对于任意的$p\in M $，$X_1(p),\dots,X_m(p) \in T_p(M)$组成$T_p(M) $的一组基，那么称流形$M $是可平行化的.由微分几何中的一些知识可知，偶数维的球面就不是可平行化的，因为其上不存在处处非零的向量场。而对于Lie群就总是可平行话的，因为群结构带来的左不变性总可以将一个点的切空间推广到整个Lie群上.

#### 0.2 映射与子流形

这里仍然只记录一些之前在微分几何中没有想太多的一些比较tricky的东西:

1. 考虑光滑映射$\varphi:M\rightarrow N $，有$\varphi^*:\mathcal{O}_y(N)\rightarrow \mathcal{O}_x(M) $.由线性代数，可知存在一个映射将$\mathcal{O}_x^*(M)\rightarrow \mathcal{O}_y^*(N) $.考虑到$\mathcal{O}^*_x(M) $ 中的元素作用到$\mathcal{O}_x(M) $中的元素上所得到的是一个实数，可知$\mathcal{O}^*_x(M)  $就是切空间，而上面所考虑的那个映射，即是$\varphi  $的外微分
$$
  (d\varphi)_x:\mathcal{O}_x^*(M)\rightarrow \mathcal{O}_y^*(N)
$$
而
$$
  (d\varphi)^\infty_x:\mathcal{O}_x^*(M)\rightarrow \mathcal{O}_y^*(N)
$$
就是除了$(d\varphi)_x $中的一阶还带上了更高阶的一些项.
___
___
___
___
___
___