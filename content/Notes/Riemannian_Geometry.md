+++
date = '2026-07-09'
draft = false
title = 'Riemannian Geometry'
weight = 1
+++


### 0. 光滑流形

参见[微分流形杂谈]({{< ref "/Notes/微分流形杂谈.md" >}}).


### 2. 黎曼度量

由于在 Riemannian 几何中有大量的指标求和,所以采用 Einstein 求和约定:上下指标相同默认表示求和,除非特别说明,一般来说求和是从 $1 $ 到空间的维数.例如
$$
  a_ib^i:=\sum_ia_ib^i
$$
分母上的上指标会被认定为是下指标,反之亦然.通常来说,会选择向量场为下指标,其系数函数为上指标,例如 $a^1X_1+a^2X_2 $ .类似地, $1 $-形式一般会用下指标标记,而其系数函数一般用上指标标记.若取一个标准的坐标基,也就是 $X=X^i\partial_i,\omega=\omega_i dx^i $ .

##### 黎曼度量

设 $M $ 是一个光滑流形,
{{% mathbox type="green" title="" %}}
一个 $M $ 上的黎曼度量 $g $ 是指一个定义在 $T_pM $ 上的内积
$$
  g_p(\cdot,\cdot)=\langle \cdot,\cdot \rangle _p,\forall p\in M
$$
且光滑地依赖于 $p $ .
{{% /mathbox %}}

1. 其中光滑依赖是指,若 $X,Y $ 是两个 $U\subset M $ 上的光滑向量场,那么 $f(p)=\langle X_p,Y_p \rangle_p $ 是 $U $ 上的一个光滑函数.
2. 注意,**黎曼度量**并不是一个传统意义上的**度量**,但是 $g $ 可以诱导出一个自然的**距离**作为 $M $ 上的度量.

应用张量的语言,由定义
$$
  g:\Gamma^\infty(TM)\times \Gamma^\infty(TM)\rightarrow C^\infty(M)
$$
也就是说 $g $ 是 $M $ 上的一个 $(0,2) $-张量,是 $C^\infty(M) $-双线性的.所以作为内积定义中的对称性和正定性,在张量的语言中,也就是 $g $ 作为一个 $(0,2) $-张量是对称且正定的.即
$$
  \boxed{\small{\text{一个黎曼度量是指一个光滑、对称且正定的(0,2)-张量场}} }
$$

在后面的计算中,经常会在局域坐标系中计算.具体地,考虑坐标系 $\Set{U,x^1,\dots,x^m} $ ,记
$$
  g_{ij}(p)=\langle \partial_i,\partial_j \rangle_p
$$
根据前面的定义,函数 $g_{ij} $  有
1. 对于任意的 $i,j $ , $g_{ij} $ 在 $p $ 处光滑.
2. $g_{ij}=g_{ji} $ ,也就是说 $g_{ij(p)} $ 在任意的 $p $ 处都对称.
3. 矩阵 $g_{ij(p)} $ 在任意 $p $ 处正定.

注意,尽管 $g $ 是内蕴定义的,但函数 $g_{ij} $ 依赖于坐标系的选择.若选择 $U $ 上另一个坐标系为 $\Set{\tilde{x}^1,\dots,\tilde{x}^m} $ ,有转移函数
$$
  \tilde{\partial}_i=\frac{\partial x^k}{\partial \tilde{x}^i}\partial_k
$$
于是
$$
  \tilde{g}_{ij}=\langle \tilde{\partial}^i,\tilde{\partial}^j \rangle =\frac{\partial x^k}{\partial \tilde{x}^i}g_{kl}\frac{\partial x^l}{\partial \tilde{x}^j}
$$
换而言之,矩阵之间 $(\tilde{g}_{ij})=J^T(g_{ij})J $ ,其中 $J $ 是Jacobian, $J_{ij}=\frac{\partial x^i}{\partial \tilde{x}^j} $ .因此对于任意 $U $ 中的光滑向量场 $X=X^i\partial_i $ 和 $Y=Y^j\partial_j $ ,
$$
  \langle X_p,Y_p \rangle_p=X^i(p)Y^j(p)\langle \partial_i,\partial_j \rangle_p=g_{ij}X^i(p)Y^j(p)
$$
所以局部上有
$$
    g=g_{ij}dx^i\otimes dx^j
$$


由于每个矩阵 $(g_{ij}) $ 都是正定的,所有可逆.令其逆为 $(g^{ij}) $ ,即
$$
  g_{ij}g^{jk}=\delta^k_i
$$
矩阵 $(g^{ij}) $ 仍是正定的,可用其定义对偶空间中的内积: 在 $T_p^*M $ 中的$g^* $ .具体地,对于任意 $U $ 中的 $1 $-形式
$$
  \omega=\omega_i dx^i,\eta=\eta_j dx^j
$$
定义
$$
  g^*(\omega,\eta)=\langle \omega,\eta \rangle^*_p:=g^{ij}(p)\omega_i(p)\eta_j(p)
$$
显然,其定义是不依赖于坐标的.





### 3. 黎曼距离

##### 曲线的长度
考虑 $\gamma:[a,b]\rightarrow M $ 为一条光滑的参数曲线.于是
$$
  \dot{\gamma}(t)=(d\gamma)(\frac{d}{dt}),\dot{\gamma}(t)\in T_{\gamma(t)}M
$$
{{% mathbox type="green" title="曲线的长度" %}}
曲线 $\gamma $ 的长度为
$$
  \begin{align*}
    Length(\gamma)&:=\int^b_a||\dot{\gamma}(t)||_{\gamma(t)}dt
    \\
    &=\int^b_a\sqrt{g_{\gamma(t)}(\dot{\gamma}(t),\dot{\gamma}(t))}dt
  \end{align*}
$$
有时会简单记作 $L(\gamma) $ .
{{% /mathbox %}}

简单起见,总会假设 $\gamma $ 是 regular (非退化)的,即 $\dot{\gamma}(t)\ne 0 $ .于是
{{% mathbox type="blue" title="" %}}
曲线长度 $L(\gamma) $ 与 regular参数化无关.
{{% /mathbox %}}
{{% proof %}}
假设曲线 $\gamma:[a,b]\rightarrow M $ 的另一个参数化为 $\gamma_1:[c,d]\rightarrow M $ .于是,存在 $t_1:[a,b]\rightarrow [c,d] $ 即
$$
  \gamma_1(t_1(t))=\gamma(t)
$$
求导数,有
$$
  \dot{\gamma}_1(t_1)\frac{dt_1}{dt}(t)=\dot{\gamma}(t)  
$$
由曲线 regular 可知其中 $\frac{dt_1}{dt}(t)\ne 0 $ ,即 $\frac{dt_1}{dt}(t) $ 严格递增或递减,于是
$$
  \begin{align*}
    L(\gamma_1)&=\int^d_c\sqrt{g_{\gamma_1(t_1)}(\dot{\gamma}_1(t_1),\dot{\gamma}_1(t_1) )}dt_1
    \\
    &=\int^b_a\sqrt{g_{\gamma(t)}((\frac{dt_1}{dt})^{-1}\dot{\gamma}(t),(\frac{dt_1}{dt})^{-1}\dot{\gamma}(t) )}\frac{dt_1}{dt} dt
    \\
    &=\int^b_a\sqrt{g_{\gamma(t)}(\dot{\gamma}(t) ,\dot{\gamma}(t) )}dt=L(\gamma)
  \end{align*}
$$
完成证明.
{{% /proof %}}

用类似地方式可以证明,若 $Id:\varphi:(M,g_M)\rightarrow (N,g_N) $ 是一个局部的isometry,于是对于 $M $ 中任何的光滑曲线 $\gamma $ 都有
$$
  L(\gamma)=L(\varphi\circ \gamma)
$$

{{% mathbox type="green" title="arc-Length" %}}
$$
  s(t)=\int^b_a|\dot{\gamma}(t) |dt
$$
就是 arc-长度.显然 $s:[a,b]\rightarrow [0,L(\gamma)] $ 是递增的.
{{% /mathbox %}}

$t=t(s) $ 是 $s=s(t) $ 的逆,诱导出 $\sigma(s)=\gamma(t(s)) $ 是曲线的 arc-length 参数化.

{{% mathbox type="blue" title="" %}}
$\langle \dot{\sigma}(s),\dot{\sigma}(s) \rangle_{{\sigma}(s)} =1 $ 
{{% /mathbox %}}

{{% proof %}}
由于 $t'(s)=\frac{1}{s'(t)}=|\dot{\gamma}(t) |^{-1} $ ,于是
$$
  \langle \dot{\sigma}(s),\dot{\sigma}(s) \rangle_{{\sigma}(s)} =\langle \dot{\gamma}(t) t'(s),\dot{\gamma}(t) t'(s) \rangle =|t'(s)|^2|\dot{\gamma}(t) |^2_{\gamma(t)}=1
$$

{{% /proof %}}

* 若 $|\dot{\gamma}(t) |=1 $ ,则称 $\gamma $ 为 Normal 的.
* 若 $|\dot{\gamma}(t) |=const. $ ,则称 $\gamma $ 为常速(constant speed)的.

> 速度,在黎曼几何中经常用到,是一个非常形象的类比.

反之,若 $|\dot{\gamma}(t) |=1  $ ,则可知 $s(t)=t+a $ ,即 $s $ 与 $t $ 只差一个常数.

作为一个简单的应用,考虑 $1 $ 维的黎曼流形,在一个局部的 'arc-length' 坐标下,黎曼度量只有唯一的分量为
$$
  g_{11}=\langle \dot{\sigma}(s),\dot{\sigma}(s) \rangle =1
$$
即 $g_{11}=ds\otimes ds $ .也就是说 **任意的一维黎曼流形都是 locally isometric 的.**

实际上,在前面的讨论中,要求曲线光滑是一个过强的条件,对于一条分段光滑的曲线,同样可以定义长度: $\gamma:[a,b]\rightarrow M $ ,有
$$
  a=a_0\lt a_1\lt \dots\lt a_N=b
$$
使得 $\gamma|_{[a_i,a_{i+1}]} $ 光滑,于是 $L(\gamma)=\sum L(\gamma|_{[a_i,a_{i+1}]}) $ .更进一步地,可见长度的定义实际上只用到了一阶导数,所以对于一条分段 $C^1 $ 的曲线,同样可以如上定义长度.

##### 黎曼距离
有了曲线的长度,就可以在黎曼流形上定义距离.具体地,考虑一个紧黎曼流形 $(M,g) $ ,于是对于任意的 $p,q\in M $ ,令
$$
  \mathcal{C}_{p,q}=\Set{\gamma:[0,1]\rightarrow M:\gamma(0)=p,\gamma(1)=q,\gamma \small{\text{ 分段光滑}} }
$$
{{% mathbox type="green" title="黎曼距离" %}}
$d(p,q)=\inf\left\{ L(\gamma):\gamma\in \mathcal{C}_{p,q} \right\}  $ 
{{% /mathbox %}}

例子:
1. 在欧氏空间 $(\R^m,g_0) $ 中,
$$
  d(x,y)=\sum_{i=1}^m(x^i-y^i)^2
$$

2. 在 Poincare 平面 $(\mathbb{H}^2,g_{hyp}) $ 中,考虑 $p=(0,a),q=(0,b) $ 且其中 $b\gt a\gt 0 $ .设有曲线
$$
  \gamma:[0,1]\rightarrow \mathbb{H}^2,\gamma(t):=(x(t),y(t)),\gamma(0)=p,\gamma(1)=q
$$
 考虑到 $g_{hyp}=\frac{1}{y^2}(dx\otimes dx ,dy\otimes dy) $  ,曲线长度 
$$
  \begin{align*}
    L(\gamma)&=\int^1_0|\dot{\gamma}(t) |dt=\int^1_0\frac{1}{y}\sqrt{x'(t)^2+y'(t)^2}
    \\
    &\ge \int^1_0\frac{y'(t)}{y(t)}dt=log\frac{b}{a}
  \end{align*}
$$
 显然是当 $x'=0,y'\ge 0 $ 时取等,对应的曲线就是 $y $ 轴上的曲线 $\gamma_\bullet $ ,也就是 $d(p,q)=log\frac{b}{a} $ .
 
> 若想推广到 $\mathbb{H}^2 $ 中任意的两点,可以找到该两点到 $y $ 轴线上的一个isometry ,然后利用上方法得到距离.具体地,这个 isometry 实际上就是mobius变换:
$$
  f(z)=\frac{az+b}{cz+d},ad-bc=1
$$
> 可以证明该变换下, $z'=f(z) $ 满足 $ds'^2=\frac{|dz'|^2}{Im (z')^2}=\frac{|dz|^2}{Im(z)^2}=ds^2. $ 即其是一个等距变换.更进一步,后面会提到,Poincare 上半平面中的测地线是一个圆心在 $x$ 轴上的半圆,而 $y $ 轴本身也是一条端点分别在 $0 $ 和 $\infty $ 的测地线,所以考虑一条经过 $z_1,z_2 $ 的测地线,分别交 $x $ 轴 $x_1,x_2 $ ,于是变换要求有 $f(x_2)=0 $ , $f(x_1)=\infty $ ,也即是
$$
  f(z)=\frac{z-x_2}{z-x_1}
$$



{{% mathbox type="blue" title="" %}}
$d $ 是 $M $ 上的一个度量,即满足
1.  $d(p,p)=0,d(p,q)\ge 0 $
2.  $d(p,q)=d(q,p) $  
3.  $d(p,q)\le d(p,r)+d(r,q) $ 

{{% /mathbox %}}

{{% proof %}}
大部分的证明都是容易的,相对tricky的是当 $p\ne q $ 时 $d(p,q)\gt 0 $ :
取一包含 $q $ 的 Chart $(\varphi,U,V) $ ,且 $p\notin U $ (由于 $M $ 是  $T_2 $ 的,所以总是能取到这样的Chart),使得 $\varphi(q)=0\in V=B_1(0)\subset \R^m $ ,那么对于
$$
  h=(\varphi^{-1})^*(g_U)
$$
$\varphi $ 是 $(V,h) $ 与 $(U,g|_U) $ 之间的等距变换.令
$$
  \lambda=\inf\left\{ (h_{ij})_x\small{\text{的本征值}} |x\in \bar{B}_{1/2}(0) \right\} 
$$
于是对于任意的 $x\in \bar{B}_{1/2}(0) $ 以及任意的 $X\in T_xV $ 有
$$
  \langle X,X \rangle _h=h_{ij}X^iX^j\ge \sum_i\lambda(X^i)^2=\lambda\langle X,X \rangle _{g_0}
$$
考虑 $\gamma $ 为连接 $p,q $ 的一条分段光滑的曲线, $\tilde{\gamma} $ 为其中第一段portion,其起点在 $0 $ ,终点落在 $\bar{B}_{1/2}(0) $ 且中间段完全落在 $B_{1/2}(0) $ 当中.所以
$$
  L(\gamma)\ge L(\tilde{\gamma})=L_h(\varphi\circ \gamma_1)\ge L_h(\tilde{\gamma})
$$
对 $\tilde{\gamma} $ 重参数化,得
$$
  \begin{align*}
    L_h(\tilde{\gamma})&=\int^1_0\sqrt{\langle \dot{\tilde\gamma}(t),\dot{\tilde\gamma}(t) \rangle_h }dt 
  \\
  &\ge \sqrt{\lambda}\int^1_0\sqrt{\langle \dot{\tilde\gamma}(t),\dot{\tilde\gamma}(t) \rangle_{g_0}}dt
  \\
  &=\sqrt{ \lambda}L_{g_0}(\tilde{\gamma})\ge \frac{\sqrt\lambda}{2}
  \end{align*}
$$
也即是
$$
  L(\gamma)\ge \frac{\sqrt\lambda}{2}\gt 0
$$
于是完成证明.
{{% /proof %}}

显然,若 $\varphi:(M,g_M)\rightarrow (N,g_N) $ 是 isometry ,那么有
$$
  d_M(p,q)=d_N(\varphi(p),\varphi(q))
$$
即 $\phi:(M,d_M)\rightarrow (N,d_N) $ 是 isometry.注意其中两个 isometry 分别是黎曼度量和其所诱导的距离度量的isometry,明确期间,后面的 isometry 专指黎曼度量,即 $g_M=\varphi^*g_N $ ,而将后者称为保持距离的,或简称为一个保距变换.

反之也同样有
{{% mathbox type="blue" title="Myers-Steenrod" %}}
设 $(M,g_M),(N,g_N) $ 都是黎曼流形,其上分别有诱导的 $d_M,d_N $ .若 $\varphi:(M,d_M)\rightarrow (N,d_N) $ 是一个保持距离的双射,那么 $\varphi $ 是一个isometry.特别地, $\varphi $ 是光滑的.
{{% /mathbox %}}

实际上,上定理还可以更强
{{% mathbox type="blue" title="Palais" %}}
黎曼流形上的黎曼距离,可以决定流形的光滑结构和黎曼度规.
{{% /mathbox %}}

进一步可以追问:
{{% mathbox type="slate" title="给定 $M $ 上任意的一个度量结构 $d $ ,是否存在 $M $ 上的黎曼度量 $g $ 使得 $d $ 被实现为 $g $ 所诱导的黎曼距离? " %}}
答案是否定的,一个经典的反例是 $\R^2 $ 中的 taxicab metric :任意两点之间都有无数条最短的曲线相连.而后面将会证明,黎曼流形中任何一点与其足够小领域中一点都只有唯一最短曲线连接,显然与上面的 taxicab metric 相矛盾.
{{% /mathbox %}}

有了黎曼度量所诱导的距离函数,可以进步研究其连续性.
{{% mathbox type="blue" title="" %}}
对于任意的 $p $ , $f(\cdot)=d(\cdot,p) $ 在 $M $ 上连续.
{{% /mathbox %}}

这里的连续当然是由流形的拓扑所定义的.
{{% proof %}}
只需要证明若 $q_i\rightarrow q $ ,则有 $f(q_i)\rightarrow f(q) $ .取 $(\varphi,U,V) $ Chart,  $q=\varphi(0) $ , $V=B_1(0)\subset \R^m $ , $q_i $ 是流形拓扑下收敛到 $q $ 的序列,即
$$
  \forall k,\exist N(k),s.t.\forall i\ge N(k),\varphi(q_i)\in B_{1/k}(0)
$$
由三角不等式,有 $|f(q_i)-f(q) |\le d(q,q_i) $ .为了证明 $f(q_i)\rightarrow f(q) $ ,即要证明 $d(q,q_i)\rightarrow 0 $ .

同样取 $h=(\varphi^{-1})^*(g|_U) $ 为 $V $ 上诱导的黎曼度量,令
$$
  \Lambda=\sup\Set{(h_{ij})_x\small{\text{的本征值}}|x\in \overline{B_{1/2}(0)} }
$$
也就是说对于任意的 $x\in \overline{B_{1/2}(0)}$ 和 $X\in T_xV $ 都有
$$
  \langle X,X \rangle_h\le \Lambda\langle X,X \rangle_{g_0}
$$
取 $\tilde{\gamma}_i:[0,1]\rightarrow V,\tilde{\gamma}_i(t)=t\varphi(q_i) $ 为连接 $\varphi (q) $ 和 $\varphi(q_i) $ 的直线段.于是对于任意的 $i\ge N(k) $ 都有
$$
  L_h(\tilde{\gamma}_i)=\int^1_0\sqrt{\langle \dot{\tilde{\gamma}_i},\dot{\tilde{\gamma}_i} \rangle_h }dt\le \sqrt{\Lambda}\int^1_0\sqrt{\langle \dot{\tilde{\gamma}_i},\dot{\tilde{\gamma}_i} \rangle_{g_0} }dt=L_{g_0}(\tilde{\gamma}_i)\sqrt{\Lambda}=\frac{\sqrt{\Lambda}}{k}
$$
也就是说
$$
  d(q,q_i)\le L_g(\varphi^{-1}\circ \tilde{\gamma}_i)=L_h(\tilde{\gamma}_i)\le \sqrt\Lambda/k
$$
可见有 $d(q,q_i)\rightarrow 0 $ ,即 $f(q_i) $ 收敛到 $f(q) $ .
{{% /proof %}}

> 注意最后一步中第一个符号是 $\le $ 而不是 $= $ ,关键在于欧氏空间中所诱导的度量和欧氏空间自然的度量 $g_0 $ 有所不同.

由上可知
{{% mathbox type="blue" title=" " %}}
$M $ 上诱导的度量拓扑和流形拓扑是相同的
{{% /mathbox %}}
{{% proof %}}
由 $f $ 的连续性就可以知道,任意的度量开球也是流形拓扑中的开集.可见流形拓扑细于度量拓扑.

反之,对于 $M $ 中任一点 $q $ 的开领域 $U $ ,形变到有Chart $(\varphi,U,V=B_1(0)) $ .重复前面证明中的步骤,可得 $\forall p \notin U $ , $d(p,q)\ge \sqrt{\lambda}/2 $ ,即半径为 $\sqrt{\lambda}/2 $ 的开球含于 $U $ 中,也就是说度量拓扑细于流形拓扑.

综上可知,两拓扑相同.
{{% /proof %}}

但是若再进一步考虑距离函数 $d(\cdot,p) $ 的光滑性,一般而言就没有上面连续性那样好的性质.例如对于欧氏空间中的
$$
  d(0,x)=\sqrt{x_1^2+x_2^2}
$$
就在 $0 $ 处不光滑.但是在其他位置都光滑.且 $d^2(0,x) $ 总是处处光滑的.

一般地,对于黎曼流形 $(M,g) $ 
1. $d(\cdot,p) $ 一般在 $q=p $ 处不是光滑的,但 $d^2(\cdot,p) $ 总是处处光滑的.
2. $d(\cdot,p) $ 在 $U\setminus {p} $ 中是光滑的,其中 $U $ 是 $p $ 的领域,但是整体上可能在某些点处并不光滑,例如对于 $(S^2,g_{round}) $ 考虑 $p=(0,0,-1) $ 也就是南极点,定义
$$
  f(q)=d(p,q)=\pi(1-\arccos{z})=\pi(1-\arccos{\sqrt{1-x^2-y^2}})
$$
在北极点也并不光滑.

从上例可见, $g_{round} $ 所诱导的并不欧氏距离,因为欧氏距离只有在 $p $ 一点处不光滑,由此再次说明了,度量结构并非都可以由任意的黎曼度量所诱导出来.

### 4. 黎曼测度

### 5. 线性联络
线性联络是一个定义在切丛上的结构.联络,顾名思义,就是联系两个不同的点点切空间,有了如此的结构,自然地就可以定义出
* 矢量沿一条曲线丛一点到另一点的**平行移动**.
* 矢量场 $Y $ 沿着 $X $ 的方向导数,也就是**协变导数**.

下面将会看到的是,这两个概念实际上是可以相互导出的,平行移动是一个很直观的概念,而协变导数在后面的应用中会更加方便.所以就像是在拓扑中先发展了邻域公理,后面觉得麻烦又发展出了现在的开集公理一样,也会先发展平行移动公理,导出协变导数,再反过来用协变导数公理导出平行移动.

另外,值得注意的是,联络结构与黎曼度量结构并没有关系.在侯伯元侯伯宇老师的书中有对联络流形更详细的介绍.

##### 平行移动公理
首先依然是考虑一些简单的例子,然后对其做一般性推广.
* 在 $\R^2 $ 中,由于任何一点的切空间都就是 $\R^2 $ 本身,所以有一个典范(canonical)的全局坐标来表示每个点的切向量,于是一个向量的平行移动可以认为就是不改变方向的移动.
* 在 $S^2 $ 中就有非平凡的情况,一个切于北极点的向量沿着不同的经线做自然的平行移动,移动到南极点 (这里的平行移动是指保持向量始终与所选经线的夹角不变),很容易看到其所得到的结果在南极点并不想同.也就是说,在 $S^2 $ 上的平行移动是依赖于所选择的路径的.

于是可以做一般的推广
{{% mathbox type="green" title="平行移动公理" %}}
平行移动结构是指一个集合:
$$
  \Set{P^\gamma|\gamma\small{\text{为流形上的分段光滑曲线}} }
$$
$\gamma:[a,b]\rightarrow M $ ,其中 $P^\gamma:T_{\gamma(a)}M\rightarrow T_{\gamma(b)}M $ 为线性同构,满足
1.  $P^{\gamma_1\circ \gamma_2}=P^{\gamma_2}\circ P^{\gamma_1} $ .
2.  $P^{-\gamma}=(P^\gamma)^{-1} $ .
3.  $P^\gamma $ 是关于 $\gamma $ 光滑的.
4.  若$\gamma_1,\gamma_2 $ 有 $\gamma_1(0)=\gamma_2(0),\dot{\gamma_1}(0)=\dot{\gamma_2}(0)   $ ,则对于任意的 $X_0\in T_{\gamma_1(0)}M $ , 有
  $$
    \frac{d}{dt}|_{t=0}P^{\gamma_1}_{0,t}(X_0)=\frac{d}{dt}|_{t=0}P^{\gamma_2}_{0,t}(X_0)
  $$
  其中 $P^{\gamma_1}_{t_1,t_2}(X_0) $ 是指沿曲线 $\gamma([t_1,t_2]) $ 的平行移动.也就是说 $P^\gamma_{0,t}(X) $ 实际上是切丛中的一条起于 $(\gamma(0),X) $ 的曲线.

{{% /mathbox %}}

其中 "$P^\gamma $ 是关于 $\gamma $ 光滑的"可以如下理解.考虑 $M $ 中的开集 $U $ ,对任意的 $u\in U $ , $\gamma_u:[0,1]\rightarrow M $ 为曲线,满足 $\gamma_u(0)=u $ ,且 $\gamma_u $ 光滑依赖于 $u $ ,即
$$
  \Gamma:U\times [0,1]\rightarrow M
$$
是光滑的.考虑 $X\in \Gamma^\infty(TM) $ ,下面映射
$$
  U\rightarrow TM 
  \\ u\mapsto P^{\gamma_u}(X_u)
$$
就定义了 $P^\gamma $ 对 $\gamma $ 对光滑性.

给定了这样的平行移动,就可以考虑 $M $ 上的方向导数,仍然先考虑欧氏空间 $\R^m $ ,对于 $X,Y\in \Gamma^\infty(T\R^m) $ ,有 $Y $ 沿 $X $ 的方向导数为
$$
  (D_XY)(x)=\lim_{t\rightarrow 0}\frac{Y(x+tX)-Y(x)}{t}
$$
要对其进行一般的推广,有一个很大的问题,即' $x+tX $ '在流形中是什么东西?进步一想到,实际上 $Y(x+tX) $ 想表示的是 $Y $ 在 $\gamma(t) $ 处的向量,该曲线满足 $\gamma(0)=x,\dot{\gamma}(t) =X(\gamma(t)) $ ,也就是说 $p+tX $ 可用上曲线代替
$$
  D_XY=\lim_{t\rightarrow 0}\frac{Y(\gamma(t))-Y(p)}{t}
$$
又遇到了新的问题,也就是上两个矢量不在同一个线性空间,无法做差,于是引入平行移动.也就是说在平行移动公理下,协变导数定义为
$$
  D_XY=\lim_{t\rightarrow 0}\frac{(P^\gamma_{0,t})^{-1}Y(\gamma(t))-Y(p)}{t}
$$
但显然,这看上去就很麻烦,更别说后面具体的计算了.所以下面考虑先直接引入协变导数.

##### 协变导数公理
先给出
$$
  \begin{align*}
  &D:\Gamma^\infty(TM)\times \Gamma^\infty(TM)\rightarrow \Gamma^\infty(TM)
  \\
  &(x,y)\mapsto D_XY
  \end{align*}
$$
局域上,有 $X=X^i\partial_i,Y=Y^j\partial_j $ ,于是在 $\R^m $ 中有
$$
  D_XY=X^iD_{\partial_i}(Y^j\partial_j)=X^i(\partial_i Y^j)\partial_j
$$
为了进行一般的推广,分别考虑对 $X,Y $ 的依赖,有
1. $D_{fX}Y=fD_XY $ ,也就是说对 $DY $ 是 $C^\infty(M) $ 线性的.
2. $D_X(fY)=fD_XY+(Xf)Y $ ,也就是说 $D_X $ 满足 Leibniz 律.

但要注意,Lie导数也是 $Y $ 沿着 $X $ 的某种方向导数,但并不是一个好的选择.因为Lie导数对 $X $ 不是 $C^\infty(M) $ 线性的.一个良好定义的方向导数在某处的求导,应该只依赖于该点处的方向,而Lie导数中用 $\phi_X $ 拉回时就用到了附近的 $X $ .所以这里重新定义了方向导数.

{{% mathbox type="green" title="线性联络" %}}
$M $ 上的一个线性联络 $\nabla $ 是指一个双线性映射
$$
  \begin{align*}
    &\nabla:\Gamma^\infty(TM)\times \Gamma^\infty(TM)\rightarrow \Gamma^\infty(TM)
    \\
    &(X,Y)\rightarrow \nabla_XY
  \end{align*}
$$
满足
1.  $\nabla_{fX}Y=f\nabla_XY $ .
2.  $\nabla_XfY=X(f)Y+f\nabla_XY $ .

{{% /mathbox %}}

可见,相较于前面用平行移动所定义的协变导数,显然是这个更方便.

再次考虑在 $\R^m $ 中
$$
  \begin{align*}
    \nabla_XY&=X^i\nabla_{\partial_i}(Y^j\partial_j)
    \\
    &=X^i\partial_i(Y^j)\partial_j+X^iY^j\nabla_{\partial_i}\partial_j
    \\
    &=X^i\partial_i(Y^j)\partial_j+X^iY^j\gamma^k{}_{ij}\partial_k
  \end{align*}
$$
任意局域上的一个 $\gamma^k{}_{ij} $ 都定义了 $\R^m $ 上的一个线性联络.

将 $\nabla $ 视为
$$
  \begin{align*}
    &\Gamma^\infty(TM)\rightarrow \Gamma^\infty(T^*M\otimes TM)
    \\
    &Y\mapsto \nabla Y
  \end{align*}
$$
其中 $\nabla Y(X,\omega)=\omega(\nabla_XY) $ ,很自然地有 $X $ 的 $C^\infty(M) $ 线性,以及
$$
  \nabla(fY)=df\otimes Y+f\nabla Y
$$
同样自然导出了其 Leibniz 律.更一般地,对于 $M $ 上的任意矢丛 $E $ ,都可定义线性联络
$$
  \nabla:\Gamma^\infty(TM)\rightarrow \Gamma^\infty(T^*M\otimes E)
$$
满足
$$
  \nabla(fs)=df\otimes s+f\nabla s,f\in C^\infty(M),s\in \Gamma^\infty(E)
$$
又考虑到微分算子是指 $M $ 上两个丛的截面之间的线性映射
$$
  \Gamma^\infty(E)\rightarrow \Gamma^\infty(F)
$$
那么 $E $ 中的联络就是指从 $E $ 中截面到 $T^*M\otimes E $ 中截面的一阶微分算子.

##### 线性联络的性质
* 局域性 $1 $ :若在 $U $ 上有 $X=\tilde{X},Y=\tilde{Y} $ ,那么
$$
  \nabla_XY=\nabla_{\tilde{X}}\tilde{Y}
$$
* 局域性 $2 $ :若 $X(p)=\tilde{X}(p) $ ,于是
$$
  (\nabla_XY)(p)=(\nabla_{\tilde{X}}Y)(p)
$$
  这也正是前面提到的线性联络所诱导的协变导数更适合作为方向导数的原因,即只依赖于所考虑点处的方向.也就是说在后面的讨论中,可以考虑 $D_v Y $ , $v \in T_pM $ 这样的东西.

* 局域性 $3 $ : 令 $\gamma:[-\epsilon ,\epsilon ]\rightarrow M $ 是一条光滑曲线, $\gamma(0)=p,\dot{\gamma}(0)=v  $  ,设 $X,Y,\bar{Y} $ 为 $M $ 上的向量场,满足 $X(P)=v $ ,且 $Y(\gamma(t))=\bar{Y}(\gamma(t)) $ .则有
$$
  \nabla_XY(p)=\nabla_X\bar{Y}(p)
$$
  即并不需要 $Y $ 在某邻域中的全部信息,只需要沿某一条曲线的信息即可.


















































































___
___
___
___
___
___
___
___
___
___