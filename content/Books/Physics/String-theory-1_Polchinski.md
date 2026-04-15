---
title: "String Thory Volume 1"
description: "Polchinski"
---
{{< progress read="40" total="328" >}}

>悲哀的是，在初次接触量子场论到正式开始学习弦论，居然过了足足两年？

##### 2026.4.8
之前在很多人的推荐下看BBS，而且BBS网上还有翻译[知乎](https://zhuanlan.zhihu.com/p/142917854)。但感觉物理细节省略得有点多，很是不习惯，换成Polchinski后观感就好多了。目前看得还不是很多，等有什么感想再来写。

##### 4.12

难滴扣胩！
总结第二章一下到现在为止都干了什么（当然是到我现在看的地方为止）。说实话就是用一套很严密、很数学的方法得到了Virasoro代数，至于这个代数有什么用我还不是很清楚，但是课上得到的轻而易举就让我感觉很慌。不得不说还是很激动的。

 2.1节
* 引出了主要讨论的对象：二维无质量标量场。
* 引入复坐标
* 得到了
$$
S = \frac{1}{2\pi \alpha'}\int d^2z \partial X^{\mu}\partial X_{\mu}
$$
* 再利用路径积分得到了运动方程
$$
<\partial \bar{\partial}X^{\mu}(z,\bar{z})...>=0 ,\text{其中...是其他不在z处的场}
$$
* 但若考虑有z处的场，就会得到一个☝️发散的结果（也就是接触项），于是引出了正规排序normal ordering，从
$$
\frac{1}{\pi \alpha'}\partial_z\partial_{\bar{z}}X^{\mu}(z,\bar{z})X^{\nu}(z',\bar{z}')=-\eta^{\mu\nu}\delta^2(z-z',\bar{z}-\bar{z}')
$$
到
$$
:X^{\mu}(z,\bar{z})X^{\nu}(z',\bar{z}'):=X^{\mu}(z,\bar{z})X^{\nu}(z',\bar{z}')+\frac{\alpha'}{2}\eta^{\mu\nu}ln|z_{12}|^2
$$
 
 2.2节 OPE
* 细致讨论了各种接触项的去处，也就是OPE的计算（其实并不细致，细节都是读者自己写的）
* 引入的～：保留singular项（开始不知道为什么，到后面清楚了。Virasoro生成元的定义Ln用到了围道积分，所以只有奇异项会贡献留数。关于为什么要这样定义生成元，其实在该节也说明了：因为这个生成元其实就是能动张量T的展开系数，而展开系数可以重构出理论）

 2.3节 Ward Id.
 * 得到了流与变换的关系，最常用的形式为
$$
Res_{z\rightarrow z_0}j(z)A(z_0,\bar{z_0})+\bar{Res}_{z\rightarrow z_0}\tilde{j}(\bar{z})A(z_0,\bar{z_0}) = \frac{1}{i\epsilon}\delta A(z_0,\bar{z_0})
$$
* 给出了重要的世界面上坐标平移所导出的能动张量
$$
T_{ab}=-\frac{1}{\alpha'}:(\partial_a X^{\mu}\partial_b X_{\mu}-\frac{1}{2}\delta_{ab}\partial_c X^{\mu}\partial^c X_{\mu}):
$$

 2.4 Conf.invariance 
* 指出T就是共形变换的生成元
* 计算一般算符与T的OPE
* 用Ward Id.得到了一般算符的共形变换
* 引出了共形权的概念（为什么没人打共形权？气抖冷）
* 计算
$$
\text{OPE  }T(z)T(0) \xRightarrow{} \text{无穷小变换} \xRightarrow{} \text{有限变换(Schwarzian derivative)}
$$

 2.5节 自由CFTs举例
 2.6节 Virasoro代数
* 具体到chapter1中的String，一通复分析计算得到了Virasoro Algebra

对，就看了这么一点。

###### 4.15

算是把第二章看完了

2.7节 Mode expansion

这一节就是把前面在2.5中提到的几个CFT用2.6里面的一些方法，计算一些基本的量，比较重点计算的主要是
* X^mu CFT
* bc CFT
  
2.8节 Vertex operators

饺子醋来咯。最展现CFT魅力的一集。
* 由于世界面w-coord可以由共形变换z=exp(-iw)，变换到一个z-coord上的unit disk(closed string)，又由于
$$
\Psi_\mathcal{A}=\int [\phi_i]_{\phi_b}exp(-S[\phi_i])\mathcal{A}(0)
$$
可知w-coord中的任意态都对应z-coord中的一个local operator at origin，此即是vertex operator.
* 计算了general升降算符与态认同的表示
* bc theory and open string camputation
* path integral and an explicit example --- single free scalar field

2.9节

累了，后面更。

---
有一些开始没想明白，后来想通了的问题

1. 为什么在共形权h的定义中
   $$
\mathcal{A}'(z')=\xi^{-h}\mathcal{A}(z) 
   $$
   h恰好是A算符共形变换的z^-2项系数，即
   $$
T(z)\mathcal{A}(0,0)=\dots+\frac{h}{z^2}\mathcal{A}(0,0)+\frac{1}{z}\partial \mathcal{A}(0,0)+\dots
   $$
   可以考虑无穷小的共形变换：
   $$
\xi=1+\epsilon
   $$
   $$
z'=(1+\epsilon)z=z+\epsilon v(z),i.e. v(z)=z
   $$
   于是由Ward恒等式可得：
   $$
\delta\mathcal{A}(z)=-\epsilon(z\mathcal{A}^{(0)}(z)+\mathcal{A}^{(1)}(z))
   $$
   另一方面，
   $$
\mathcal{A}'(z')=\xi^{-h}\mathcal{A}(z) =(1+\epsilon)^{-h}\mathcal{{A}}
=(1-\epsilon h)\mathcal{A}
\\
\mathcal{A}'(z')=\mathcal{A}'(z+\epsilon z)=\mathcal{A}'(z)+\epsilon z \partial \mathcal{A}(Z)
\\
\xRightarrow{}\delta\mathcal{A}=\mathcal{A}'(z)-\mathcal{A}(z)=-h\epsilon \mathcal{A}(z)-\epsilon z\partial\mathcal{A}(z)
   $$
   于是
   $$
\mathcal{A}^{(1)}(z)=h\mathcal{A}(z)
   $$
