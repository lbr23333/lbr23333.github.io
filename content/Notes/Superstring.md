---
title : "lecture note on superstring"
description : "还不太会，真的劳累"
date : 2026-05-18
weight : 1
---
- [1.超对称变换](#1超对称变换)
- [2.超对称作用量](#2超对称作用量)

#### 1.超对称变换

假设bosons到fermions的超对称变换为
$$
  \delta_\epsilon\phi=\epsilon^a\psi_a=\bar\epsilon\psi
$$
那么考虑到$(\delta_\epsilon\phi)^*=\delta_\epsilon\phi$，对上式中右边取复，有
$$
  \begin{align*}
    (\bar\epsilon\psi)^*=(\epsilon^\dagger\rho^0\psi)^\dagger=\psi^\dagger(\rho^0)^\dagger\epsilon=-\psi^\dagger\rho^0\epsilon=-\bar{\psi}\epsilon
  \end{align*}
$$
可见$\bar\epsilon\psi$是纯虚的，所以要加上一个i，再加上一个不确定的系数，即
$$
  \delta_\epsilon\phi=iA\bar\epsilon\psi
$$
反之，对$\psi$的超对称变换应该回到bosons，也就是说
$$
    \delta_\epsilon\psi_a=B\epsilon_b(\rho^\alpha)^b_a\partial_\alpha\phi
$$
注意其中$a,b$都是旋量指标。为验证其自洽性，对$\phi$做两次超对称变换，考虑不同顺序所得到的差$[\delta_{\epsilon_1},\delta_{\epsilon_2}]\phi$，计算可得(这个结果中似乎省略了一些系数，一个整体的4，否则不能于下面的协变结果(1)等价)
$$
  [\delta_{\epsilon_1},\delta_{\epsilon_2}]\phi=i\epsilon^{+}_1\epsilon^+_2(\partial_+\phi)+i\epsilon^{-}_1\epsilon^-_2(\partial_-\phi)
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

可见两次超对称变换的对易子相当于一个世界面上的一个平移变换。另一方面，对于费米子，也应该有自洽性，即考虑两次超对称变换的对易子作用到一个旋量场上，完全同理与上面的结算，可得
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
并重新规定前面的变换常数为:
$$
  \begin{align*}
    & \delta_\epsilon X^\mu=iB\epsilon^a\psi^\mu_a
    \\& \delta_\epsilon\psi^\mu_a=C\epsilon_b(\rho^\alpha)^b_a\partial_\alpha X^\mu
  \end{align*}
$$
注意通过量纲分析可知，其中的$A，B$实际上是一个带有长度量纲的数，也就是说可以通过加上$\alpha'$恢复。进一步，为了使得该作用量在超对称变换下保持不变$\delta_\epsilon S_{test}=0$，可以得到上$A,B,C$之间的一个关系：
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
  S_{test}=\frac{1}{4\pi\alpha'}
  \int d^2\sigma\,
  \left[
    G_{\mu\nu}
    \partial_\alpha X^\mu\partial^\alpha X^\nu
    +
    i\alpha'G_{\mu\nu}
    \bar\psi^\mu\rho^\alpha\partial_\alpha\psi^\nu
  \right]
$$
___

___

___