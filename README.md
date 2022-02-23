# 时间序列分析

## 什么是时间序列？
时间序列定义为在一定时间间隔内按时间顺序测量的某个数量。
从最广泛的形式来说，时间序列分析是关于推断过去一系列数据点发生了什么，并试图预测未来会发生什么。

## 时间序列表现形式
1.随机性：由许多不确定因素引起的序列变化，当数据没有明显的模式特征的话，我们认为它是平稳的，Y值在一个范围内随着时间上下浮动

![image](https://user-images.githubusercontent.com/25822507/154907168-4fc59ce4-3dd9-4790-ad60-39e951139ece.png)

2.长期趋势变化：受某种基本因素的影响，数据依时间变化时表现为一种确定倾向，它按某种规则稳步地增长或下降。使用的分析方法有：移动平均法、指数平滑法、模型拟和法等

![image](https://user-images.githubusercontent.com/25822507/154907328-d2d245b5-8ed6-4ec5-90b3-1db30b471fb5.png)

3.季节性周期变化：受季节更替等因素影响，序列依一固定周期规则性的变化，又称商业循环。采用的方法：季节指数

![image](https://user-images.githubusercontent.com/25822507/154907440-4ba4fc83-f267-4160-bd58-a960fa773d7e.png)

4.循环变化：周期不固定的波动变化

## 如何判断序列是否平稳？
判断序列平稳不平稳，一般采用两种方法：

1.看图法（时序图）

![image](https://user-images.githubusercontent.com/25822507/155258835-7c934564-12b4-496c-be5d-03acb0facd82.png)

分析：什么样的图不平稳，先说下什么是平稳，平稳就是围绕着一个常数上下波动。

看看上面这个图，很明显的增长趋势，不平稳。

2.自相关系数和偏相关系数

自相关和偏相关图，Q统计量和伴随概率

![image](https://user-images.githubusercontent.com/25822507/155258917-55ca7a9e-be26-49e5-a017-06d6def8b7c4.png)

分析：判断平稳与否的话，用自相关图和偏相关图就可以了。

平稳的序列的自相关图和偏相关图不是拖尾就是截尾。
截尾就是在某阶之后，系数都为 0 ，怎么理解呢，看上面偏相关的图，当阶数为 1 的时候，系数值还是很大， 0.914. 二阶长的时候突然就变成了 0.050. 后面的值都很小，认为是趋于 0 ，这种状况就是截尾。
再就是拖尾，拖尾就是有一个衰减的趋势，但是不都为 0 。

自相关图既不是拖尾也不是截尾。以上的图的自相关是一个三角对称的形式，这种趋势是单调趋势的典型图形。


## 采用什么算法？

### 判断依据

如果自相关是拖尾，偏相关截尾，则用 AR 算法

如果自相关截尾，偏相关拖尾，则用 MA 算法

如果自相关和偏相关都是拖尾，则用 ARMA 算法， ARIMA 是 ARMA 算法的扩展版，用法类似 。

### 基本步骤 

平稳序列

- 获取时间序列
- 时间序列绘图
- 检验序列平稳性
- 绘制ACF PACF
- ADF检验
- 模型预测
- 预测值还原
- 预测误差检验

非平稳序列

- 1.获取时间序列
- 2.时间序列绘图
- 3.检验序列平稳性
- 4.绘制ACF PACF
- 5.ADF检验
- 6.序列差分运算
- 7.检验ACF PACF 值
- 8.ADF检验（重复6-8步骤，做n阶差分，直至序列平稳）
- 9.模型预测
- 10.预测值还原
- 11.预测误差检验

