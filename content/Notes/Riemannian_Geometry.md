+++
date = '2026-07-09'
draft = false
title = 'Riemannian Geometry'
+++

##  Prelimiaries

### 光滑流形

## Riemannian Manifolds


### 2. 黎曼度量



### 3. 黎曼距离

#### 3.1 曲线的长度
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
证明: 假设曲线 $\gamma:[a,b]\rightarrow M $ 的另一个参数化为 $\gamma_1:[c,d]\rightarrow M $ .于是,存在 $t_1:[a,b]\rightarrow [c,d] $ 即
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
完成证明 $\Box $ .

用类似地方式可以证明,若 $Id:\varphi:(M,g_M)\rightarrow (N,g_N) $ 是一个局部的isometry,于是对于 $M $ 中任何的光滑曲线 $\gamma $ 都有
$$
  L(\gamma)=L(\varphi\circ \gamma)
$$
{{% proof %}}
123

{{% /proof %}}




















___
___
___
___
___