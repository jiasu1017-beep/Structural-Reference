# 2.5.5 模态动力学分析

### 2.5.5 模态动力学分析

**产品：** Abaqus/Standard

模态动力学过程提供线性系统的时间历史分析。激发给定为时间的函数：假设振幅曲线被指定使得激发幅度在每个增量内线性变化。当模型被投影到用于其动力学表示的特征模态上时，我们在时间 *t* 获得以下方程组：

![](../graphics/stm_eqn01218.gif)其中索引 ![](../graphics/stm_eqn00904.gif) 和 ![](../graphics/stm_eqn01219.gif) 跨越特征空间；![](../graphics/stm_eqn01220.gif) 是投影的黏性阻尼矩阵；![](../graphics/stm_eqn01221.gif) 是模态 ![](../graphics/stm_eqn01219.gif) 的"广义坐标"（该模态中响应的振幅）；![](../graphics/stm_eqn01222.gif) 是无阻尼模态 ![](../graphics/stm_eqn01219.gif) 的固有频率（作为在模态动力学时间历史分析之前的特征频率步骤中特征值的平方根获得）；![](../graphics/stm_eqn01223.gif) 是投影到该模态上的荷载大小（模态的"广义荷载"）；![](../graphics/stm_eqn01224.gif) 是 *f* 在时间增量期间的变化，即 ![](../graphics/stm_eqn00883.gif)。

如果投影阻尼矩阵是对角的，[方程 2.5.5-1](02s05a28.md) 变为以下解耦方程组：

![](../graphics/stm_eqn01225.gif)其中 ![](../graphics/stm_eqn01226.gif) 是由关系给出的临界阻尼比

![](../graphics/stm_eqn01227.gif)其中 ![](../graphics/stm_eqn01228.gif) 是模态黏性阻尼系数，![](../graphics/stm_eqn01229.gif) 是模态 ![](../graphics/stm_eqn01219.gif) 中的模态质量。
### 解耦系统的求解

解耦方程的求解可以容易地获得，作为荷载的特定积分和齐次方程（无右边）的解。这些解可以组合并写成一般形式

![](../graphics/stm_eqn01230.gif)其中 ![](../graphics/stm_eqn01231.gif) 和 ![](../graphics/stm_eqn01232.gif)、![](../graphics/stm_eqn01233.gif) 是常数，因为我们假设荷载在时间增量上仅线性变化（即 ![](../graphics/stm_eqn01234.gif) 是常数）。

对于非刚体运动（![](../graphics/stm_eqn01235.gif)），此解有三种情况，取决于模态平衡方程中的阻尼是大于、等于还是小于临界阻尼（即取决于 ![](../graphics/stm_eqn01236.gif) 是正、零还是负）。
### 耦合系统的求解

[方程 2.5.5-3](02s05a28.md) 可以推广以处理投影阻尼矩阵中的完全耦合。设矩阵 ![](../graphics/stm_eqn00162.gif) 分裂为其对角和非对角部分，所以

![](../graphics/stm_eqn01237.gif)然后，附加假设非对角阻尼力在时间增量上线性变化，解耦系统的方程可以重写为

![](../graphics/stm_eqn01238.gif)其中 ![](../graphics/stm_eqn01239.gif) 由下式给出

![](../graphics/stm_eqn01240.gif)![](../graphics/stm_eqn01239.gif) 是完全填充的，但仅是 ![](../graphics/stm_eqn00883.gif) 的函数，因此对于给定分析只需分解一次。
### 积分系数

对于非刚体运动（![](../graphics/stm_eqn01235.gif)），此解有三种情况，取决于模态平衡方程中的阻尼是大于、等于还是小于临界阻尼（即取决于 ![](../graphics/stm_eqn01236.gif) 是正、零还是负）。阻尼小于临界

这是最常见的情况。伴随

![](../graphics/stm_eqn01241.gif)我们得到

![](../graphics/stm_eqn01242.gif)

![](../graphics/stm_eqn01243.gif) 阻尼等于临界

在这种情况下

![](../graphics/stm_eqn01244.gif)

![](../graphics/stm_eqn01245.gif)阻尼高于临界

在这种情况下，伴随

![](../graphics/stm_eqn01246.gif)我们得到

![](../graphics/stm_eqn01247.gif)

![](../graphics/stm_eqn01248.gif)

![](../graphics/stm_eqn01249.gif)带阻尼的刚体模态

如果有限元模型中有刚体模态，将有一个或几个为零的特征值。运动方程（[方程 2.5.5-1](02s05a28.md)）简化为

![](../graphics/stm_eqn01250.gif)

对于刚体模态只能指定 Rayleigh 阻尼，因为临界阻尼为零。此外，由于它是刚体模态，只出现质量阻尼因子 ![](../graphics/stm_eqn00904.gif)（刚度阻尼需要身体有应变）。对于这种情况

![](../graphics/stm_eqn01251.gif)

![](../graphics/stm_eqn01252.gif)无阻尼的刚体模态

对于无阻尼刚体模态的特殊情况，运动方程（[方程 2.5.5-1](02s05a28.md)）简化为

![](../graphics/stm_eqn01253.gif)对于这种情况

![](../graphics/stm_eqn01254.gif)
### 模态动力学分析中的结构阻尼

结构阻尼是一种常用的阻尼模型，将阻尼表示为复刚度。这种表示对频域分析（如稳态动力学，其解已经是复数）没有困难。然而，在时域中，解必须保持为实值。为了允许用户在时域中应用他们的结构阻尼模型，开发了一种将结构阻尼转换为等效黏性阻尼的方法。该技术设计成这样：在频域中，如果投影阻尼矩阵是对角的，则施加的黏性阻尼与结构阻尼相同。

我们从单自由度振子方程开始，

![](../graphics/stm_eqn01255.gif)其中 *m* 是质量，*c* 是黏性阻尼因子，*k* 是刚度，*x* 是响应，*f* 是力，![](../graphics/stm_eqn01256.gif) 是结构阻尼因子。如果我们用质量归一化并假设谐波输入，我们得到关系

![](../graphics/stm_eqn01257.gif)其中 ![](../graphics/stm_eqn01091.gif) 是固有频率，![](../graphics/stm_eqn01258.gif) 是激励频率，![](../graphics/stm_eqn01040.gif) 是谐波响应的系数，![](../graphics/stm_eqn01259.gif) 是谐波输入的系数。黏性阻尼因子 *c* 和临界阻尼因子 ![](../graphics/stm_eqn01040.gif) 之间的关系是 ![](../graphics/stm_eqn01260.gif)。

基于以上两个方程，如果我们希望黏性阻尼因子与结构阻尼因子具有相同的效果，我们必须

![](../graphics/stm_eqn01261.gif)如果我们进一步假设 ![](../graphics/stm_eqn01262.gif)，关系简化为

![](../graphics/stm_eqn01263.gif)现在我们考虑有限元系统方程，

![](../graphics/stm_eqn01264.gif)其中 ![](../graphics/stm_eqn01265.gif) 是有限元黏性阻尼矩阵，![](../graphics/stm_eqn01266.gif) 是有限元结构阻尼矩阵。如果我们将这些方程投影到特征模态上，阻尼矩阵变为

![](../graphics/stm_eqn01267.gif)可能是完全填充的。如果我们取 ![](../graphics/stm_eqn01265.gif) 和 ![](../graphics/stm_eqn01266.gif) 是对角的情况，它们的对角元素可以写成

![](../graphics/stm_eqn01268.gif)其中 ![](../graphics/stm_eqn00904.gif) 是特定模态。保持为单自由度系统开发的关系 ![](../graphics/stm_eqn01269.gif) 对于这个对角情况需要

![](../graphics/stm_eqn01270.gif)对于非对角矩阵，等效黏性阻尼的表达式变为

![](../graphics/stm_eqn01271.gif)其中 D 是对角矩阵，其条目由下式给出

![](../graphics/stm_eqn01272.gif)
### 节点和单元变量的响应

时间积分以广义坐标进行，然后物理变量的响应通过求和立即可得：

![](../graphics/stm_eqn01273.gif)

![](../graphics/stm_eqn01274.gif)

![](../graphics/stm_eqn01275.gif)

![](../graphics/stm_eqn01276.gif)其中 ![](../graphics/stm_eqn01277.gif) 是模态，![](../graphics/stm_eqn01278.gif) 是模态应变振幅，![](../graphics/stm_eqn01279.gif) 是模态应力振幅，![](../graphics/stm_eqn01280.gif) 是与每个特征向量 ![](../graphics/stm_eqn00904.gif) 对应的模态反力振幅。
### 初始条件

在步骤开始时，初始位移和初始速度必须转换为广义坐标的等效值，这仅在特征向量数等于自由度数时才能精确完成。由于通常不是这种情况，广义坐标位移和速度的初始值计算为

![](../graphics/stm_eqn01281.gif)其中 ![](../graphics/stm_eqn01282.gif) 是特征向量 ![](../graphics/stm_eqn00904.gif) 的广义质量，![](../graphics/stm_eqn01283.gif) 是特征向量，![](../graphics/stm_eqn01284.gif) 是质量矩阵，![](../graphics/stm_eqn01285.gif) 是初始位移。

类似地，对于初始速度

![](../graphics/stm_eqn01286.gif)

对于由先前模态动力学分析给出初始条件的情况，广义位移、速度和加速度简单地从前一个分析中获取。
### 基础运动定义

许多线性动力学问题涉及求解结构对"基础运动"的响应：作为结构位移被规定点的位移、速度或加速度的时间历史。在所有情况下，这些基础运动都转换为加速度历史。如果位移或速度历史在时间 ![](../graphics/stm_eqn01287.gif) 0 时有非零值，则在时间 ![](../graphics/stm_eqn01287.gif) 0 和 ![](../graphics/stm_eqn01288.gif) 时对加速度历史进行修正。如果给出速度，在 ![](../graphics/stm_eqn01287.gif) 0 时的加速度为

![](../graphics/stm_eqn01289.gif)如果给出位移，在 ![](../graphics/stm_eqn01287.gif) 0 和 ![](../graphics/stm_eqn01288.gif) 时的加速度为

![](../graphics/stm_eqn01290.gif)在上述表达式以及随后的表达式中，上标 * 表示用户定义的振幅数据。

如果为表格或等间距振幅曲线定义给出速度，加速度由中心差分规则定义

![](../graphics/stm_eqn01291.gif)如果给出位移，加速度由中心差分规则定义

![](../graphics/stm_eqn01292.gif)

响应是相对于基础计算的。如果需要节点变量的总值，则将基础的运动添加到相对值：

![](../graphics/stm_eqn01293.gif)其中

![](../graphics/stm_eqn01294.gif)
### 参考

### 参考

"Abaqus Analysis User's Guide" 第6.3.7节"瞬态模态动力学分析"