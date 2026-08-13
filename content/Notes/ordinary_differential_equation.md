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
当 $t=0 $ 时显然是可逆的,因为就是线性的函数.而要证明 $t=1 $ 时仍有局部上的可逆性,实际上可以证明对于任意的 $t\in [0,1] $ 都是可逆的.现在固定一个 $y $ ,寻找 $f_t $ 下 $y $ 的原像,由于随 $t $ 的改变会使得该原像改变,所以记作 $x(t) $ , $f_t(x(t))=y $ ,即有
$$
  \begin{equation}
    y=y_0+A(x(t)-x_0)+t\varphi(x(t))
  \end{equation}
$$
若反函数存在,则上式对于任意接近 $y_0 $ 的 $y,t $ 都成立,也就是.对上式求导
$$
  0=A\frac{dx(t)}{dt}+\varphi(x(t))+t\sum^n_{j=1}\frac{\partial \varphi_i}{\partial x_j}\frac{dx_j(t)}{dt}
$$
即
$$
  \sum_{j=1}^n(A_{ij}+t\frac{\partial \varphi_i}{\partial x_j})\frac{dx_j}{dt}=-\varphi_i(x(t))
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

### 一般形式常微分方程的建立
1. 单个自变量: $x $ 或 $t $ .(多个自变量是PDE).
2. 多个因变量: $y'(x),\dots,y^{(n)}(x) $ 或 $x'(t),\dots,x^{(n)}(t) $ .
3. 方程: 一般而言,有多少因变量就有多少方程.

于是可以将ODE一般地表示为
$$
  F_i(x,y_1,\dots,y_n;y_1',\dots,y_n';\dots;y^{(N)}_1,\dots,y^{(N)}_n)=0
$$

注意:虽然自变量的个数一般是有限个,但是方程中可能会出现无穷多次导数,如斐波那契列
$$
  \begin{align*}
    &u(x+2)=u(x+1)+u(x)
    \\
    &\sum_{k=0}^\infty\frac{u^{(k)}(x)}{k!}2^k=\sum_{k=0}^\infty\frac{u^{(k)}(x)}{k!}+u(x)
  \end{align*}
$$
就出现了无穷多阶导数,一般称之为差分方程.但是在该课程中只会考虑有限次导数.

### 化简
1. 高阶变一阶
$$
  y''+y=0
$$
令 $y_1=y,y_2=y' $ ,于是上面的方程就是
$$
  y_1=y_2
  \\
  y_2'=-y_1
$$
对于上面一般形式
$$
  F_i(x,y_1,\dots,y_n;y_1',\dots,y_n';\dots;y^{(N)}_1,\dots,y^{(N)}_n)=0
$$
就可以令 $y_{i,k}=y^{(k)}_i $ , $i=1,\dots,n,k=0,\dots,N-1 $ ,得到
$$
  F_i(x;y_1,\dots,y_m;\dots;y_{1,N-1}',\dots,y_{n,N-1}')=0
$$
进一步还有 $y'_i,k=y_{i,k+1} $ , $i=1,\dots,n,k=0,\dots,N-2 $,一共就有 $n+n(N-1)=nN $ 个方程.取 $m=nN $ ,重编号为 $y_1,\dots,y_m $.保持了原方程的因变量数等于方程数.另外,可以将 $y_1,\dots,y_n $ 理解为一个矢量的分量.于是更简单地,可以将一般方程记作
$$
  F_i(x,y,y')=0
$$
这样的形式.

2. 隐式变显式:
$$
  y'_i=f_i(x,y),i=1,\dots,n
$$
利用隐函数定理局部求解后一般就写成这个结果.

3. 非自治变自治(非必要)
$$
  y'_i=f_i(x,y)
$$
所谓的**自治**是指 $f_i $ 不依赖 $x $ ,否则就死非自治的.非自治变自治总是容易实现的,直接将 $x $ 当作为 $y $ 的一个分量,即令 $y_{n+1}=x $ ,微分方程即为
$$
  \begin{cases}
    y_i=f_i(y_{n+1};y),i=1,\dots,n
    \\
    y_{n+1}'=1
  \end{cases}
$$
就成了自治方程,可记作
$$
  y'_i=f_i(y),i=1,\dots,n
$$

### 方程的解
设 $\Omega $ 是 $\R^n $ 中的一个区域, $I $ 是 $\R $ 中的一个区间,
$$
  f_i:I\times\Omega\rightarrow \R,i=1,\dots,n
$$
满足一定的条件,于是可以研究
$$
  \begin{equation}
    \frac{dy_i}{dx}=f_i\left ( x,y \right ) i=1,\dots,n
  \end{equation}
$$
若存在 $I $ 的一个子区间 $J $ 以及映射
$$
  \varphi:J\rightarrow \Omega,x\mapsto(\varphi(x),\dots,\varphi_n(x))
$$
使得
$$
  \frac{d\varphi_i}{dx}=f_i\left ( x,\varphi \right ) i=1,\dots,n
$$
那么就称 $\varphi $ 是上(2)式的解.

例子:(注意到这里还并没有引入具体的求解技巧,所以可以认为下面的结果都是瞪出来的)

1️⃣  $y'=f(x) $ , $y=\int_{x_0}^xf(x)dx+Const. $ 若再要求 $y(x_0)=y_0 $ ,则有唯一解 $Const.=y_0 $ .一般而言, $y_i'=f_i(y) $ , $i=1,\dots,n $ 的解中可以包含 $n $ 个任意常数.

2️⃣  $y'=ry $ , $y=y_0e^{rx} $ 

3️⃣  $y''+y=0 $ , $y(x)=c_1\cos x+c_2\sin x $ , $c_1,c_2\in \R $,其解构成一个二维的线性空间. 

4️⃣  $y''+3yy'+y^3=0 $ , $y(x)=\frac{P'(x)}{P(x)} $ , $P(x)=C_0+C_1x+C_2x^2 $ .乍一看似乎非常奇怪,因为二阶方程得到了三个未定的常数.实际上,解应该是
$$
  y(x)=\frac{c_1+2c_2x}{c_0+c_1x+c_2x^2}
$$
满足 $y(x,c_0,c_1,c_2)=y(x,\lambda c_0,\lambda c_1,\lambda c_2) $ ,且 $(c_0,c_1,c_2)\ne (0,0,0) $ .可见解实际上在一个 $\mathbb{RP}^{2}  $ 流形上,当 $C_0\ne 0 $ 时, 就可以只由 $2 $ 个常数表示解.

> 微分方程 $y'_i=f_i(x,y) $ 的解的全体一般而言构成一个 $n $ 维流形.上面的 $c_0\ne 0 $ 就是因为一个局部Chart无法cover整个 $\mathbb{RP}^{2} $ 这在ODE中是常见的,ODE总是在一个局域的Chart中表示,所以总会因此丢失一些信息.实际上,上面的解的三个Chart $c_0\ne 0,c_1\ne 0,c_2\ne 0 $ 构成了 $\mathbb{RP}^{2}  $ 的一个图册.总之,解出来的通解仍不一定是全部的解.

设 $\Omega,I,f_i $ 与前一致,若存在 $I $ 的子区间 $J $ 和 $\R^n $ 的开子集 $U=\Set{(c_1,\dots,c_n)}$ 以及映射
$$
  \varphi:J\times U\rightarrow \Omega
$$
使得对于任意的 $c\in U $ , $\varphi(\cdot,c):J\rightarrow \Omega $ 是 $(2) $ 式的解,且对于任意的 $x,c $  $\det(\frac{\partial\varphi_i}{\partial c_j})_{i,j=1,\dots,n}(x,c)\ne 0 $ ,则称 $\varphi $ 给出了 $(2) $ 的一个**通解**.

### 定解条件
对于方程
$$
  y'_i=f_i(x,y),i=1,\dots,n
$$
称 $y_i(x_0)=y_{i,0} $ 为初值条件.(在考虑物理问题时, $x $ 一般是时间,所以一般就取为0).
$$
  \boxed{\text{方程+初值条件}\rightarrow \text{初值问题}}
$$
一般又称为Cauthy问题.

弦振动问题 $y''+y=0 $ ,将其两端固定 $y(0)=0,y(1)=0 $ 就是边值条件.
$$
  \boxed{\text{方程+边值条件}\rightarrow \text{边值问题}}
$$
边值问题相较于初值问题而言更可能**零解**,例如上问题 $y=0 $ ,该问题出现零解的原因在于差一个常数,若考虑 $y''+\lambda y=0 $ ,在 $\lambda=? $ 时会有非零解?解得
$$
  y=c_1\cos \sqrt{\lambda}x+c_2\sin\sqrt{\lambda}x
$$
若要求满足上面的边值条件,只有让 $\lambda=(n\pi)^2 $ 才可得到非零解.

后面考虑的问题大多都是初值问题.

> 从几何上来讲,出现这一问题其实很容易理解,初值问题所给出的类似 "$y(0)=a,y'(0)=b $ "这样的条件是局域的,它只关系到一个点;而边值问题给出整个边界的条件,是全局的,其必须与动力学相容,而前面也提到ODE是局域演化的,所以就容易出现问题.可以说:边值问题筛选轨迹,而初值问题直接决定了一个轨迹.





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
2.  $\Gamma $ 是古典上的曲线,更严格来说称之为**一维子流形**,所以后面都这样叫.

例如考虑 $\R^3 $ 中的曲线,可用两曲面交得
$$
  \begin{cases}
    F_1(x,y,z)=0\\F_2(x,y,z)=0
  \end{cases}
$$
其解是否为一个一维子流形,就要用到欧氏空间中的反函数定理等(也就是淑芬中学的).下面是一些关于曲线与一维子流形常用的结论:
1.  $\R^n $ 中一个一维子流形 $\Gamma $ 是指,在 $\Gamma $ 上任意一点都可以选取一个局域的Chart( $\varphi,U,V $ ), $\varphi:x\mapsto y(x) $ 使得在 $V $ 中, $U\cap \Gamma $ 可以表示为
$$
  U\cap \Gamma=\Set{x\in U|y^2(x)=\dots=y^n(x)=0}
$$
也就是曲线在 Chart 中的拉直.

2. 在 $\varphi:J\rightarrow \R^n $ 的语言下,一维子流形就还要考虑是否正则. $\Gamma=Im(\varphi) $ 是 $\Omega $ 中的一维正则子流形,当且仅当满足下面条件
   *  $\varphi $ 是单的
   *  $\varphi'\ne 0 $ ( $d\varphi $ 为单)
   *  $\varphi:J\rightarrow \Gamma $ 是同胚
    (即 $\varphi $ 是一个嵌入)

在ODE中第一个和第三个条件一般来说都是相对容易实现的,更多的是对第二个条件的考虑.若将ODE视为一条曲线,那么 $\varphi'\ne 0 $ 也就是曲线的切向量 $X\ne 0 $ .考虑标准的捕食者—被捕食者模型(Lotka-Volterra Model)
$$
  \begin{align*}
    u'=u(-\alpha+\beta v),v'=v(\gamma-\delta u)
  \end{align*}
$$
若边值条件为
$$
  u_0(t)=\gamma/\delta,v_0(t)=\alpha/\beta
$$
那么就始终有 $u'=v'=0 $ ,也就是曲线的切向量始终为 $0 $ ,即对应的是流形上的一个点.

另外,对于前面曲线和一维子流形,其切向量的描述也是有些不同的.具体来说,由于一维子流形没有一个具体的参数化,所以其切向量可以乘上任意的倍数;而对于曲线就有一个标准的切向量场.有了切向量的概念,就可以讨论ODE与曲线的相切:
{{% mathbox type="green" title="" %}}
对于
$$
  \frac{dx_i}{dt}=X_i(t),i=1,\dots,n
$$
与 $\Omega $ 中一个一维子流形 $\Gamma $ ,若对于任意的 $p\in \Gamma $ 有 $X(p)\in T_p\Gamma $ ,那么称 $\Gamma $ 与 $X $ 相切.
{{% /mathbox %}}







---
---
---
---
---