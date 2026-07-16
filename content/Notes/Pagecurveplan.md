可以。围绕我们拟定的项目

$$
  \boxed{\text{有限维幺正黑洞蒸发模型中的纠缠熵与 Page 曲线}}
$$
可以。围绕我们拟定的项目

$$
  \boxed{\text{有限维幺正黑洞蒸发模型中的纠缠熵与 Page 曲线}}
$$


我建议把文献分成七组。每组都标出：

* **A：必须精读**
* **B：选择性阅读**
* **C：作为严格参考或后续进阶**

不需要一开始把所有文献都读完。真正的项目主线大约只需要精读六到八份材料。

---

# 一、密度矩阵、偏迹与 Schmidt 分解

这是项目的第一层基础。你需要能够熟练处理

[
\rho_{AB}=|\psi\rangle\langle\psi|,
\qquad
\rho_A=\operatorname{Tr}*B\rho*{AB},
\qquad
|\psi\rangle
============

\sum_i\sqrt{\lambda_i},
|i\rangle_A|i\rangle_B.
]

## A1. John Preskill, *Quantum Information and Computation*, Chapter 2

**建议精读部分：**

* density operator；
* ensemble；
* composite systems；
* partial trace；
* Schmidt decomposition；
* purification。

Preskill 的第二章以物理语言讲述开放系统的状态、约化密度矩阵和 Schmidt 分解，很适合你从普通量子力学过渡到量子信息。([preskill.caltech.edu][1])

### 读完后应完成

1. Bell 态的约化密度矩阵；
2. GHZ 态各子系统的约化态；
3. 证明二分纯态满足
   [
   S(\rho_A)=S(\rho_B);
   ]
4. 证明纯态等价于
   [
   \operatorname{Tr}\rho^2=1.
   ]

---

## C1. John Watrous, *The Theory of Quantum Information*, Chapter 2.1

Watrous 的第 2.1 节系统定义量子态、约化态和纯化；他的写法更加接近有限维泛函分析和算子理论，适合你在 Preskill 中遇到定义不够精确时查阅。

这里需要注意：Watrous 通常不使用物理学中常见的 Dirac 记号，因此第一次读可能稍不习惯。该书本身定位也是偏定义、定理与证明的研究生级参考书。

### 本阶段阅读顺序

[
\boxed{
\text{Preskill Ch.2}
\longrightarrow
\text{自己计算}
\longrightarrow
\text{Watrous §2.1 查严格定义}
}
]

---

# 二、量子信道与开放量子系统

为了比较“幺正蒸发”和“信息真正丢失”，需要理解量子信道

[
\mathcal E:
\mathcal L(\mathcal H_A)
\longrightarrow
\mathcal L(\mathcal H_B),
]

以及 Kraus 表示

[
\mathcal E(\rho)
================

\sum_a K_a\rho K_a^\dagger,
\qquad
\sum_aK_a^\dagger K_a=I.
]

## A2. John Preskill, *Quantum Information*, Chapter 3

这一章重点讲：

* 广义测量；
* 开放系统演化；
* quantum channels；
* Kraus operators；
* depolarizing channel；
* 系统—环境表示。

Preskill 明确把量子信道解释为与环境相互作用的开放系统演化，这与黑洞蒸发模型中的“只观察辐射而忽略内部自由度”直接对应。([preskill.caltech.edu][2])

### 项目中重点学习

你暂时不必精读所有测量理论，优先掌握：

[
\text{unitary dilation},
\quad
\text{partial trace},
\quad
\text{Kraus representation},
\quad
\text{complementary channel}.
]

---

## C2. Watrous, *The Theory of Quantum Information*, Sections 2.2 and Chapter 3

Watrous 第 2.2 节给出量子信道的定义、表示和基本例子；第 3 章讨论态与信道之间的距离，包括态判别、fidelity 和信道距离。

你的小项目第一阶段只需要读：

* §2.2.1：信道的定义；
* §2.2.2：信道的各种表示；
* §3.1：态的可区分性；
* §3.2：fidelity。

diamond norm 可以暂时跳过。

---

# 三、von Neumann 熵、互信息和熵不等式

这是 Page 曲线最直接的数学语言。

需要掌握：

[
S(A)=-\operatorname{Tr}\rho_A\log\rho_A,
]

[
I(A:B)=S(A)+S(B)-S(AB),
]

以及

[
S(A)=S(B)
]

对二分纯态成立的原因。

## A3. Watrous, *The Theory of Quantum Information*, Chapter 5

第五章系统讲解：

* Shannon 熵；
* von Neumann 熵；
* 相对熵；
* 条件熵；
* 互信息；
* 熵不等式；
* 量子信息压缩。

这是项目中熵理论最适合查阅的严格参考。

### 推荐阅读范围

第一遍主要读：

* §5.1：经典熵；
* §5.2：量子熵；
* 关于次可加性和强次可加性的部分。

不必立刻完整掌握 source coding theorem 的证明。

---

## B3. John Preskill, *Quantum Shannon Theory*

Preskill 的 Quantum Shannon Theory 讲义包含经典 Shannon 理论、量子压缩、纠缠的量化和 decoupling principle；它比 Watrous 更强调这些量在信息任务中的物理意义。([arXiv][3])

对于当前项目，优先看：

* Shannon entropy；
* von Neumann entropy；
* mutual information；
* entanglement entropy；
* decoupling 的基本思想。

### 这一阶段最重要的理解

不要只把熵当成“混乱程度”。你要区分：

[
S(\rho_A)
]

可能表示：

1. 对系统状态的经典无知；
2. 系统 (A) 与另一个系统 (B) 的纠缠；
3. 对不可观测自由度取偏迹之后的信息损失。

在二分纯态情形中，(S(\rho_A)) 完全是纠缠熵。

---

# 四、随机纯态与 Page 公式

这是项目的数学核心。

设

[
\mathcal H=\mathcal H_A\otimes\mathcal H_B,
\qquad
\dim\mathcal H_A=m,\quad
\dim\mathcal H_B=n,
]

且 (m\leq n)。随机选取总系统纯态后，研究

[
\left\langle S(\rho_A)\right\rangle.
]

## A4. Don N. Page, *Average Entropy of a Subsystem*（1993）

这是项目最重要的原始论文之一。

Page 给出了平均子系统熵公式

[
\left\langle S_A\right\rangle
=============================

## \sum_{k=n+1}^{mn}\frac1k

\frac{m-1}{2n},
\qquad m\leq n,
]

并得到大维数近似

[
\left\langle S_A\right\rangle
\simeq
\log m-\frac{m}{2n}.
]

这说明，当 (m\ll n) 时，较小子系统的平均熵非常接近其最大值 (\log m)。需要注意的是，Page 在原文中把精确公式作为猜想提出，同时证明了相应的渐近行为。([arXiv][4])

### 第一遍怎样读

不必立即复现随机矩阵积分。先弄清楚：

1. 随机态是按什么测度选取的；
2. 为什么较小子系统几乎最大混合；
3. 为什么总态纯却有
   [
   S_A=S_B;
   ]
4. 为什么熵在 (m\sim n) 附近达到峰值。

---

## B4. Siddhartha Sen, *Average Entropy of a Subsystem*（1996）

Sen 的论文给出了 Page 精确公式的证明。([arXiv][5])

这篇比较适合作为项目的数学进阶部分。第一次项目可以：

* 引用 Page–Sen 公式；
* 数值验证公式；
* 不要求完整重现证明。

若你后面想把项目做得更数学化，可以尝试理解证明中约化密度矩阵本征值的联合概率分布。

---

## B5. Foong and Kanno, *Proof of Page’s Conjecture on the Average Entropy of a Subsystem*（1994）

这是另一份对 Page 猜想的早期证明。([APS Link][6])

Sen 与 Foong–Kanno 不必同时精读。选择一篇即可。对你而言，Sen 的篇幅较短，可以先选 Sen。

---

## C3. Eugenio Bianchi and Pietro Donà, *Typical Entanglement Entropy in the Presence of a Center: Page Curve and Its Variance*（2019）

这篇论文不只计算平均熵，还研究熵的方差，并说明大系统中平均值具有典型性；它还讨论当可观测量代数存在中心、Hilbert 空间不再简单分解成张量积时如何推广 Page 型结果。([arXiv][7])

它适合回答一个容易忽略的问题：

> 数值模拟中看到平均 Page 曲线，是否意味着大多数随机态都接近这条曲线？

第一阶段只需阅读导言和关于普通张量积分解的部分。

---

# 五、有限维黑洞蒸发玩具模型

Page 公式本身描述的是随机二分纯态，还不是一个随时间演化的黑洞蒸发模型。你还需要人为定义：

[
\mathcal H_B(t)\otimes\mathcal H_R(t)
]

以及每一步的演化。

## A5. Steven G. Avery, *Qubit Models of Black Hole Evaporation*（2011）

这篇论文专门讨论黑洞蒸发的量子比特玩具模型，构造了足以描述幺正和非幺正蒸发的一般模型，并比较具体例子。作者还讨论了从 Hawking 型非幺正演化连续变形成幺正过程需要多大的修正。([arXiv][8])

### 对项目最有帮助的部分

重点关注：

* 内部 Hilbert 空间；
* 新产生的辐射量子比特；
* 每一步演化的等距映射；
* 幺正模型与 Hawking 型模型的区别；
* 为什么“小修正”通常不够恢复幺正性。

### 阅读难点

这篇论文比简单的 Page 随机态模型更接近黑洞蒸发，但符号较多。建议先完成自己的三到六量子比特模型，再读 Avery；否则容易陷入模型分类而失去直觉。

---

## 可自行构造的最小模型

你可以先不完全照搬论文，而是定义离散时间演化：

[
V_t:
\mathcal H_{B_t}
\longrightarrow
\mathcal H_{B_{t+1}}\otimes\mathcal H_{r_{t+1}},
]

其中 (r_{t+1}) 是新发射出的一个辐射量子比特。

每一步计算

[
\rho_{R_t}


\operatorname{Tr}_{B_t}
|\Psi_t\rangle\langle\Psi_t|,
\qquad
S(R_t)


-\operatorname{Tr}\rho_{R_t}\log\rho_{R_t}.
]

Avery 的论文可以帮助你判断所构造的映射是否真的代表幺正信息转移。

---

# 六、Page 曲线与黑洞信息问题

前面讨论的是有限维量子信息模型，这一组文献负责说明它为何与真正的黑洞相关。

## A6. Don N. Page, *Information in Black Hole Radiation*（1993）

Page 假设黑洞形成和蒸发可由 (S)-矩阵描述，进而研究信息何时以及如何出现在 Hawking 辐射中。他的主要结论是：早期辐射中可提取的信息极少，而在蒸发经过大约“中点”后，信息释放显著加快。([arXiv][9])

这篇论文负责把随机子系统熵转化为蒸发黑洞的辐射熵.


### 阅读时要区分两篇 Page 论文

1. *Average Entropy of a Subsystem*：
   研究随机二分纯态的平均熵；
2. *Information in Black Hole Radiation*：
   把这一思想应用到幺正黑洞蒸发。

两篇应当连着读，但目标不同。

---

## A7. Daniel Harlow, *Jerusalem Lectures on Black Holes and Quantum Information*

这是黑洞与量子信息交叉领域的经典讲义，内容包括黑洞量子物理、信息悖论、firewall 问题和 AdS/CFT 中与黑洞信息相关的部分。([arXiv][10])

### 项目阶段的读法

不要从头到尾强行通读。优先寻找：

* Hawking calculation 的信息论表述；
* Page time；
* scrambling；
* black hole complementarity；
* firewall paradox。

等你完成 Page 曲线数值模型后再读，很多抽象表述会变得具体。

---

## B6. Joseph Polchinski, *The Black Hole Information Problem*（2016）

Polchinski 的综述更侧重传统黑洞信息问题的论证路线，并与 Harlow 偏量子信息的讲法形成互补。([arXiv][11])

阅读重点：

* Hawking 的半经典结论；
* 纯态到混态的问题；
* complementarity；
* AMPS/firewall；
* 不同解决方案各自牺牲了什么假设。

---

## B7. Daniel Harlow, *Black Holes in Quantum Gravity*（2023）

这篇较新的综述面向较广泛的物理读者，重点包括黑洞信息问题、弦论中的黑洞熵计数以及全息中的时空涌现，并且不预设读者已掌握弦论或全息。([arXiv][12])

它很适合作为完成小项目后的“下一步地图”。

---

# 七、量子纠错与 Hayden–Preskill 模型

这是项目的扩展部分，不必在最初八周全部完成。

## A8. John Preskill, *Quantum Error Correction*, Chapter 7

该章系统介绍：

* 编码与解码；
* error syndrome；
* 量子纠错条件；
* stabilizer code；
* 噪声作用下的信息恢复。

Preskill 的课程页面显示这一章专门讨论量子纠错码及其如何保护量子信息免受环境噪声影响。([preskill.caltech.edu][13])

你暂时只需要读到 Knill–Laflamme 条件：


$$
  P E_a^\dagger E_bP=C_{ab}P.
$$


---

## B8. Knill et al., *Introduction to Quantum Error Correction*（2002）

这篇讲义强调量子纠错的“解码”与“子系统”观点，并讨论量子噪声的描述以及容错所需条件。([arXiv][14])

它尤其有助于理解：

> 纠错并不意味着物理量子比特没有受到破坏，而是逻辑信息仍可以从剩余自由度中恢复。

这正是全息和黑洞信息恢复中反复出现的思想。

---

## A9. Patrick Hayden and John Preskill, *Black Holes as Mirrors: Quantum Information in Random Subsystems*（2007）

这篇论文研究一个已经与早期 Hawking 辐射高度纠缠的“老黑洞”。在黑洞内部演化幺正且快速混合的假设下，新投入黑洞的量子信息在少量额外辐射发出后便可被恢复；论文还把这种过程与接近擦除信道容量的量子纠错编码联系起来。([arXiv][15])

### 为什么放在最后

它同时需要：

* 随机幺正演化；
* purification；
* decoupling；
* mutual information；
* quantum error correction；
* Page time。

因此它不是入门材料，而是这个小项目完成后的最佳升级方向。

---

# 八、最精简的必读清单

若希望控制阅读量，第一阶段只读下面七项：

1. **Preskill, Chapter 2**
   密度矩阵、偏迹、Schmidt 分解。([preskill.caltech.edu][1])

2. **Preskill, Chapter 3**
   开放系统和量子信道。([preskill.caltech.edu][2])

3. **Watrous, Chapter 5 的熵部分**
   von Neumann 熵和熵不等式。

4. **Page, *Average Entropy of a Subsystem***
   Page 平均熵公式。([arXiv][4])

5. **Page, *Information in Black Hole Radiation***
   Page 曲线的黑洞解释。([arXiv][9])

6. **Avery, *Qubit Models of Black Hole Evaporation***
   有限维蒸发模型。([arXiv][8])

7. **Harlow, *Jerusalem Lectures***
   把玩具模型放回真实黑洞信息问题中。([arXiv][10])

对应的阅读逻辑是

[
\boxed{
\rho,\operatorname{Tr}_B,\text{Schmidt}
\rightarrow
\mathcal E
\rightarrow
S(\rho)
\rightarrow
\text{random states}
\rightarrow
\text{Page curve}
\rightarrow
\text{qubit evaporation}
\rightarrow
\text{black-hole interpretation}
}
]

---

# 九、建议的文献—项目对应表

| 项目任务            | 主要文献            | 完成目标                     |     |
| --------------- | --------------- | ------------------------ | --- |
| 计算 Bell/GHZ 约化态 | Preskill Ch.2   | 熟练偏迹                     |     |
| 构造开放系统演化        | Preskill Ch.3   | 理解 Kraus 与环境             |     |
| 计算纠缠熵           | Watrous Ch.5    | 熟悉 (S,I,S(A              | B)) |
| 生成随机纯态          | Page 1993       | 验证平均熵公式                  |     |
| 画 Page 曲线       | Page 两篇论文       | 理解先升后降                   |     |
| 构造逐步蒸发模型        | Avery 2011      | 比较幺正与非幺正                 |     |
| 理解物理意义          | Harlow 讲义       | 联系信息悖论                   |     |
| 扩展到信息恢复         | Hayden–Preskill | 理解 scrambling 与 decoding |     |

我建议实际从 **Preskill 第二章**开始。完成密度矩阵、偏迹和 Schmidt 分解后，第一项正式任务可以定为：

[
\text{解析并数值计算 Bell、GHZ、W 三类态的约化密度矩阵与纠缠熵。}
]

这会成为后续黑洞蒸发模型的计算模板。

[1]: https://www.preskill.caltech.edu/ph219/chap2_13.pdf?utm_source=chatgpt.com "Quantum Information and Computation Chapter 2"
[2]: https://www.preskill.caltech.edu/ph219/chap3_15.pdf?utm_source=chatgpt.com "Quantum Information Chapter 3"
[3]: https://arxiv.org/abs/1604.07450?utm_source=chatgpt.com "Quantum Shannon Theory"
[4]: https://arxiv.org/abs/gr-qc/9305007 "[gr-qc/9305007] Average Entropy of a Subsystem"
[5]: https://arxiv.org/abs/hep-th/9601132?utm_source=chatgpt.com "Average Entropy of a Subsystem"
[6]: https://link.aps.org/doi/10.1103/PhysRevLett.72.1148?utm_source=chatgpt.com "Proof of Page's conjecture on the average entropy of a ..."
[7]: https://arxiv.org/abs/1904.08370?utm_source=chatgpt.com "Typical entanglement entropy in the presence of a center: Page curve and its variance"
[8]: https://arxiv.org/abs/1109.2911 "Qubit Models of Black Hole Evaporation"
[9]: https://arxiv.org/abs/hep-th/9306083 "[hep-th/9306083] Information in Black Hole Radiation"
[10]: https://arxiv.org/abs/1409.1231 "[1409.1231] Jerusalem Lectures on Black Holes and Quantum Information"
[11]: https://arxiv.org/pdf/1609.04036?utm_source=chatgpt.com "The Black Hole Information Problem"
[12]: https://arxiv.org/abs/2304.10367 "Black holes in quantum gravity"
[13]: https://www.preskill.caltech.edu/ph229/notes/chap7.pdf?utm_source=chatgpt.com "Chapter 7 Quantum Error Correction"
[14]: https://arxiv.org/abs/quant-ph/0207170 "[quant-ph/0207170] Introduction to Quantum Error Correction"
[15]: https://arxiv.org/abs/0708.4025 "[0708.4025] Black holes as mirrors: quantum information in random subsystems"
