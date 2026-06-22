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
  - [1.1 Lie群](#11-lie群)
  - [1.2Lie代数](#12lie代数)
    - [Lie代数的表示](#lie代数的表示)
  - [1.3 李群的李代数](#13-李群的李代数)
  - [1.4 包络代数](#14-包络代数)
  - [1.5 子群和子代数](#15-子群和子代数)
  - [1.6 局部同构群](#16-局部同构群)
  - [1.7 同态](#17-同态)
  - [1.8 Lie's 基本定理](#18-lies-基本定理)
  - [1.9 闭子群、齐性空间、轨道空间](#19-闭子群齐性空间轨道空间)
  - [1.10 指数映射](#110-指数映射)


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

{{% mathbox type="blue" title="Frobenius定理" %}}
$N$ 是光滑流形, $\mathcal{L} $ 是 $N$ 上的 $m$ 维的对合的分布,则过 $N$ 上任意点 $p$ ,都存在唯一的极大积分子流形 $M_p $ .$\mathcal{L} $的任何积分子流形都是 $N$ 的拟正则子流形,并且是某个极大积分子流形的开子流形.
{{% /mathbox %}}

证明要点:对于$p\in N $.直接构造出
$$
  M_p=\{q\in N|\text{存在一条分片光滑的}\mathcal{L}\text{的积分曲线连接}p,q \}
$$
(ref,Warner,GTM94)

以上就是微分流形的基础部分.
___

### 1.Lie群与Lie代数
#### 1.1 Lie群

先引入一个更一般的概念**拓扑群**:
{{% mathbox type="green" title="拓扑群" %}}
  $X $是一个拓扑空间,若其有群结构,即
 1. $\mu:X\times X\rightarrow X |(x,y)\mapsto xy |$连续
 2. $i: X\rightarrow  X |x\mapsto x^{-1}  |$连续
 3. 单位元$e\in X $
 满足$(xy)z=x(yz),ex=xe=x,\forall x, \exist ! y $使得$yx=xy=e $

 那么称$X $是一个拓扑群.
{{% /mathbox %}}


加上光滑结构就得到了**Lie群**:
{{% mathbox type="green" title="Lie群" %}}
若$G$ 是一个光滑流形,其上有光滑映射$\mu:G\times G \rightarrow G,i:G\rightarrow  G $以及$e\in G $,满足群的定义.则称$G $是一个Lie群.
{{% /mathbox %}}

*实际上,由上可见其实在任意的一个范畴里都可以定义一个类似的结构.*

对于Lie群而言,可以先*遗忘*其光滑结构,视为一个拓扑群,且该拓扑群是$A_2,T_2 $且局部欧的.于是自然就引出了Hilbert第五问题:
{{% mathbox type="purple" title="" %}}
是否所有的连续群都是可微群?如果不行,至少加上什么条件?

{{% /mathbox %}}
放在这里就是拓扑群至少在什么条件下,能变成一个Lie群?在1950s有一群人先给出了一个没那么强的形式:拓扑群+Locally Euclidean+T2 ==> Lie群.后来发展成

{{% mathbox type="blue" title="G-Yamabe" %}}
若$G$局部紧.则对于其单位元的任何开领域$U$,都存$G $的开子集$G' $以及一切包含于$U $的$G' $紧正规子群$K $,使得$G'/k $是Lie群.

$\iff$

局部紧群一定是Lie群的射影极限.
{{% /mathbox %}}

若$G $连通,则$G'=G $.

> 什么事射影极限,我也不懂


拓扑群有一个很强的结论:
{{% mathbox type="blue" title="拓扑群的开子群一定是闭的" %}}
{{% /mathbox %}}
证明:设$H $是$G $的一个开子群,那么由陪集分解$G=\bigcup_{x\in G}xH $.其中$xH=\varphi^{-1}(H) $,其中 $\varphi:y\mapsto x^{-1}y$ ,由Lie群的定义可知 $\varphi $是连续的,于是可知$xH $也是开的.那么对于 $H=G\setminus \bigcup_{x\ne e}xH $ ,由于其他的陪集 $xH $  都是开集且开集并为开,可知$H $是闭的.$\Box $

于是,对于连通的 $G $ ,其只有平庸的开子群,因为非空的开子群既开又闭,只能是 $G $ .

{{% mathbox type="green" title="Lie群同态" %}}
设$G_1,G_2 $是两个Lie群,若$\varphi:G_1\rightarrow G_2 $是群同态,且是光滑的.则称之为一个Lie群同态.
{{% /mathbox %}}
例子🌰: 

$G=(\R,+) $:$\varphi:G\rightarrow G $是群同态,即$\varphi(x+y)=\varphi(x)+\varphi(y) $.若$\varphi $是连续的,那么可知$\varphi(x)=cx $.


> 实际上,在一点处的联系、单调、可测,同样可以得到上结论,可见光滑的条件是过强的.

下面
{{% mathbox type="green" title="左平移与右平移" %}}
$l_a:G\rightarrow G,l_a(x)=ax $为左平移,$r_a:G\rightarrow G,r_a(x)=xa $为右平移. $a\in G $ 
{{% /mathbox %}}

这是群结构所带来的,由Lie群的定义可知,左平移与右平移都是光滑的,而且其逆也是光滑的.即左右平移都是微分同胚.实际上,两者的作用一致,在后面通常默认选择做平移处理问题.

> 因为左撇子更习惯?

{{% mathbox type="slate" title="" %}}
$i_a:G\rightarrow G,i_a(x)=axa^{-1} $是Lie群同态,因为
$$
  i_a(xy)=a(xy)a^{-1}= ax(a^{-1}a)ya^{-1}=i_a(x)i_a(y)
$$
{{% /mathbox %}}

{{% mathbox type="green" title="Lie子群" %}}
设$G,H $ 都是Lie群,若 $H\subset G$ 既是子流形,又是子群,那么称之为$M $的一个Lie子群.
{{% /mathbox %}}

但实际上, $H $ 为Lie群的条件是有点过强的.

> 有李子群,那有没有菠萝群

{{% mathbox type="blue" title="" %}}
设$G$是Lie群,$H $是$G $的子群(仅代数意义上的子群).
* 若$H $是拟正则嵌入子流形,那么$H $是Lie子群;
* 若$H $是正规嵌入子流形,那么$H $是闭的Lie子群.
{{% /mathbox %}}

证明:考虑$\nu:G\times G\rightarrow G ,\nu(x,y)\mapsto xy^{-1} $,那么由Lie群的定义,$\nu $是光滑的.若考虑
$$
  \tilde{\nu}=\nu|_{H\times H}:H\times H\rightarrow H\xhookrightarrow{j}G
$$

那么若$j $是拟正则嵌入,   $u:H\times H\rightarrow H $使得$\tilde{\nu}=j\circ u $,可知$u $是光滑的,所以$H $是一个Lie群.

进一步,若$j $是正则嵌入,可知是局部闭的,即$H $是$\bar{H} $中的开集,其中$\bar{H } $有子空间拓扑.$\bar{H} $是闭子群,$H $是$\bar{H} $中的开子群.再由前面的定理“拓扑群中的开子群都是闭子群”,可知$H $是$\bar{H} $中的闭子群,由于闭包是最小包含$H $的闭集,可知$H=\bar{H} $.$\Box$

> 正则子流形是局部闭的:对于正则子流形 $S(\dim S=i) $ ,考虑嵌入到的空间 $M(\dim M=m) $ 中的光滑结构,其中一个Chart为 $U $ ,那么 $S\cap U $ 在该Chart的坐标下就为 $x^{j+1}=\dots=x^m=0 $ ,那么根据投影映射的连续性,就有 
$$
  S\cap U =F^{-1}(0),F(p)=(x^{i+1}(p),\dots,x^n(p))
$$
所以 $S\cap U $ 是闭的.也就是说对于 $S $ 中任意一点,都有一个开邻域 $U $ 使得 $S\cap U $ 为闭集.满足局部闭的定义.

可见群结构使得光滑结构上的局部闭性质变成了整体闭.实际上,后面将会证明 Cartan闭子群定理:
$$
  \small{\text{闭子群}}\iff\small{\text{正则Lie子群}}
$$
可见 闭 在Lie群中是一个非常强的条件.

一些Lie群的例子:(感觉这个位置有点尴尬)
* $\R^n,\mathbb{C}^n $
* $\mathbb{C}^*=\{z\in \mathbb{C} | z\ne 0\} $
* $T^m=\{(z^1,\dots,z^m)\in \mathbb{C}^m:|z^i|=1 \}=(S^1)^m $
* $\Gamma $是$\mathbb{C}^m  $的$\mathbb{Z}^m $子模,有$T^m=\mathbb{C}^m/\Gamma $.($\Gamma $可以视为$\mathbb{C} $中的一种lattice,取其中一个晶胞并做粘合的操作也就是等价于上面所说的模去操作,这样在一个物理壬看来会更形象一点)
* 还有就是前面提到过的各种矩阵群
* $T^n(n,\R)=\{\begin{bmatrix}
  1 & &*
  \\ & \ddots &
  \\0& & 1
\end{bmatrix} \in Mat(n,\R) \} $,上三角矩阵:
考虑到上三角矩阵群的维数$\frac{1}{2}n(n+1) $,那么其一定可以用$GL(n,\R) $群的某些基前系数为0表示,即其在$GL $中就是一个正则嵌入子流形,所以进步一根据前面的定理可知,$T^n(n,\R) $是一个闭的Lie子群.

#### 1.2Lie代数
在习惯上,似乎有两种Lie代数:一种是物理壬喜欢的用Lie括号定义的Lie代数,另一种是数学壬定义的Lie群单位元的切空间.实际上是同一个东西,本节中先考虑前者.

记 $\mathbb{k} $ 为一个含幺交换环(一般来说可以就当成是一个域,比如 $\R,\mathbb{C} $ ).那么一个 $\mathbb{k} $ 代数就是 $(A,\mu) $ ,定义为
$$
  A:\mathbb{k}-module
  \\
  \mu :A\times A\rightarrow A
$$
对于 $(A_1,\mu_1),(A_2,\mu_2) $ , 若 $\varphi:A_1\rightarrow A_2 $ 是一个 $\mathbb{k} $ -同态,即
$$
  \varphi(\mu_1(x,y))=\mu_2(\varphi(x),\varphi(y))
$$
那么称 $\varphi $ 是一个 $\mathbb{k} $ -代数同态.

{{% mathbox type="green" title="Lie代数" %}}
对于一个 $\mathbb{k} $  -代数 $(A,[\cdot,\cdot]) $ :
$$
  [\cdot,\cdot] :A \times A\rightarrow A
  \\
  (x,y)\mapsto [x,y]
$$
若满足
1.  $[x,x]=0,\forall x\in A $ 
2.  Jacobi恒等式
$$
  [[x,y],z]+[[y,z],x]+[[z,x],y]=0
$$
则称 $(A,[\cdot,\cdot]) $ 是 $\mathbb{k} $ 上的Lie代数.常用 $\mathfrak{g} $ 来表示Lie代数.
{{% /mathbox %}}

注意: 上面条件1有些情况下可以换成 1'条件:
$$
  [x,y]=-[y,x]
$$
有很多书上也都是这么定义的.乍一看:
1. 取 $[x+y,x+y] $ 并利用双线性就能从 1 $\rightarrow  $ 1'
2. 考虑 $[x,x]=-[x,x] $ ,也即是 $2[x,x]=0 $ 似乎能得到 1' $\rightarrow  $ 1.但是 $\mathbb{k} $ 只是一个含幺交换群, $2 $ 在其中不一定有逆,所以就会出问题.比如 $\mathbb{k}=\mathbb{Z}_2 $ ,在 1' 条件下就会变成诡异的
$$
  [x,y]=[y,x]
$$

前面的 $\mathbb{k} $ 代数同态具体到Lie代数就是,在 $(\mathfrak{g}_1,[,]_1) $ 与 $(\mathfrak{g}_2,[,]_2) $ 之间有
$$
  \varphi:\mathfrak{g}_1\rightarrow \mathfrak{g}_2,\varphi([x,y]_1)=[\varphi(x),\varphi(y)]_2
$$

设 $\mathfrak{g} $ 中有一组基为 $x_1,\dots,x_n $ ,那么
$$
  [x_i,x_j]=\sum_{k=1}^n C^k_{ij}x_k
$$
称 $C^k_{ij} $ 为 $(\mathfrak{g},[,]) $ 关于基 $\Set{x_1,\dots,x_n} $ 的结构常数.
1. 根据 $[x_i,x_i]=0 $ 可知 $C^k_{ij}+C^k_{ji}=0 \Rightarrow C^k_{ii}=0 $ .
2. 根据Jacobi恒等式,有
$$
  \sum^n_{l=1}(CC+CC+CC)=0
$$

Q:给定 $C^k_{ij} $ 能否找到所有的Lie代数结构? 设 $\mathbb{k}=\mathbb{C} $ , $V $ 是一个 $n $ 维的 $\mathbb{C} $ 空间,那么就是在问 $V $ 上有多少Lie括号?

取一组基 $\Set{x_1,\dots,x_n} $ ,考虑可能的 $\Set{C^k_{ij}|i,j,k=1,\dots,n} $ .那么
$$
  A_n=\Set{C^k_{ij}\in\mathbb{C}^{n^3}|C^k_{ij}+C^k_{ji}=0,\sum(CC+CC+CC)=0}
$$
就是一些二次曲面和一些平面交得的代数簇. $A_n $ 上每一点都是一个Lie代数结构.

还可以对已有的 $\mathbb{k} $ -Lie代数换成另一个 $\mathbb{K} $ Lie代数,其中 $\mathbb{K} $ 是交换、结合的 $\mathbb{k} $ -代数.对于 $\mathbb{k} $ 上的Lie代数 $\mathfrak{g} $ ,有
$$
  \mathfrak{g}_{\mathbb{K}}=\mathbb{K}\otimes_{\mathbb{k}}\mathfrak{g}
$$
$\otimes_{\mathbb{k}} $ 意味着多重 $\mathbb{k} $ 线性.即对于 $\mathfrak{g}_{\mathbb{K}} $ 中的 $\sum^m_i x_i\otimes_{\mathbb{k}}a_i $ , $\mathbb{k} $ 中的元素乘到 $x_i $ 或 $a_i $ 上都是可以"提出来"的.对于
$$
  [x\otimes a,y\otimes b]_{\mathfrak{g}_{\mathbb{K}}}=(xy)\otimes[a,b]_{\mathfrak{g}}
$$
可验证$[,]_{\mathfrak{g}_{\mathbb{K}}} $:
1.  反称
2.  满足 Jacobi 恒等式

另外,显然 $(\mathfrak{g},[,]_{\mathfrak{g}_{\mathbb{K}}}) $ 是 $\mathbb{K} $ 代数.所以 ${\mathfrak{g}_{\mathbb{K}}} $ 是一个 $\mathbb{K} $ 上的Lie代数.

例:
1. $\mathfrak{g}=\R,\mathbb{K}=\mathbb{C} $, $\mathfrak{g}_{\mathbb{C}} $ 称为 $\mathfrak{g}_\R  $ 的复化.

{{% mathbox type="green" title="Lie子代数与理想" %}}
设 $\mathfrak{g} $ 是一个 $\mathbb{k} $ -代数,对于 $\mathfrak{g} $ 的两个子集 $a,b $ ,
$$
  [a,b]=Span\Set{(x,y)|x\in a,y\in b}=\Set{\sum^n_{i=1}(x_i,y_i)|x_i\in a,y_i\in b}
$$

1. 若 $\mathfrak{h} $ 是 $\mathfrak{g} $ 的 $\mathbb{k} $ -子模,满足 $[\mathfrak h,\mathfrak h]\subseteq \mathfrak h $ ,则称 $\mathfrak h $ 是一个Lie子代数.
2. 设 $\mathfrak{h} $ 是一个Lie子代数,若 $[\mathfrak{h},\mathfrak{g}]\subset \mathfrak{h} $ ,则称 $\mathfrak{h} $ 为 $\mathfrak{g} $ 的一个理想.
{{% /mathbox %}}

{{% mathbox type="blue" title="Lemma." %}}
1. 设 $\varphi:g_1\rightarrow g_2 $ 是Lie代数同态,那么 $Im(\varphi) $ 是 $g_2 $ 的子代数, $Ker(\varphi) $ 是 $g_1 $ 的子理想.
2. 设 $h $ 是 $g $ 的理想记 $q=g/h $ ,有
$$
  [x+h,y+h]_g:=[x,y]_g+h
$$
则 $q $ 是一个Lie子代数, $g\rightarrow q $ 的投影是Lie代数同态.
{{% /mathbox %}}

这都是抽象代数中的结论.证明略.

设 $g_1,\dots,g_m $ 是一些李代数.有
$$
g=g_1\times \dots \times g_m
\\
g=g_1\oplus \dots \oplus g_m
$$
前者是笛卡尔积,后者是作为 $\mathbb{k} $ - module.但实际上是差不多的.对于直和
$$
  x=(x_1,\dots,x_m)=x_1\oplus\dots\oplus x_m
  \\
  [x,y]_g:=[x_1\oplus\dots\oplus x_m,y_1\oplus \dots\oplus y_m]=\bigoplus_{i=1}^n[x_i,y_i]
$$
对于不同Lie代数 $g_i $ 中的元素 $x_i $ ,其之间是不想干的.即 $[x_i,x_j]=0,i\ne j $ ,于是
$$
  [g_i,g_j]_g=0
$$
称
$$
  g=\bigoplus_{i=1}^m g_i
$$
为 $g_1,\dots,g_m $ 的直和.(在老瓦的书上是用笛卡尔积处理的,结果是一致的,因为有限维的直和笛卡尔积本来就是一样的.)

后面可能会遇到 $g=b\oplus n $ ,但是 $[b,n]\ne 0 $ 的情况,也就是说只是作为 $\mathbb{k} $ -module的直和分解,而不是作为Lie代数的分解.

一些例子:
1. $(V,[,])$, $[,]=0 $ 是 $V $ 上的 Abelian 李代数.
2. $\mathfrak{gl}(V)=End(V) $ , $[X,Y]=XY-YX $ ,实际上 $\mathfrak{gl}(n,\mathbb{k})=Mat(n,\mathbb{k}) $.
3.  $\mathfrak{sl}(n,\mathbb{k})=\Set{A\in \mathfrak{gl}(n,\mathbb{k})|tr(A)=0} $
4.  $\mathfrak{o}(n,\mathbb{k})=\Set{A\in \mathfrak{gl}(n,\mathbb{k})|A^T+A=0} $
5.  $\mathfrak{s_p}(2n,\mathbb{k})=\Set{A\in Mat(2n,\mathbb{k})|A^TJ+JA=0} $, $J=\begin{bmatrix}
  0 &-I_n\\I_n &0
\end{bmatrix} $ 
6. $\mathfrak{u}(n)=\Set{A\in Mat(n,\mathbb{C})|A^\dagger+A=0} $,其中 $A^\dagger $ 并不是 $\mathbb{C} $ 线性的,所以只是 $\R $ 代数.
7. 在微分流形中,已经知道了 $\mathfrak{X}(M) $ 是一个Lie代数,因为 $[X,Y]\in \mathfrak{X},\forall X,Y\in \mathfrak{X} $ .但更具体地来说, $\mathfrak{X}(M) $ 只是 $\R $ 上的Lie代数,作为 $C^\infty(M) $-module, $\mathfrak{X}(M) $ 并不是 $C^\infty(M) $ 上的Lie代数,因为 $[,] $ 并不是 $C^\infty(M) $  线性的.
8.  $A $ 是一个 $\R $ 代数, $\mu: A\times A\rightarrow A $ , $(a,b)\mapsto ab $ .导子:  $D:A\rightarrow A $ ( $\mathbb{k} $ module同态)
$$
  D(ab)=D(a)b+aD(b)
$$
Fact: $D_1,D_2 $ 是导子,则 $[D_1,D_2]=D_1D_2-D_2D_1 $ 也是导子.
$$
  Der(A)=\Set{D:A\rightarrow A|D\small{\text{是导子}}}  \subseteq End_{\mathbb{k}}(A)
$$
若 $\mathfrak{g} $ 是一个Lie代数,则 $Der(\mathfrak{g}) $ 也是.例如,
$$
  ad:\mathfrak{g}\rightarrow Der(\mathfrak{g}),X\mapsto ad_X
  \\
  ad_X:\mathfrak{g}\rightarrow \mathfrak{g},Y\mapsto [X,Y]
$$
$ad_X $ 是一个导子,因为
$$
  ad_X([Y,Z])=[ad_X(Y),Z]+[Y,ad_X(Z)]
$$
展开后就是Lie代数所满足的 Jacobi恒等式,即 Jacobi恒等式实际上是导子的 Leibniz律.



> 实际上,在下一节中会证明,上面的(2)--(6)就是前面提到过的几个矩阵群的Lie代数,将会看到,即便是最简单的 $GL(n,\R) $ 也没那么容易证明其Lie代数就是 $\mathfrak{gl}(n,\R) $ .
##### Lie代数的表示
就和一般的表示一样,为了方便研究,选择将其放在某些具有线性结构的对象中处理.在Lie代数中,这个线性的对象就是前面所提到的 $\mathfrak{gl} $ .

设 $\mathfrak{g} $ 是一个 $\mathbb{k} $ -Lie代数, $V $ 是一个 $\mathbb{k} $ 模, $\mathfrak{gl}(V) $ 是一个 $\mathbb{k} $ Lie代数.若有一个Lie代数同态
$$
  \varphi:\mathfrak{g} \rightarrow \mathfrak{gl}(V)
$$
则 $V $ 是一个 $\mathfrak{g}  $ 模, $(V,\varphi) $ 是一个 $\mathfrak{g}  $ 的表示.
> 实际上,在大多数情况下,用到的都是 $\mathbb{k} =\R,\mathbb{C} $ .该情况下, $V $ 就是一个(复)线性空间.于是一个表示就是将 $\mathfrak{g}  $ 中的元素同态为该线性空间中的线性变换 $\mathfrak{gl}(V)\subseteq  End(V) $ .

1.  $dim V=1 $ , $\varphi =0 $ 是平凡表示.
2.  $ad: \mathfrak{g} \rightarrow Der(\mathfrak{g} )\subseteq \mathfrak{gl}(\mathfrak{g} )  $ 是伴随表示.



#### 1.3 李群的李代数









#### 1.4 包络代数









#### 1.5 子群和子代数
























#### 1.6 局部同构群
>关于前面覆叠空间的部分,可参考[拓扑学笔记]({{< ref "Notes/Topology.md" >}})

对于一般的拓扑空间,其具有万有覆叠空间的充要条件是,该空间道路连通、局部道路连通且半局部单连通.由于默认考察的对象都是连通的流形,再考虑到流形具有局部欧的性质,所以这些条件都是自动满足的.也即是说:
{{% mathbox type="blue" title="Lemma 1 光滑流形覆叠空间的存在性" %}}
若 $M $ 是一个光滑流形,那么存在 $M $ 的万有覆叠空间 $\tilde{M} $ ,且 $\tilde{M} $ 上有唯一的微分结构,使得 $\pi:\tilde{M}\rightarrow M $ 是一个光滑映射.
{{% /mathbox %}}

{{% mathbox type="blue" title="Lemma 2 提升引理" %}}
设 $\varphi:(X,x_0)\rightarrow (Y,y_0) $ 是一个覆叠映射, $(Z,z_0) $ 是一道路连通、局部道路连通且半局部单连通的空间.那么若 $\alpha:(Z,z_0)\rightarrow (Y,y_0) $ 满足 $\alpha_*(\pi_1(Z,z_0))\subset \varphi_*(\pi_1(X,x_0)) $ ,那么存在唯一的提升映射 $\tilde{\alpha}:(Z,z_0)\rightarrow (X,x_0) $ 使得 $\varphi\circ \tilde{\alpha}=\alpha $ .
{{% /mathbox %}}
后面所考虑的情况中, $X,Z $ 一般都是单连通的,也就是说上面的提升映射总是存在的.

{{% mathbox type="blue" title="" %}}
$G $ 是连通的Lie群, $\tilde{G} $ 是其万有覆叠空间, $\pi:\tilde{G}\rightarrow G $ 是其覆叠映射,那么对于任意的 $\tilde{e}=\pi^{-1}(e) $ ,存在 $\tilde{G} $ 上的唯一以 $\tilde{e} $ 为单位元的Lie群结构,且 $\pi $ 仍是群同态.
{{% /mathbox %}}
证明: 关键在于定义群乘法和逆.再次用到一个经典的trick,即乘法和逆直接用除法来定义.考虑
$$
  \alpha:\tilde{G}\times \tilde{G}\rightarrow G,(\tilde{x},\tilde{y})\mapsto \pi(\tilde{x})\cdot\pi(\tilde{y})^{-1}
$$
👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷

于是之后可以用覆叠空间的分类去对Lie群进行分类.

一些例子
$\pi:\R^n\rightarrow \mathbb{T}^n $.显然就是 $\R\rightarrow \R/\mathbb{Z}=\mathbb{T} $  ,即  $\pi_1(\mathbb{T}^n)=\mathbb{Z}^n $ .

\{{% mathbox type="slate" title=" $SU(2)$与 $SO(3)$ " %}}
$$
  \tilde{G}=SU(2)=\small{\set{A=\begin{bmatrix}a &b \\ c& d
\end{bmatrix}\in Mat(2,\mathbb{C})|A^\dagger A=I ,det(A)=1}}
$$
  即 $\begin{bmatrix}\bar a &\bar c \\ \bar b& \bar d
    \end{bmatrix} \begin{bmatrix}a &b \\ c& d
    \end{bmatrix}=\begin{bmatrix}1 &0 \\ 0& 1
    \end{bmatrix}$ , $ad-bc=1 $ 
    可知即
    $$
      c=-\bar{b},d=\bar{a},|a|^2+|b|^2=1
    $$
    即 $A=\begin{bmatrix}a &b \\ -\bar b& \bar a
    \end{bmatrix} ,|a|^2+|b|^2=1$ .令 $a=x+iy,b=z+iw $ 那么就是 $x^2+y^2+z^2+w^2=1 $ .也就是说,作为流形, $SU(2)\cong S^3 $ .进一步就可知 $\pi_1(SU(2))=0 $ .

再考虑
    $$
      \mathbb{H}_2=\Set{b=\begin{bmatrix}
        x &y\\z &w
      \end{bmatrix}\in Mat(2,\mathbb{C})|B^\dagger =B}
    $$
有 $\tilde{G}=SU(2) $ 作为其万有覆叠, $\varphi:\tilde{G}\times \mathbb{H}_2\rightarrow \mathbb{H}_2 $,具体地
    $$
      (A,B)\mapsto ABA^{-1}=\varphi_A(B)
    $$
注意其中 $A\in SU(2) $  ,所以有
    $$
      tr(\varphi_A(B))=tr(B)\\
      det(\varphi_A(B))=det(B)
    $$
取 $V=\Set{B\in \mathbb{H}_2|tr(B)=0} $ ,可得
    $$
      B=\begin{bmatrix}
        x_3 & x_1+ix_2 \\ x_1-ix_2 & -x_3
      \end{bmatrix}=x_1\sigma_1+x_2\sigma_2+x_3\sigma_3,x_i\in \R
    $$
其中 $\sigma_i $ 是Pauli矩阵.所以 $\varphi|_V:\tilde{G}\times V\rightarrow V $ 也保 $det ,tr $ .特别地, 
    $$
      det(B)=-(x_1^2+x_2^2+x_3^2),det(\varphi_A(B))=det(B)
    $$
可见 $\varphi_A:V\cong \R^3\rightarrow V\cong \R^3 $ 是保度规的,也就是说 $\varphi_A\in O(3) $ ,由于 $\tilde{G} $ 连通,而 $\varphi $ 是连续映射,所以实际上只会映射到含有单位元的连通分支
    $$
      \varphi : \tilde{G}\rightarrow SO(3)
    $$
下再说明 $\varphi $ 是满的,实际上直接计算可得
    $$
      \varphi\begin{bmatrix}
        a &b\\-\bar b&\bar a
      \end{bmatrix}=
      \begin{bmatrix}
        Re(a^2-b^2) & -Im(a^2+b^2) & -2Re(ab)
        \\
        Im(a^2-b^2) & Re(a^2+b^2) & -2Im(ab)
        \\
        2Re(\bar a b) & 2Im(\bar a b) & |a|^2-|b|^2
      \end{bmatrix}
    $$
由欧拉角,只需要证明绕任意轴的旋转可以由上得到,就证明了任意的转动能由上得到.取适当的 $a,b $ 即可证明.

综上, $SU(2) $ 是 $SO(3) $ 的万有覆叠空间.实际上,考虑到 $SO(3)\cong \mathbb{RP}^3 $ ,可知 $SU(2) $ 是其二重覆叠.
{{% /mathbox %}}

Q: 是否所有的Lie群都是矩阵群?

A: 不是,可以用万有覆叠进行证明.
👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷



#### 1.7 同态
考虑到对于群同态 $\varphi:G_1\rightarrow G_2 $ ,有结论
1.  $\varphi(G_1) $ 是 $G_2 $ 的子群.
2.  $Ker(\varphi) $ 是 $G_1 $ 的正规子群.

自然会问,对于一个Lie群同态:
$$
  \Phi:G_1\rightarrow G_2
$$
是否有
1.  $\Phi(G_1) $ 是否为 $G_2 $ 的Lie子群?
2.  $Ker(\Phi) $ 是否为 $G_1 $ 的正规子群?

另外, $\Phi $ 诱导出的 $\varphi:\mathfrak{g}_1\rightarrow \mathfrak{g}_2  $ ,同样会有两个问题:
1. $\varphi(\mathfrak{g}_1 ) $ 是 $\mathfrak{g}_2  $ 的Lie子代数吗?
2. $Ker(\varphi) $ 是 $\mathfrak{g}_1  $ 的理想吗?

由于 $\mathfrak{g}  $ 是线性空间,所以上面两条是显然成立的.








#### 1.8 Lie's 基本定理









#### 1.9 闭子群、齐性空间、轨道空间









#### 1.10 指数映射

设 $G $ 是一个Lie群, $\mathfrak{g}  $ 是 $G $ 的Lie代数.对于实数加法群 $\R $ ,其Lie代数也是 $\R $ , Lie括号为 $[,]=0 $ .若
$$
  \Phi:\R\rightarrow G
$$
是李群同态,则 $\varphi=d\Phi:\R\rightarrow \mathfrak{g}  $ 是一个Lie代数同态.

反之,若 $\varphi:\R\rightarrow G $ 是一个Lie代数同态(注意到其中 $\R $ 的运算 $[,]=0 $ 是平凡的,所以同态总是成立),又注意到 $\R $ 是单连通的,所以有Lie群同态 $\Phi:\R\rightarrow G $ 使得 $d\Phi=\varphi $ .具体地
$$
  \varphi:\R\rightarrow \mathfrak{g} ,t\mapsto \varphi(t)
$$
记 $X=\varphi(1) $ ,则 $\varphi(x)=t\cdot X $ ,因为 $\varphi $ 是一个线性映射.即完全由 $X $ 这一元素决定.对于 $X\in \mathfrak{g}  $ 记 $\varphi_X(t)=tX $ . $\Phi_X(t) $ 就是 $\varphi_X $ 所对应的Lie群同态.

{{% mathbox type="blue" title="Lemma" %}}
 $\Phi_{sX}(t)=\Phi_X(st) $ 
{{% /mathbox %}}
证明:  $t=0,\Phi_{\dots}(0)=e,\forall \dots $ 成立,因为 $\Phi $ 是同态.在 $e $ 附近取一Chart $U $ , 坐标为 $u=(u^1,\dots,u^n) $ 且 $u^i(e)=0 $ . 对于 $X\in \mathfrak{g}  $ , $X $ 在 $U $ 上就是
$$
  X=\sum^n_{i=1}X^i(u)\frac{\partial}{\partial u^i}
$$
设 $\Phi_X(t)=(u^1(t),\dots,u^n(t)) $ (就是 $X $ 的单参数微分同胚群),因为
$$
  \frac{d}{dt}\Phi_X(t)=X^i(u(t))
$$
所以
$$
  \begin{cases}
    \frac{d u^i}{dt}=X^i(u(t))
    \\
    u^i(0)=0
  \end{cases}
$$ 
对于 $\Phi_X(st)=(u^1(st),\dots,u^n(st)) $ ,有
$$
  \frac{du^i(st)}{dt}=s X^i(u(st))
$$
对于 $\Phi_{sX}(t)=(\tilde{u}^1(t),\dots,\tilde{u}^n(t)) $ 有
$$
  \frac{d\tilde u^i(t)}{dt}=s X^i(\tilde u(t))
$$
有同样的ODE与初始条件,由ODE解的唯一性可知两者相等.对于超出了 $U $ 的部分,总是有
$$
  \Phi_{sX}(t)=(\Phi_{sX}(t/n))^n,\Phi_{X}(st)=(\Phi_{X}(st/n))^n
$$
收缩回 $U $ 中.于是完成证明.

注意这里有一个比较 subtle 的地方,可能会问:为什么不是
$$
  d\Phi_X=\varphi_X=tX
$$
而是
$$
  \frac{d}{dt}\Phi_X(t)=X^i(u(t))
$$
注意 $\R $ 的双重身份:
1. $\Phi_X(t) $ 一方面是 $X $ 的流.由定义,
$$
  d\Phi_X(t)/dt=X_{\Phi_X(t)}=X(u^i(t))
$$
2. 另一方面是Lie群同态.考虑其微分
$$
  \varphi_X=d\Phi_X:\R\rightarrow \mathfrak{g} , c\frac{d}{dt}\mapsto cX=\varphi(c)
$$
其中 $\R $ 是Lie代数,其中元素为 $c d/dt $ , $d(\Phi_X)_0(c\frac{d}{dt})=cX $ , 所以 $(d\Phi_X)_0(\frac{d}{dt})=X $.与上一致.实际上是 $\R $ 的切空间是其本身所带来的一些小问题.

{{% mathbox type="green" title="指数映射" %}}
指数映射是指
$$
  \exp:\mathfrak{g} \rightarrow G,X\mapsto exp(X)=\Phi_X(1) ,1\in \R
$$
{{% /mathbox %}}

有一些比较显然的性质:
1.  $exp(0)=e,0\in \mathfrak{g} ,e\in G $ .
2.  $exp((t+s)X)=exp(tX)\cdot exp(sX) $ since
$$
  L.H.S=\Phi_X(t+s)=\Phi_X(t)\cdot\Phi_X(s)=R.H.S
$$
3. $exp(-X)=(exp(X))^{-1} $ .

在前面得到 $\Phi:\R\rightarrow G $ 对应的 $\varphi(t)=d\Phi(t)=tX $ .也得到了
$$
  X=(d\Phi_X)_0(\frac{d}{dt})
$$
称为 $\Phi $ 的无穷小生成元.更具体地:
$$
  t\mapsto exp(tX)=\Phi_X(t)
$$
是过 $e $ 的 $X $ 的积分曲线.那么过 $g\in G $ 的 $X $ 的积分曲线就是
$$
  t\mapsto g\cdot exp(tX)
$$
设 $f $ 是 $g $ 附近定义的一个函数,有
$$
  X(g)(f)=df_g(X_g)=(\frac{d}{dt}|_{t=0}f)(X_g)=\frac{d}{dt}|_{t=0}(f(g\cdot \exp(tX)))
$$
该式子在研究微分方程的单参数变换群时经常用到.

{{% mathbox type="blue" title="指数映射的局部微分同胚" %}}
若 $\exp:\mathfrak{g}\rightarrow G  $ 是光滑的,且存在 $0\in \mathfrak{g} $ 的开邻域 $U $  和 $e\in G $ 的开邻域 $V $ 使得
$$
  \exp:U\rightarrow V
$$
是微分同胚.
{{% /mathbox %}}
显然,对于Lie群单位元所在的连通区域 $G^\circ $ ,可以利用左平移在任意点上找到这样的微分同胚.

证明: 在 $e $ 附近取Chart $U $ ,有坐标系为 $(u^1,\dots,u^n) $ ,设 $X_1,\dots,X_n $ 为 $\mathfrak{g}  $ 的一组基.且 $(X_i)(e)=\frac{\partial}{\partial u^i} $ ,设
$$
  X_i=\sum^n_{j=1}F^j_i(n)\frac{\partial}{\partial u^j},i=1,\dots,n
$$
对于 $X\in \mathfrak{g}  $ , $X=x_1X_1+\dots+x_nX_n $ .设
$$
  \Phi_X(t)=(u^1(t),\dots,u^n(t))
$$
那么
$$
  \frac{du^i}{dt}=X^i(u(t))=x_1F^i_1+\dots+x_nF^i_n,i=1,\dots,n
$$
解记为 $u^i(t;x_1,\dots,x_n) $ ,那么
$$
  \exp(X)=\Phi_X(1)=(u^1(1;x_1,\dots,x_n),\dots,u^n(1;x_1,\dots,x_n))
$$
由 ODE 定理: $\exp(X) $ 是光滑的.总可以取到 $e $ 处足够小的 $V $ 使得 $\exp $ 是可逆的,于是就是局部的微分同胚.











___
___
___
___
___