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
  [g]:=f^{-1}_\bullet([1])
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
* 还可以计算 $T^2 $ 的基本群为 $\pi_1(T^2)=\mathbb{Z}^2 $ .也是一个交换群.实际上,后面引入的自由群会更加直接地从代数上说明为什么是一个交换群,更直观的图像仍参见[拓扑学]({{< ref "/Notes/Topology.md" >}}).

#### 同伦群的初等计算

### 黎曼几何

___
___
___
___