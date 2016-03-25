---
published: true
author: Charles
layout: post
title:  "假设检验"
date:   2016-03-23 15:30
categories: 机器学习 统计学
---

### 假设检验
假设检验（hypothesis  test）亦称**显著性检验**（significant test），是先对总体的参数或分布作出某种假设，然后用适当的方法，根据样本对总体提供的信息，推断此假设应当拒绝或不拒绝。

比如，我们观察到一组独立地从同一个分布采样出来的样本。如果想了解这个分布的性质，可以针对这个分布的参数做出两个不同的假设。一个叫**零假设** $H_0$，另一个叫**备选假设** $H_1$ 。比如针对分布的期望值 $\mu$，零假设可以是 $\pmb{H}_0:u = u_0$，备选假设可以是 $\pmb{H}_1: u\neq u_0$。假设检验过程根据观察到的样本决定接受其中一个假设。


----------


#### 基本原理

假设检验的基本原理包括，

 1. 假设零假设 $H_0$ 成立，选择一个零假设成立时概率分布已知的统计量，然后再选择一个显著性水平 $\alpha$。
 2. 选定统计量概率低的区域，使得这个区域的概率等于显著性水平 $\alpha$。
 3. 根据观察到的样本，计算统计量的值是否落在低概率区域。
 4. 如果落在低概率区域，则拒绝零假设；如果没有落在低概率区域，则接受零假设。


----------


#### 两类错误

假设检验有**两类错误**，第一类型错误和第二类型错误。第一类型错误，是零假设成立的情况下拒绝零假设。第二类型错误，是备选假设成立的情况下接受零假设。

|     Type    | Decision:Accept $H_0$ | Decision:Reject $H_1$ |
|:-----------:|:---------------------:|:---------------------:|
| Truth:$H_0$ |    Correct Decision   |      Type I Error     |
| Truth:$H_1$ |     Type II Error     |    Correct Decison    |

> 是不是想起了我们分类器评估准则里面的 [混淆矩阵][1] .

### 实例分析

#### $t$ 检验
t 检验是针对分布期望 $u$ 的检验。假设一组服从正态分布的数据样本,

$$\begin{eqnarray} 
1.0,\quad1.2,\quad1.4,\quad1.1,\quad1.3,\quad1.2 
\end{eqnarray}$$

我们想知道检验样本均数所代表的总体均数 $\mu$ 是否与已知总体均数 $\mu_0$ 有差别，利用 t 检验:

![此处输入图片的描述][2]



http://www.gotoli.us/%E7%BB%9F%E8%AE%A1%E5%81%87%E8%AE%BE%E6%A3%80%E9%AA%8C%E4%B8%80t%E6%A3%80%E9%AA%8C


  [1]: http://charlesx.top/2016/03/Classification-Model-Performance/
  [2]: http://7xjbdi.com1.z0.glb.clouddn.com/hy_set.png?imageView2/2/w/300