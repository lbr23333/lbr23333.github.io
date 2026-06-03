---
title : "lecture note on superstring"
description : "还不太会，真的劳累"
date : 2026-05-18
weight : 1
---
- [Preliminaries](#preliminaries)
  - [1.路径积分与配分函数](#1路径积分与配分函数)
  - [2.对称与守恒](#2对称与守恒)
- [玻色弦](#玻色弦)
- [超弦](#超弦)
  - [0.Majorana表示与一些约定](#0majorana表示与一些约定)
  - [1.超对称变换](#1超对称变换)
  - [2.超对称作用量](#2超对称作用量)
  - [3.超空间与超场](#3超空间与超场)
  - [4.RNS边界条件](#4rns边界条件)
  - [5.RNS弦的量子化](#5rns弦的量子化)
  - [6.GSO投影](#6gso投影)


### Preliminaries

#### 1.路径积分与配分函数

#### 2.对称与守恒

介绍一个在场论中没那么常用的方法:
{{% mathbox type="blue" title="Noether方法" %}}
对于一个具有全局对称性的 $d $-  维系统,对称性由参数 $\epsilon  $ 描述.若先将其局域化为 $\epsilon(\sigma) $ ,那么对于变换 $\phi\rightarrow \phi+\epsilon^\mu(\sigma)\partial _\mu\phi(\sigma) $ ,由于是一个对称性变换,作用量不变 $\delta S=0 $ .  可知 $\boxed{\delta S=\int d^d\sigma j^\mu_\alpha\partial ^\alpha\epsilon_\mu }$ ,因为只有这样才能使得当 $\sigma $ 回到全局的常数时有 $\delta S=0 $ .

进一步,由分布积分, $\int d^2\sigma \partial ^\alpha j^\mu_\alpha\epsilon =0 $ ,即有 $\boxed{\partial ^\alpha j_\alpha^\mu=0} $ .

还有守恒荷 $Q^\mu=\int d^{d-1}\sigma j^\mu_0 $ ,有 $\boxed{\frac{dQ^\mu}{d\tau}=0} $ . 因为
$$
  \frac{dQ^\mu}{d\tau}=\int d^{d-1}\sigma \frac{dj^\mu_0}{d\tau}=\int d^{d-1}\sigma \sum_{i=1}^{d-1}\partial_ij^\mu_i
  =\int_{\Sigma\rightarrow \infty} dS_i j^\mu_i=0
$$

{{% /mathbox %}}

Ward恒等式:生成元 $\sim $ 守恒荷

考虑 $\phi'(x)=\phi(x)-i\omega_aG_a\phi $ , $\langle O \rangle=\langle \phi(x_1)\dots\phi(x_n) \rangle $ ,令 $\langle 1 \rangle =1 $ ,于是 $\langle O \rangle =\frac{1}{Z}\int [D\phi]O(x)e^{iS} $ , $\langle O' \rangle = \frac{1}{Z}\int [D\phi']O(x')e^{iS'} $ ,解析延拓到欧氏时空,那么
$$
  \begin{align*}
    \delta\langle O \rangle &=\langle \delta O \rangle =\langle O'-O \rangle =\langle O' \rangle -\langle O \rangle 
    \\
    & =\int d^d x\partial _\mu \langle j^\mu_a O \rangle  \omega^a
  \end{align*}
$$
这里假设了 $\delta\left| \Omega \right\rangle =0$. 而另一方面,记 $\phi(x^1)=\phi^1 $ , 有
$$
  \langle \delta O \rangle =\langle \sum_{j=1}^k \phi^1\dots\delta \phi^j\dots\phi^k \rangle =-i\omega_a\langle \sum_{j=1}^k \phi^1\dots G_a\phi^j\dots\phi^k \rangle 
$$
对比上下两式,可得
$$
  \partial_\mu\langle j^\mu_a(x)O(y) \rangle =-i\langle  \sum_{j=1}^k \phi^1\dots G_a\phi^j\dots\phi^k\rangle \delta(x^j-y^j)
$$

考虑到在全区域积分中全导数项为 $0 $ , 即有
$$
  0=-i\langle  \sum_{j=1}^k \phi^1(y^1)\dots G_a\phi^j(y^j) \dots\phi^k(y^k) \rangle
$$
若再对于每一个 $y_j $ 考虑,即积分区域不再是全区域,而只是包含某一个 $y^j $ 的区域 $\Sigma $ ,则
$$
  \begin{align*}
    \int_{\Sigma}dx\partial _\mu\langle j^\mu O \rangle &=\int_{\partial \Sigma}dx \langle j^\mu_a O \rangle = -\int_{\Sigma^+} d\vec{x}\langle j^\mu_a O \rangle +\int_{\Sigma^-} d\vec{x}\langle j^\mu_a O \rangle
    \\
    &=-\langle Q_a|_{\Sigma^+}O \rangle +\langle Q_a|_{\Sigma^-}O \rangle
  \end{align*}
$$
由路径积分的编时,上即 $-\langle Q_a O \rangle+\langle O Q_a  \rangle =\langle [Q_a,O] \rangle  $ .即
$$
  -i\langle  \sum_{j=1}^k \phi^1(y^1)\dots G_a\phi^j(y^j) \dots\phi^k(y^k) \rangle=\langle [Q_a,O] \rangle
$$
可以发现,积分区域只包含 $\phi(y_j) $ ,其他的场根本就不重要,完全可以设为 $1 $ ,即
$$
  \boxed{[\hat Q_a,\hat\phi]=iG_a\hat\phi}
$$
更形式化一点也就是
$$
  {[\hat Q_a,\cdot]=iG_a}
$$
{{% mathbox type="slate" title=" $\langle \delta O \rangle= \int d^d x\partial _\mu \langle j^\mu_a O \rangle  \omega^a $ " %}}
证明: 考虑到 
$$
  \begin{align*}
    \langle O \rangle &=\frac{1}{Z}\int [D\phi]O[\phi]e^{-S[\phi]} 
    \\
    &=\frac{1}{Z}\int [D\phi']O[\phi']e^{-S[\phi]'} 
  \end{align*}
$$
考虑到遍历所有的场构型 $[D\phi]=[D\phi '] $ , 以及所考虑的是非反常对称,那么
$$
  \begin{align*}
    &\langle O \rangle =\langle O' \rangle 
    \\
    & =\frac{1}{Z}\int [D\phi']O[\phi']e^{-S[\phi]'} 
    \\
    & =\frac{1}{Z}\int [D\phi](O+\delta O)e^{-S-\delta S} 
    \\
    & =\frac{1}{Z}\int [D\phi](O+\delta O)(1-\delta S)e^{-S}
    \\
    & =\frac{1}{Z}\int [D\phi](O+\delta O-O\delta S)e^{-S}  
  \end{align*}
$$
于是
$$
  \begin{align*}
    &\int [D\phi](\delta O-O\delta S)e^{-S}=0
    \\
    \Rightarrow & \langle \delta O-O\delta S \rangle =0
  \end{align*}
$$
利用前面所得到的 $\delta S=-\int d^dxj^\mu_a\partial_\mu\omega_a$ 
$$
  \begin{align*}
    \langle \delta O \rangle &=\langle O\delta S \rangle 
    \\
    & =\langle -O\int d^dxj^\mu_a\partial_\mu\omega_a \rangle 
    \\
    & =-\int [D\phi] (O\int d^dxj^\mu_a\partial_\mu\omega_a )e^{-S}
    \\
    & =-\int d^dx[\int [D\phi] (Oj^\mu_a)e^{-S}]\partial_\mu\omega_a
    \\
    & = -\int d^dx\langle Oj^\mu_a \rangle \partial_\mu\omega_a
    \\
    & = \int d^dx\partial_\mu\langle Oj^\mu_a \rangle \omega_a
  \end{align*}
$$
于是完成了证明.
{{% /mathbox %}}







### 玻色弦



### 超弦
#### 0.Majorana表示与一些约定

考虑二维的Dirac gamma 矩阵,以示区分用$\rho $表示,有
$$
  \{\rho^\alpha,\rho^\beta \}=2\eta^{\alpha\beta},\eta^{\alpha\beta}=\begin{bmatrix}
    -1 &0
    \\0 & 1
  \end{bmatrix}
$$
在Majorana表示下,$\rho^0=\begin{bmatrix}0 &1\\ -1 &0\end{bmatrix} $,$\rho^1=\begin{bmatrix}0 &1\\ 1 &0\end{bmatrix} $,以及
$$
  \rho^3=\rho^0\rho^1=\begin{bmatrix}1 &0\\ 0 &-1\end{bmatrix}
$$
还有电荷共轭,$C^2=-1,C\rho^\alpha C^{-1}=-(\rho^\alpha)^{\dagger} $,可知在Majorana表现下,$C=\begin{bmatrix}0 &1\\ -1 &0\end{bmatrix}  $ .

还有Majorana条件:$\bar{\psi}=\psi^\dagger \rho^0=\psi^TC $,可见在Majorana表示下,场是实的.

一些符号约定:
* $\alpha,\beta $指标用于矢量指标,$a,b $指标用于旋量
* 有些地方会默认不写旋量指标,例如与QFT中一样约定$\rho^\alpha=(\rho^\alpha)^b_a $,$\bar{\psi}^a=\psi^T_aC^{ba} $.后面会用 $\psi_a $ 表示 $\psi_a $,$\psi^a $ 表示 $\bar{\psi}^a $,即用旋量指标的位置表示共轭,于是可知$C $可用于升降旋量指标.
$$
  \psi^a=\psi_bC^{ba}\Rightarrow \bar\psi^a=\psi^T_bC^{ba}
$$
于是
$$
  \bar{\epsilon }\psi=\epsilon^a\psi_a=\epsilon^0\psi_0+\epsilon^1\psi_1=-\psi_0\epsilon^0-\psi_1\epsilon^1=\psi^1\epsilon_1+\psi^0\epsilon_0=\bar{\psi}\epsilon
$$
其中第三步是因为交换了费米子,第四步是用$C $升降指标,注意$C $的符号导致最后又出现一个负号.




#### 1.超对称变换

假设bosons到fermions的超对称变换为
$$
  \delta_\epsilon\phi=\epsilon^a\psi_a=\bar\epsilon\psi
$$
这是自然的,因为两个费米子组合成一个玻色子.那么考虑到$(\delta_\epsilon\phi)^*=\delta_\epsilon\phi$，对上式中右边取复，有
$$
  \begin{align*}
    (\bar\epsilon\psi)^*=(\epsilon^\dagger\rho^0\psi)^\dagger=\psi^\dagger(\rho^0)^\dagger\epsilon=-\psi^\dagger\rho^0\epsilon=-\bar{\psi}\epsilon
  \end{align*}
$$
可见$\bar\epsilon\psi$是纯虚的，所以要加上一个i，再加上一个不确定的系数，即
$$
  \boxed{\delta_\epsilon\phi=iA\bar\epsilon\psi}
$$
反之，对$\psi$的超对称变换应该回到bosons，也就是说
$$
    \boxed{\delta_\epsilon\psi_a=B\epsilon_b(\rho^\alpha)^b_a\partial_\alpha\phi}
$$
注意其中$a,b$都是旋量指标。为验证其自洽性，对$\phi$做两次超对称变换，考虑不同顺序所得到的差$[\delta_{\epsilon_1},\delta_{\epsilon_2}]\phi$，计算可得 ~~这个结果中似乎省略了一些系数，一个整体的4，否则不能于下面的协变结果(1)等价~~
$$
  [\delta_{\epsilon_1},\delta_{\epsilon_2}]\phi=4(i\epsilon^{+}_1\epsilon^+_2(\partial_+\phi)+i\epsilon^{-}_1\epsilon^-_2(\partial_-\phi))
$$
注意其中$\epsilon$上的$\pm$是旋量指标，而$\partial$的$\pm$是世界面上的光锥坐标，即
$$
  \begin{align*}
    \rho^{\pm}=\rho^0\pm\rho^1,
    \rho^+=\begin{bmatrix}
       0 & 2\\
       0 & 0
    \end{bmatrix},
    \rho^-=\begin{bmatrix}
       0 & 0\\
       -2 & 0
    \end{bmatrix}
  \end{align*}
$$
于是
$$
  \begin{align*}
    &\delta_\epsilon\psi_a=B\epsilon_b(\rho^\alpha)^b_a\partial_\alpha\phi
    \\ \Rightarrow &\delta_\epsilon\psi_+=B\epsilon_b(\rho^\alpha)^b_+\partial_\alpha\phi\xlongequal{a=+唯一确定}B\epsilon_+(\rho^+)^+_-\partial_+\phi=2B\epsilon_-\partial_+\phi
    \\& =-2B\epsilon^+(\partial_+\phi)
    \\ \Rightarrow &\text{Similarly,}\delta_\epsilon\psi_-=-2B\epsilon^-(\partial_-\phi)
  \end{align*}
$$
再代入到前面的对易式并利用Grassmann数$\epsilon$的反对易关系，将整体的一个2吸收到AB中，就能得到结果。进一步简化可得
$$
  \begin{equation}
    [\delta_{\epsilon_1},\delta_{\epsilon_2}]\phi=2i(\bar\epsilon_1\rho^\alpha\epsilon_2)\partial_\alpha\phi
  \end{equation}
$$
其中计算的细节仍是对指标的把握：
$$
  2i(\bar\epsilon_1\rho^+\epsilon_2)\partial_+\phi=2i(-2\epsilon_{1,-}\epsilon_{2,-})\partial_+\phi=-4i\epsilon^+_1\epsilon^+_2\partial_+\phi
$$
第二项同理。

可见**两次超对称变换的对易子相当于一个世界面上的一个平移变换**。另一方面，对于费米子，也应该有自洽性，即考虑两次超对称变换的对易子作用到一个旋量场上，完全同理与上面的结算，可得
$$
  [\delta_{\epsilon_1},\delta_{\epsilon_2}]\psi=2i(\bar{\epsilon_1}\rho^\alpha\epsilon_2)\partial_\alpha\psi+i(\epsilon^+_2\epsilon^-_1-\epsilon^-_1\epsilon^+_2)\partial_+\psi_-+(+\leftrightarrow -)
$$
为了让理论自洽，也就是让两种场的变换一致，即需要上面两种代数一致，要求
$$
 \begin{align*}
     \begin{cases} \partial_+\psi_-=0 & 
  \\  \partial_-\psi_+=0
  & \end{cases}
  \Leftrightarrow\text{Dirac equation}
 \end{align*}
$$
也就是说，$\psi$满足Dirac方程才能使得理论自洽，即
$$
  \text{SUSY is closed on-shell under}\{\phi,\psi\}
$$
后面会介绍off-shell的方法。
___
#### 2.超对称作用量

> 每次遇到这样细节很多的计算，老师就会留作作业...

根据之前的结论，费米子场应该满足其Dirac方程，也就是说作用量所导出的费米子场的运动方程应该为Dirac方程的形式，所以作用量也是一个类似Dirac作用量的东西。于是考虑一个测试作用量:
$$
  S_{test}=\frac{1}{2\pi\alpha'}
  \int d^2\sigma\,
  \left[
    \frac12\,
    G_{\mu\nu}
    \partial_\alpha X^\mu\partial^\alpha X^\nu
    +
    iA\,G_{\mu\nu}
    \bar\psi^\mu\rho^\alpha\partial_\alpha\psi^\nu
  \right]
$$
**并重新规定前面的变换常数为**:
$$
  \boxed{\begin{align*}
    & \delta_\epsilon X^\mu=iB\epsilon^a\psi^\mu_a
    \\& \delta_\epsilon\psi^\mu_a=C\epsilon_b(\rho^\alpha)^b_a\partial_\alpha X^\mu
  \end{align*}}
$$
注意通过量纲分析
$$
  [\delta_{\epsilon_1},\delta_{\epsilon_2}]\phi=2i(\bar{\epsilon_1}\rho^\alpha\epsilon_2)\partial_\alpha
$$
其中$\delta:field\mapsto filed $应该没有量纲,故可知
$$
  [B]=[A][C],[A]^{1/2}=[C]^{-1}
$$
考虑到QFT中的费米子作用量,可知$[A]=L^2, $于是$[C]=L^{-1},[B]=L,[\psi]=L^{-1/2} $,而这些量纲总是可以通过加上$\alpha'$来使得其暂时为$0 $.进一步，为了使得该作用量在超对称变换下保持不变$\delta_\epsilon S_{test}=0$，可以得到上$A,B,C$之间的一个关系：
$$
  \begin{align*}
    &\delta_\epsilon(\frac{1}{2}\partial_\alpha X^\mu\partial^\alpha X_\mu)
    =\partial_\alpha(\delta_\epsilon X^\mu)\partial_\alpha X^\mu
    =iB\partial_\alpha(\epsilon_+\psi^\mu_--\epsilon_-\psi^\mu_+)\partial^\alpha X_\mu
    \\& iA\delta_\epsilon(\bar{\psi}^\mu\rho^\alpha\partial_\alpha\psi_\mu)=iA\delta_\epsilon(-2\psi^\mu_-\partial_+\psi_{\mu,-}-2\psi^\mu_+\partial_-\psi_{\mu,+})\partial^\alpha X^\mu
    \\& =i4AC(\partial_-X^\mu\epsilon_+\partial_+\psi_{\mu,-}+\psi^\mu_-\partial_+\partial_-X^\mu\epsilon_+)+(\epsilon_-)
  \end{align*}
$$
> 里面的$(\epsilon_-)$交给读者自己算（
> 其实算不算都无所谓了，因为只对上面的$\epsilon_+$左边分就能得到结果
> 我说这是(作业)'有没有懂的.

考虑到$0=\delta_{\epsilon^+}S$并代入上面的各项，于是得
$$
  \text{若取}B=\sqrt{\frac{\alpha'}{2}},C=\frac{1}{\sqrt{\alpha'}},then~A=\frac{\alpha'}{2}
$$
即超对称作用量为
$$
  \boxed{\begin{align*}
    S_{SUSY}&=\frac{1}{4\pi\alpha'}
  \int d^2\sigma\,
  \left[
    G_{\mu\nu}
    \partial_\alpha X^\mu\partial^\alpha X^\nu
    +
    i\alpha'G_{\mu\nu}
    \bar\psi^\mu\rho^\alpha\partial_\alpha\psi^\nu
  \right]
  \\& =\frac{1}{4\pi \alpha'}\int d^2\sigma[\partial_aX\cdot\partial^aX+i\alpha'(\psi_+\partial_-\psi_++\psi_-\partial_+\psi_-)]
  \end{align*}}
$$

#### 3.超空间与超场

显然前面所得到的作用量只是将玻色和费米的简单相加,没有显式体现出超对称.可以采取另一种方法:增加一对Grassmann 方向:
$$
  X^\mu(\sigma^0,\sigma^1)\rightarrow \Phi(\sigma^0,\sigma^1,\theta^0,\theta^1)\Rightarrow superfield
$$
其中$\theta $是Grassmann数.将其在$(0,0,\theta^+,\theta^- )$处展开,由Grassmann数的性质
$$
  \Phi(0,\theta)=\Phi^{(0,0)}+\Phi^{(0,1)}\theta^-+\Phi^{(0,1)}\theta^++\Phi^{(1,1)}\theta^+\theta^-
$$
为了match上超对称,有
$$
  \Phi=X^\mu+\sqrt{\frac{\alpha'}{2}}\psi^\mu\theta^++\sqrt{\frac{\alpha'}{2}}\psi^\mu_-\theta^-+hF^\mu\theta^+\theta^-
$$
对其进行超对称变换:
$$
  \delta\Phi=\delta X^\mu+\sqrt{\frac{\alpha'}{2}}\delta\psi^\mu\theta^++\sqrt{\frac{\alpha'}{2}}\delta\psi^\mu_-\theta^-+h\delta F^\mu\theta^+\theta^-
$$
另外由$\delta\Phi=i(\epsilon^\alpha Q_\alpha)\Phi$以及$\delta X^\mu=i\sqrt{\frac{\alpha'}{2}}(\epsilon^+\psi^\mu_++\epsilon^-\psi^\mu_-) $,对比可知
$$
  Q_\pm\sim \partial_{\theta^\pm}
$$
考虑到还有$\sqrt{\frac{\alpha'}{2}}\delta\psi^\mu\theta^+$项,即可知$Q_+$本身应该还有一个$\theta^+ $,即
$$
  Q_+=\partial_{\theta^+}+i\theta^+\partial_+,
  Q_-=\partial_{\theta^-}-i\theta^-\partial_-
$$
{{% mathbox type="slate" title="" %}}
实际上还有另一种方法确定$Q $,考虑到正确的超对称变换应该满足“两个超对称变换的对易是一次时空中的平移”:
$$
  2i\epsilon^+_1\epsilon^+_2\partial_+=[\delta_{\epsilon_1},\delta_{\epsilon_2}]=[i\epsilon^+_1Q_+,i\epsilon ^+_2Q_+]=-\epsilon^+_2\epsilon^+_1\{Q_+,Q_+ \}
$$
可知$\{Q_+,Q_+ \}=2i\partial_+ $,再令$Q_+=\partial_{\theta^+}+k $就可以解得$k=i\theta^+\partial_+$.

对于$Q_- $完全同理进行处理,但要注意前面得到时空上平移结论中的符号,$Q_-=\partial_{\theta^-}-i\theta^-\partial_- $.

并且可见,$Q_\pm$满足正确的超对称反对易关系.这个是该操作使得无需像$S_{SUSY}$中那样,需要费米子满足运动方程才能使得“两次超对称变换的对易为时空上的平移”成立.
{{% /mathbox %}}
{{% mathbox type="slate" title="“几何”超对称变换" %}}
对于$Q_A=\frac{\partial}{\partial \bar{\theta}^A}+i(\rho^\alpha\theta_A\partial_\alpha)$,方便起见可以引入一个任意的反对易参数$\epsilon_A$,于是$\bar\epsilon Q$可以作为超对称变换的生成元:
$$
  \delta \theta^A=[\bar{\epsilon }Q,\theta^A]=\epsilon^A,
  \delta \sigma^\alpha=[\bar{\epsilon }Q,\sigma^\alpha]=i\bar{\epsilon}\rho^\alpha\theta
$$
{{% /mathbox %}}
于是可以对$\Phi $进行超对称变换:
$$
  \begin{align*}
    \delta_\epsilon\Phi&=i(\epsilon^+Q_++\epsilon^-Q_-)\Phi
    \\& =i\epsilon^+(\sqrt{\frac{\alpha'}{2}}\psi^\mu_++\theta^-F^\mu+i\theta^+\partial_+X^\mu+i\sqrt{\frac{\alpha'}{2}}\theta^+\theta^-\partial_+\psi^\mu_-)
    \\& +i\epsilon^-(\sqrt{\frac{\alpha'}{2}}\psi^\mu_-+\theta^+F^\mu-i\theta^-\partial_-X^\mu-i\sqrt{\frac{\alpha'}{2}}\theta^+\theta^-\partial_-\psi^\mu_+)
  \end{align*}
$$
注意其中用到了$\theta $作为Grassmann数的性质,即$\theta^2=0 $.再对比各项中的$\theta $,于是可得到:
$$
  \boxed{\begin{align*}
    &\delta_\epsilon\psi^\mu_+=-\sqrt{\frac{2}{\alpha'}}\epsilon^+\partial_+X^\mu-i\sqrt{\frac{2}{\alpha'}}\epsilon^-F^\mu
    \\
    &\delta_\epsilon\psi^\mu_-=\sqrt{\frac{2}{\alpha'}}\epsilon^-\partial_-X^\mu+i\sqrt{\frac{2}{\alpha'}}\epsilon^+F^\mu
    \\
    & \delta_\epsilon X^\mu=i\sqrt{\frac{\alpha'}{2}}(\epsilon^+\psi^\mu_++\epsilon^-\psi_-^\mu)
    \\
    & \delta_\epsilon F^\mu=-\sqrt{\frac{\alpha'}{2}}(\epsilon^+\partial _+\psi^\mu_--\epsilon^-\partial_-\psi_+^\mu)
  \end{align*}}
$$
也就是说,最后所得到的超对称变换是封闭的.于是下一步自然就是构造包含超场的作用量,那么很自然的,这个作用量:
* 像之前在玻色弦中证明$S_{NG} $ 作用量和$S_{pol} $作用量一致一样,该作用量应该在积去场$F $后可以回到前面的超对称作用量.
* $S_{off-shell}(X^\mu,\psi^\mu=0,F^\mu=0)=S_{pol} $

首先自然会想到的是
$$
  S=-\frac{1}{4\pi \alpha'}\int d^2\sigma d^2\theta (\partial_+\Phi^\mu)(\partial_-\Phi_\mu)
$$
但是这个作用量并不符合上面两条.若定义超导数(super-derivative):
$$
  D_\pm=\frac{\partial }{\partial \theta^\pm}-i\theta^\pm\partial_\pm
$$
有$\{Q_\pm,D_\pm \}=0$,这说明超场的超导数$D_\pm\Phi$在超对称变换下与其本身$\Phi$一致,于是另一个猜测是
$$
   S=-\frac{1}{4\pi \alpha'}\int d^2\sigma d^2\theta (D_+\Phi^\mu)(D_-\Phi_\mu)
$$
展开可得:
$$
  D_+\Phi^\mu=i\Phi^\mu_++i\theta^-F^\mu-i\theta^+\partial _+X^\mu+\theta^+\theta^-\partial _+\Phi_-^\mu
  \\
  D_+\Phi^\mu=i\Phi^\mu_--i\theta^+F^\mu-i\theta^-\partial _-X^\mu-\theta^+\theta^-\partial _-\Phi_+^\mu
$$
利用Grassmann数的积分,就有
$$
  S=\frac{1}{4\pi \alpha'}\int d^2\sigma[\partial_+X^\mu\partial _-X_\mu+i\Phi^\mu_+\partial _-\Phi_{+,\mu}+i\Phi^\mu_-\partial_+\Phi_{-,\mu}+F^\mu F_\mu]
$$
可见,$F $的运动方程就是$\frac{\delta S}{\delta F^\mu}=F^\mu=0$,代回就得到了前面的$S_{SUSY}$.可见所得到的作用量符合前面的预期,即
$$
  \boxed{  S=-\frac{1}{4\pi \alpha'}\int d^2\sigma d^2\theta (D_+\Phi^\mu)(D_-\Phi_\mu)}
$$
作为超场的作用量,显式地表达出了超对称.

虽说如此,但显然还是之前的$S_{SUSY}$更方便进行一些分析.

其对称性与玻色弦中的分析几乎一致,固定$g_{\mu\nu}=\eta_{\mu\nu} $后还剩下 Conformal Symmetry.



#### 4.RNS边界条件

对于费米子部分的边界条件可以完全同理于玻色弦给出:
{{% mathbox type="slate" title="Recall of the boundary condition of Bosonic String" %}}
考虑到$S=\frac{T}{2}\int d^2\sigma \partial_\alpha X^\mu\partial^\alpha X_\mu$,其有表面项为
$$
  -T\int d\tau [(X_\mu'\delta X^\mu)^{\sigma=\pi}_{\sigma=0}]=0
$$
即
$$
  \delta X^\mu=0 ~~ Dirichlet
  \\
  \partial_{\sigma^1}X_\mu=0 ~~ Newmann
$$
{{% /mathbox %}}
有类似的表面项为
$$
  \int d^2\sigma\delta(\psi_+\partial _-\psi_++\psi_-\partial _+\psi_-)
  \\
  =\int d^2\sigma[\partial _-(\psi_+\delta\psi_+)+(+\leftrightarrow-)]
  \\
  =-\int d^2\sigma\partial_1[(\psi_+\delta\psi_+)-(+\leftrightarrow-)]
  \\
  =-\int d\tau[(\psi_+\delta\psi_+-\psi_-\delta\psi_-)^{\sigma=l}_{\sigma=0}]
$$

对于开弦,要求上面两端分别为$0 $,即在两端都有
$$
  \psi_+^\mu=\pm\psi^\mu_-
$$
注意,这里所谓的“费米子场”实际上在世界面上是矢量场,所以可以出现转一圈后并没有取到负号的情况.对于费米子部分并没有像玻色弦中那样的独立的$X,\delta X$,也就是说有了上面的条件后自然就有了
$$
  \delta\psi^\mu_\pm|_{\sigma=0}=\pm\delta\psi^\mu_\pm|_{\sigma=l}
$$
但其实并不需要两端都要求这样,其相对差异只是惯例问题,也就是说总是可以先确定
$$
  \psi_+^\mu|_{\sigma=0}=\psi^\mu_-|_{\sigma=0}
$$
于是对于$\sigma=l $处都选取就是nontrivial的了:
* Ramond边界条件:
$$
  \psi_+^\mu|_{\sigma=l}=\psi^\mu_-|_{\sigma=l}
$$
一般简称之为R型费米场,展开有:
$$
  \begin{aligned}
  \psi_{-}^{\mu}(\sigma, \tau) & =\frac{1}{\sqrt{2}} \sum_{n \in \mathbb{Z}} d_{n}^{\mu} e^{-i n\frac{2\pi}{l}(\tau-\sigma)} 
  \\
  \psi_{+}^{\mu}(\sigma, \tau) & =\frac{1}{\sqrt{2}} \sum_{n \in \mathbb{Z}} d_{n}^{\mu} e^{-i n\frac{2\pi}{l}(\tau+\sigma)}
  \end{aligned}
$$
注意这里依然使用的Doubling trick.
* Neveu-Schwarz边界条件:
$$
  \psi_+^\mu|_{\sigma=l}=-\psi^\mu_-|_{\sigma=l}
$$
一般称之为NS型费米场,展开有
$$
  \begin{aligned}
  \psi_{-}^{\mu}(\sigma, \tau) & =\frac{1}{\sqrt{2}} \sum_{n \in \mathbb{Z}+\frac{1}{2}} b_{r}^{\mu} e^{-i r\frac{2\pi}{l}(\tau-\sigma)} 
  \\
  \psi_{+}^{\mu}(\sigma, \tau) & =\frac{1}{\sqrt{2}} \sum_{n \in \mathbb{Z}+\frac{1}{2}} b_{r}^{\mu} e^{-i r\frac{2\pi}{l}(\tau+\sigma)} 
  \end{aligned}
$$
后面会默认$m,n $为整数,$r,s $为半整数.

对于闭弦,即要求周期性边界条件:
$$
  \psi_\pm(\sigma)=\pm \psi_\pm(\sigma+l)
$$
每种都可以使得前面的表面项为$0 $.即左行和右行模式都可以分别加上R型或NS型边界条件:
* 对于右行可以选取:
$$
  \begin{align*}
    \psi_{-}^{\mu}(\sigma, \tau) & =\frac{1}{\sqrt{2}} \sum_{n \in \mathbb{Z}} d_{n}^{\mu} e^{-i n\frac{2\pi}{l}(\tau-\sigma)} 
    \\ \text{或  }
    \psi_{-}^{\mu}(\sigma, \tau) & =\frac{1}{\sqrt{2}} \sum_{n \in \mathbb{Z}+\frac{1}{2}} b_{r}^{\mu} e^{-i r\frac{2\pi}{l}(\tau-\sigma)} 
  \end{align*}
$$
* 相应的对于左行就有:
$$
  \begin{align*}
    \psi_{-}^{\mu}(\sigma, \tau) & =\frac{1}{\sqrt{2}} \sum_{n \in \mathbb{Z}}\tilde d_{n}^{\mu} e^{-i n\frac{2\pi}{l}(\tau-\sigma)} 
    \\ \text{或  }
    \psi_{-}^{\mu}(\sigma, \tau) & =\frac{1}{\sqrt{2}} \sum_{n \in \mathbb{Z}+\frac{1}{2}}\tilde b_{r}^{\mu} e^{-i r\frac{2\pi}{l}(\tau-\sigma)} 
  \end{align*}
$$

对于上面不同的组合,分别称之为NS-NS,NS-R,R-NS,R-R类型的闭弦.

这里理应还提到关于Super-Virasoro算符相关,但

#### 5.RNS弦的量子化

引入世界面上费米场的反对易关系:
$$
  \{\psi^\mu_A(\sigma,\tau),\psi^\nu_B(\sigma',\tau) \}=\pi\eta^{\mu\nu}\delta_{AB}\delta(\sigma-\sigma')
$$

于是根据其展开,就可以得到展开系数之间的反对易关系:
$$
  \{b^\mu_r,b^\nu_s\}=\eta^{\mu\nu}\delta_{r+s,0}
  \\
  \{d^\mu_m,d^\nu_n\}=\eta^{\mu\nu}\delta_{m+n,0}
$$


**光锥量子化**:
利用残余的共形不变性,除了可以取到对于玻色场的光锥规范:
$$
  X^+(\sigma,\tau)=x^++\alpha'p^+\tau
$$
对于费米子场也有:
$$
  \psi^+(\sigma,\tau)=0
$$
由于Virasoro约束,与$X^-$不再独立一样,$\psi^-$也不再是一个独立的自由度.所以,所有激发的物理态都由横向的产生算符作用在基态上得到.具体来说,Virasoro约束为
$$
  \psi\cdot\partial _+X=0
$$
和
$$
  (\partial_+X)^2+\frac{i}{2}\psi\cdot\partial_+\psi=0
$$
于是在上面的光锥规范下:
$$
  \begin{align*}
    \partial _+X^-&=\frac{1}{p^+}(\partial _+X^i\partial _+X^i+\frac{i}{2}\psi^i\partial _+\psi^i)
    \\
    \psi^-&=\frac{2}{p^+}\psi^9\partial _+X^i
  \end{align*}
$$
展开即有:
$$
  \begin{aligned}\alpha_{n}^{-}= & \frac{1}{2 p^{+}} \sum_{i=1}^{D-2}\left(\sum_{m=-\infty}^{\infty}: \alpha_{n-m}^{i} \alpha_{m}^{i}:\right. \\& \left.+\sum_{r=-\infty}^{\infty}(r-n / 2): b_{n-r}^{i} b_{r}^{i}:\right)-\frac{a \delta_{n}}{2 p^{+}} \\b_{r}^{-}= & \frac{1}{p^{+}} \sum_{i=1}^{D-2} \sum_{s=-\infty}^{\infty} \alpha_{r-s}^{i} b_{s}^{i} .\end{aligned}
$$
显然同样是只有$\alpha_0^- $才需要 Normal Ordering.于是可以计算,为了保持Lorentz代数
$$
  [L^{i-},L^{j-}]=-(p^+)^{-2}\sum^\infty_{m=1}\Delta_m(\alpha^i_{-m}\alpha^j_m-\alpha^j_{-m}\alpha^i_m)
$$
其中应有$\Delta=0$,即
$$
  \Delta_m=\left(\frac{D-2}{8}\right)+\frac{1}{m}\left(2a-\frac{D-2}{8}\right)
$$
于是可得$D=10,a=\frac{1}{2}$.这个结果也可以通过$\zeta$函数的重整化得到,结果有
$$
  a_R=0,a_{NS}=\frac{d-2}{16}
$$
于是可以给出RNS开弦的谱,注意到
$$
  \alpha'M^2=\sum_{n=1}^\infty\alpha_{-n}^i\alpha_{n}^i+\sum_{r=1/2}^\infty rb^i_{-r}b^i_{r}-\frac{1}2
$$
于是
$$
  \boxed{NS}:a_{NS}=\frac{1}{2},\alpha_{-m}^i,b_{-r}^i
  \\
  \begin{matrix}
    0 &\alpha'm^2 &Spin &D.O.F
    \\
    |p\rangle & -\frac{1}{2} & 0(Scalar) & 1
    \\
    b_{-\frac{1}{2}}^i|p\rangle & 0 & 1(Vector) & 8(SO(8))
    \\
    b_{-\frac{1}{2}}^jb_{-\frac{1}{2}}^i|p\rangle & \frac{1}{2} & 2(anti-symmetry-tensor) & 8\times 7/2=28
    \\
    {\alpha}_{-1}^i|p\rangle & \frac{1}{2} & 1 & 8
  \end{matrix}
$$
其中最后的$(28+8)=36$ 构成了$SO(9)$的表示.可见,NS开弦中没有费米子,虽然有费米场,但在时空中的激发都是玻色子.

{{% mathbox type="slate" title="" %}}
实际上,这里根据一些细节也可以给出$a_{NS}=1/2$:注意到$i$只有横向自由度,也就是只能取$1,...,8$,所以可以由此确定其小群为$SO(8)$,也就是说在十维时空中激发出的是一个无质量的矢量粒子,那么就可以得到$a_{NS}=1/2$.
{{% /mathbox %}}

对于R型可以同样进行分析,但是有一点与上NS型不同的是:
$$
  \{d^\mu_m,d^\nu_n\}=\eta^{\mu\nu}\delta_{m+n,0},m,n\in \Z
$$
有$\{d^i_0,d^j_0\}=\delta^{ij}$,对比gamma矩阵的$\{\gamma^i,\gamma^j\}=2\delta^{ij}$,可知$d_0$实际上就是gamma矩阵.而又由gamma矩阵所作用的空间是旋量空间,所以可知激发的$d_0|p\rangle$实际上就是费米子基态,注意其质量与$|p\rangle$一样都是0,所以也是一种基态.进一步
$$
  d_j^\pm=d^{j\pm}_0=(d_0^{2j}\pm i d^{2j+1}_0)/\sqrt{2}
$$
那么$d_0^i$所给出的其他各种基态族就是$\{d^{1+}\dots d^{4+}_0|p\rangle\}$,而这些基态一共有$2^4=16$种,其中对于有偶数个作用的有$1+6+1=8$种,构成了10-dim时空中一个实的正手征旋量(Majorana-Weyl旋量),即$8_s$;剩下的奇数个作用的态同样有$4+4=8$个,构成了负的手征旋量,即$8_c$.分别用$|\alpha\rangle,|\alpha'\rangle$表示.

于是可以给出R型的谱:
$$
   \boxed{R}:a_{R}=0,\alpha_{-m}^i,d_{-m}^i
  \\
  \begin{matrix}
    0 &\alpha'm^2 &Spin &D.O.F
    \\
    d_0^i|p\rangle & 0 & Spinor & 16
    \\
    (d^{1+}\dots d^{4+}_0|p\rangle)
    \\
    d_{-1}^i|a\rangle & 1 & SO(9)(target~space) & 8_v\times 8_s
    \\
    d_{-1}^i|a'\rangle & 1 &  \cup & 8_v\times 8_c
    \\
    \alpha_{-1}^i|a\rangle & 1 & SO(8)(Worldsheet)  & 8_v\times 8_s
    \\
    \alpha_{-1}^i|a'\rangle & 1 &   & 8_v\times 8_c
  \end{matrix}
$$
> 注意到这里的质量都标记的是$\alpha'M^2$,而在particle极限下,$\alpha'=0$,所以这些有质量的态$M^2=\frac{N-a}{\alpha'}\rightarrow \infty$,也即是说基本上不可能在对撞实验中探测到.

但其实上面的两个表格还是有点问题的.

#### 6.GSO投影

实际上,上面的结果还是有一些问题的:
* Tachyon的存在
* 谱不是时空超对称的,例如零质量的粒子中,玻色子为$8_v$,而费米子$8_s+8_c$有16种.

该问题的解决就是用到了GSO投影.

首先定义一个$G$-宇称算符:
* 对于NS型:
$$
  G=(-1)^{F+1}=(-1)^{\sum_{r=1/2}^\infty b^i_{-r}b^i_r}+1
$$
  其中$F $实际上得到的就是$b $模式的数目.,也就是世界面上费米子的数量.因此这个算符判断一个态对应的世界面费米激发是奇数个还是偶数个.
* 对R类型,相应的定义是
$$
  G=\Gamma_{11}(-1)^{\sum_{r=1/2}^\infty b^i_{-r}b^i_r}
$$其中
$$
  \Gamma_{11}=\Gamma_0\Gamma_1\dots\Gamma_9
$$
有$(\Gamma_{11})^2=1,\{\Gamma_11,\Gamma^\mu\}=0$,和四维的QFT中一样,其本质态也是手征态:
$$
  \Gamma_{11}\psi=\pm\psi
$$
手征确定的态称为Weyl旋量.

对于NS类型,GSO投影只保留$G$-宇称为正的态,即
$$
  (-1)^{F_NS}=-1
$$
即所有的NS型的激发态都应该有奇数个$b$激发模式.对于R型,前面提到16种基态种有正负手征基态各八种$8_s+8_c$,选择对哪一种投影掉只是一个选择问题,这里选择将保留手征为正的$|a\rangle$,而$|a'\rangle$被投影掉,所以只剩下8个费米子,于是就match上了玻色子的数量.另外,前面表格中的 $\boxed{NS}$ 型的激发态中,$\alpha'M^2=1/2$的态也都会被投影掉,于是就match上了 $\boxed{R}$ 型中没有半整数质量的情况.

当然,还有一大类没有讨论,也就是 $\boxed{closed~string}$ .分析闭弦谱,分开左行和右行是很自然的.前面提到一共有四种可能,分别是:R-R,R-NS,NS-R,NS-NS.对于NS型,其基态快子被投影掉;而对于R型,可以选择基态手征的正负,也就是有两种选择,这两种选择分别被称为TypeIIA和TypeIIB:
* TypeIIB中,R型的左行和右行基态手征相同,明确起见都取正.记作$|+\rangle_R$,于是可以知道TypeIIB中的零质量态有
  * $|+\rangle_R\otimes|+\rangle_R$
  * $\tilde{b}^i_{-1/2}|0\rangle_{NS}\otimes{b}^i_{-1/2}|0\rangle_{NS} $
  * $\tilde{b}^i_{-1/2}|0\rangle_{NS}\otimes|+\rangle_R$
  * $|+\rangle_R\otimes{b}^i_{-1/2}|0\rangle_{NS}$
  每种类型都包含$8\times 8=64$个物理态.
* TypeIIA中,R类型的左行和右行基态手征相反,分别记为$|+\rangle_R,|-\rangle_R$,于是同样可以得到谱中的无质量态:
  * $|-\rangle_R \oplus|+\rangle_R $
  * $\tilde{b}^i_{-1/2}|0\rangle_{NS}\otimes{b}^i_{-1/2}|0\rangle_{NS} $
  * $\tilde{b}^i_{-1/2}|0\rangle_{NS}\otimes|+\rangle_R $
  * $|-\rangle_R\otimes{b}^i_{-1/2}|0\rangle_{NS} $
  
每种II型闭弦的无质量谱中,都包含两个Majorana-Weyl引力微子,它们形成$\mathcal{N}=2$ 超引力多重态.这些多重态中的每一个态,都在理论中扮演重要作用.这四种类型的每一种,都有64个无质量态,我们总结在下面:

NS-NS型: IIA和IIB型相同.谱中包含一个**胀子**为标亮(1),一个反对称的2-form规范场(28),一个对称无迹二阶张量--引力子($35_v$).

NS-R和R-NS型: 这两种类型中的每一种,都包含一个自旋3/2的引力微子(56)和一个自选1/2的胀微子的费米子(8).IIB中两个引力微子手性相同,而IIA中相反.

R-R型: 将一对Majorana-Weyl旋量张量积后得到的玻色子.在IIA中,两个Majorana-Weyl旋量手性相反,也就是说得到的是一个1-form(向量)规范场(8)和一个3-form规范场(56).在IIB中,两个Majorana-Weyl旋量手性相同,也就是说得到的是一个0-form(标亮)规范场(1),一个2-form规范场(28),和一个场强自对偶的4-form规范场(35).

> 2026.6.1 到此先告一段落.






___

___

___


$$
  \boxed{\rho^\alpha\partial_\alpha\psi=0,
  \rho^0=\begin{bmatrix}
    0&-i
    \\ i &0
  \end{bmatrix}
  \rho^1=\begin{bmatrix}
    0&i
    \\ i &0
  \end{bmatrix}
  }
  \\
  \boxed{\\then ~  0=\rho^\alpha\partial_\alpha\psi=\rho^0\partial_0\psi+\rho^1\partial_1\psi=-i\begin{bmatrix}
    \partial_0\psi_+-\partial_1\psi_+
    \\\partial_0\psi_-+\partial_1\psi_-
  \end{bmatrix}}
$$
> 我也不知道当时为什么要把这个留在这,但是就先放着吧.