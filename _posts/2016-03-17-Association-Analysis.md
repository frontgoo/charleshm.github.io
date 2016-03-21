---
published: true
author: Charles
layout: post
title:  "关联分析"
date:   2016-03-17 9:30
categories: 数据挖掘
---


**关联规则**反映一个事物与其它事物之间的相互依存性和关联性。如果两个或者多个事物之间存在一定的关联关系，那么，其中一个事物发生就能够预测与它相关联的其它事物的发生。比如经典的购物篮事务(market basket transaction)，通过顾客放入购物篮中商品之间的**同现关系**(co-occurrence)来分析顾客的购买习惯，实现商品的交叉销售和推荐。 

![此处输入图片的描述][1]

从上面的数据中我们可以提取如下的规则：

$$\{ \text{尿布} \} \rightarrow \{ \text{啤酒} \} $$

这表明尿布和啤酒的销售关系存在很强的联系，因为许多购买尿布的顾客也购买了啤酒，零售商可以利用这类规则，帮助他们发现新的商机。

那我们如何提取出这样的关联规则呢？

----------

#### 基本概念
- 项集，支持度计数，频繁项集

![此处输入图片的描述][2]


----------


- 关联规则，支持度，置信度

![此处输入图片的描述][3]


----------


举个简单例子，熟悉下公式。

考虑关联规则： $\\{Milk,Diaper\\} \Rightarrow Beer$，

$$\begin{align*}
s & = \frac{\sigma(Milk,Diaper,Beer)}{|T|} = \frac{2}{5} = 0.4\\
c & = \frac{\sigma(Milk,Diaper,Beer)}{\sigma(Milk,Diaper)} = \frac{2}{3} = 0.67
\end{align*}$$

这里面还有一个小 trick， 下面的关联规则都源自于同一个项集 $\\{ \text{啤酒，尿布，牛奶} \\}$，它们都有相同的支持度。当我们的项集 $\\{ \text{啤酒，尿布，牛奶}\\}$ 为非频繁，我们可以立即剪掉这6条候选规则，而不必计算其置信度。

![此处输入图片的描述][4]

----------

#### 关联规则挖掘
大多数关联规则挖掘算法都可以分为两个主要步骤：

- **频繁项集产生**：其目标是发现满足最小支持度阈值的所有项集(frequent itemset).
- **规则提取**：从上一步发现的频繁项集中提取所有高置信度的规则，这些规则称为强规则(strong rule).

一般来说，一个包含 $k$ 个项的数据集可能产生 $2^k-1$个频繁项集（不包括空集），我们的项集搜索空间是非常巨大的。

![此处输入图片的描述][5]

最直接的思路，

![此处输入图片的描述][6]

![此处输入图片的描述][7]


  [1]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-21_195111.png?imageView2/2/w/400
  [2]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-21_212028.png
  [3]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-21_212722.png
  [4]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-21_213839.png
  [5]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-21_220257.png?imageView2/2/w/400
  [6]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-21_220925.png
  [7]: http://7xjbdi.com1.z0.glb.clouddn.com/2016-03-21_220800.png?imageView2/2/w/400