---
title: "Superstring Thory Volume 1"
description: "Green,Schwarz,WItten"
---

> 看这本书主要是因为课上老师主要参考，但读了才发现内容这么丰富
> 这里记录的都是Polchinski中没有的，作为一个补充
## chapter 2 Free Bosonic Strings
### 2.2 老的协变量子化
- 相对于BRST来说老
##### 从该量子化中只能得到反常常数和维数为
$$
a=1,D=26\\or \\ a\le 25,D\le 25
$$

### 2.3 光锥规范量子化
- 考虑将前面协变量子化中的Virasoro约束条件直接“嵌入”到坐标的选择当中，从而使得构造出来的态都是物理的
- 正如其他做了规范选择的方法一样，在历史上总是比一些更系统的方法更早出现，但足以从中窥探到许多物理，比如光锥量子化首次给出了对偶模型是弦理论模型
#### 2.3.1光锥规范与Lorentz代数
首先选择了光锥坐标，即
$$
X^+=\frac{X^0+X^{D-1}}{\sqrt{2}},X^-=\frac{X^0-X^{D-1}}{\sqrt{2}}
$$
> 注意区分这里的时空中的光锥坐标与世界面上的sigma光锥坐标

考虑剩余规范所对应的重参数化
$$
\sigma^+\rightarrow\tilde{\sigma}^+(\sigma^+),\sigma^-\rightarrow\tilde{\sigma}^-(\sigma^-)
$$
>剩余规范是指无穷小重参数化
$$
\delta\sigma^{\mu}=\xi^{\mu}\\
\partial^{\mu}\xi^{\nu}+\partial^{\nu}\xi^{\mu}=\Lambda\eta^{\mu\nu}
$$
考虑到世界面上光锥坐标，有
$$
\partial^{+}\xi^{+}+\partial^{+}\xi^{+}=\Lambda\eta^{++}=0\\
\xRightarrow{}\partial^{+}\xi^{+}=0\\
\xRightarrow{}\partial_{-}\xi^{+}=0\\
\xRightarrow{}\xi^+=\xi^+(\sigma^+)\\
\text{Similarly, }\xi^-=\xi^-(\sigma^-)
$$

于是将
$$
\tau\rightarrow\tilde{\tau}=\frac{1}{2}[\tilde{\sigma}^+(\tau+\sigma)+\tilde{\sigma}^-(\tau-\sigma)]\\
\sigma\rightarrow\tilde{\sigma}=\frac{1}{2}[\tilde{\sigma}^+(\tau+\sigma)-\tilde{\sigma}^-(\tau-\sigma)]
$$
其中第一个式子是下方程的解
$$
(\frac{\partial^2}{\partial\tau^2}-\frac{\partial^2}{\partial\sigma^2})\tilde{\tau}=0
$$
可见该方程就是时空中X所满足的方程，所以可以就选定某个X为世界面上的tau，在光锥坐标下，最方便的选择是
$$
\tilde{\tau}=X^+/p^++const.\\
X^+(\sigma,\tau)=x^++p^+\tau
$$
这就是光锥规范。
