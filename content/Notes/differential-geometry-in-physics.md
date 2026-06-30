---
title : "topology and differetial geometry in physics"
description : "Note on lecture"
weight : 1
ShowToc : true
TocOpen : true 
---

> 原本以为是很严谨的，没想到是和物理系中其他课一样的草率。不过如果视作motivation去进一步学习，那便是极佳的。



### 流形概述

见[微分流形杂谈]({{< ref "/Notes/微分流形杂谈.md" >}}).


### 辛几何在经典力学中的应用(入门)

待施工


### 同调群与 de Rham 理论

一些基础的内容在另一个Note中可以看到，所必须的是关于[微分形式]({{< ref "Notes/微分流形杂谈.md#differetial_form" >}})的部分。

#### 0.一些Preliminaries和符号规定

* 外微分的幂零性:$d^2=0$。其证明是很显然的，考虑到$d^2\omega=\frac{\partial^2\omega}{\partial x^i\partial x^j}dx^i\wedge dx^j\wedge dx^{\mu_1}\dots\wedge dx^{\mu_k}$中偏导数是对称而楔积是反对称的，所以为0.
* 称$\omega$为闭形式，如果$d\omega=0$.
* 称$\omega$为恰当形式，如果存在$\alpha$使得$\omega=d\alpha$.
* 

#### 1.基础概念

设$0\le r\le m,p_0,p_1,\dots p_r$是$\mathbb{R}^{r+1}$中r+1个几何独立的点，所谓的几何独立是指他们不全都位于任何一个(r-1)维的超平面上。那么称
$$
  \{x\in\mathbb{R}^m|x=\sum_{i=0}^{r}c_ip_i,c_i\ge0,\sum_{i=0}^r c_r=0 \}
$$
为一个r-单纯形，记作$\sigma=<p_0p_1\dots p_r>$.

例如，$\sigma^0=<p_0>$就是一个单点$p_0$.同理,$\sigma^1,\sigma^2,\sigma^3$就分别是线段，三角形和四面体。

在$\sigma^r$中任取q+1个点构成$\sigma^q$，称之为$\sigma^r$的一个q-面.且若$\sigma^q\ne\sigma^r$，则称之为$\sigma^r$的一个真面，记作$\sigma^q<\sigma^r$.

$K$是$\mathbb{R}^m$中有限多个单形的集合，$K$是一个单纯复形，如果
* 对于K中的任意单形$\sigma$,$\sigma'<\sigma\Rightarrow\sigma'\in K$
* 对于K中有交的单形$\sigma,\sigma'$，其交$\sigma\cap\sigma'$为$\sigma,\sigma'$的公共边，即$\sigma\cap\sigma'<\sigma,\sigma\cap\sigma'<\sigma'$.

复形K的全体单形的全体点构成点空间$｜K｜\subset \mathbb{R}^m$成为一个多面体，而K为该多面体的一个单纯剖分，或称之为三角剖分，剖分。注意多面体允许有不同的三角剖分。

> 剖分是很重要的，它将一个复杂（或者说研究起来很复杂）的几何对象简化成了许多个三角形，而显然这个剖分是与所研究的对象同胚的。于是总是可以利用一些同胚不变量对该几何对象进行研究，这就是代数拓扑的意义。

定向的单形，$r\ge1$的单形总是可以引入两种不同的定向，如
$$
  \begin{align*}
    \sigma^1&=(p_0p_1)=-(p_1p_0)
    \\
    \sigma^2&=(p_0p_1p_2)=(p_1p_2p_3)=\dots=-(p_1p_0p_3)=\dots
  \end{align*}
$$

如果复形K有$I_r$个r定向单形$\sigma^r_i,1\le i\le I_r$,定义复形的一个r-链为
$$
  c_r=\sum_{i=1}^{I_r}n_i\sigma_i^r,n_i\in \mathbb{Z}
$$
显然K中所有的r-链$c_r$构成一个群$C_r(K)$，称之为链群，且有$C_r(K)\simeq\mathbb{Z}\oplus\mathbb{Z}\oplus\dots\oplus\mathbb{Z}$.

再定义边缘算子$\partial_r:C_r(K)\rightarrow C_{r-1}(K)$为:
$$
  \partial_r(p_0p_1\dots p_r)=\sum_{i=0}^r(-1)^i(p_0\dots \hat p_i\dots p_r)
$$
如$\partial_0p_0=0,\partial_1(p_0p_1)=p_1-p_0,\partial_2(p_0p_1p_2)=(p_1p_2)-(p_0p_2)+(p_0p_1)$.

于是可以构造一个链复形:
$$
  0\hookrightarrow C_n(K) \xrightarrow{\partial_n}C_{n-1}(K)\xrightarrow{\partial_{n-1}}\dots\xrightarrow{\partial_1}C_1(K)\xrightarrow{\partial_1}C_0(K)\xrightarrow{\partial_0}0
$$
对于满足$\partial_rc=0$的$c$，其全体构成$C_r(K)$的子群$Z_r(K)$，称为r-闭链，显然有$C_0(K)=Z_0(K)$.对于满足$c=\partial_{r+1}c',c'\in C_{r+1}(K)$的全体，同样构成子群$B_r(K)$,显然对于最高维的$m=dimK,B_m(K)=\emptyset$.

可以计算得到，边缘算子同样具有幂零性$\partial^2=\partial_r\partial_{r+1}=0$，也就是说“边缘的边缘为0”。

有了这些基础，就可以引入同调群。

#### 2.同调群








流形 $M$ 上，  $r$-阶闭形式的全体组成了$Ker(d_r)$，而r阶恰当形式的全体为$Im(d_{r-1})$.于是外微分的幂零性就等价于$Im(d_{r-1})\subset Ker(d_r)$.这是一个很好性质

### HOMOTOPY GROUPS

引入一种新的等价关系,考虑 $\mathcal{F} $ 是从拓扑空间 $X $ 到拓扑空间 $Y $ 的连续映射集,对于 $f,g\in \mathcal{F} $ ,若在 $Y $ 中 $f(X) $ 可以连续形变到 $g(X) $ ,那么称 $f $ 同伦于 $g $ .其中连续形变是指连续映射
$$
  \mathcal{F}:I\times X\rightarrow Y
$$
其中 $I=[0,1] $ .有 $\mathcal{F}(0,x)=f(x),\mathcal{F}(1,x)=g(x) $ .

若在拓扑空间 $X,Y $ 之间存在连续映射 $f:X\rightarrow Y,g:Y\rightarrow X $ 使得
$$
  f\circ g=Id_Y,g\circ f=Id_X
$$
那么称空间 $X,Y $ 是同伦等价的,并称 $f,g $ 为其之间的同伦等价.

#### 映射空间与同伦群
在拓扑空间 $\Sigma,X $ 中分别取定**基点** $\sigma_0\in\Sigma,x_0\in X $ ,考虑所有保持基点的映射 $f:\Sigma\rightarrow X $ ,即 $f(\sigma_0)=x_0 $ ,所有的保持基点的连续映射构成一个映射空间 $X^\Sigma=\{f|f:\Sigma\rightarrow X,f(\sigma_0)=x_0 \} $ .
{{% mathbox type="slate" title="例子" %}}
* 显然 $X^{\{1\}}={f_0} $ 是一个单点集,由单个映射 $f_0(1)=x_0 $ 所构成.
* 对于 $S^0=\{ \pm 1  \} \rightarrow X $ 的 $X^{\{ S^0 \} } $ ,基点为 $f(1)=x_0 $ ,所以 $f $ 完全由 $f(-1) $ 所确定, $\forall f\in X^{ S^0  },f\xLeftrightarrow{1:1}f(-1)\in X $,也就是说 $X^{ S^0 }\simeq X $.  
* 显然,对于离散的多点集 $\Sigma=\{ \sigma_0,\sigma_1,\dots,\sigma_n \}  $ 到 $X $ 所构成的 $X^{\left\{ \Sigma \right\} } $ 有
$$
  X^{\left\{ \Sigma \right\} }\cong \underbrace{X \times \dots \times X}_n
$$

{{% /mathbox %}}

{{% mathbox type="green" title="约定" %}}
 $\cong $ 表同胚, $\simeq $ 表同伦, $\sim $ 是同调或者一般的等价关系.
{{% /mathbox %}}

> 似乎与另一个Note中的符号不一致( )

由此可以定义所谓的**道路空间**和**圈空间**: $X^{[0,1]},X^{S^1} $:
$$
  X^{[0,1]}=\left\{ f|f(t)\in X;f(0)=x_0 \right\} 
  \\
  X^{S^1}=\left\{ f|f(t)\in X;f(0)=f(1)=x_0 \right\} 
$$
另外,保基映射 $f:\Sigma_2\rightarrow \Sigma_1,g:X_1\rightarrow X_2 $  诱导了   $g^f:X_1^{\Sigma_1}\rightarrow X_2^{\Sigma_2} $ ,其中 $g^f(h)=g\circ h\circ f ,\forall h\in X_1^{\Sigma_1}$ 
>  $\Sigma_2\xrightarrow{f}\Sigma_1\xrightarrow{h}X_1\xrightarrow{g}X_2 $

{{% mathbox type="blue" title=" $g^f $ 的结合性" %}}
具有某种结合性,也就说,对于另外两个保基映射 $f':\Sigma_3\rightarrow \Sigma_2,g':X_2\rightarrow X_3 $ ,那么
$$
  {g'}^{f'}\circ g^f=(g'\circ g)^{f\circ f'}:X_1^{\Sigma_1}\rightarrow X_3^{\Sigma_3}
$$
根据连续函数的复合的结合律可以很容易得到.实际上,也就是将
$$
  \Sigma_2\xrightarrow{f}\Sigma_1\xrightarrow{h}X_1\xrightarrow{g}X_2 
$$
增长到了
$$
  \Sigma_3\xrightarrow{f'}
  \Sigma_2\xrightarrow{f}\Sigma_1\xrightarrow{h}X_1\xrightarrow{g}X_2 
  \xrightarrow{g'}X_3 
$$
{{% /mathbox %}}

> 注意上指标中 $f,f' $ 的反结合.

根据该性质, 设 $f_t,g_t $ 分别是两个伦移,那么 $H(\cdot,t)={g_t}^{f_t}:X_1^{\Sigma_1}\rightarrow X_2^{\Sigma_2} $ 就给出了从 $g_0^{f_0} $ 到 $g_1^{f_1} $ 的伦移,因为连续函数的复合还是连续函数.

{{% mathbox type="blue" title="同伦复合" %}}
若 $\Sigma_1\simeq\Sigma_2,X_1\simeq X_2 $ ,那么 $X_1^{\Sigma_1}\simeq X_2^{\Sigma_2} $ 


{{% /mathbox %}}

根据同伦的定义,存在一些复合为 $\mathbb{1} $的函数,再结合上命题就很容易证明. 

推论: 道路空间总是可缩的,即 $X^{[0,1]} \simeq X^{\left\{ 1 \right\} }\simeq \left\{ f_0 \right\}  $ .这在直观上也是很显然的: 在任何空间中,一条道路总是能沿着自身缩到一点.

{{% mathbox type="blue" title="楔和点函子性" %}}
给定拓扑空间 $X_j,Y_j $ 及连续保基映射 $f_j:X_j\rightarrow Y_j $ ,存在 $\vee_{i}f_j:\vee_j X_j\rightarrow \vee_j Y_j $,具有如下性质
* 若 $g_j:Y_j\rightarrow Z_j $ 是连续保基映射,那么
$$
  \left(\bigvee_j g_j\right )\circ \left(\bigvee_j f_j\right )=\bigvee_j (g_j\circ f_j)
$$
* 若 $f_j\simeq g_j:X_j\rightarrow Y_j  $  是同伦等价的映射,那么
$$
  \bigvee_j f_j\simeq \bigvee_j g_j:\bigvee_j X_j\rightarrow \bigvee_j Y_j
$$
{{% /mathbox %}}
> 直观上,可以将 $\bigvee_j X_j $ 理解成一朵花🌸,不同的 $X_j $ 就是各个花瓣,对其做楔和也就是将其粘到一起,只在中心一点相交. $f_j $ 的保基性使得其基点只能取为花的中心(也即交点 $x_0,y_0 $ ),否则会导致函数多值.这样的视角下,后面两个性质就几乎是显然的了. 

具体的证明: 给出显式的表达, $F=\bigvee f_j:\bigvee X_j\rightarrow \bigvee Y_j $ 自然地定义为
$$
  F([x])=\left( \bigvee _j f_j \right) ([x])=[f_k(x)],x\in X_k,k\in J
$$

可以证明该定义的良定性,即与 $[x] $ 的代表元选取无关,实际上楔和中所诱导的等价类也只有两种,即交点和非交点(花蕊与花瓣):
* 对于各个交点 $x=\mathring{x_k} $ ,选择任意的 $\mathring{x}_j,j\in J $ ,其都被 $F $ 映射到 $\bigvee_j  Y_j $ 中的交点处,所以与代表元选取无关.实际上,由于每个花瓣空间中的保基映射都是确定一个基点的,所以 $\bigvee _jX_j $ 空间各 $X_j $ 只能在同一点楔和,否则会导致函数多值.
* 对于 $x\in X_k/\left\{ \mathring{x}_k \right\}  $ ,显然等价类 $[x]=\left\{ x \right\}  $ 只有一个元素,自然良定.

那么,令 $G=\bigvee g_j:\bigvee Y_j\rightarrow \bigvee Z_j $ ,当 $x\in X_k $ , $f_k(x)\in Y_k $ 时,有
$$
  G\circ F([x])=G([f_k(x)])=[g_k\circ f_k(x)]
  \\
  =\left( \bigvee(g_j\circ f_j) \right) ([x])
$$
于是我们证明了第一个性质.对于第二条: 设 $f_j\simeq g_j $ ,有伦移
$$
  H_j:X_j\times [0,1]\rightarrow Y_j
$$
定义
$$
  H(\cdot,t)=\bigvee_j H_j(\cdot,t):\bigvee_j X_j\rightarrow \bigvee_j Y_j
$$
提供了 $\bigvee f_j $ 到 $\bigvee g_j $ 的伦移,自然就是第二条结论. $\Box $ 

由上命题,可以得到一个推论:若 $X_j\simeq Y_j,\forall j\in J $ ,则 $\bigvee X_j \simeq \bigvee Y_j $.由同伦的定义和上命题第一条任意证明.于是,若 $Y\simeq \left\{ \mathring{y} \right\}  $是可缩空间,那么 $X\vee Y\simeq X\vee \left\{ \mathring{y} \right\} \cong X $ .

> 在直观上也是显然的,楔和是一点并,所以一个可缩的空间楔和上任意一个空间并不改变该空间作为子空间的可缩性.

完全同理地,可以得到 smash product 的相关同伦性质.

先简单回顾 smash product 的定义
$$
  X\wedge Y:=(X\times Y)/(X\vee Y)
$$
例如:
* 对于单点集 $\left\{ \mathring{y} \right\}  $ 和以 $\mathring{x} $ 为基点的空间 $X$ ,前面已经知道了
$$
  X\vee \left\{ \mathring{y} \right\}\cong \left( X\times \left\{ \mathring{y} \right\} \right) \cup \left( \left\{ \mathring{x} \right\} \times \left\{ \mathring{y} \right\}\right) 
  \\
  =X\times \left\{ \mathring{y} \right\}
$$
于是
$$
  X\wedge\left\{ \mathring{y} \right\}=(X\times \left\{ \mathring{y} \right\})/(X\vee \left\{ \mathring{y} \right\})
  \\
  \cong (X\times \left\{ \mathring{y} \right\})/(X\times \left\{ \mathring{y} \right\})
  \\
  =\left\{ \mathring{x} \right\}\times\left\{ \mathring{y} \right\}=\left\{ (\mathring{x}, \mathring{y}) \right\}
$$
也就是说 $X\wedge\left\{ \mathring{y} \right\} $ 同胚于一个单点集.

* 对于 $X\wedge S^0=X\wedge \left\{ \pm 1 \right\}  $ ,可以类似处理.不妨选取 $x_0,+1 $ 为基点,那么
$$
  X\vee S^0=(X\times \left\{ + 1 \right\} )\cup (\left\{ \mathring{x}\times S^0 \right\} )
$$
于是
$$
  \begin{align*}
    X\wedge S^0&=(X\times S^0)/(X\vee S^0)
    \\ &=X\times \left\{ -1 \right\} \cong X
  \end{align*}
$$
> 这里最后一步的商细节如下:
>
> 首先考虑 
$$
  X\times S^0=(X\times \left\{ +1 \right\} )\cup (X\times \left\{ -1 \right\} ) =X_{top} \cup X_{down}
$$
> 于是 $(X\times S^0)/(X\times\left\{  +1 \right\} )\cong (\left\{ \mathring{x} \right\} \times \left\{ +1 \right\} )\cup (X\times \left\{ -1 \right\} ) $ .
> 再模去 $\left\{ \mathring{x} \right\} \times \left\{ \pm 1 \right\}  $ 也就是得到
$$
  (\left\{ \mathring{x} \right\} \times \left\{ +1 \right\} )\cup (X_{down}/\left\{ (\mathring{x},-1) \right\}  )\cong X_{down}
$$

可知在 Smash Product 中, $S^0 $ 是类似单位元的东西.

*  $X\wedge S^1 $ :(图解法)
  
    可以想象类似 $T^2 $ 的东西,
    ![picsol1](/images/Topology/picsol1.pdf)
    应用图解法可以得到 $X\wedge S^1 $ 得到的是 $X $ 作为赤道面所旋转出来的“实心球”. 对于 $S^m\wedge S^1=S^{m+1} $ 的更直观解释来自于 Nakahara:
    ![$S^m\wedge S^1= S^{m+1}$](/images/Topology/Smashproduct1.pdf)
    (图中ai画的有点小问题)

> 粗略来说,可以将 $X_1\times X_2 $ 视为一种丛, $(X_1\times X_2)/(X_1\wedge X_2) $ 就是这个丛模去底空间和一根 fiber ,于是就得到了一个蝉蛹状的东东.
> ![蝉蛹](/images/Topology/Smashproduct2.pdf)
> 
> 也就是同胚于一点用 $X_1 $ 沿 $X_2 $ 绕出来的一个拓扑空间


同理,类似于前面楔和的函子性,有 smash Product 的函子性:
{{% mathbox type="blue" title="smash product 的函子性" %}}
对于 $X_i,Y_i $ , $f_i:X_i\rightarrow Y_i $ 是连续保基的( $i=1,2 $ ).存在
$$
  f_1 \wedge f_2:X_1\wedge X_2\rightarrow Y_1\wedge Y_2
$$
有
1. 若 $g_i:Y_i\rightarrow Z_i ,i=1,2$ ,则
$$
  (f_1\bigwedge f_2)\circ (g_1\bigwedge g_2)=(f_1\circ g_1)\bigwedge (f_2\circ g_2)
$$

2. 若 $f_j\simeq g_j:X_j\rightarrow Y_j $ 是同伦的映射,那么
$$
  f_1\bigwedge f_2\simeq g_1\bigwedge g_2:X_1\bigwedge X_2\rightarrow  Y_1\bigwedge Y_2
$$

{{% /mathbox %}}

证明: 令 $F([x])=(f_1\wedge f_2)([x_1,x_2])=[f_1(x_1),f_2(x_2)] $ .其良定性与前面楔和中的证明同理:
1.  $[x_1,x_2]\in X_1\wedge X_2 $ 只会映到 $(\mathring{x}_1,\mathring{x}_2) $ .
2.  $[x_1,x_2]\notin X_1\wedge X_2 $ 就是映到 $(f_1(x_1),f_2(x_2)) $ .

都与代表元的选取无关.然后构造同伦就可以证明.

{{% mathbox type="blue" title="推论" %}}
1. 若 $X_j\simeq Y_j $ 是同伦等价的,则
$$
  X_1\bigwedge X_2\simeq Y_1\bigwedge Y_2
$$
1. 任意的 $X $ 与可缩的 $Y $ 的 smash product 是可缩的.因为
$$
  X\bigwedge Y\simeq X\bigwedge \Set{\mathring{y}}\simeq \Set{(\mathring{x}, \mathring{y})}
$$

{{% /mathbox %}}

根据上面的第二条推论, $X $ 的约化角锥 $C(X)=X\wedge [0,1] $ 是可缩的.

> 约化角锥同样是很容易通过图像解释的.最后的结果是一个 $X $ 为底面的半实心球体,其相应的半球面由 $\partial X\wedge [0,1] $ 给出.

楔和与 smash product 满足分配律和结合律:
1.  $(X\vee Y)\wedge Z\cong (X\wedge Z)\vee (Y\wedge Z) $ 
2.  $(X\wedge Y)\wedge Z\cong X\wedge (Y\wedge Z ) $ 

> 其中结合律在下面三个条件之一满足时才成立:
> 1.  $X,Y $ compact , and $X $ is  $T_2 $ .
> 2.  $Y,Z $ compact , and $Z $ is  $T_2 $ .
> 3.  $X,Z $ is LCH .

还满足
{{% mathbox type="blue" title="" %}}
1.  若$X,Y $ 为  $T_2 $ 空间,那么
$$
  Z^{X\vee Y}\cong Z^X \times Z^Y
$$

2. 若 $X,Y $ 为紧致的 $T_2 $ 空间,那么
$$
  Z^{X\wedge Y}\cong (Z^Y)^X
$$

3. 若 $X $ 为 $T_2 $ 空间,那么
$$
  (Y\times Z)^X\cong Y^X\times Z^X
$$

所以才称之为楔和和 smash product.
{{% /mathbox %}}

例子:后面考虑的高阶同伦群中所用到的"高阶"圈空间 $X^{S^n} $ 实际上也就是圈空间的圈空间的圈空间的圈空间
$$
  \Omega(\Omega(\dots\Omega(X)))\cong X^{S^1\wedge \dots \wedge S^1}\cong X^{S^n}
$$

考虑 $X^\Sigma $ 中的同伦保基映射 $f,g:\Sigma\rightarrow X $ , $f\simeq g $ ,在 $X^\Sigma $ 中确定了一个等价关系,其同伦等价类 $[f] $ 形成的空间为
$$
  [\Sigma,X]=\Set{[f]:f\in X^\Sigma}=X^\Sigma/\simeq 
$$
于是
{{% mathbox type="green" title="同伦群" %}}
$n $-阶同伦群定义为 $\pi_n(X)=[S^n,X] $ 
{{% /mathbox %}}

连续保基映射 $f:Y_0\rightarrow Y_1 $ 诱导了同伦等价类空间中的映射
$$
  f_\bullet:[X,Y_0]\rightarrow [X,Y_1]
$$
该映射是良好定义的,因为很容易验证, $f_\bullet([h])=[f\circ h] $ 与代表元 $h $ 的选取无关.

{{% mathbox type="blue" title=" $\bullet $ 的函子性" %}}
1. 若 $f\cong f':Y_0\rightarrow Y_1 $ ,那么
$$
  f_\bullet=f_\bullet':[X,Y_0]\rightarrow [X,Y_1]
$$
1.  $Id $ 所诱导的 $Id_\bullet $ 仍是恒等映射.
2.  若 $g:Y_1\rightarrow Y_2 $ ,那么
$$
  (g\circ f)_\bullet=g_\bullet \circ f_\bullet :[X,Y_0]\rightarrow [X,Y_2]
$$

{{% /mathbox %}}

由定义,都是显然的.

> 实际上,这里是更一般的函子.更多用到的是 $\pi_n $ 的函子性,将一个带基点的拓扑空间范畴,对应到一个群范畴.更多可以参见拓扑的笔记.

根据函子性,若 $f:Y_0\rightarrow Y_1 $ 是同伦等价映射,那么所诱导的 $f_\bullet $ 是双射.若 $[X,Y] $ 都是有群结构的空间,那么 $f_\bullet $ 实际上是同构.

> 双射是集合范畴态射中的“同态”.

{{% mathbox type="blue" title="" %}}
若对于一切空间 $X $ , $f_\bullet:[X,Y_0]\rightarrow [X,Y_1] $ 都是双射,那么 $f:Y_0\rightarrow Y_1 $ 是同伦等价映射, $Y_0\simeq Y_1 $ .
{{% /mathbox %}}

证明: 实际上这也是函子性的体现.取 $X=Y_1 $ ,那么存在
$$
  f^{-1}_\bullet:[Y_1,Y_1]\rightarrow [Y_1,Y_0]
$$
还存在 $g:Y_1\rightarrow Y_0 $ ,
$$
  [g] : =f^{-1}_\bullet([1])
$$
即 $f_\bullet([g])=[f\circ g]=[1] $ ,也就是
$$
  f\circ g \simeq 1
$$
同理,取 $X=Y_0 $ 可以得到 $g\circ f\simeq 1 $ .于是完成证明. $\Box $ 

{{% mathbox type="blue" title="Whitehead 定理" %}}
若 $\pi_n(Y_0)\cong \pi_n(Y_n) ,\forall n$ ,那么
$$
  Y_0\simeq Y_1
$$

{{% /mathbox %}}

后面将看到,由于 $S^n $ 是  $AH'I $-空间,所以 $\pi_n(X)=[S^n,X] $ 具有群结构,且在 $n\gt 1 $ 时是交换群.

另外,可以完全同理地建立  $f:X_0\rightarrow X_1 $ 所诱导的$f^\bullet:[X_1,Y]\rightarrow [X_0,Y] $ 的理论:
* $g^\bullet(f)=f\circ g $ 
* 其也具有函子性,不过是一个反变函子.也就是说保映射规则为
$$
  (f\circ g)^\bullet=g^\bullet \circ f^\bullet
$$
 
* 若 $f^\bullet:[X_1,Y]\rightarrow [X_0,Y] $ 对于任何的拓扑空间 $Y $ 都是双射,那么 $f $ 是同伦等价映射 $X_0\simeq X_1 $ .


#### 群结构

设 $Y $ 为一个拓扑空间, $\mathring{y}\in Y $ 为其基点.若存在映射
$$
  m:Y\times Y\rightarrow Y
$$
满足 $m\circ i_1\simeq m\circ i_2 \simeq 1_Y $ ,其中 $i_1,i_2 $ 都是含入映射
$$
  i_1,i_2:Y\rightarrow Y\times Y,i_1(y)=(y,\mathring{y}),i_2(y)=(\mathring{y},y)
$$
于是可以由 $m $ 定义 $Y $ 中两点的乘法,要求基点对应单位元
*  $\forall y,y'\in Y $ , $y\cdot y'=m(y,y')\in Y $ .
*  $y\cdot \mathring{y}=m(y,\mathring{y})\simeq m\circ i_1(y)\simeq 1_Y(y)=y $.
*  $\mathring{y}\cdot y =y $ 同理.

称定义了如此 $m $ 的空间 $Y $ 为 Hopf-空间,下简称 H空间.

进一步,H空间 $Y $ 称为结合的(AH-space),如果有
$$
  m\circ (m\times 1_Y)\simeq m\circ (1_Y\times m):Y\times Y\times Y\rightarrow Y
$$
于是
*  $m\circ(m\times 1_Y)(y_1,y_2,y_3)=m(m(y_1,y_2),y_3)=(y_1\cdot y_2)\cdot y_3 $ 
*  $m\circ(1_Y\times m)(y_1,y_2,y_3)=m(y_1,m(y_2,y_3))=y_1\cdot (y_2\cdot y_3) $ 

由于 $m\circ (m\times 1_y)\simeq m\circ (1_Y\times m)$ ,所以上两式相等,也就是结合律成立.

再进一步,可以定义逆元.先引入一个对角映射
$$
  \Delta_Y:Y\rightarrow Y\times Y,\Delta_Y(y)=(y,y)
$$
若 $Y $ 上存在映射 $u:Y\rightarrow Y $ 使得
$$
  m\circ (u\times 1_Y)\circ \Delta_Y\simeq m\circ(1_Y\times u)\circ \Delta_Y\simeq e_Y
$$
于是称 H空间 $Y $ 是有逆的.因为
$$
  e_Y(m)=m\circ (u\times 1_Y)\circ \Delta_Y(y)=m\circ (u\times 1_Y)(y,y)=u(y)\cdot y
$$
也就是说 $u(y)=y^{-1} $ .同理可以得到右逆也是 $u(y)=y^{-1} $ .

{{% mathbox type="green" title="AHI空间" %}}
一个 AHI空间 就是指结合、可逆的Hopf空间.
{{% /mathbox %}}

{{% mathbox type="blue" title="" %}}
对于任意的拓扑空间 $X $ , AHI空间 $Y $ , $[X,Y] $ 可以赋予一个群结构.
{{% /mathbox %}}
证明: 对于任意的 $f,g\in Y^X $ ,令 $f\cdot g=m\circ (f\times g)\circ \Delta_X \in Y^X $. 由于对于同伦等价的 $f\simeq f',g\simeq g' $ , 有
$$
  m\circ (f\times g)\circ \Delta_X\simeq m\circ (f'\times g')\circ\Delta_X
$$
于是 $[f\cdot g] $ 只依赖于同伦类 $[f],[g] $ ,所以 $[f\cdot g] $ 良定.根据 $Y $ 空间的AHI性质,
* 结合律
$$
  \begin{align*}
    (f\cdot g)\cdot h&=m\circ ((f\cdot g)\times h)\circ \Delta_X
    \\&= m\circ([m\circ (f\times g)\circ \Delta_X]\times h)\circ \Delta_X
    \\&= m\circ(m\times 1_Y)\circ (((f\times g)\circ \Delta_X)\times h)\circ \Delta_X
    \\&= m\circ(m\times 1_Y)\circ (f\times g\times h)\circ \Delta_X
    \\& \simeq m\circ (1_Y\circ m)\circ(f\times g\times h)\circ \Delta_X
    \\& =f\cdot (g\cdot h)
  \end{align*}
$$
其中的 $\Delta_X $ 都是 $x\mapsto (x,x) $ ,但后面可能会出现同一个符号代表 $x\mapsto (x,x) $ 与 $ x\mapsto (x,x,x) $ 的情况.
* 单位元: 可以同理验证,单位元就是恒等映射.
* 逆元:  $[f]^{-1}=[u\circ f] $ .

{{% mathbox type="blue" title="" %}}
设 $Y $ 是一个 AHI空间,任意的映射 $g:X_0\rightarrow X_1 $ 所诱导的
$$
  g^\bullet:[X_1,Y]\rightarrow [X_0,Y]
$$
是群同态.特别地,当 $g $ 是同伦等价, $g^\bullet $ 是群同构.
{{% /mathbox %}}

回顾 $g^\bullet $ , $g^\bullet(f)=f\circ g $ .于是证明是容易的: 对于任意的 $f,f':X_1\rightarrow Y $ 
$$
  \begin{align*}
    g^\bullet(f\cdot f')&=(f\cdot f')\circ g
    \\&=m\circ (f\times f')\circ \Delta_{X_1}\circ g
    \\&=m\circ (f\times f')\circ (g\times g)\circ\Delta_{X_0}
    \\&=m\circ ((f\circ g)\times (f'\circ g))\circ \Delta_{X_0}
    \\&=(f\circ g)\cdot(f'\circ g)
    \\&=g^\bullet(f)\cdot g^\bullet(f')
  \end{align*}
$$

由对偶性,上述的 $X $ 的任意性和 $Y $ 的 AHI性质可以对换,在考虑同伦群 $\pi_n=[S^n,Y] $ 时更方便.将 $X\vee X $ 视为 $X\times X $ 的子集
$$
  (X\times \Set{\mathring{x}})\cup (\Set{\mathring{x}}\times X)
$$
引入投影映射 $p_1,p_2 $ 和折叠
$$
  \nabla_X:X\vee X\rightarrow X,\nabla_X(x,\mathring{x})=\nabla_X(\mathring{x},x)=x
$$
可以同前定义 AH'I空间.

若在拓扑空间上存在 $\mu:X\rightarrow X\times X $ 满足
$$
  p_1\circ \mu\simeq \mu\circ p_2\simeq 1_X
$$
则称之为 H'空间.若还有
* 结合:  若 $(\mu\vee 1_X )\circ \mu\simeq (1_X\vee \mu)\circ \mu $ 
* 逆: 若 $\nabla_X\circ (\nu \vee 1_X)\circ \mu\simeq \nabla_X\circ (1_X\vee \nu )\circ \mu \simeq e_X$ ,其中 $e_X $ 是常值映射.

则称之为 AH'I空间.

{{% mathbox type="blue" title="" %}}
对于任意的拓扑空间 $Y $ , AH'I空间 $X $ , $[X,Y] $ 可以赋予一个群结构.且一样有连续映射 $g:Y_0\rightarrow Y_1 $ 所诱导出的
$$
  g_\bullet:[X,Y_0]\rightarrow [X,Y_1]
$$
为群同态.特别地,当 $g $ 是同伦等价,那么 $g_\bullet $ 是群同构.
{{% /mathbox %}}

证明几乎与前完全一致.

{{% mathbox type="blue" title=" $S^1 $ 是AH'I空间" %}}

{{% /mathbox %}}
证明: 具体考虑乘法 $\mu:S^1\rightarrow S^1\vee S^1 $ ,也就是
$$
  S^1\Huge{\circ \xrightarrow{\mu} \infty} \small{S^1\vee S^1} 
$$
对两个圆进行参数化,就很容易构造 $p_1\circ \mu $ 以及 $p_2\circ \mu $  与恒等映射 $1_{S^1} $ 之间的同伦.所以 $S^1 $ 是一个 H'空间.结合性与逆元也很容易构造同伦.所以  $S^1 $ 是一个 AH'I空间.也就是说 $\pi(Y)=[S^1,Y] $ 具有群结构.

{{% mathbox type="blue" title="" %}}
设 $X,Y $ 为拓扑空间
* 若其中之一为 AH'I空间,那么 $X\wedge Y $ 仍是 AH'I空间
* 若 $X $ 是 $T_2 $ 的,那么 $Y^X $ 是 AHI空间当且仅当 $X $ 为AH'I空间或者 $Y $ 为 AHI空间.

{{% /mathbox %}}

所以
* $S^n,X\wedge S^1 $ 都是 AH'I空间,也就是说 $\Omega(Y) $ 为 AHI空间.进一步可知, $\pi_n(Y)=[S^n,Y] $ 以及 $[X,\Omega(Y)] $ 均有群结构.

* $\pi_0(Y) $ 一般没有群结构,描述 $Y $ 的连通分支集.但是当 $Y $ 是AHI空间时,可以赋予群结构.

{{% mathbox type="blue" title="" %}}
若 $X_1,X_2 $ 都是 AH'I空间,那么 $[X_1\wedge X_2,Y] $ 是交换群.

特别地, 当 $n\ge 2 $ , $\pi_n(Y) $ 是交换群.
{{% /mathbox %}}

一般来说, $\pi_1(Y) $ 不是交换群.但是也有特例,对于只有一种非平凡环路的空间,其基本群就是交换群,例如 $S^1 $ .

* 可以计算 $\pi_1(S^1)=\mathbb{Z} $ ,可以用Gauss所定义的 "缠绕数" 去计算,主要就是用到 $S^1\simeq \R\setminus \Set{0} $ .或者用覆叠空间去计算,详细见[拓扑学]({{< ref "/Notes/Topology.md" >}}).
* 还可以计算 $T^2 $ 的基本群为 $\pi_1(T^2)=\mathbb{Z}^2 $ .也是一个交换群,可以用上面的缠绕数方法,由于 $T^2=S^1\times S^1 $ ,所以很容易得到其基本群为 $\mathbb{Z} $  .实际上,后面引入的自由群会更加直接地从代数上说明为什么是一个交换群,因为 $T^2 $ 上两种不同的圆周相互之间是可以互换顺序的,更直观的图像仍参见[拓扑学]({{< ref "/Notes/Topology.md" >}}).

下面系统地阐述自由群及其在同伦群中的应用.

简单来说,自由群就是各个生成元所组成的各种可能的 word 的集合.,例如对于两个生成元
$$
  F_2[a,b]=\Set{a^{m_1}b^{n_1}a^{m_2}b^{n_2}\dots a^{m_k}b^{n_k}:m_i,n_j\in \mathbb{Z},k\ge 0}
$$
一般来说,由于并没有交换律 $ab=ba $ ,所以上面的自由群并不是交换群.

例如,对于 $S^1\vee S^1 $ ,其基本群 $\pi_1(S^1\vee S^1)\cong F_2[a,b] $ . $S^1\vee S^1 $  就是
$$
  \Huge{8}
$$
中间交点为基点,沿上圆走则是 $a $ ,下圆走是 $b $ .于是自由群中的元素 $a^2b^6a^5b^2 $ 就是指先沿上圆走 $2 $ 圈,再沿着下圆走 $6 $ 圈,再沿着上圆 $5 $ 圈,最后再沿着下圆 $2 $ 圈回到基点.

同理可以知道更多生成元所构成的自由群.特别地,对于只有一个生成元的自由群,其天然是一个交换群,这可以解释 $S^1 $ 的基本群是一个交换群.将上面的 $S^1\vee S^1 $ 推广到更多,就得到了
$$
  \pi_1(\underbrace{S^1\vee S^1\vee \dots\vee S^1}_n)\cong F_n[a_1,\dots,a_n]
$$
> 这实际上是 Van Kampen 定理的一个特例,更多仍参见拓扑学笔记.

一般的有限生成群 $G $ 可以从自由群中添加一些关系得到.例如
*  $\mathbb{T}^2=(S^1\vee S^1)\cup_f \mathbb{B}^2  $ , 其中 $f:\partial \mathbb{B}^2\rightarrow S^1\vee S^1 $  有  
$$
  \pi_1(\mathbb{T}^2)=\Set{\pi_1(S^1\vee S^1)|aba^{-1}b^{-1}=1} =\Set{a^nb^m}\cong \mathbb{Z}\oplus \mathbb{Z}
$$

推广到 $\Sigma_g $ 就是
$$
  \pi_1(\Sigma_g)=\Set{\pi_1(\bigvee_{2g}S^1)|a_1b_1a_1^{-1}b_1^{-1}\dots a_gb_ga_g^{-1}b_g^{-1}=1}  
$$
可见其并不像 $\pi_1(T^2) $ 那样是一个交换群.


定义 $(X,A) $ 的相对基本群为 $\pi_n(X,A) $ 是上面映射的全体模去同伦等价关系后所得到的商集.由等价类 $[f] $ 构成:
$$
  \pi_n(X,A)=\Set{[f]:f(\mathbb{I}^n_+)\subset X,f(\partial\mathbb{I}^n_+)\subset A,f(\mathbb{J}_+^{n-1})=\Set{\mathring{x}}}
$$

其群运算与同伦群是相似的.一般来说 $n\ge 3 $ 时是交换群, $n=2 $ 时通常非交换,而 $n=1 $ 时一般不构成群.这些都是可以通过同伦群的性质推广而来.


#### 同伦群的初等计算

##### 相对同伦群

更一般地,考虑映射
$$
  f:(\mathbb{I}^n_+,\partial\mathbb{I}^n_+,\mathbb{J}_+^{n-1})\rightarrow (X,A,\mathring{x})
$$
其中 $\mathbb{I}^n_+,\partial\mathbb{I}^n_+,\mathbb{J}_+^{n-1} $ 分别是 $n $-维立方体、其边界和除了底面所以边界的集合. $A $ 是拓扑空间 $X $ 的一个子空间, $\mathring{x} $ 为 $A $ 的基点.
![相对同伦](/images/Topology/relative_homotopy.pdf)

定义 $(X,A) $ 的相对基本群为 $\pi_n(X,A) $ 是上面映射的全体模去同伦等价关系后所得到的商集.由等价类 $[f] $ 构成:
$$
  \pi_n(X,A)=\Set{[f]:f(\mathbb{I}^n_+)\subset X,f(\partial\mathbb{I}^n_+)\subset A,f(\mathbb{J}_+^{n-1})=\Set{\mathring{x}}}
$$

其群运算与同伦群是相似的.一般来说 $n\ge 3 $ 时是交换群, $n=2 $ 时通常非交换,而 $n=1 $ 时一般不构成群.这些都是可以通过同伦群的性质推广而来.

> 关于 $\pi_2(X,A) $ 一个直观的例子就是前面提到的 $T^2 $ ,有 $\pi_2(T^2,S^1\vee S^1) $ .其结果是 $F_2*F_2 $ ,所以是非交换的.具体的计算见后.

考虑边界算子 $\partial $ 将 $f $ 限制在 $\mathbb{J}_+^{n-1} $ 上,于是回到了同伦群:
$$
  \partial:\pi_n(X,A)\rightarrow \pi_{n-1}(A),\partial[f]:=[\partial f]\in \pi_{n-1}(A)
$$

* 含入映射 $i:A\hookrightarrow X $ 诱导了同态映射
$$
  i_*:\pi_n(A)\rightarrow \pi_n(X)
$$
参见前 $\bullet $ 的函子性.
* 含入映射 $j:\Set{\mathring{x}}\hookrightarrow A $ 将"绝对"映射 $f:(\mathbb{I}^n_+,\partial\mathbb{I}^n_+)\rightarrow (X,A) $  视为相对映射 $j_*f:(\mathbb{I}^n_+,\partial\mathbb{I}^n_+,\mathbb{J}_+^{n-1})\rightarrow (X,A,\mathring{x}) $ ,同样诱导了群同态:
$$
  j_*:\pi_n(X)\rightarrow \pi_n(X,A)
$$

于是
$$
  \boxed{\dots\rightarrow \pi_n(A)\xrightarrow{i_*}\pi_n(X)\xrightarrow{j_*}\pi_n(X,A)\xrightarrow{\partial}\pi_{n-1}(A)\rightarrow \dots}
$$
构成正合列,即前面一个映射的 $Im $ 是后一个映射的 $\ker $ .
*  $Im(i_*)=\ker(j_*) $ .注意 $\pi_n(X) $ 中的等价类是将边界都映为基点的,自然在映射 $j_* $ 下得到单位元,也就是 $j_*\circ i_*=0 $ ,即 $Im(i_*)\subset \ker j_* $ .另一方面,若 $j_*[g]=0 $ ,这说明 $[g] $ 是同伦于常值映射 $\mathring{x} $ 的同伦等价类.而 $\pi_n(X,A) $ 中属于该等价类的就完全落在 $A $ 中.

> $\pi_n(X) $ 是 $X $ 中保持基点 $\mathring{x} $ 的等价类,而 $X_n(X,A) $ 中除了保持基点,还固定底面 $A $ 上的等价类不变. 所以 $\pi_n(X) $ 中的单位元,也即是平凡的等价类,含入映射到 $\pi_n(X,A) $ 中后所得到的就是完全落在底面 $A $ 中的等价类.可以想象原本的基点扩展成了一个面.


##### 计算

考虑纤维化:  $F\xhookrightarrow{i}E\xrightarrow{p}B $ ,将上正合列应用到此,有
$$
  \boxed{\dots\rightarrow \pi_n(F)\xrightarrow{i_*}\pi_n(E)\xrightarrow{j_*}\pi_n(E,F)\xrightarrow{\partial}\pi_{n-1}(F)\rightarrow \dots}
$$
投影映射 $p\rightarrow E $ 诱导了同态映射
$$
  p_*: \pi_n(E,F)\rightarrow \pi_n(B,\Set{\mathring{b}})\cong \pi_n(B)
$$
若 $B $ 是 Hausdorff空间并且局部可缩,那么有同态提升性质(HLP).

> 实际上就是提升引理,覆叠空间的存在性.而在流形中,上面两条性质是自动满足的.HLP 也就是将底空间 $B $  提升为 $E $ 的映射提升.

可以证明, $p $ 作为覆叠映射,所诱导出的 $p_* $ 是双射.也就是说,纤维化
$$
  F\xhookrightarrow{i}E\xrightarrow{p}B
$$
诱导了长正合序列.
$$
  \dots\rightarrow \pi_n(F)\rightarrow \pi_n(E)\rightarrow \pi_n(B)\rightarrow \pi_{n-1}(F)\rightarrow 
  \\
  \dots\rightarrow \dots\rightarrow \pi_0(F)\rightarrow \pi_0(E)\rightarrow \pi_0(B)=0
$$
可以据此做一些计算.
1. 对于离散群 $\Gamma $ 作用到拓扑空间 $X $ ,轨道空间 $M=X/\Gamma $ 作为基空间给出纤维化 $\mathcal{O}\hookrightarrow X\rightarrow M $ ,其中 $\mathcal{O}\cong \Gamma $ 是群轨道.
若 $X $ 是连通且单连通空间,那么 $\pi_0(X)=\pi_1(X)=0 $ ,正合列变为短正合列
$$
 0\rightarrow \pi_1(M)\xrightarrow{g}\pi_0(\Gamma)\xrightarrow{h}0
$$
根据正合列的性质可知 $g $ 是双射.所以 $\pi_1(M)\cong \pi_0(\Gamma) $ ,由于 $\Gamma $ 是离散群,所以 $\pi_0(\Gamma)\cong \Gamma $ .
具体地,对于 $T^n=\R^n/\mathbb{Z}^n $ ,有 $\pi_1(T^n)=\mathbb{Z}^n $ ,特别地 , $\pi_1(S^1) =\mathbb{Z}$.

2. 考虑映射 $f:S^n\rightarrow S^1,n\ge 2 $ ,因为$\pi_1(S^1)=\mathbb{Z} $ 离散,又连续映射 $f $ 所诱导的基本群范畴中的 $f_* $ 是同态,所以其像只能是 $Im(f_*)=\Set{e} $ .所以可以提升成 $\tilde{f}:S^n\rightarrow \R $ ,由于 $\R $ 可缩,故 $\tilde{f} $ 零伦,所以 $f=\tilde{f}\circ p $ 也是零伦的.也就是说 $\pi_n(S^1)=0,n\ge2 $ .可以一般地推广为 $\pi_n(S^m)=0,n\lt m $ .
3. Hurewicz定理: 若 $X $ 连通,那么
$$
  H_1(X,\mathbb{Z})\cong \pi_1(X)/[\pi_1(X),\pi_1(X)]
$$
例如,结合上一条结论,对于 $S^n $ ,有 $\pi_{m\lt n}(S^n)=0 $ .所以
$$
  \pi_n(S^n)\cong H_n(S^n,\mathbb{Z})\cong \mathbb{Z}
$$

4. Hopf-纤维化
   
   考虑 $S^1\hookrightarrow S^3\xrightarrow{p}S^2 $ .将 $S^3,S^2 $ 分别嵌入到 $\mathbb{C}^2,\mathbb{C}\times \R $ 中,也就是
   $$
     S^3: |z_0|^2+|z_1|^2=1,(z_0,z_1)\in \mathbb{C}^2
     \\
     S^2: |z|^2+x^2=1,(z,x)\in \mathbb{C}\times \R
   $$
   映射 $p $ 定义为 $p(z_0,z_1)=(2z_0z_1^*,|z_0|^2-|z_1|^2), $ 显然对于 $(z_0,z_1)\in S^3 $ 有 $p(z_0,z_1)\in S^2 $ .所以诱导出了正合列
   $$
     \dots\rightarrow \pi_{n+1}(S^1)\rightarrow \pi_{n+1}(S^3)\rightarrow \pi_{n+1}(S^2)\rightarrow \pi_n(S^1)\rightarrow \pi_n(S^3)\rightarrow \dots
   $$
   从中可以得到:
   * 对于 $n=1 $ , 由于 $\pi_2(S^3)=\pi_1(S^3)=0 $ ,所以
   $$
     0\rightarrow \pi_2(S^2)\rightarrow \pi_1(S^1)\rightarrow 0
   $$
   对于超短正合列,有 $\pi_2(S^2)\cong \pi_1(S^1)\cong \mathbb{Z} $ .
   * 对于 $n\ge 2 $ ,由于 $\pi_{n+1}(S^1)=\pi_n(S^1)=0 $ ,所以
   $$
     0\rightarrow \pi_{n+1}(S^3)\rightarrow \pi_{n+1}(S^2)\rightarrow 0
   $$
   即 $\pi_{n+1}(S^3)\cong  \pi_{n+1}(S^2) $ .特别地, $\pi_{3}(S^3)\cong  \pi_{3}(S^2)\cong \mathbb{Z} $ .

> 一直感觉对于 $m\gt n $ 的 $\pi_m(S^n) $ 非 $0 $ 是一件非常诡异的事情.
   
5. 特殊正交群 $G=SO(N) $ 保持 $\R^N $ 空间中的欧氏度规不变,也就是保持 $S^{N-1} $ 不变.其有保持 $S^{N-1} $ 的北极点不变的子群 $SO(N-1) $ .实际上,保持任何点都有自群为 $SO(N-1) $ .所以 $SO(N)/SO(N-1)\cong S^{N-1} $ .有纤维化
$$
  SO(N-1)\hookrightarrow SO(N)\xrightarrow{p} S^{N-1}
$$
诱导出正合列
$$
  \dots\pi_{n+1}(SO(N-1))\rightarrow \pi_{n+1}(SO(N))\rightarrow \pi_{n+1}(S^{N-1})
  \\
  \rightarrow \pi_n(SO(N-1))\rightarrow \pi_n(SO(N))\rightarrow \pi_n(S^{N-1})\rightarrow \dots
$$

由此可计算**一阶同伦群**: 取 $N=2 $ ,由于 $SO(1) $ 为单点集,是可缩的,所以 $\pi_n(SO(1))=0 ,\forall n $ ,于是
$$
  0\rightarrow \pi_n(SO(2))\rightarrow \pi_n(S^1)\rightarrow 0
$$
有
$$
  \pi_n(SO(2))\cong \pi_n(S^1)\cong \begin{cases}
    \mathbb{Z},&n=1\\0,&n\ge 2
   \end{cases}
$$
另外,取 $N\ge 4 $ ,有 $\pi_1(S^{N-1})=\pi_2(S^{N-1})=0 $ ,于是有
$$
  0\rightarrow \pi_1(SO(N-1))\rightarrow \pi_1(SO(N))\rightarrow 0
$$
可知有 $\pi_1(SO(3))\cong \pi_1(SO(4))\cong \pi_1(SO(5))\cong \dots $ .另一方面,由于 $SO(3)\cong SU(2)/\mathbb{Z}_2 $ ,而且 $SU(3) $ 单连通,是 $SO(3) $ 的万有覆叠空间.所以 $\pi_1(SO(3))\cong \mathbb{Z}_2 $ .

> 旋量群 $Spin(n) $ 在 $n\gt2 $ 时总是单连通的,所以 $Spin(n) $ 总是 $SO(n) $ 的万有覆叠空间.所以, $\pi_1(SO(n\gt 2))=\mathbb{Z}_2 $ .

对于**二阶同伦群**,考虑纤维化 $ \mathbb{Z}_2\hookrightarrow S^3\rightarrow SO(3) $ 有
$$
  0=\pi_2(\mathbb{Z}_2)\rightarrow \pi_2(S^3)\rightarrow \pi_2(SO(3))\rightarrow \pi_1(Z_2)=0
$$
于是 $0=\pi_2(S^3)\cong  \pi_2(SO(3)) $ .

另外在 $N\ge 5 $ 时考虑前面的长正合列,有 $\pi_2(S^{N-1})=\pi_3(S^{N-1})=0 $ ,于是有 $\pi_2(SO(4))=\pi_2(SO(5))=\pi_2(SO(6))=\dots $ .另一方面,在前面得到了结果 $\pi_1(SO(4))=\mathbb{Z}_2 $ .另一方面, $SO(4)\cong Spin(4)/\mathbb{Z}_2 $  . 于是又有纤维化
$$
  \mathbb{Z}_2\hookrightarrow Spin(4)\rightarrow SO(4)
$$
其中
$$
  \pi_2(Spin(4))=\pi_2(SU(2)\times SU(2))=\pi_2(SU(2))\times \pi_2(SU(2))=0
$$
所以有正合列为
$$
  0=\pi_2(Spin(4))\rightarrow \pi_2(SO(4))\rightarrow \pi_2(\mathbb{Z}_2)=0
$$
也就是说
$$
  \pi_2(SO(4))=\pi_2(SO(5))=\pi_2(SO(6))=\dots=0
$$

对于**三阶同伦群**,首先考虑纤维化 $\mathbb{Z}_2\hookrightarrow S^3\rightarrow SO(3) $ ,可得 $\pi_3(SO(3))\cong \pi_3(S^3)=\mathbb{Z} $ .另外,根据前面的纤维化 $\mathbb{Z}_2\hookrightarrow Spin(4)\rightarrow SO(4) $ ,可得 $\pi_3(SO(4))\cong \pi_3(Spin(4))\cong \mathbb{Z}^2 $ .对于 $N\ge 6 $ ,有
$$
  \pi_3(SO(5))=\pi_3(SO(6))=\dots
$$
而其中 $SO(6)=Spin(6)/\mathbb{Z}_2=SU(4)/\mathbb{Z}_2 $ ,构造纤维化可以得到 $\pi_3(SO(6))\cong \pi_3(SU(4)) $,而后面将证明 $\pi_3(SU(4))=\mathbb{Z} $ .

类似地,可以得到更高阶同伦群的结果,从上面的计算过程可见,即便有了正合列,也需要一些已知的结果,而实际上这些已知的结果才是高度非平凡的.又例如,在计算**四阶同伦群**时,要用到 $\pi_4(S^3)\cong \pi_4(S^2)\cong \mathbb{Z}_2 $ ,从而计算得到
$$
  \begin{align*}
    &\pi_4(SO(3))= \pi_4(S^4)=\mathbb{Z}_2
    \\
    &\pi_4(SO(4))=\pi_4(S^3)\times \pi_4(S^3)=\mathbb{Z}_2\times \mathbb{Z}_2
  \end{align*}
$$
另外,还有一个一般的结果:
$$
  \pi_n(SO(n+2))=\pi_n(SO(n+3))=\pi_n(SO(n+4))=\dots
$$

6. 特殊幺正群 $G=SU(N) $ ,由于是保持 $\mathbb{C}^N $ 中的内积,类似于上面 $SO(N) $ 的处理,完全同理地有
$$
  SU(N-1)\hookrightarrow SU(N)\rightarrow S^{2N-1}
$$

取 $N=2 $ 可得 $\pi_n(SU(2))\cong \pi_n(S^3) $ ,这是显然的,因为本来就有 $SU(2)\cong S^3 $ .

取 $N\gt 1+\frac{n}{2} $ ,有 $\pi_{n+1}(S^{2N-1})=\pi_n(S^{2N-1})=0 $ ,所以正合列为
$$
  0\rightarrow \pi_{n}(SU(N-1))\rightarrow \pi_n(SU(N))\rightarrow 0
$$
即 $\pi_n(SU([\frac{n}{2}]+1))=\pi_n(SU([\frac{n}{2}]+2))=\dots $ ,分别取 $n=1,2,3 $ 就有
$$
  \begin{align*}
    &0=\pi_1(SU(1))=\pi_1(SU(2))=\pi_1(SU(3))=\dots
    \\&0=\pi_2(SU(2))=\pi_2(SU(3))=\dots
    \\&\mathbb{Z}=\pi_3(SU(2))=\pi_3(SU(3))=\dots
  \end{align*}
$$

##### 小结
总结一下,纤维化是指有了一个
$$
  F\hookrightarrow E\xrightarrow{p}B
$$
之后,诱导出的正合列
$$
  \dots\rightarrow \pi_n(F)\xrightarrow{i_*}\pi_n(E)\xrightarrow{j_*}\pi_n(E,F)\xrightarrow{\partial}\pi_{n-1}(F)\rightarrow \dots
$$
中 $p $ 所诱导的 $p_* $ 使得 $\pi_n(E,F)\cong \pi_n(B) $ ,所以得到所需要的正合列为
$$
  \dots\rightarrow \pi_n(F)\xrightarrow{i_*}\pi_n(E)\xrightarrow{j_*}\pi_n(B)\xrightarrow{\partial}\pi_{n-1}(F)\rightarrow \dots
$$
再据此处理一些问题.不过总是只能得到同伦群之间的一些相对关系,一些关键的结果总是从其他一些非平凡的过程中得到.


### 计算结果总结

在这里总结一下各种同调群、同伦群的结果,并简单叙述其计算方法.

$\boxed{\small{\text{同调群}} } $ 











$\boxed{\small{\text{同伦群}} } $ 





### 黎曼几何

___
___
___
___