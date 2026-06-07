---
title : "Brief introduction on Topology"
description : "ref wang"
weight : 1
date : 2026-06-07
---
- [3. 连通性与基本群](#3-连通性与基本群)
  - [3.1 连通性](#31-连通性)
  - [3.2 道路连通](#32-道路连通)
    - [范畴间的函子](#范畴间的函子)
  - [3.3同伦](#33同伦)




### 3. 连通性与基本群

#### 3.1 连通性

#### 3.2 道路连通

道路连通略强于连通,但由于其几何直观,在后面将看到其在几何中的一些用途.
> 数学中很多事情都是这样,对于一个非常 general 的概念可能并没有那么好用,但是加上一定限制或者说更多的一些要求后,就变得very nice.但是我也没有说连通性本身是一个很坏的性质咯,只是对于物理壬而言似乎一般都是默认处理道路连通的问题,因为后面将会看到,在流形上,道路连通 $\iff $ 连通.对于道路连通而言,最重要的是,我们可以对其进行代数计算,从而利用代数去研究拓扑,这就是代数拓扑的基本思想.

首先给出道路的定义
{{% mathbox type="green" title="道路" %}}
 设$X $ 是一拓扑空间, $x_0,x_1\in X $ .那么如果连续映射 $\gamma:[0,1]\rightarrow X $ 满足条件  $\gamma(0)=x_0,\gamma(1)=x_1 $ ,那么就称 $\gamma $ 是一条从 $x_0 $ 到 $x_1 $ 的道路(path).如果 $x_0=x_1 $ ,那么称之为圈(loop).
{{% /mathbox %}}

于是得到了道路空间和圈空间
$$
  \begin{align*}
    &\Omega(X;x_0,x_1)=\left\{ \gamma\in \mathcal{C}([0,1],X)|\gamma(0)=x_0,\gamma(1)=x_1   \right\} 
    \\
    &\Omega(X;x_0)=\left\{ \gamma\in \mathcal{C}([0,1],X)|\gamma(0)=\gamma(1)=x_0 \right\} 
  \end{align*}
$$
还有一个特殊的道路 $\gamma_x:\gamma_x(t)=x,\forall t\in [0,1] $ ,即是一个常值映射,称之为常值道路.


如果急不可待地去想做一些代数的操作,
{{% mathbox type="green" title="道路的逆与道路的积" %}}
1. 逆: $\bar{\gamma}(t):=\gamma(1-t) $ 
2. 积:  $\gamma_1*\gamma_2(t)=\begin{cases}
  \gamma_1(2t),&0\le t\le \frac12
  \\
  \gamma_2(2t-1),&\frac 12 \le t\le 1
\end{cases} $ 
{{% /mathbox %}}

将发现这些其实是非常不代数的,因为道路是一个映射,其定义除了依赖于象空间中的曲线,还依赖于具体的映射,对某条道路做重参数化就可能会使得其不同于前.另外 $\bar{\gamma}*\gamma\ne \gamma*\bar{\gamma} $ 也是由于这个原因,可见最基本的代数性质都无法满足.这是因为要求太严了,但这里先按下不表,先对前面定义的道路连通做一些讨论.

{{% mathbox type="green" title="道路连通性" %}}
若拓扑空间 $X $ 中任意两点都能用一条道路连接,就称 $X $ 为道路连通的.
{{% /mathbox %}}
显然,道路连通 $\Rightarrow $ 连通.反证:假设不连通的 $X=A\cup B,A\cap B=\emptyset $ 是道路连通的,取 $x\in A,y\in B $ 以及一条 $x $ 到 $
y $ 的道路 $\gamma $ ,那么
$$
  [0,1]=\gamma^{-1}(A)\cup \gamma^{-1}(B)
$$
是非空的不交开集的并,这与 $[0,1] $ 的连通性相矛盾.

反之,可以找到“拓扑学家的sine曲线”作为反例:
$$
  X=\left\{ (x,\sin\frac{\pi}{x})|0\le x\le 1 \right\} \cup \left\{ (0,y)|-1\le y\le 1 \right\} 
$$
是连通的,但不是道路连通的.
> 其连通性可利用结论:若 $A $ 连通,那么 $\bar A $ 连通立马得到.

再考虑其不是道路连通:反证,假设道路连通,存在道路 
$$
  \gamma(t)=(\gamma_1(t),\gamma_2(t)) ,\gamma(0)=(0,0),\gamma(1)=(1,0)
$$
令 $s=\sup \left\{ t|\gamma_1(t)=0 \right\}  $ ,也就是“刚要离开y轴的点”.那么一定有 
$$
  s<1,\gamma_1(s)=0 
$$
且
$$
  \gamma_1(t)>0,\forall t>s
$$
于是
$$
  \gamma_2(t)=\sin \frac{\pi}{\gamma_1(t)} ,\forall t>s
$$
所以存在递减的序列 $t_n\rightarrow s $ 使得 $\gamma_1(t_n)=\frac{2}{2n+1} $,于是
$$
  \gamma_2(t_n)=(-1)^n
$$
并没有趋近于 $\gamma_2(s) $ ,矛盾!

> 这实际上还告诉我们,不同于“连通子集的闭包是连通的”,道路连通子集的闭包不一定是道路连通的.这反应了 连通性 是一种拓扑性质,而 道路连通 更接近于一种几何性质.

但是也有很多好的情况,例如对欧氏空间的“星形”子集,就是一个连通且道路连通的.实际上
{{% mathbox type="blue" title="局部欧+连通开集 $\Rightarrow $ 道路连通" %}}
 $X $ 是局部欧空间, $U\subset X $ 是一个连通开集,那么 $U $ 是道路连通的.
{{% /mathbox %}}
其证明主要用到,对于欧氏空间,其连通开集 $U $ ,使得可以证明:取一基准点 $x $ ,
$$
  A=\left\{ y\in U|x\text{ is linked with }y \right\} 
$$
1. 对于任意与 $x $ 道路连通的点 $y $ 的开领域 $V\simeq B(0,1) $ ,故其中的点  $y' $ 与 $y $ 是道路连通的,那么可以构造一个从 $x $ 到 $y' $ 的道路,故 $V\subset A $ ,于是  $A $ 是开集.
2. 同理,对于不与 $x $ 道路连通的点 $y $ ,其开领域中任意点也不与 $x $ 道路连通,于是可知 $A^c $ 是开集,即 $A $ 是闭的.

于是 $A $ 是连通的.可以看到,很大程度上是利用了局部欧性质所得到的局部的道路连通性,而这在上面“拓扑学家的sine曲线”中是没有的.
> 分析$y\in[-0.1,0.1]$可以看到都是断开的线段.

另外,也正是从这可以得到:拓扑流形的道路连通性等价于其连通性.

于是,抽离出上面分析得到的结果,可以定义
{{% mathbox type="green" title="局部道路连通" %}}
👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷
{{% /mathbox %}}

从而类似上面的证明可以得到:
{{% mathbox type="blue" title="连通+局部道路连通 $\Rightarrow $ 道路连通" %}}

{{% /mathbox %}}
但反之,道路连通 $\cancel{\Rightarrow} $ 连通+局部道路连通.例如对于将 $(0,0),(1,0) $ 用一条道路连接起来的“拓扑学家的sine曲线”,其是道路连通,但不是局部道路连通的.

{{% mathbox type="blue" title="道路连通被连续映射保持" %}}

{{% /mathbox %}}
这几乎是显然的,因为对于连续映射 $f:X\rightarrow Y $ 和道路 $\gamma $ ,其复合
$$
  f\circ \gamma:[0,1]\rightarrow Y
$$
就是从 $f(x_1) $ 到 $f(x_2) $ 的道路.

{{% mathbox type="blue" title="star region 的道路连通性" %}}
 $X_\alpha $ 是道路连通的,且 $\bigcap_\alpha X_\alpha\ne \emptyset $ ,那么 $\bigcup_\alpha X_\alpha $ 是道路连通的. 
{{% /mathbox %}}

{{% mathbox type="blue" title="任意积的道路连通性" %}}

{{% /mathbox %}}
由乘积拓扑的性质,其连续性由每一个分量的连续保证.也就是说对于每一个 $(x),(y)\in \Pi_\alpha X_\alpha $ ,总是可以选每一个子空间中的 $\gamma_\alpha $ 连接 $x_\alpha,y_\alpha $ ,于是 $\gamma(t)=(\gamma_\alpha(t)) $ 就是连接 $(x),(y) $ 的道路.

{{% mathbox type="purple" title="弧连通" %}}
前面定义的道路连通 $\gamma $ 映射没有过多的要求,其甚至可以是自相交的,但是在某些问题中,如果 $\gamma $ 是一个拓扑嵌入将会更方便.这样的 $\gamma $ 称之为弧.于是就可以定义弧连通空间.可以证明在 Hausdorff 空间中,弧连通等价于道路连通.
{{% /mathbox %}}

根据连通和道路连通,可以定义两个等价关系:
1.  $x\sim y \iff $ 存在一个连通子集 $A $ 使得 $x,y \in A$
2.  $x\overset{p}{\sim} y \iff $  存在连接 $x,y $ 的道路

容易证明都是等价关系.并分别称其等价类为**连通分支**和**道路连通分支**.并可以得到两个商空间
$$
  \pi_c(X):=X/\sim,\pi_0(X):=X/\overset{p}{\sim}
$$
> 直观来看,商映射就是将等价类都捏成点,也就是将所有的连通分支或者道路连通分支捏成一点,上面俩就是表征的连通分支的数量.

{{% mathbox type="blue" title="" %}}
 $\pi_c(X) $ 是完全不连通的, 也就是说$\pi_c(X) $ 是 T1 空间.
{{% /mathbox %}}
证明👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷

但是对于 $\pi_0(X) $ 就不是这样,其作为商空间,它的商拓扑没有那么好.如前面的“拓扑学家的sine曲线”,用 $v,s $ 分别表示竖直部分和sine部分.,那么
$$
  \pi_0(X)=\left\{ v,s \right\} ,
$$
商拓扑是
$$
  \mathcal{T}=\left\{ 0,\left\{ s \right\} ,\left\{ v,s \right\}  \right\} 
$$
可以证明:  $\pi_0(X) $ 是道路连通的,但不是 T1 的.所以一般选择遗忘 $\pi_0(X) $ 上的拓扑结构,而只是将其作为一个集合看待.

##### 范畴间的函子

函子建立起了范畴之间的联系.
{{% mathbox type="green" title="函子" %}}
设 $\mathcal{C},\mathcal{D} $ 是两个范畴,从 $\mathcal{C} $ 到 $\mathcal{D} $ 的函子是一个对应,使得
1. 将 $Ob(\mathcal{C}) $ 中的每一个对象 $X $ 对应到 $Ob(\mathcal{D }) $ 中的 $F(X) $ .
2. 将 $(\mathcal{C}) $ 中的每一个态射 $f\in Mor(X,Y) $ 都对应到  $\mathcal{D} $ 中的 $F(f)\in Mor(F(X),F(Y)) $ ,且满足:
   * 对于范畴 $\mathcal{C} $ 中的任意对象 $X $ ,都有
   $$
     F(Id_X)=Id_{F(X)}
   $$
   * 对于范畴 $\mathcal{C} $ 中的任意态射 $f\in Mor(X,Y) $ 和 $g\in Mor(Y,Z) $ 都有
   $$
     F(f\circ g)=F(g)\circ F(f)
   $$

{{% /mathbox %}}

实际上,前面所讨论的 $\pi_0 ,\pi_c $ 就是两个函子.连续映射将 $X $ 的连通分支映射到 $Y $ 的连通分支中,即
$$
  \pi_c(f):\pi_c(X)\rightarrow \pi_c(Y),[x]\mapsto[f(x)]
$$

{{% mathbox type="blue" title=" $\pi_c $ 的函子性" %}}
映射$\pi_c(f)\in \mathcal{C}(\pi_c(X),\pi_c(Y)) $ ,满足
$$
  \pi_c(Id_X)=Id_{\pi_c(X)}
  \\
  \pi_c(g\circ f)=\pi_c(g)\circ \pi_c(f)
$$
{{% /mathbox %}}
证明:对于恒等映射 $Id_X:x\in X\mapsto x $ ,所以 $\pi_c(Id_X):\pi_c(X)\rightarrow \pi_c(X) $ ,对于连通分支 $[C] $ :
$$
  \pi_c(Id_X)([C])=[Id_X(C)]=[C]
$$
另一方面 $Id_{\pi_c(X)}:[C]\mapsto[C] $.所以相等.

对于 $  \pi_c(g\circ f)([C])=[(g\circ f)(C)]=[g(f(C))] $ .

另一方面, $(\pi_c(g)\circ \pi_c(f))([C])=\pi_c(g)[f(C)]=[g(f(C))] $.

于是完成证明.

实际上, $\pi_c $ 是一个从拓扑空间范畴到一个完全不连通拓扑空间范畴的函子
$$
  \boxed{\pi_c:\mathcal{TOP}\rightarrow \mathcal{TOP}_{todis}}
$$

而根据前面的分析,可以完全同理地得到 $\pi_0 $ 的函子性.
{{% mathbox type="blue" title=" $\pi_0 $ 的函子性" %}}
映射$\pi_0(f)\in \mathcal{C}(\pi_0(X),\pi_0(Y)) $ ,满足
$$
  \pi_0(Id_X)=Id_{\pi_0(X)}
  \\
  \pi_0(g\circ f)=\pi_0(g)\circ \pi_0(f)
$$
{{% /mathbox %}}
由于选择遗忘商空间中的拓扑结构,实际上 $\pi_0 $ 是一个从拓扑空间范畴到集合范畴的函子
$$
  \boxed{\pi_0:\mathcal{TOP}\rightarrow \mathcal{SET}}
$$
在应用 $\pi_c,\pi_0 $ 时,显然失去了除了连通分支个数以外的所有信息,于是可以一眼看出:连通分支数不同的拓扑空间,其一定不同胚.因为同胚是 $\mathcal{TOP} $ 中的同构,而 $\mathcal{SET} $ 中的同构是双射,根据函子保持映射复合关系,可知其保同构,也就是说对于同胚的两个拓扑空间,在上函子作用后,得到的是两个一一对应的集合,也就是两个元素个数相等的连通等价类.

#### 3.3同伦
{{% mathbox type="green" title="连续形变" %}}

{{% /mathbox %}}

有了 $F\in\mathcal{C}(T,\mathcal{C}(X,Y)) $  ,由于其中 $\mathcal{C}(X,Y ) $ 上复杂的紧开拓扑,应该考虑一个更简单的 $G\in \mathcal{M}(T\times X,Y) $ 使得有 $G(t,x);=F(t)(x) $ .
{{% mathbox type="blue" title="" %}}
1. 若 $G\in \mathcal{C}(T\times X,Y) $,则 $F\in \mathcal{C}(T,\mathcal{C}(X,Y)) $
2. 若 $X $ 为 LCH 空间,那么 
$$
  G\in \mathcal{C}(T\times X,Y) \iff F\in \mathcal{C}(T,\mathcal{C}(X,Y)) 
$$

{{% /mathbox %}}
证明👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷

于是就得到了一个非常方便的(几乎)等价刻画.

{{% mathbox type="green" title="同伦" %}}
存在$F:[0,1]\times X\rightarrow Y $连续,使得
$$
  F(0,x)=f_0(x),F(1,x)=f_1(x)
$$
称 $f_0 $ 和 $f_1 $ 是同伦的,记作 $f_0\sim f_1 $ . 且称 $F $ 是其之间的一个同伦.
{{% /mathbox %}}
根据前面的命题,可以知道, $f_0\sim f_1 $  $\Rightarrow $  $f_0,f_1\in (\mathcal{C}(X,Y),\mathcal{T}_{c.o.}) $ 在同一道路连通分支中.而若 $X $ 是 LCH 空间,那么任意从 $f_0 $ 到 $f_1 $ 的连续形变都由一个同伦给出,即 $f_0\sim f_1 $   $\iff $  $f_0,f_1 $ 在同一个道路连通分支中.


___
___
___
___
___