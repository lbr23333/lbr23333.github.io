---
title : "ordinary differential equation"
weight : 1
ShowToc : true
TocOpen : true 
---

# 基本概念

## 例子与定义
* 二体问题
* 最速降线,考虑平面直角坐标系中从 $(0,h) $ 滑到 $(l,0) $ .考虑到动能为
$$
  \frac{1}{2}mv^2(x)=mg(h-y(x))
$$
可得到速度 $v=\sqrt{2g(h-y)} $ ,于是时间
$$
  T=\int^l_0\frac{ds}{v(x)}=\int^l_0\frac{\sqrt{1+y'(x)^2}}{\sqrt{2g(h-y(x))}}dx
$$
还有 $y(0)=h,y(l)=0 $ .这里的 $T[y] $ 实际上是一个泛函.伯努利用光学得到了类似的结果
$$
  \frac{\sin\varphi}{v(x)}=c
$$
也就是
$$
  \frac{\frac{1}{\sqrt{1+y'(x)^2}}}{\sqrt{2g(h-y(x))}}=c
$$
伯努利时期的人擅长于一些曲线的方程构造,所以当时人们一眼就看出来这是一个摆线方程.然而到这只是浅显地解决了这个问题,Euler对其做了一般的推广,也就是变分法.考虑
$$
  T[y+z]-T[y]
$$
其中 $z $ 很小,且 $z(0)=z(l)=0 $ 从而固定了边界.令
$$
  L[y,y']=\frac{\sqrt{1+y'(x)^2}}{\sqrt{2g(h-y(x))}}
$$
则
$$
  \begin{align*}
    &T[y+z]-T[y]
    \\
    =&\int^l_0(L[y+z,y'+z']-L[y,z])dx
    \\
    =&\int^l_0(L[y,y']+\frac{\partial L}{\partial y}z+\frac{\partial L}{\partial y'}z'+\mathcal{O}-L[y,y'])dx
    \\
    =&\int^l_0(\frac{\partial L}{\partial y}z+\frac{\partial L}{\partial y'}z')dx+\mathcal{O}(\dots)
    \\
    =&\int^l_0(\frac{\partial L}{\partial y}z)dx+\frac{\partial L}{\partial y'}z\big|^l_0-\int^l_0\frac{d}{dx}(\frac{\partial L}{\partial y'}z)dx+\mathcal{O}(\dots)
    \\
    =&\int^l_0(\frac{\partial L}{\partial y}-\frac{d}{dx}\frac{\partial L}{\partial y'})zdx+\mathcal{O}(\dots)
  \end{align*}
$$
Euler 定义其中的
$$
  \frac{\delta T}{\delta y}=\frac{\partial L}{\partial y}-\frac{d}{dx}\left ( \frac{\partial L}{\partial y'} \right ) 
$$
泛函极值等价于 $\delta T/ \delta y=0 $ .于是就得到了Euler-Lagrange方程
$$
  \frac{\partial L}{\partial y}-\frac{d}{dx}\left ( \frac{\partial L}{\partial y'} \right ) =0
$$

* Lens的形状方程
* 人口模型
* 恒等式证明,考虑
$$
  f(x)=\sum_{n\ge 1}\frac{x^m}{n^2C^n_{2n}}
$$
对于不熟悉级数展开而无法注意到其等价函数的情况,可以如下操作.
$$
  \begin{align*}
    & f'(x)=\sum_{n\ge 1}\frac{2nx^{2n-1}}{n^2C^n_{2n}}
    \\
    & f''(x)=\sum_{n\ge 1}\frac{2n(2n-1)x^{2n-2}}{n^2C^n_{2n}}
  \end{align*}
$$
令 $n=m+1 $ 可以得到
$$
  f''(x)=1+\sum_{m\ge 1}\frac{m^2x^{2m}}{m^2C^m_{2m}}=1+\frac{1}{4}(x\frac{d}{dx})^2f(x)
$$
再加之 $f(0)=0,f'(0)=0 $ 就有
$$
  f(x)=2(\arcsin\frac{x}{2})^2
$$
特别地,取 $x=1 $ ,有
$$
  \sum_m\frac{1}{n^2C^n_{2n}}=\frac{\pi^2}{18}
$$

* 反函数定理的证明:这应该是这几个例子中对于后面的数学最nontrivial的一个.考虑 $\R^n $ 中的一个区域 $\Omega $ ,
$$
  f:\Omega\rightarrow \R^n
$$
是 $C^1 $ 的,且对于 $\Omega $ 中的 $x_0 $ , $det f'(x_0)\ne 0 $ .那么存在 $x_0 $ 的开领域 $U $ 使得 $f:U\rightarrow f(U) $ 是双射,则 $f^{-1}:f(U)\rightarrow U $ 也是 $C^1 $ 的,记 $f'(x_0)=A $ ,考虑加上一个「扰动项」 $\varphi $ (余项),使得
$$
  f(x)=f(x_0)+A(x-x_0)+\varphi(x)
$$
于是 $\frac{\partial\varphi}{\partial x_j}=\frac{\partial f_i}{\partial x_j}-A_{ij} $ 连续,且 $\frac{\partial \varphi_i}{\partial x_j}(x_0)=0 $ .考虑
$$
  f_t(x)=f(x_0)+A(x-x_0)+t\varphi(x)
$$
当 $t=0 $ 时显然是可逆的,因为就是线性的函数.而要证明 $t=1 $ 时仍有局部上的可逆性,实际上可以证明对于任意的 $t\in [0,1] $ 都是可逆的.
$$
  \begin{equation}
    y=y_0+A(x(t)-x_0)+t\varphi(x(t))
  \end{equation}
$$
若反函数存在,则上式对于任意的 $y,t $ 都成立,也就是.对上式求导
$$
  0=A\frac{dx(t)}{dt}+\varphi(x(t))+t\sum^n_{j=1}\frac{\partial \varphi_i}{\partial x_j}\frac{dx_j(t)}{dt}
$$
即
$$
  \sum_{j=1}^n(A_{ij}+t\frac{\partial \varphi_i}{\partial x_j})\frac{dx_j}{dt}=-\varphi_i(x+t)
$$
所以反函数存在等价于上微分方程有解.二对于任意的 $t\in [0,1] $ 存在 $U $ ,使得 $U $ 上有
$$
  \det (A_{ij}+t\frac{\partial \varphi_i}{\partial x_j})\ne 0
$$
上方程即
$$
  \frac{dx_j}{dt}=-()^{-1}_{jk}\varphi_k(x(t))
$$
根据后面将证明的ODE解的存在性就可得到, $x_i $ 存在于 $t\in [0,1] $ .


## 几何解释

考虑自治方程
$$
  y'_i=f_i(y),i=1,\dots,n
$$
有解为 $y_i=\varphi_i(x) $ , $i=1,\dots,n $ 使得
$$
  \varphi'_i=f_i(\varphi(x))
$$
考虑 $(y_1,\dots,y_n)\in \Omega $ ,映射
$$
  \varphi:J\rightarrow \Omega
  \\
  x\mapsto (\varphi_1(x),\dots,\varphi_n(x))
$$
令 $\Gamma=Im(\varphi) $ ,于是又有逢曲线必考虑的
1.  $\varphi $ 是曲线,包含了参数化信息.
2.  $\Gamma $ 是古典上的曲线,更严格来说称之为一维子流形,所以后面都这样叫.

例如考虑 $\R^3 $ 中的曲线,可用两曲面交得
$$
  \begin{cases}
    F_1(x,y,z)=0\\F_2(x,y,z)=0
  \end{cases}
$$
其解是否为一个一维子流形,就要用到欧氏空间中的反函数定理等(也就是淑芬中学的).
1.  $\R^n $ 中一个一维子流形 $\Gamma $ 是指,在 $\Gamma $ 上任意一点都可以选取一个局域的Chart( $\varphi,U,V $ ), $\varphi:x\mapsto y(x) $ 使得在 $V $ 中, $U\cap \Gamma $ 可以表示为
$$
  U\cap \Gamma=\Set{x\in U|y^2(x)=\dots=y^n(x)=0}
$$
也就是曲线的拉直.

2. 在 $\varphi:J\rightarrow \R^n $ 的语言下,一维子流形就还要考虑是否正则. $\Gamma=Im(\varphi) $ 是 $\Omega $ 中的一维正则子流形,当且仅当满足下面条件
   *  $\varphi $ 是单的
   *  $\varphi'\ne 0 $ 
   *  $\varphi:J\rightarrow \Gamma $ 是同胚
    (即 $\varphi $ 是一个嵌入)

