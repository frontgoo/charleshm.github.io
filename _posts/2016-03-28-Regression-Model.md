---
published: true
author: Charles
layout: post
title:  "回归分析"
date:   2016-03-28 14:30
categories: 机器学习 统计学
---

#### 基本假定[^1]

回归分析中对随机扰动项的假定，

$$Y = X\hat{\beta}+e$$

- **零均值**：$E(u_i\|X_i)=0$
- **同方差**：对于每一个 $X_i$，$u_i$的条件方差等于某个常数

$$Var(u_i|X_i)=\sigma^2 \Rightarrow Var(Y_i|X_i)=\sigma^2$$

![此处输入图片的描述][1]

- **无自相关**：$Cov(u_i,u_j)=0$

- **随机扰动项与解释变量不相关**: $Cov(u_i,X_i)=0$


- **无多重共线性假定**

> 假定各解释变量之间不存在线性关系，或各个解释变量观测值之间线性无关。

- **正态性假定**: $u_i \sim \mathcal{N}(0,\sigma^2)$

----------

#### OLS 估计

![此处输入图片的描述][2]

----------

**统计特性**， 

![此处输入图片的描述][4]

----------

**无偏估计**：估计量的数学期望等于被估计参数。

![此处输入图片的描述][3]


----------

### 基本假定不满足

需要专门讨论无**多重共线性、同方差、 无自相关**。

#### 多重共线性[^2]

![此处输入图片的描述][5]

- 存在多重共线性时，OLS估计式变得**不确定**或不精确 .    
- OLS估计式方差变得很大，**标准误差**增大 .          
- 当多重共线性严重时，甚至可能使估计的回归系数 符号相反，得出完全错误的结论 .        
- 区间估计和假设检验会出现错误 .      

----------

分析多重共线性**后果**时应注意：

- 存在多重共线性时,OLS估计式还是**最佳线性无偏估计**式（BLUE）

> 无偏性是重复抽样的特性；"最小方差"是相对于其他估计方法而言：（相对于其他方法方差最小，并不是说相对于估计量的值就小）“方差变大”是相对于无多重共线性而言 .

- 多重共线性的影响程度与解释变量在方程中的相对“地位”有关 .
- 如果研究目的仅在于预测 Y ，而解释变量 X 之间的多重共线性关系的性质在未来将继续保持（前提条件），这时多重共线性可能并不是严重问题，而应着重于可决系数高，F 检验显著。

----------
 
#### 异方差性[^3] 

![此处输入图片的描述][6]

存在**异方差**时，OLS估计仍然是**无偏**估计，但是,

- OLS估计式**不再具有最小方差特性** .
- 解释变量的显著性检验**失效** .
- **预测精度降低**,区间预测面临困难 .

----------

#### 自相关[^4]

$$Cov(u_i,u_j)=E(u_iu_j)\not= 0$$

自相关的后果,

- 参数的OLS估计式仍然是**无偏的**
- 用OLS估计的参数的方差**不再具有最小方差**
- 低估 $u_i$ 的真实方差


----------

[1]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-30_223648.png?imageView2/2/w/400
[2]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-31_092444.png
[3]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-31_092931.png
[4]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-31_093425.png
[5]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-31_095044.png
[6]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-31_100124.png?imageView2/2/w/400


[^1]: [多元线性回归模型](http://www.sssidea.org/ecn/chapter3.pdf)
[^2]: [多重共线性](http://www.sssidea.org/ecn/chapter4.pdf)
[^3]: [异方差性](http://www.sssidea.org/ecn/chapter5.pdf)
[^4]: [自相关性](http://www.sssidea.org/ecn/chapter6.pdf)