---
title : "Brief introduction on Topology"
description : "ref appendix of GTM218"
weight : 1
---

### Homotopy and the Fundamental Group

If $X $ and $Y $ are topological spaces and $F_0,F_1:X\rightarrow Y $ are continuous maps, a homotopy from $F_0 $ to $F_1 $ is a continuous map $H:X\times I\rightarrow Y $ satisfying
$$
  H(x,0)=F_0(x),H(x,1)=F_1(x),\forall x\in X
$$
If the homotopy exists, we say $F_0 $ and $F_1 $ are homotopic, and write $F_0\simeq F_1 $.If 
$$
  H(x,t)=F_0(x)=F_1(x),\forall t\in I ,\forall x\in A,
$$
the maps $F_0 $ and $F_1 $ are said to be homotopic relative to $A $.

Both "homotopic" and "homotopic relative to $A $" are equivalence relations on the set of all continuous maps from $X $ to $Y $.

> 我将回到舒适区

同伦最重要的应用是在路径。称$f_0,f_1 $是**道路同伦**的，如果
$$
  \begin{align*}
    & H(s,0)=f_0(s) ; H(s,1)=f_1(s)
    \\
    & H(0,t)=f_0(0)=f_1(0)
    \\
    & H(1,t)=f_0(1)=f_1(1)
  \end{align*}
$$
对于拓扑空间$X $中的任意两点$p,q $，道路同伦是一个定义在“从$p $到$q $的所有道路所组成的空间”的等价关系，其中一条道路的等价类记作$[f] $.