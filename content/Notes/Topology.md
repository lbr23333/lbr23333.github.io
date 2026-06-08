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
    - [道路同伦](#道路同伦)
  - [3.4 基本群](#34-基本群)
    - [$\\pi\_1 $ 的函子性](#pi_1--的函子性)




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

> 为什么要引入紧开拓扑 $\mathcal{T}_{c.o.} $ 作为连续函数空间 $\mathcal{C}(X,Y) $ 的拓扑?
>
> (似乎有些问题👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷)
> 
> 对于逐点收敛拓扑,它太弱了,因为逐点收敛的函数,其极限函数可能并不收敛,换句话说,逐点收敛拓扑只能保证有限个点处的取值,而点与点之间的映射可能非常糟糕.对于一致收敛拓扑,它由太强了,依赖于度规.而紧开拓扑的的子基为 $S(K,U)=\left\{ f\in \mathcal{C}(X,Y)|f(K)\subset U \right\}  $ ,其中 $K $ 是 $X $ 中的紧集, $U $ 是 $Y $ 中的开集.在 $LCH $ 空间下,紧开拓扑等价于在紧集上一致收敛.是唯一能够让 $G\in \mathcal{C}(T\times X,Y) \iff F\in \mathcal{C}(T,\mathcal{C}(X,Y))  $ 完美成立的拓扑.选择紧集 $K $ 也是为了保证一定的有界性.
>
> 对于上面的 $X $ 不是 LCH 空间,很容易给出一个反例: 
> 
> $X=\mathbb{Q},Y=\mathbb{R} $ , 如果已经有一个同伦 $H\in \mathcal{C}(I\times \mathbb{Q},\R)$ 总是能得到连接 $f_0,f_1 $ 的道路 $\gamma(t) $ .
> 
> 但若只是有在映射空间 $\mathcal{C}(X,Y) $ 中构造道路 $\gamma(t)=f_t $  , 考虑一整个区间上的连续性就会出问题,例如考虑 $U=(-1,1)\cap\mathbb{Q} $ , 根据前点集拓扑学 , 没有紧集 $K $ 能够包含 $U $ .也就是说对于上面的 $\gamma(t) $ 根本无法构造一个同伦 $H(t,x)\in \mathcal{C}(I\times \mathbb{Q},\R) $ .
>
> 更具体一点,实际上
$$
  H:I\times X\xrightarrow{f\times Id}\mathcal{C}(X,Y)\times X\xrightarrow{ev}Y
$$
>其中 $ev $ 是赋值映射,即 $ev(f_t,x)=f_t(x) $ .选择构造 $f_0(x)=0 $ 为常值映射 , 划定 $\R $ 中的开集 $V=(-0.1,0.1) $ ,若 $H $ 连续,则一定有一个包含 $(f_0,0) $ 的开集 $S(K,U)\times W $ 被 $ev $ 映射到 $V $ 中,但是没有紧集能包含 $W $ ,对于 $W $ 中紧集之外的点,其根本不受子基 $S(K,U) $ 的约束.注意 $S(K,U) $ 是映射空间中的开集.
> 
> 若是 LCH 空间,就存在管状领域使得对于紧集 $K $ 总是有开集 $V\subset K $ 使得这一切都是好的.

引入记号,对于每一个 $f\in \mathcal{C}(X,Y) $ , 记 $[f] $ 为 $f $ 的同伦等价类.且记 $[X,Y] = \mathcal{C}(X,Y)/\sim  $ 为 $\mathcal{C}(X,Y) $ 中的同伦等价类.对于两个映射 $f_0,f_1 $ 能放在同一个等价类中,就是说存在 $H\in\mathcal{C}(X\times I,Y) $ 为 $f_0,f_1 $ 的同伦.另外映射空间的道路连通分支 $\pi_0(\mathcal{C}(X,Y)) $  中两个映射对应其中同一个元素当且仅当存在 $\gamma\in \mathcal{C}(I,\mathcal{C}(X,Y)) $  . 因此根据前面的分析,若 $X $ 为 LCH 空间,那么 $[X,Y]=\pi_0(\mathcal{C}(X,Y)) $  .

一个特殊情况是,若 $X $ 为单点集,那么 $f_0,f_1 $ 的象也都是单点.于是 $f_0,f_1 $ 同伦 $\iff $ 对应的两个点可以由 $Y $ 中的道路连接.即
$$
  [\left\{ pt \right\} ,Y]=\pi_0(Y)
$$

{{% mathbox type="blue" title="" %}}
1. 若 $f_i\in \mathcal{C}(X,Y),g_i\in \mathcal{C}(Y,Z),i=1,2 $ ,且 $f_1\sim f_2,g_1\sim g_2 $ ,那么 $g_1\circ f_1\sim g_2\circ f2 $ .
{{% /mathbox %}}
证明是容易的,显式构造出两个同伦并进行等时复合就能得到.

于是同伦类的下列操作都是良定的:
1. 复合: $[X,Y]\times [Y,Z]\rightarrow [X,Z] ;([f],[g])\mapsto [g\circ f] $ .
2. 拉回
3. 推前

{{% mathbox type="green" title="零伦" %}}
若 $f\in \mathcal{C}(X,Y) $ 同伦于某个常值映射,那么称之为零伦的.
{{% /mathbox %}}

例如,对于欧氏空间中的星状域 $Y\subset \R^n $ ,存在中心点 $y_0\in Y $ 使得与任何点道路连通.那么对于任意的拓扑空间 $X,Z $ 都有:
* 任意连续映射 $f\in \mathcal{C}(X,Y) $ 是零伦的.因为有
$$
  F(t,x)=ty_0+(1-t)f(x)
$$
* 任意连续映射 $f\in \mathcal{C}(Y,Z) $ 是零伦的.因为有
$$
  F(t,y)=f(ty_0+(1-t)y)
$$
{{% mathbox type="green" title="可缩空间" %}}
若拓扑空间 $X $ 的恒等映射 $Id_X $ 是零伦的,则称之为可缩空间.
{{% /mathbox %}}
1. 由上例,可知欧氏空间中的星状域都是可缩的.
2. 对于拓扑空间 $X $ 的锥空间 $C(X)=X\times[0,1]/X\times\left\{ 0 \right\}  $ 都是可缩的,证明过程与星状域类似,构造
$$
  H((x,t),s)=(x,(1-s)t)
$$
  由此还可知,任意的拓扑空间都能被嵌入到某个可缩空间.

类似于同胚,可以定义:
{{% mathbox type="green" title="同伦等价" %}}
对于 $X,Y $ 若存在 $f\in\mathcal{C}(X,Y) $ 和 $g\in\mathcal{C}(Y,X) $ 使得
$$
  f\circ g \sim Id_Y,g\circ f \sim Id_X
$$
则称 $X,Y $ 是同伦等价的,记作 $X\sim Y $ .并称 $f,g $ 为 $X,Y $ 之间的同伦等价.
{{% /mathbox %}}

显然同伦等价是一个比同胚要弱的关系.

##### 道路同伦

回到最开始,我们想定义一套代数运算来处理拓扑问题,但是遇到了一些问题.具体来说,一大问题是道路是参数依赖的,于是可以进行重参数化
{{% mathbox type="green" title="重参数化" %}}
对于 $X $ 中的两个道路 $\gamma_1,\gamma_2 $ , 连续映射 $f:[0,1]\rightarrow [0,1] $ 满足, $f(0)=0,f(1)=1 $ 使得
$$
  \gamma_2\circ f=\gamma_1
$$
则称 $\gamma_2 $ 是 $\gamma_1 $ 的重参数化.
{{% /mathbox %}}
显然,重参数化前后的两个道路是同伦的. $F(t,s)=\gamma_1((1-t)s+tf(s)) $ 就是同伦.
> 本质上是用到了 $[0,1] $ 的凸性,即任何 $[0,1]\rightarrow [0,1] $ 的连续映射都是同伦的,故 $f:s\mapsto f(s),Id:s\mapsto s $ 是同伦的,即对于任意的 $t $ , $(1-t)s+tf(s) $ 都是一个介于 $s $ 与 $f(s) $ 之间的点.

所以道路运算都是保同伦类的:
{{% mathbox type="blue" title="道路运算保同伦类" %}}
对于任意的 $\gamma_i\in \Omega(X;x_i,x_{i+1}),\gamma\in \Omega(X;x_1,x_2) $ :
1.  $(\gamma_1*\gamma_2)*\gamma_3\sim \gamma_1*(\gamma_2*\gamma_3) $ 
2.  $\gamma_{x_1}*\gamma\sim \gamma $ 
3.  $\gamma*\bar{\gamma}\sim \gamma_{x_1},\bar\gamma*{\gamma}\sim \gamma_{x_2} $ 
{{% /mathbox %}}

于是自然会去想研究道路同伦类的代数运算,如 $[\gamma_1]*[\gamma_2]=[\gamma_1*\gamma_2] $ , 但是 $\gamma_1,\gamma_2 $ 可能首尾不相连,所以 $ \gamma_1*\gamma_2 $ 可能根本就没有意义.于是进一步定义固定端点的同伦:
{{% mathbox type="green" title="道路同伦" %}}

记作 $\gamma_0\underset{p}{\sim}\gamma_1 $ 

$\gamma $ 的道路同伦等价类: $[\gamma]_p $

固定端点 $x_0,x_1 $ 的道路同伦等价类集合: $\pi(X;x_0,x_1) $ .
{{% /mathbox %}}

{{% mathbox type="blue" title="良定性" %}}

{{% /mathbox %}}

{{% mathbox type="blue" title="群胚" %}}

{{% /mathbox %}}

可见,对于
$$
  \pi(X)=\bigcup_{x,y\in X}\pi(X;x,y)
$$
取逆运算是处处有定义的,但是乘法只能在部分元素之间进行,只有“首尾相连”的道路同伦类才能相乘.但若再进一步,将每一个固定端点的道路首尾设作为同一点,就不会有上面问题.

#### 3.4 基本群
令 $\pi_1(X,x_0)=\pi(X;x_0,x_0) $ ,就是一个群.因为显然任意两个元素可以相乘而且封闭,有单位元 $e=[\gamma_{x_0}]_p $ 以及逆元 $[\gamma]_p^{-1}=[\bar\gamma]_p $ .

于是就有
{{% mathbox type="blue" title=" $\pi_1(X,x_0) $ 群运算" %}}

{{% /mathbox %}}

{{% mathbox type="green" title="基本群" %}}
称 $\pi_1(X,x_0) $ 为以 $x_0 $ 为基点的基本群.
{{% /mathbox %}}

对于在同一个道路分支的 $x_1,x_2 $ , $\pi_1(X,x_1),\pi_1(X,x_2) $ 是同构的,因为总是存在连接 $x_1,x_2 $ 的道路 $\lambda $ ,于是在 $\pi_1(X,x_1) $ 中的元素 $[\gamma]_p $ 就可以构造 $\lambda^{-1}*\gamma*\lambda\underset{p}{\sim}\gamma $ 使得 $[\lambda^{-1}*\gamma*\lambda]_p\in \pi_1(X,x_2) $ .所以之后考虑道路连通的空间 $X $ 都可以省去基点 $x_0 $ ,即其基本群(族)为 $\pi_1(X) $ .

{{% mathbox type="green" title="单连通空间" %}}
设 $X $ 是道路连通空间,若其基本群是平凡的,即 $\pi_1(X)=\set{e} $ ,则称 $X $ 为单连通空间.
{{% /mathbox %}}
于是欧氏空间中的星形域都是单连通的.后面将证明
$$
  \pi_1(S^n,x_0)\cong \begin{cases}
    \mathbb{Z}&,n=1
    \\
    \set{e}& ,n\ge 2
  \end{cases}
$$
也就是说 $S^1 $ 不是单连通的,而 $S^n(n\ge 2) $ 是单连通的.直观上来说,单连通的概念很好理解,也就是衡量空间中有没有“洞”.具体地,由于 $[0,1] $ 是LCH空间,所以
$$
  \pi_1(X,x_0)=\Omega(X,x_0)/\underset{p}{\sim}=\pi_0(\Omega(X,x_0))
$$
即基本群 $\pi_1(X,x_0) $ 衡量的是圈空间 $\Omega(X,x_0) $ 的道路连通性:
* 对应于 $\pi_1(X,x_0) $ 中单位元的圈 $\iff $ 能在  $X $  中收缩到一点的圈
* 对应于 $\pi_1(X,x_0) $ 中同一元素的两个圈 $\iff $ 能在  $X $  中通过连续形变相互转化的圈.

#####  $\pi_1 $ 的函子性

根据前面的描述,已经知道了 
$$
  \boxed{\pi_1:\mathcal{Pointed TOP}\rightarrow \mathcal{GROUP}}
$$
即是一个从固定点的拓扑空间范畴到群范畴的对应,但目前还不能说明是一个函子,因为要证明其保持态射的一些性质.

 $\mathcal{Pointed TOP} $ 中
* 对象是带有固定点的拓扑空间 $(X,x_0) $ 
* 态射是带有固定点的联系映射 $f\in \mathcal{C}((X,x_0),(Y,y_0)) $ ,满足 $f(x_0)=y_0 $ .

对于道路同伦的 $\gamma_1\underset p\sim \gamma_2 $ ,由于连续映射 $f $ 有 $f\circ \gamma_1\underset p\sim f\circ\gamma_2 $.所以 $f $  自然诱导了基本群之间的映射
$$
  f_*:\pi_1(X,x_0)\rightarrow \pi_1(Y,y_0),[\gamma]_p\mapsto[f\circ \gamma]_p
$$
可以验证 $f_* $ 继承了 $f $ 在固定点拓扑空间范畴中的性质:
1. 群同态: $f_*([\gamma_1]_p*[\gamma_2]_p)=f_*([\gamma_1*\gamma_2]_p)=[f\circ(\gamma_1*\gamma_2)]_p=[(f\circ\gamma_1)*(f\circ\gamma_2)]_p =[f\circ\gamma_1]_p*[f\circ\gamma_2]_p $ .
2. 恒等:  $Id_X\mapsto Id_{\pi_1(X,x_0)} $ 
3. $(g\circ f)_* =g_*\circ f_* $ ,  since  $(g\circ f)_*([\gamma]_p) =g_*([f\circ \gamma]_p)=([g\circ f\circ \gamma]_p)=g_*\circ f_*([\gamma]_p)  $ .

也就是说 $\pi_1 $ 确实是两个范畴之间的函子.函子是保等价性的:
{{% mathbox type="blue" title="基本群是拓扑不变量" %}}
若 $f:X\rightarrow Y $ 是一个同胚,那么 $f_* $ 是基本群之间的同构:
$$
  f_*:\pi_1(X,x_0)\simeq \pi_1(Y,f(x_0))
$$
{{% /mathbox %}}
证明:
$$
  f_*\circ (f^{-1})_*=(f\circ f^{-1})_*=(Id_Y)_*=Id_{\pi_1(Y,y_0)}
  \\
  (f^{-1})_*\circ f_*=(f^{-1}\circ f)_*=(Id_X)_*=Id_{\pi_1(X,x_0)}
$$
即 $f_*,(f^{-1})_* $ 是互逆的群同态,即群同构.

根据函子将乘法对象映到乘法对象,还有
{{% mathbox type="blue" title="乘积空间的基本群" %}}
$\pi_1(X\times Y,(x_0,y_0))\cong \pi_1(X,x_0)\times \pi_1(Y,y_0) $ 
{{% /mathbox %}}
证明: 对于乘积空间,有有投影映射:
$$
  p_1:(X\times Y,(x_0,y_0))\rightarrow (X,x_0)
  \\
  p_2:(X\times Y,(x_0,y_0))\rightarrow (Y,y_0)
$$
于是由函子作用后,得到群范畴中的投影映射:
$$
  \pi_1(p_1)=p_{1*}:\pi_1(X\times Y,(x_0,y_0))\rightarrow \pi_1(X,x_0)
  \\
  \pi_1(p_)=p_{2*}:\pi_1(X\times Y,(x_0,y_0))\rightarrow \pi_1(Y,y_0)
$$
于是有
$$
  \varphi:\pi_1(X\times Y,(x_0,y_0))\rightarrow \pi_1(X ,x_0)\times \pi_1(Y,y_0)
  \\
  \varphi([\gamma])= (p_{1*}[\gamma],p_{2*}[\gamma])=([p_1\circ \gamma],[p_2 \circ \gamma])
$$
再构造其逆
$$
  \psi:\pi_1(X ,x_0)\times \pi_1(Y,y_0)\rightarrow \pi_1(X\times Y,(x_0,y_0))
  \\
  \psi([\gamma_1],[\gamma_2])=[\gamma_1\times\gamma_2]
$$
显然是良定的:
$$
  \forall \alpha,\gamma_1\in [\gamma_1],\beta,\gamma_2\in [\gamma_2],
  \\
  \psi([\alpha],[\beta])=[\alpha\times\beta]=[\gamma_1\times\gamma_2]=\psi([\gamma_1],[\gamma_2])
$$
是群同态:
$$
  \psi([\alpha]\cdot[\alpha'],[\beta]\cdot[\beta'])=\psi([\alpha],[\beta])\cdot\psi([\alpha'],[\beta'])
$$
还可以验证
$$
  \psi\circ\varphi=Id,
  \\
  \varphi\circ\psi=Id.
$$
于是就证明了
$$
  \pi_1(X\times Y,(x_0,y_0))\cong \pi_1(X,x_0)\times \pi_1(Y,y_0).
$$


















___
___
___
___
___