# 6.1.2 加速度图的基线校正

### 6.1.2 加速度图的基线校正

**产品：** Abaqus/Standard

![](../graphics/stm_eqn07908.gif)![](../graphics/stm_eqn07909.gif)![](../graphics/stm_eqn07910.gif)Abaqus/Standard为时域分析提供加速度记录的基线校正。校正技术是Newmark（1973）提出的。将加速度校正添加到原始数据记录中，以产生校正后的加速度记录，使得事件期间的均方根速度最小。加速度校正在整个事件期间是抛物线的：

![](../graphics/stm_eqn07911.gif)![](../graphics/stm_eqn07912.gif)![](../graphics/stm_eqn05771.gif)![](../graphics/stm_eqn01304.gif)其中表示时间间隔的限值，和是通过速度最小化获得的常数：

![](../graphics/stm_eqn07913.gif)![](../graphics/stm_eqn07914.gif)![](../graphics/stm_eqn07915.gif)其中是 通过积分校正加速度记录获得的校正速度记录。

![](../graphics/stm_eqn05771.gif)可以证明，对于每个时间间隔，由以下公式定义

![](../graphics/stm_eqn07916.gif)![](../graphics/stm_eqn07917.gif)![](../graphics/stm_eqn07918.gif)![](../graphics/stm_eqn07919.gif)![](../graphics/stm_eqn07920.gif)![](../graphics/stm_eqn07921.gif)其中；；和定义为

![](../graphics/stm_eqn07922.gif)![](../graphics/stm_eqn07923.gif)![](../graphics/stm_eqn07909.gif)这里表示通过积分未校正加速度记录获得的未校正速度记录。这些速度是通过假设未校正和校正加速度在原始加速度历史的每个时间增量上线性变化而获得的。对于校正加速度记录来说，这并不精确（因为校正随时间呈抛物线变化），但假定加速度历史以足够小的时间增量离散化，因此这是一个可以忽略的误差。

### 参考

### 参考

"Abaqus Analysis User's Guide"第34.1.2节"振幅曲线"
