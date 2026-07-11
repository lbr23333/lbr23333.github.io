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
有 $(V,h) $ 与 $(U,g|_U) $ 同构.令
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









___
___
___
___
___