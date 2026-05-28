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
- [1.Lie群与Lie代数](#1lie群与lie代数)


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
   $M $是一个光滑流形,$N\subset M$且$N $上有光滑结构,若$i:N\rightarrow M $是一个嵌入,那么称$N $是$M $的子流形.若$i $还是正则的,那么称$N $是正则子流形.

   正则值定理(关于正则值,仍然可以参见 [微分几何]({{< ref "/Notes/微分流形杂谈.md" >}})):$M,N $ are smooth manifolds, $\varphi:M\rightarrow N $ is smooth. For $y\in N $, let $M'=\varphi^{-1}(y) $. If $\forall x
   \in M' , rank(d\varphi)_x=n $, then $M' $ is a regular submanifold of $M $ with $m-n $ dimensions. And such $y $ is the regular value of $N $.

    这个定理在微分几何中几乎被一笔带过,但其实是一个证明子流形的有力工具,下面给给出一些李群的例子:
    * $Mat(n,\R)\simeq \R^{n^2} $:矩阵群,包罗万象,~~老霸道了~~.
    * $GL(m,\R)=\{M\in Mat(n,\R)|det(M)\ne 0 \} $是$Mat(n,\R) $的一个开子集,因为$det $是一个连续函数,0是$\R $中的闭集,所以$GL $就是开.
    * $SL(n,\R)=\{M\in Mat(n,\R)|det(M) = 1 \} $: 用上面的正则值定理,为了证明其是$Mat $的一个子流形,就是要证明$1 $是$Mat $的正则值,又即是证明$(d(det))_M:\R^{n^2}\rightarrow \R $是满的.这也是相对容易的,考虑行列式的Laplace展开,有$\frac{\partial}{\partial a_{ij}}(det M)=A_{ij} $.而$det(M)=1 $就要求至少有一个$A_{ij}\ne 0$,所以就可以构造任意符号要求的矩阵,使得$A_{ij} $可以取到$\R $,即$(d(det))_M:\R^{n^2}\rightarrow \R $是满🐍.从而说明$SL(n,\R) $是矩阵群的一个子流形.
    * $O(n,\R)=\{A\in Mat(n,\R)|A^TA=I_n \} $也是一个矩阵群的子流形,考虑:
  
      $SMat(n,\R)=\{M\in Mat(n,\R)|M ~ is ~ symmetric \}=\{M\in Mat(n,\R)|M=A^TA \} $以及映射
    $$
       \begin{align*}
        &P:Mat(n,\R)\simeq R^{n^2} \rightarrow SMat(n,\R)\simeq R^{n(n+1)/2}
        \\
        & P(A)= A^TA
      \end{align*}
    $$
    显然$O(n,\R)=P^{-1}(I_n) $,要证$O(n,\R) $是子流形,即证明$\forall A\in O(n,\R),(dP)_A:Mat(n,\R) \rightarrow SMat(n,\R)  $是满的.(注意对于线性Lie群,其切空间就是其本身.)

      考虑$P(A+\epsilon B)-P(A)=\epsilon (dP)_A(B)+O(\epsilon ) $,于是在上映射下即$(A^T+\epsilon B^T)(A+\epsilon B)-A^TA= \epsilon (B^TA+A^TB)+O(\epsilon ) $,于是就是要证明$(dP)_A(B)=B^TA+A^TB $是满的.也就是要证明,对于任意的$C\in SMat(n,\R) $,都有$C=B^TA+A^TB $.注意到,取$B=AC/2 $,即
    $$
      A^T(\frac{AC}{2})+\frac{1}{2}(C^TA^TA)=C
    $$
    即对于任意的$C $都可以找到一个$B $使得$A^TB+B^TA=C $,也就是说$dP_A $是满的,即对于任意的$A^TA=a $,$a $都是$P $的正则值,特别的,$1 $也是,即$O(n,\R) $是$Mat(n,\R)  $的一个子流形.

    * Symplectic Group:为了引入辛群,先考虑
    $$
      J=\begin{bmatrix}
        0 & -I_n\\ I_n & 0
      \end{bmatrix}
      \in Mat(n,\R) ~~~
      J^T=J,J^2=-I_{2n}
    $$
    考虑
    $$
      \varphi:Mat(n,\R) \rightarrow AMat(2n,\R)  ~~~ \varphi(A)=A^TJA
    $$ 
    其中类似于$SMat $定义了$SMat $即反对称矩阵集.辛群$S_p(n,\R)=\varphi^{-1}(J) $.完全可以同理于上说明辛群是$Mat(n,\R)  $的子流形:

      对于$A\in \varphi^{-1}(J) $,即$A^TJA=J $.考虑
        $$
        \begin{align*}
           (d\varphi)_A:Mat(2n,\R) \rightarrow AMat(2n,\R)
        \end{align*}
        $$
      同样有$\varphi(A+\epsilon B)-\varphi(A)=\epsilon (d\varphi)_A(B)+O(\epsilon ) $,即
        $$
          (A^T+\epsilon B^T)J(A+\epsilon B)-A^TJA=\epsilon (A^TJB+B^TJA)+O(\epsilon )
        $$
      即证$B\mapsto A^TJB+B^TJA $是满的.仍是解方程$C=A^TJB+B^TJA $,依旧是注意到有$B=-\frac{1}{2}AJC $.即得到$d\varphi$是满的.
      > 思考题: 对于任意辛群中元素A,$det(A)=1$.

7. Frobenius定理
   这是微分几何中的重点,但这里还是强调一下,因为在有了Lie代数,反过来要构造其所对应的一个Lie群就要用到该定理.

   先定义**分布**的概念:分布就是切丛的一个子空间.具体来说考虑$M $是$N $的子流形,对于$x\in M\subset N,T_xM\subset T_x(N)$,对$N $上每一个点$x $都指定一个$T_x(N) $的$m $维子空间$L_x $.$\mathcal{L}=L_x|x\in N $就是一个$m $维的分布.

   考虑$N $上一个坐标卡$V $,设其坐标为$(x^1,\dots,x^n) $,则$V $上的$C^\infty $向量场可用基表示为
   $$
     X=\sum_{i=1}^na^i(x)\frac{\partial}{\partial x^i},a^i\in C^\infty
   $$
   且总可以找到$L_x=Span\{X_1(x),\dots,X_m(x) \} $,其中$X_i(x)\in T_x(N) $.若$X_i\in \mathfrak{X}(N) $,就称$\mathcal{L} $是一个$C^\infty $的分布.(但注意上面的定义都是local的,光滑性依赖于所选择坐标卡)如$m=1,N=S^2n $上就没有处处非零的向量场,自然选不到一个全局都好的基,也就没有一个全局的光滑分布(也就是前面提到过的不可平行化).

   然后继续给出几个定义:
   * 对于$N $的子流形$M $,存在$N $上的一个分布$\mathcal{L} $,使得$L_x=T_x(M),\forall x\in M $,就称$M $是$N $关于$\mathcal{L} $的一个**积分子流形**.有时会将条件弱化成$T_x(M)\subset L_x $,但想表达的意思是差不多的.
   * 若对于$\forall x\in N,\exist  $过点$x $的$\mathcal{L} $的积分子流形,那么称$\mathcal{L} $是**可积的**.我们知道,对易操作对于切向量来说是封闭的,即$X,Y\in L_x=T_x(M) $.所以$\mathcal{L} $可积就意味着$[X,Y]\in T_x(M) $,更加形式化一点就是$[\mathcal{L},\mathcal{L}]\subset \mathcal{L} $
  
    于是,反过来.若$[\mathcal{L},\mathcal{L}]\subset \mathcal{L} $,则称$\mathcal{L} $是**对合的**.
    
    局部Frobenius定理所考虑的就是是否有
    $$
      \text{对合}\iff \text{可积}
    $$
    证明在微分几何中是常见的.进一步就是整体的 Frobenius定理:
      > N是光滑流形,$\mathcal{L} $是N上的m维的对合的分布,则过N上任意点p,都存在唯一的极大积分子流形$M_p $.$\mathcal{L} $的任何积分子流形都是N的拟正则子流形,并且是某个极大积分子流形的开子流形.

      证明要点:对于$p\in N $.直接构造出
      $$
        M_p=\{q\in N|\text{存在一条分片光滑的}\mathcal{L}\text{的积分曲线连接}p,q \}
      $$
      (ref,Warner,GTM94)

      以上就是微分流形的基础部分.
___

### 1.Lie群与Lie代数

先引入一个更一般的概念**拓扑群**:
> $X $是一个拓扑空间,若其有群结构,即
> 1. $\mu:X\times X\rightarrow X |(x,y)\mapsto xy |$连续
> 2. $i: X\rightarrow  X |x\mapsto x^{-1}  |$连续
> 3. 单位元$e\in X $
> 满足$(xy)z=x(yz),ex=xe=x,\forall x, \exist ! y $使得$yx=xy=e $
>
> 那么称$X $是一个拓扑群.

加上光滑结构就得到了**Lie群**:
> 若$G$ 是一个光滑流形,其上有光滑映射$\mu:G\times G \rightarrow G,i:G\rightarrow  G $以及$e\in G $,满足群的定义.则称$G $是一个Lie群.

实际上,由上可见其实在任意的一个范畴里都可以定义一个类似的结构.





___
___
___
___
___