# 4.3.9 变形塑性

### 4.3.9 变形塑性

**产品：** Abaqus/Standard

Abaqus/Standard中提供了变形塑性理论，以允许对延性金属进行完全塑性分析，通常在 small-displacement条件下，用于断裂力学应用。该模型基于Ramberg-Osgood关系。本节中定义了详细的本构模型。获得完全塑性解的程序通常包括增量加载直到响应是完全塑性的。

该模型称为变形塑性，因为应力由总机械应变定义，没有历史依赖。没有"卸载"准则（允许在应变反向后立即恢复初始弹性刚度），因此该模型仅在持续流动情况下作为塑性模型有用。它实际上是一个非线性弹性模型；但在极限状态，当整个试样或结构响应处于塑性状态时，由于其简单的形式，这是塑性响应的有用等价表示。
### 一维模型

基本一维模型为

![](../graphics/stm_eqn05986.gif)其中![](../graphics/stm_eqn01110.gif)是应力，![](../graphics/stm_eqn00377.gif)是机械应变，*E*是杨氏模量（定义为应力-应变曲线在零应力处的斜率），![](../graphics/stm_eqn00904.gif)是"屈服"偏移（从这个意义上说，当![](../graphics/stm_eqn05987.gif)时，![](../graphics/stm_eqn05988.gif)），*n*是"塑性"（非线性）项的硬化指数：![](../graphics/stm_eqn05989.gif)。

该模型描述的材料行为在所有应力水平下都是非线性的，但对于常用的硬化指数值（![](../graphics/stm_eqn05990.gif)或更大），非线性仅在应力大小接近或超过![](../graphics/stm_eqn05690.gif)时才变得显著。
### 多轴推广

第一个 term 的推广使用线性"弹性"关系；非线性项通过使用Mises应力势和相关流动法则推广到多轴应力状态，给出多轴模型

![](../graphics/stm_eqn05991.gif)其中

![](../graphics/stm_eqn00399.gif)

是应变张量，

![](../graphics/stm_eqn00033.gif)

是应力张量，

![](../graphics/stm_eqn05992.gif)

是等效静水应力，

![](../graphics/stm_eqn05993.gif)

是Mises等效应力，

![](../graphics/stm_eqn05994.gif)

是应力偏量，和

![](../graphics/stm_eqn01854.gif)

是泊松比。

行为的线性部分可能是可压缩或不可压缩的，取决于泊松比的值，但行为的非线性部分是不可压缩的（因为流动正交于Mises应力势）。由于该模型通常用于变形以塑性流动为主的情况，建议将此材料模型与选择性减缩积分单元或"杂交"（混合公式）单元一起使用（平面应力除外）。
### 应变能密度

该模型通常用于在需要*J*积分的断裂力学中获得完全塑性解。对于*J*积分评估，需要应变能密度。这是

![](../graphics/stm_eqn05995.gif)从[公式4.3.9-2](04s03a111.md)这可以得为

![](../graphics/stm_eqn05996.gif)
### 应力解

在每个积分点的分析过程中，运动学解的最新估计被提供给本构程序，后者必须提供针对所使用材料模型计算的相应应力张量。由于此材料模型是非线性的，我们使用下面描述的方法求解应力。

单轴情况（唯一的非零应力分量是一个直接应力）

在这种情况下

![](../graphics/stm_eqn05997.gif)其中现在![](../graphics/stm_eqn05998.gif)。

我们使用Newton法求解[公式4.3.9-3](04s03a111.md)得到![](../graphics/stm_eqn01110.gif)。将![](../graphics/stm_eqn05999.gif)写为![](../graphics/stm_eqn01110.gif)的校正，[公式4.3.9-3](04s03a111.md)的Newton方程为

![](../graphics/stm_eqn06000.gif)

![](../graphics/stm_eqn06001.gif)作为初始猜测，如果![](../graphics/stm_eqn06003.gif)我们使用![](../graphics/stm_eqn06002.gif)，如果![](../graphics/stm_eqn06005.gif)则使用![](../graphics/stm_eqn06004.gif)（符号选择与![](../graphics/stm_eqn00377.gif)相同）。

在这种情况下材料刚度矩阵为

![](../graphics/stm_eqn06006.gif)所有由运动学定义应变分量的情况

当所有应变分量由运动学定义时（即除单轴和平面应力情况外的所有情况），将[公式4.3.9-2](04s03a111.md)投影到![](../graphics/stm_eqn06007.gif)上给出

![](../graphics/stm_eqn06008.gif)体积行为的线性关系。定义偏应变为

![](../graphics/stm_eqn06009.gif)并使用[公式4.3.9-2](04s03a111.md)，我们得到

![](../graphics/stm_eqn06010.gif)定义等效偏应变为

![](../graphics/stm_eqn06011.gif)并使用[公式4.3.9-4](04s03a111.md)，我们得到标量方程

![](../graphics/stm_eqn06012.gif)该方程使用Newton法求解*q*：

![](../graphics/stm_eqn06013.gif)

![](../graphics/stm_eqn06014.gif)对于单轴情况，我们将使用起始猜测：

![](../graphics/stm_eqn06015.gif)和

![](../graphics/stm_eqn06016.gif)[公式4.3.9-6](04s03a111.md)也可用于定义

![](../graphics/stm_eqn06017.gif)以便[公式4.3.9-4](04s03a111.md)变为

![](../graphics/stm_eqn06018.gif)因此，一旦知道*q*，![](../graphics/stm_eqn05748.gif)就被定义；从而，![](../graphics/stm_eqn00033.gif)已知为

![](../graphics/stm_eqn06019.gif)材料刚度定义如下。从[公式4.3.9-7](04s03a111.md)我们有

![](../graphics/stm_eqn06020.gif)且[公式4.3.9-6](04s03a111.md)给出

![](../graphics/stm_eqn06021.gif)且从[公式4.3.9-5](04s03a111.md),

![](../graphics/stm_eqn06022.gif)使用这些结果，[公式4.3.9-8](04s03a111.md)变为

![](../graphics/stm_eqn06023.gif)现在

![](../graphics/stm_eqn06024.gif)

![](../graphics/stm_eqn06025.gif)和

![](../graphics/stm_eqn06026.gif)结合这些结果，我们获得材料刚度为

![](../graphics/stm_eqn06027.gif)平面应力

对于这种情况，我们假设材料完全不可压缩来求解![](../graphics/stm_eqn00033.gif)。然后我们使用这个解作为Newton循环的起始猜测来找到![](../graphics/stm_eqn00033.gif]。最后，我们计算相应的材料刚度矩阵。

不可压缩近似：

在这种情况下![](../graphics/stm_eqn06028.gif)和![](../graphics/stm_eqn06029.gif)，所以![](../graphics/stm_eqn06030.gif)是已知的，[公式4.3.9-6](04s03a111.md)可以像之前一样求解*q*。[公式4.3.9-7](04s03a111.md)然后定义![](../graphics/stm_eqn05748.gif)，平面应力约束要求![](../graphics/stm_eqn03408.gif)，所以

![](../graphics/stm_eqn06031.gif)从而，我们获得解的初始估计

![](../graphics/stm_eqn06032.gif)

![](../graphics/stm_eqn06033.gif)和

![](../graphics/stm_eqn06034.gif)实际应力的Newton解：

[公式4.3.9-2](04s03a111.md)定义应力，其中对于这种情况，

![](../graphics/stm_eqn06035.gif)

![](../graphics/stm_eqn06036.gif)和

![](../graphics/stm_eqn06037.gif)因此，[公式4.3.9-2](04s03a111.md)变为

![](../graphics/stm_eqn06038.gif)这些方程使用Newton法求解：

![](../graphics/stm_eqn06039.gif)

![](../graphics/stm_eqn06040.gif)

![](../graphics/stm_eqn06041.gif)材料刚度直接从[公式4.3.9-9](04s03a111.md)可得为

![](../graphics/stm_eqn06042.gif)
### 参考

### 参考

"Deformation plasticity,"  Section 23.2.13 of the Abaqus Analysis User's Guide
