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
    - [pi\_1的函子性](#pi_1的函子性)
    - [作为固定点拓扑空间范畴中同伦等价类的pi\_1](#作为固定点拓扑空间范畴中同伦等价类的pi_1)
    - [基本群的性质](#基本群的性质)
  - [3.5 圆的基本群的计算](#35-圆的基本群的计算)
    - [S^n(n大于2)的基本群](#snn大于2的基本群)
    - [S^1的基本群](#s1的基本群)
  - [3.6 Van Kampen 定理](#36-van-kampen-定理)
  - [3.7 覆叠空间](#37-覆叠空间)
    - [另外一些覆叠空间的例子](#另外一些覆叠空间的例子)
    - [群作用与覆叠空间](#群作用与覆叠空间)
    - [提升引理](#提升引理)
    - [万有覆叠空间](#万有覆叠空间)
  - [3.8 覆叠空间的分类](#38-覆叠空间的分类)




## 3. 连通性与基本群

迷宫右手原则是指,对于一个规则的树状迷宫,沿着右边墙壁走总是能走出去.因为标准的迷宫是指任意两点之间只会有一条路,没有闭合的回路(也就是树图).于是正确的路径就总是把整个迷宫分成了两半,沿着右边那一半的边界,总是能够走出去.对于非标准的迷宫,会出现一些“孤岛”,使得右手原则不再生效.这就是连通性.

![Labyrinth](/images/Topology/ Labyrinth.png)

### 3.1 连通性

### 3.2 道路连通

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

#### 范畴间的函子

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

### 3.3同伦
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

#### 道路同伦

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

### 3.4 基本群
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

#### pi_1的函子性

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

#### 作为固定点拓扑空间范畴中同伦等价类的pi_1

实际上,基本群有一个更加general的写法.由于 $\pi_1(X,x_0) $ 等于 $\Omega(X,x_0)$ 中的道路等价类,而 $\Omega(X,x_0)$ 中的元素,也就是loops,本来就给出了一个将 $S^1=[0,1]/{0\sim 1} $ 映射到 $X $ 的商映射,其中将 $\left\{ 0,1 \right\}  $ 都映射到 $x_0 $ ,所以 $\Omega(X,x_0)=\mathcal{C}((S^1,\left\{ 0,1 \right\} ),(X,x_0 )) $ .而前面得到了
$$
  \pi_1(X,x_0)=\pi_0(\Omega(X,x_0))
$$
若记 $p=\left\{ 0,1 \right\}  $ ,那么
$$
  \pi_1(X,x_0)=\pi_0(\mathcal{C}((S^1,\left\{ 0,1 \right\} ),(X,x_0 )))=[(S^1,p),(X,x_0 )]
$$
更一般地,可以如下考虑:

在带有基点的连续映射空间 $\mathcal{C}((X,x_0),(Y,y_0)) $ 中,考虑同伦(连续形变),要求基点在形变过程中保持不变,那么设 $f_0,f_1 $ 是两个带有相同基点的连续映射,有其之间的保持基点的同伦 $F:[0,1]\times X\rightarrow Y $ 使得
$$
  F(0,x)=f_0(x),F(1,x)=f_1(x),\forall x\in X
  \\
  F(t,x_0)=y_0,\forall t\in [0,1]
$$
可以证明这是一个等价关系.将商空间就记作 $[(X,x_0),(Y,y_0)] $ .

将该方法用到前面的 $\pi_0 $ 上,解释为 带基点空间里,连续映射的同伦类的集合. 只是将 $S^1\rightarrow S^0 $ ,取 $p=\left\{ 1 \right\} \in S^0 $ 
> 注意 $S^1=\left\{ 0,1 \right\}  $ 

那么 $\pi_0(X,x_0)=[(S^0,p),(X,x_0 )] $
* 一个从 $(S^0,p) $ 到 $(X,x_0) $ 的带基点的连续映射 $f $ 
  
   $\iff $ 一个满足条件 $f(1)=x_0 $ 的映射 $f:\left\{ \pm 1 \right\} \rightarrow X $ 

   $\iff $ 单点 $f(-1)\in X $ 

* 两个带基点的映射 $f_1,f_2:(S^0,1)\rightarrow (X,x) $ 是同伦的
  
   $\iff $ 存在连接 $f_1(-1) $ 和 $f_2(-1) $ 的连续曲线 $\gamma(t)=F(t,-1) $ 

    $\iff $  $f_1(-1) $ 和 $f_2(-1) $ 位于 $X $ 的同一个道路连通分支中.

这正是前面所得到的结论: $\pi_0(X) $ 为 $X $ 的道路等价类的集合.

最后,完全可以将此推广到更高阶,于是有同伦群
$$
  \pi_n(X,x_0):=[(S^n,p),(X,x_0 )]
$$
关于同伦群的一个简单介绍,可以参见[这个讲义]({{< ref "Notes/differential-geometry-in-physics.md" >}}).后面应该会更系统学习一下代数拓扑,但不是在这里.


> 考虑如下一个问题:
>
> 若已知 $\pi_1(X,x_0)=\left\{ e \right\}  $ ,是否能得到 $X $ 是单连通的?
> 
>---是不能的,可能会想是因为没有 $x_0 $ 想关的信息.但实际上,就算对于任意的 $x_0 $ 都有 $\pi_1(X,x_0)=\left\{ e \right\}$ 成立,依然无法得到结论.因为对于有多个道路连通分支的 $X $ 而言,$\pi_1(X,x_0)=\left\{ e \right\}  $ 总是成立的.
>
> 所以,高阶的同伦群对于次高阶的,就像 $0 $ 阶的 $\pi_0 $ 只能探测空间的道路连通分支数一样,它只能探测次高阶的“某种意义”上的道路连通分支.因为前面我们也得到过
$$
  [X,Y]=\pi_0(\mathcal{C}(X,Y))
$$
> 若将 $X $ 视作为 $S^n $ 那么就是
$$
  \pi_n(X)=\pi_{n-1}(\Omega(X))=\pi_{n-2}(\Omega(\Omega X))=\dots=\pi_0(\Omega^n X)
$$

#### 基本群的性质

{{% mathbox type="blue" title="基本群的基点选取无关性" %}}
若 $x_0,x_1 $ 在 $X $ 的同一个道路连通分支中,则对于任意从 $x_0 $ 到 $x_1 $ 的道路  $\lambda $ , 映射$\Gamma_\lambda:\pi_1(X,x_0)\rightarrow \pi_1(X,x_1) ,\Gamma_\lambda([\gamma]_p)\mapsto[\bar\lambda*\gamma*\lambda]_p $ 是一个同构.
{{% /mathbox %}}
证明是简单的,其实前面也提到过,考虑从 $x_0 $ 的圈前后加上一个 $\lambda $ 道路就得到了 $x_1 $ 的圈,具体地:先证明上映射是一个同态
$$
  \begin{align*}
    \Gamma_\lambda([\gamma_1]_p*[\gamma_2]_p)&=\Gamma_\lambda([\gamma_1*\gamma_2]_p)
    \\
    &=[\bar\lambda*\gamma_1*\gamma_2*\lambda]_p
    \\
    & =[\bar\lambda*\gamma_1*\lambda]_p*[\bar\lambda*\gamma_2*\lambda]_p
    \\
    & = \Gamma_\lambda([\gamma_1]_p) * \Gamma_\lambda([\gamma_2]_p)
  \end{align*}
$$
反之完全同理证明 $\Gamma_\lambda^{-1} $ 也是一个同态,即 $\Gamma_\lambda $ 是一个同构.

所以对于道路连通的拓扑空间,任意点的基本群都是同构的,那么就可以省去基点,用 $\pi_1(X) $ 表示 $X $ 的基本群(族).由于总是可以将不同的道路连通分支分开考虑,所以在后面的讨论中,总是假设 $X $ 是一个道路连通的拓扑空间.

前面提到 $\pi_1 $ 是一个函子,将拓扑空间之间的映射对应到一个诱导映射 $f_* $ ,对于不同的映射 $f_1,f_2:X\rightarrow Y $ , 有
{{% mathbox type="blue" title=" $f_* $ 的“同伦不变性”" %}}
若 $f_1\sim f_2\in\mathcal{C}(X,Y) $ ,那么 $\Gamma_\lambda:\pi_1(Y,y_1)\rightarrow \pi_1(Y,y_2) $ 作为群同态,有 $(f_2)_*=\Gamma_\lambda\circ (f_1)_* $ .
{{% /mathbox %}} 
证明思路完全同理遇上,对于基点分别在 $y_1,y_2 $ 的两个圈,也可以利用前后加上 $\lambda $ 道路使得两个圈的基点相互转换.(可以想象 $\phi^3 $ 模型中的两个泡的真空图)具体地,
$$
  G:[0,1]\times[0,1]\rightarrow Y,G(t,s)=F(t,\gamma(s))
$$
$\bar\lambda_t* G(t,s)* \lambda_t $ 就是一个 $\bar\lambda* (f_1\circ \gamma)* \lambda $ 与 $f_2\circ \lambda $ 的同伦.

{{% mathbox type="blue" title="基本群的同伦不变性" %}}
$X,Y $ 是同伦等价的拓扑空间,那么 $\pi_1(X)\cong \pi_1(Y) $ .
{{% /mathbox %}}
证明:设其同伦为 $f:X\rightarrow Y,g:Y\rightarrow X,f\circ g\sim Id_Y $ ,有
$$
  \Gamma_\lambda\circ f_*\circ g_*=Id:\pi_1(Y,f(x_0))\rightarrow \pi_1(Y,f(x_0))
$$
由于 $\Gamma_\lambda $ 是群同构,可知 $f_* $ 是满射, $g_* $ 是单射.反之可得, $f_* $ 是单射, $g_* $ 是满射.即
$$
  f_*:\pi_1(X,x_0)\rightarrow \pi_1(Y,f(x_0))
$$
是群同构.

> 但似乎,前面提到,对于同伦的 $X,Y $ ,它们的全阶同伦群都是同构的,这似乎暗示可以利用 $\pi_n $ 的函子性进行证明?然而实际上,上面的证明其实就是利用了函子性
$$
  \pi_1:\mathcal{TOP_*}\rightarrow \mathcal{GROUP}
$$
> 所以 $(g\circ f) _*=g_*\circ f_* $ ,而上面的证明中实际上应该是
$$
  \Gamma_\lambda\circ (g\circ f)_*=(Id_X)_*=Id
$$
> 也就说其实上面的证明中已经用到了.
> 
> 对于更高阶的同伦群,可以同理证明.注意到高阶的同伦群由于天然的有 $\pi_1(S^n)=0,n\ge 2 $ ,所以甚至不需要用到上面转换基点所用到的 $\Gamma $ ,也就是说
$$
  (g\circ f)_*=(Id_X)_*=Id
$$
> 于是就有了类似的结论.
>
> 关于基本群的 non-Abelian 性质和更高阶的同伦群的 Aelian 性.后面还会再谈到,但是这里可以先给出一些直观的例子,并先简单说明为什么.下图直观展示了基本群的 non-Abelian 性

![基本群的非Abelian性](/images/Topology/fund_group_nonabelian.png)
> 而对于更高阶的同伦群,前面提到了 $\pi_1(S^n)=0 $ ,直观上来看就是

![高阶同伦群的Abelian性](/images/Topology/homotopy_grp_abelian.jpg)

> 可见天然地有道路同伦.根本原因在于,我们所定义的道路同伦是保基点的.这也导致了 $\pi_0 $ 没有一些很好的群性质.如果我们选择保“基线”而不是保基点,那么显然上图就跟前面基本群那张图一样遇到一些阻碍,即不能再轻易使得两边是“保基线同伦”的了.
>
> 就此打住.

引入形变收缩的性质: 若有收缩 $r:X\rightarrow A $ 使得 $r\sim Id_X $ ,则称 $A $ 为 $X $ 的一个形变收缩.并称 $A $ 为 $X $ 的形变收缩核.
{{% mathbox type="blue" title="形变收缩 $\Rightarrow $ 相同基本群" %}}
若 $A $ 是 $X $ 的形变收缩核,那么 $\pi_1(X)\cong \pi_1(A) $ .
{{% /mathbox %}}
证明也是很显然, $i:A\hookrightarrow X\Rightarrow r\circ i=Id_A $ ,且 $i\circ r=r\sim Id_A $ ,也就是说 $r,i $ 是 $A,X $ 的同伦,即 $A\sim X $ ,由前命题, $\pi_1(X)\cong \pi_1(A)  $ .

特别的,对于可缩空间 $X\sim \left\{ pt \right\}  $ ,其基本群即
$$
  \pi_1(X)\cong \pi_1(\left\{ pt \right\} )\cong \left\{ e \right\} 
$$
即可缩空间都是单连通的.

> 其实这里的形变收缩很直观地反应了同伦与同胚的区别,对于一些形如 $\huge* $ 的东西,其可以收缩到一点 $\huge{\cdot} $ ,也就是说 $\huge{*}\sim \huge{\cdot} $ .但是这两个东西显然是不同胚的,考虑到前面的一个结论,同胚的两个空间去掉同胚对应的一点后,仍然是同胚的,但是上面俩去掉中间一点后甚至前者都不是连通的了,显然不是同胚的.

> 实际上,这里也可以利用 $\pi_n $ 的函子性进行一些推广,对于同伦等价的 $X\sim Y $ 由
$$
  f\circ g\sim Id,g\circ f\sim Id,
$$
由 $\pi_n $ 对应到群范畴即是
$$
  f_*\circ g_*\sim Id_{\pi_n(X)},g_*\circ f_*\sim Id_{\pi_n(Y)},
$$
可得到 $\pi_n(X)\cong \pi_n(Y) $ 
>
> 本质上,同伦群作为商空间,将几何上的同伦等价 $\sim $ 转化为代数上的同构 $\cong $ 就是代数拓扑的核心思想.

### 3.5 圆的基本群的计算

#### S^n(n大于2)的基本群

{{% mathbox type="blue" title="并集的单连通性" %}}
若 $X=U\cup V $ ,其中 $U,V $ 都是 $X $ 中的单连通开集,且 $U\cap V $ 是道路连通的,则 $X $ 是单连通的.
{{% /mathbox %}}
证明:👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷

于是对于 $S^n(n\ge 2) $ 总是可以选南北两个大半球cover住整个 $S^n $ ,而且两个大半球都是单连通的,其交也显然是道路连通的.所以 $S^n(n\ge 2) $ 都是单连通的,即
{{% mathbox type="blue" title="" %}}
$n\ge 2 $ , $\pi_1(S^n)\cong \left\{ e \right\}  $ .
{{% /mathbox %}}

进一步,由于 $R^n\setminus\set{0}\sim S^{n-1} $ ,所以还有
{{% mathbox type="blue" title="" %}}
$n\ge 3 $ , $\pi_1(R^n\setminus\set{0})\cong \left\{ e \right\}  $ .
{{% /mathbox %}}

####  S^1的基本群
> 没想到最简单的非平凡基本群都这么复杂...

### 3.6 Van Kampen 定理


















> 不是那么值得一提的是, $\pi_1(T^2)=\mathbb{Z}^2=\langle \alpha,\beta|\alpha\beta\alpha^{-1}\beta^{-1}=1 \rangle  $ 的 Abelian 性体现在 $(a,b)+(c,d)=(c,d)+(a,b) $ , 也就是说对于 $T^2 $ 上的两种不同的loops所构成的一整个 loop ,其中的 $\alpha,\beta $ 的先后是可以交换的,而不是 $(a,b)=(b,a) $ .




### 3.7 覆叠空间

> 物理中常见的 $SU(2) $ 作为 $SO(3) $ 的二重覆盖,其实就在说是一个二重的覆叠空间.实际上,前面我们已经遇到过了覆叠空间,在计算 $\pi_1(S^1)\cong \mathbb{Z} $ 是所用到的 $p:\R\rightarrow S^1 $ 中, $\R $ 就是作为 $S^1 $ 的覆叠空间出现.

{{% mathbox type="green" title="覆叠空间" %}}
对于拓扑空间 $X $ ,若存在另一个拓扑空间 $\tilde X $ 和映射 $p:\tilde X\rightarrow X $ ,使得对于任意的 $x\in X $ ,存在一个 $x $ 的开邻域 $U $ 满足:
1.  $p^{-1}(U)=\bigcup_\alpha V_\alpha $ , 其中 $V_\alpha \subset \tilde{X}$ 是无交的开集,即 $V_\alpha \cap V_\beta=\emptyset $ .
2.  对于 $p|_{V_{\alpha}}:V_\alpha\rightarrow U $ 即将 $p $ 限制到某一个 $V_\alpha $ 上, $p|_{V_{\alpha}}  $ 是一个同胚.

那么称 $\tilde{X} $ 为 $X $ 的一个覆叠空间, $p $ 为相应的覆叠映射.对于任意的 $x $ , $p^{-1}(x) $ 为 $x $ 的纤维.
{{% /mathbox %}}

> 在代数拓扑中,几何上的直观是很重要的,在各种证明中几乎都是先有了几何上的直观证明,再将其严格化为自然语言.所以后面我会尽可能地加上一些图,以帮助直观理解证明.
>
> 一个有用的例子是前面已经用过的“弹簧”:
> ![弹簧](/images/Topology/coveringspace1.png)
>
> 后面会看到这是一个非常“标准”的例子.

#### 另外一些覆叠空间的例子

#### 群作用与覆叠空间

若群 $G $ 在拓扑空间 $\tilde{X} $ 上的作用,满足对于任意的 $\tilde{x}\in\tilde{X} $ ,存在 $\tilde{x} $ 的开邻域 $\tilde{U} $ ,使得对于任意的 $g\in G $ , $g\cdot\tilde{U}\cap \tilde{U}=\emptyset $  .那么称 $G $ 是纯不连续的.

{{% mathbox type="blue" title="" %}}
若 $G $ 作用到 $\tilde{X} $ 上是纯不连续的,那么 $\tilde{X} $ 是商空间 $X=\tilde{X}\setminus G $ 的覆叠空间.
{{% /mathbox %}}

证明:(主要依赖于群结构和群元的作用是一个同胚)

#### 提升引理
{{% mathbox type="green" title="映射的提升" %}}

{{% /mathbox %}}


{{% mathbox type="green" title="general 提升引理" %}}

{{% /mathbox %}}

由此可得到道路的提升引理和同伦的提升引理.




{{% mathbox type="blue" title="提升的唯一性" %}}

{{% /mathbox %}}

对于一般映射的提升, $f $ 提升到 $\tilde{f} $ ,由 $\pi_1 $ 的 函子性,有
$$
  f_*(\pi_1(Y,y_0))=p_*(\tilde{f}_*(\pi_1(Y,y_0)))\subset p_*(\pi_1(\tilde{X},\tilde{x}_0))
$$
这就是提升存在的必要条件.实际上,在 $Y $ 是道路连通且局部道路连通时,这就是充要条件.
{{% mathbox type="blue" title="提升的存在性" %}}
$p:(\tilde{X},\tilde{x}_0)\rightarrow (X,x_0 ) $ 是一个覆叠映射,并且 $f:(Y,y_0)\rightarrow (X,x_0) $ 是连续的. 若$Y $ 是道路连通且局部道路连通时,那么 $f $ 可以被提升为 $\tilde{f} $ 当且仅当
$$
  f_*(\pi_1(Y,y_0))\subset p_*(\pi_1(\tilde{X},\tilde{x}_0))
$$
{{% /mathbox %}}

可由此再次得到,  对于 $n\ge 2 $ ,任意连续映射 $f:S^n\rightarrow S^1 $  是零伦的.因为 $\pi_1(S^n)=\Set{e} $ ,所以 $Im(f_*)=\Set{e} $ . $S^n $ 是道路连通且是局部道路连通的,可以被提升到 $\tilde{f}:S^n\rightarrow \R $ . $\R $ 是可缩的,所以 $\tilde{f} $ 零伦.那么 $f=p\circ \tilde{f} $ 也是零伦的.也就是说 $\pi_n(S^1)=\Set{e} $ .





{{% mathbox type="blue" title="基本群与终点群" %}}
$p:\tilde{X}\rightarrow X $ 为一个覆叠映射, $\tilde{x}_0\in \tilde{X} $ 且 $x_0=p(\tilde{x}_0) $ .定义一个提升对应:
$$
  \alpha:\pi_1(X,x_0)\rightarrow p^{-1}(x_0)
  \\
  \alpha([\gamma]_p):=\tilde{\gamma}(1)\in p^{-1}(x_0)
$$
其中 $\tilde{\gamma} $ 是 $\gamma $ 满足 $\gamma(0)=\tilde{x}_0 $ 的唯一提升.那么
1.  $\alpha:\pi_1(X,x_0)\rightarrow p^{-1}(x_0) $ 是良定的.
2.  若 $\tilde{X} $ 是道路连通的,那么 $\alpha $ 是满射.
3.  若 $\tilde{X} $ 是单连通的,那么 $\alpha $ 是双射.
{{% /mathbox %}}
> 注意在 $X $ 中的loop,在其覆叠空间中不一定再是一个loop,可能只是一个path.如在 $\R\rightarrow S^1 $ 中.这个证明也可以用该例子直观想象.
>
> 另外,这里关于 $\alpha $ 的满射有点微妙.可以想象两个分离的“弹簧”分别为 $\R_{up} $ 和 $\R_{down} $ ,其覆叠映射规则都和前一样,这两个 $\R $ 的并显然不是道路连通的,所以选定 $\tilde{x}_0 $ 在其中一个 $\R $ 后, $\alpha $ 只能映射到这个 $\R $ ,从而不是满的.

证明:





#### 万有覆叠空间

{{% mathbox type="green" title="万有覆叠空间" %}}
若 $\tilde{X} $ 为 $X $ 的一个覆叠空间,且 $\tilde{X} $ 是单连通的,那么称之为 $X $ 的万有覆叠空间.
{{% /mathbox %}}

{{% mathbox type="blue" title="群作用与基本群的群结构" %}}
设 $G $ 在 $\tilde{X} $ 上的作用是纯不连续的,从而 $p:\tilde{X}\rightarrow X=\tilde{X}\setminus G$  是覆叠映射,那么
1. 对于任意的 $x_0\in X $ 以及 $\tilde{x_0}\in p^{-1}(x_0) $ ,存在一个群同态
$$
  \beta:\pi_1(X,x_0)\rightarrow G
$$
2.  若 $\tilde{X} $ 是道路连通的,那么 $\beta $ 是满射.
3.  若 $\tilde{X} $ 是单连通的,那么 $\beta $ 是双射.
{{% /mathbox %}}

证明:

由于 $G $ 是纯不连续的,那么对于 $p^{-1}(x_0) $ 中的各个点,可以用 $G $ 中的元素将其联系起来,即对于任意的 $\tilde{x}_1\in p^{-1}(x_0) $ ,存在 $g\in G $ 使得 $\tilde{x}_1 =g\cdot \tilde{x}_0$ .定义
$$
  \rho: p^{-1}(x_0)\rightarrow G,\tilde{x}_1\mapsto g
$$
由群作用的定义,这是一个双射.那么
$$
  \beta:\rho\circ\alpha:\pi_1(X,x_0)\rightarrow G
  \\
  [\gamma]\xmapsto{\alpha}\tilde{\gamma}(1)=\tilde{x}_1\xmapsto{\rho}g
$$
由于 $\rho $ 是一个群同构,所以由前面 $\alpha $ 的性质就可以得到2.3.性质.

下面证明 $\beta $ 是一个群同态.考虑两个基本群中元素的代表元 $\gamma_1,\gamma_2 $ ,分别有唯一的提升为 $\tilde{\gamma}_1,\tilde{\gamma}_2 $ ,令
$$
  g_1=\beta([\gamma_1]_p),g_2=\beta([\gamma_2]_p)
  \\
  g_1\cdot\tilde{x}_0=\tilde{\gamma}_1(1),g_2\cdot\tilde{x}_0=\tilde{\gamma}_2(1)
$$
那么 $g_1\cdot\tilde{\gamma}_2 $ 是从 $g_1\cdot \tilde{x}_0=\tilde{\gamma}_1(1) $  到 $g_1\cdot \tilde{\gamma_2}(1)=g_1g_2\cdot \tilde{x}_0 $ 的一条道路.由道路提升的唯一性可知
$$
  \widetilde{\gamma_1*\gamma_2}=\tilde{\gamma}_1*(g_1\cdot\tilde{\gamma}_2)
$$
所以 
$$
\widetilde{\gamma_1*\gamma_2}(1)=\tilde{\gamma}_1*(g_1\cdot\tilde{\gamma}_2)(1)=g_1\cdot \tilde{\gamma}_2(1)=g_1g_2\cdot \tilde{x}_0
$$
即
$$
  \beta([\gamma_1]_p,[\gamma_2]_p)=\beta([\gamma_1*\gamma_2]_p)
  =\rho((\widetilde{\gamma_1*\gamma_2})(1))=g_1g_2=\beta([\gamma_1]_p)\beta([\gamma_2]_p)
$$
于是完成了证明.


由此可得,因为 $\mathbb{RP}^{2} =S^2\setminus \mathbb{Z}_2 $ ,所以 $\pi_1(\mathbb{RP}^{2} )=\mathbb{Z}_2 $ .进一步,考虑 $f:\mathbb{RP}^{2}\rightarrow S^1  $ .由于没有从 $\mathbb{Z}_2\rightarrow \mathbb{Z} $ 的非平凡群同态 $f $ ,所以 $Im(f_*)=\Set{e} $ ,将 $f $ 提升为 $\tilde{f}:S^n\rightarrow \R $ . $\R $ 可缩可得 $\tilde{f} $ 零伦,于是 $f=p\circ \tilde{f} $ 也是零伦.



### 3.8 覆叠空间的分类
由上一节,已经得到了: 当 $\tilde{X} $ 单连通,也就是 $\tilde{X} $ 作为 $X $ 的万有覆叠时,有一个 $X $ 的基本群到  $G $ 群的同构.但若考虑较小的一个覆盖呢?考虑到前面的结论: $p_*:\pi_1(\tilde{X},\tilde x_0)\rightarrow \pi_1(X,{x}_0) $ 是单同态,也就是说有 $\pi_1(X,{x}_0) $ 的子群 $p_*(\pi_1(X,{x}_0)) $ 同构于 $\pi_1(\tilde{X},\tilde{x}_0) $ .前面两个结果暗示: 存在 $X $ 的基本群到 $X $ 的覆叠空间之间的一一对应,而且该对应是反序的,因为最小的子群 $\Set{e} $ 所对应的是“最大的”万有覆叠空间.

> 虽然这里的“最大”来得有点突然,在后面会给出解释.但这里可以先考虑,结合前一节最后的命题,若 $\tilde{X} $ 不是万有覆叠,那么就没有一个同构,而只是一个从基本群到 $G $ 的同态.这就暗示了越小的子群对应的是越大的覆叠空间.

对于给定的拓扑空间 $X $ ,若已经有了万有覆叠空间,那么对于任意的 $x\in X $ ,存在其开邻域 $U $ 同胚于 $\tilde{X} $ 中的一个开集 $\tilde{U} $ ,即
$$
  p|_{\tilde{U}}:\tilde{U}\rightarrow U 
$$
是一个同胚.那么 $U $ 中的任意一个 loop 都能被提升到 $\tilde{U} $ 中的一个 loop  $\tilde{\gamma} $ .由于是万有覆叠,其基本群平凡,所以 $\tilde{\gamma} $ 是零伦的,复合上投影映射,即有 $\gamma $ 是零伦的.于是就得到了存在万有覆叠的必要条件: 对于任意的 $x $ ,存在其一个邻域 $U $ 使得 $U $ 中任意的圈在 $X $ 中都是零伦的.(注意只要求在 $X $ 中而不要求在 $U $ 中)换句话说,对于包含映射 $i:U\rightarrow X $ 所诱导的 $i_*:\pi_1(U,x)\rightarrow \pi_1(X,x) $ 是平凡同态,即 $i_*(\pi_1(U,x))=\Set{e} $ .称满足该条件的拓扑空间为**半局部单连通空间**.

> 直观上来说,也就是 $X $ 中不能有任意小的洞.
>
> 由于并没有要求 $U $ 中任意的圈在 $U $ 中单连通,所称之为半局部单连通.

{{% mathbox type="blue" title="万有覆叠空间的存在性" %}}
若 $X $ 是道路连通且是局部道路连通的,那么 $X $ 存在万有覆叠 $\tilde{X} $  $\iff $  $X $ 是半局部单连通的.
{{% /mathbox %}}
称 $U $ 是 $X $ 中的基本开集,如果 $U $ 是 $X $ 中道路连通开集,且 $i_*(\pi_1(U,x))=\Set{e} $ .

证明概要:
1. 构造 $\tilde{X}=\Set{[\gamma]_p} $ ,其中 $\gamma $ 是以 $x_0 $ 为起点的一条 $X $ 中的道路.投影映射 $p:\tilde{X}\rightarrow X $ , $[\gamma]_p\mapsto \gamma(1) $ ,因为 $X $ 道路连通,所以 $p $ 是满射.
2. 👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷 


{{% mathbox type="blue" title="一般覆叠空间的存在性" %}}
设 $X $ 是道路连通,局部道路连通且半局部单连通空间.则对于 $\pi_1(X,x_0) $ 的任意子群 $H $ ,存在 $X $ 的覆叠空间 $p:\tilde{X}_H\rightarrow X $ 和基点 $\tilde{x}_0\in p^{-1}(x_0) $ 使得
$$
  p_*(\pi_1(\tilde{X},\tilde{x}_0))=H
$$
{{% /mathbox %}}
证明:👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷

有了子群 $H\subset \pi_1(X,x_0) $ 与 $X $ 的覆叠空间之间对应的存在性之后,考虑其唯一性.考虑 $X $ 的两个覆叠空间 $p_1:\tilde{X}_1\rightarrow X $和 $p_2:\tilde{X}_2\rightarrow X $  ,若存在一个同胚 $h:\tilde{X}_1 \rightarrow \tilde{X}_2$ 使得
$$
  p_1=p_2\circ h
$$
则称这两个覆叠空间是同构的, $h $ 为一个**覆叠空间同构**.
(交换图)👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷

实际上,上面的同构是一族同构,因为对于基本群总是要带上基点考虑.考虑 $h:\tilde{X}_1\rightarrow \tilde{X}_2 $ 为 $X $ 覆叠空间的同构,那么对于任意的 $x_0\in X $ , $h $ 是从 $p^{-1}_1(x_0) $ 到 $p^{-1}_2(x_0) $ 之间的一一映射.分别取其中的 $\tilde{x}_1,\tilde{x}_2 $ ,其中 $\tilde{x}_2=h(\tilde{x}_1) $  ,有

(交换图)👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷👷

即 $p_2\circ h=p_1,p_1\circ h^{-1}=p_2 $ ,由 $\pi_1 $ 的函子性,有
$$
  (p_1)_*(\pi_1(\tilde{X}_1,\tilde{x}_1))=(p_2)_*(\pi_1(\tilde{X}_2,\tilde{x}_2))
$$
于是得到了关于 $X $ 的两个不同的覆叠空间同构的必要条件: 同构的覆叠空间对于 $\pi_1(X,x_0) $ 中相同的子群.加上一定条件后,就得到了覆叠空间与基本群的子群对应的唯一性:
{{% mathbox type="blue" title="覆叠空间的唯一性" %}}
设 $X $ 是道路连通且局部道路连通的拓扑空间,那么 $X $ 的两个道路连通的覆叠空间 $p_1:(\tilde{X}_1,\tilde{x}_1)\rightarrow (X,x_0) $ 和 $p_1:(\tilde{X}_2,\tilde{x}_2)\rightarrow (X,x_0) $ 之间存在保基点的覆叠空间同构 $h:(\tilde{X}_1,\tilde{x}_1)\rightarrow (\tilde{X}_2,\tilde{x}_2) $  $\iff $ 
$$
  (p_1)_*(\pi_1(\tilde{X}_1,\tilde{x}_1))=(p_2)_*(\pi_1(\tilde{X}_2,\tilde{x}_2))
$$
特别地,如果 $X $ 还是半局部单连通的,那么 $X $ 的万有覆叠空间在同构的意义下唯一.
{{% /mathbox %}}
证明: 必要性已经得到证明.对于充分性:存在
$$
  (p_1)_*(\pi_1(\tilde{X}_1,\tilde{x}_1))=(p_2)_*(\pi_1(\tilde{X}_2,\tilde{x}_2))
$$
即两个覆叠空间相互满足提升存在性条件,那么可以分别提升 $p_1,p_2 $ :
$$
  \tilde{p}_1:(\tilde{X}_1,\tilde{x}_1)\rightarrow (\tilde{X}_2,\tilde{x}_2)
  \\
  \tilde{p}_2:(\tilde{X}_2,\tilde{x}_2)\rightarrow (\tilde{X}_1,\tilde{x}_1)
$$
有
$$
  p_1=p_2\circ \tilde{p}_1\\
  p_2=p_1\circ \tilde{p}_2
$$
由提升的唯一性,可得 $\tilde{p}_1\circ \tilde{p}_2=Id_{\tilde{X}_2},\tilde{p}_2\circ \tilde{p}_1=Id_{\tilde{X}_1}$ .即可知 $\tilde{p}_1 $ 就是两个覆叠空间之间的同构.

于是根据子群之间的关系,就可以得到
{{% mathbox type="blue" title="带基点覆叠空间的分类定理" %}}
对于道路连通,局部道路连通且半局部单连通的拓扑空间 $X $ ,由
$$
  (\tilde{X},\tilde{x}_0) \longleftrightarrow p_*(\pi_1((\tilde{X},\tilde{x}_0)))
$$
之间的对应关系,可以得到
$$
  \set{\small{\text{道路连通覆叠空间}}p:(\tilde{X},\tilde{x}_0)\rightarrow (X_0,x_0)\small{\text{在保基点同构下的同构类}}}
$$
与
$$
  \Set{\pi_1(X,x_0)\small{\text{的子群}}}
$$
之间的一个一一对应,且反序.即若
$$
  (p_1)_*(\pi_1(\tilde{X}_1,\tilde{x}_1))\subset (p_2)_*(\pi_1(\tilde{X}_2,\tilde{x}_2))
$$
当且仅当存在一个覆叠映射 $p_3:(\tilde{X}_1,\tilde{x}_1)\rightarrow (\tilde{X}_2,\tilde{x}_2) $ 使得 $p_1=p_2\circ p_3 $ .
{{% /mathbox %}}
若忽略基点,那么有 
{{% mathbox type="blue" title="覆叠空间的分类定理" %}}
对于道路连通,局部道路连通且半局部单连通的拓扑空间 $X $ 
$$
  \set{\small{\text{道路连通覆叠空间}}p:\tilde{X}\rightarrow X_0\small{\text{的同构类}}}
$$
和
$$
  \Set{\pi_1(X,x_0)\small{\text{的子群的共轭类}}}
$$
之间存在一一对应.
{{% /mathbox %}}


于是终于知道了为什么万有覆叠空间是“万有的”,因为其基本群为 $\Set{e} $ ,即 $p_*(\pi_1(\hat{X},\hat{x}))=\Set{e} $ ,对于 $X $ 的基本群的任一其他子群, $\Set{e} $ 当然是该子群的子群,即 $\hat{X} $ 总是 $X $ 其他覆叠空间的覆叠空间.


下面给出一些应用覆叠空间的例子:

1. 判断 $\mathbb{RP}^2 $ 是否为 Klein bottle 的覆叠空间?反之呢?
   两个空间具有覆叠关系,说明其具有同胚的万有覆叠空间.注意到 $\mathbb{RP}^2 $ 的万有覆叠空间为 $S^2 $ ,而 Klein bottle 的万有覆叠为 $\R^2 $ ,显然不是同胚的.所以其相互之间都不为覆叠空间.

   另外还可以通过其基本群进行判断, 
   $$
     \pi_1(KB)=\langle a,b|ab^{-1}a^{-1}b^{-1}=1 \rangle,\pi_1(\mathbb{RP}^2)=\mathbb{Z}_2
   $$
    无限群不可能嵌入到有限群中,所以 Klein  不可能覆叠 $\mathbb{RP}^2 $ .另一方面, $\pi_1(KB) $ 没有 $\mathbb{Z}_2 $ 子群,所以反之也不成立.

    那么  $\pi_1(KB) $ 是什么?
    * 不妨先考虑其二重覆叠空间,即 $\pi_1(\tilde{X})\setminus \mathbb{Z}_2\cong \pi_1(KB) $ :显然对于自由群 $\langle a,b|baba^{-1}=1 \rangle  $ 到 $\mathbb{Z} $ 的非平凡同态的选择有三种: 
      * $\phi(a)=0,\phi(b)=1 $ , $a,b^2 \in ker(\phi) $ ,令 $x=a,y=b $ ,可得新的约束关系为 $xy=yx $ ,即所得到的是 $\langle a,b \rangle  \cong \mathbb{Z}\times\mathbb{Z}   $ ,即该情况下的2覆叠空间为环面 $T^2 $ .
      *  $\phi(a)=1,\phi(b)=0 $
      *  $\phi(a)=1,\phi(b)=1 $ 
  
> 为什么属于 Ker 才能成为生成元?可见前面 群作用与基本群的群结构 .只有当 $\beta $ 将其映到Ker中,才对应到 $p^{-1}(x_0) $ 中的同一点,也才可以将底空间 $X $ 中的圈映到 $\tilde{X} $ 中的圈,否则为 path 根本就不在 $\pi_1(\tilde{X}) $ 中.

2. 寻找对于所有覆叠空间 $\iff $ 寻找基本群的子群
  * 例如对于 $\mathbb{RP}^{n} \times \mathbb{RP}^{m}  $ ,有
   $$
     \pi_1(\mathbb{RP}^{n} \times \mathbb{RP}^{m} )\cong Z_2\oplus Z_2=\set{e,a}\oplus \set{e,b}
   $$
   所以有子群为
   $$
     \set{e},\set{e,a},\set{e,b},\set{e,ab},\set{e,a,b,ab}
   $$
   分别对应覆叠空间为
   $$
     S^n\times S^m,\mathbb{RP}^{n} \times S^m,S^n \times \mathbb{RP}^{m} ,
     \\
     S^n\times S^m\setminus (v,w)\sim (-v,-w),\mathbb{RP}^{n} \times \mathbb{RP}^{m}
   $$
  * 又如对于 $S^1\vee S^1 $ ,有
  $$
    \pi_1(S^1\vee S^1)=\langle a,b \rangle 
  $$
  
  * 还如对于 $T^2 $ 

3. 对于任意的拓扑群,都有一个万有覆叠.另外对于拓扑群的任意覆叠空间仍是一个覆叠空间.
  
   
   






___
___
___
___
___
___
___