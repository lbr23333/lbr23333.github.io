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

可参见[微分几何杂谈]({{< ref "/Notes/微分流形杂谈.md" >}}).这里所补充的都是一些在微分几何中随口一提，但是在Lie群中非常重要的topics.(好吧，其实一路写下来感觉有些可有可无.)

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

2. 另外还有一个常见的误区：
$$
  d\varphi(X)\in \mathfrak{X}(N),X\in \mathfrak{X}(M)
$$
但是这其实是可能有些问题的，主要出现在$\varphi $不单或不满的时候.

可以定义：若$X\in\mathfrak{X}(M),Y\in \mathfrak{X}(N) $使得对于任意的$p\in M $都有
$$
  (d\varphi)_p(X(p))=Y(\varphi(p))
$$
那么称x和y是$\varphi $-相关的.

同理可以定义 differential operator 的$\varphi $-相关性：
$$
  \varphi:M\rightarrow N
$$
$D $是$M$上的微分算子，$\tilde D $是$N $上的微分算子，即
$$
  D:C^\infty(M)\rightarrow C^\infty(M),\tilde{D}:C^\infty(N)\rightarrow C^\infty(N)
$$
称$D $和$\tilde{D} $是$\varphi $-相关的，若下图表交换
$$
  \begin{matrix}
    &C^\infty(M)&\xrightarrow{D}&C^\infty(M)
    \\&\uparrow\varphi^*& &\uparrow\varphi^*
    \\&C^\infty(N)&\xrightarrow{\tilde D}&C^\infty(N)
  \end{matrix}
$$

3. $M $的所有微分同胚所构成的群称为$M $的微分同胚群，记作$Diff(M) $.可以视为一种无穷维的Lie群，其Lie代数即是$Vect(M) $.
   
4. 对于浸入和淹没的概念，其实在拓扑流形中就存在。

   对于淹没$\varphi:M\rightarrow N ,m n$总可以找到局域坐标使得在某点处
   $$
     \tilde{\varphi}(x^1,\dots,x^m)=(x^1,\dots,x^n)
   $$
    其中$\tilde{\varphi} $是$\varphi_V\circ\varphi\circ\varphi_U^{-1} $

    对于浸入也同样有
    $$
      \tilde{\varphi}(x^1,\dots,x^m)=(x^1,\dots,x^m,\underbrace{0,\dots,0}_{n-m})
    $$
    这两个概念都没有用到光滑性,所以完全可以定义拓扑淹没和拓扑浸入,具体的就是对于拓扑流形使得$\tilde{\varphi} $是某种投影映射或者某种包含映射.

    若$M $是光滑流形,而$N $是拓扑流形,那么若$\varphi M \rightarrow N $是一个拓扑淹没,而且$\varphi $是满的,于是存在$N $上唯一的光滑结构使得$\varphi $是一个光滑的淹没.

    若满足“$\varphi M \rightarrow N $是一个拓扑淹没,而且$\varphi $是满的”,那么称$N $为$M $关于$\varphi $的商.

5. 不同书上对于嵌入的定义也不尽相同,这里进行一个统一:
   $\varphi M\rightarrow N $是一个浸入:
   * $\varphi $是单的,那么称$\varphi $是一个嵌入(embedding)
   * $\varphi $是同胚,那么称$\varphi $是一个正则嵌入(regular embedding)

    区别很明显,其实之前在微分几何中也提到过.对于嵌入来说,嵌入流形可以只赋予原像的拓扑,而没有像空间的子空间拓扑,那么就有可能出现一些没那么好的东西.而正则嵌入要求$\varphi $是一个同胚,即正则嵌入的子流形被赋予的像空间中的子拓扑结构和继承的原像空间中的拓扑一致,那么就避免了很多不好的情况.对此,下面两个例子是非常经典的:

    * $\R\rightarrow \R^2 $最后趋近于自相交:(待插图)
      就是一个嵌入,但不是一个正则嵌入,因为其在最后趋近相交的位置没有一个很好的子空间拓扑
    * [环面上的无理流](https://en.wikipedia.org/wiki/Linear_flow_on_the_torus)
      似乎在泛函分析中是可以证明,这样的流在$\R $上是密度均匀的,但是我没学过...

    还有一些后面会用到的定理:

    设$\varphi:M\rightarrow N $是一个正则嵌入:
    (a) 对于$y\in \varphi(M) $存在$y $的开领域$V $以及$V $上的一个光滑映射$F:V\rightarrow \R^{n-m} $使得$\varphi(M)\cap V=\{z\in V|F(z)=0 \} $
    (这实际上就是子流形的方程解的描述)
    (b)对于$x\in M,y=\varphi(x)\in \varphi(M) $,分别存在$x,y $的开领域$U,V $使得$\varphi(U)=\varphi(M)\cap V $
    (子流形的参数方程描述)
    (c)设$P $是一个光滑流形,$U:P\rightarrow M $是一个任意的映射,那么
    $U $是光滑的$\iff $ $\varphi\circ U: P\rightarrow N $是光滑的.(证明就利用正则嵌入在像空间有足够好的局域性质)
    
    反例:(待补充)

6. 子流形:
   $M $是一个光滑流形,$N\subset M$,若$i:N\rightarrow M $是一个嵌入,那么称$N $是$M $的子流形.若$i $还是正则的,那么称$N $是正则子流形.

   正则值定理(关于正则值,仍然可以参见 [微分几何]{{< ref "/Notes/微分流形杂谈.md" >}}):$M,N $ are smooth manifolds, $\varphi:M\rightarrow N $ is smooth. For $y\in N $, let $M'=\varphi^{-1}(y) $. If $\forall x
   \in M' , rank(d\varphi)_x=n $, then $M' $ is a regular submanifold of $M $ with $m-n $ dimensions. And such $y $ is the regular value of $N $.

    这个定理在微分几何中几乎被一笔带过,但其实是一个证明子流形的有力工具,下面给给出一些例子:
    * $Mat(n,\R)\simeq \R^{n^2} $
    * $GL(m,\R)$

___
___
___
___
___
___