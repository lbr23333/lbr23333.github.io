---
title : "ordinary differential equation"
weight : 1
ShowToc : true
TocOpen : true 
---

# 基本概念

## 例子与定义

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

