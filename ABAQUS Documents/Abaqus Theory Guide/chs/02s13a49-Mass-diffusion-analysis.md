# 2.13.1 质量扩散分析

### 2.13.1 质量扩散分析

**产品：** Abaqus/Standard

Abaqus/Standard提供了对一种材料通过另一种材料的瞬态或稳态扩散进行建模的能力，例如氢通过金属的扩散（[Crank（1956）](07s01a01-References.md)、[deGroot和Mazur（1962）](07s01a01-References.md)）。主导方程是Fick方程的扩展，以允许扩散物质在基体材料中具有不均匀的溶解度。

![](../graphics/stm_eqn02465.gif)![](../graphics/stm_eqn00155.gif)基本求解变量（用作网格节点上的自由度）是"归一化浓度"（通常称为扩散物质的"活度"），![](../graphics/stm_eqn02465.gif)其中*c*是扩散物质的质量浓度，*s*是其在基体材料中的溶解度。这意味着当网格包含共享节点的不同材料时，归一化浓度在不同材料之间的界面上是连续的。由于![](../graphics/stm_eqn00155.gif)扩散相分压的平方根，界面两侧的分压相同；假设界面处满足Sievert定律。
### 主导方程

扩散问题从扩散相的质量守恒要求定义：

![](../graphics/stm_eqn02466.gif)其中*V*是任何体积，其表面为*S*，![](../graphics/stm_eqn00483.gif)*S*的外法线，![](../graphics/stm_eqn02404.gif)扩散相浓度的通量，![](../graphics/stm_eqn02467.gif)离开*S*的浓度通量。

使用散度定理，

![](../graphics/stm_eqn02468.gif)由于体积是任意的，这提供了逐点方程

![](../graphics/stm_eqn02469.gif)

等效的弱形式为

![](../graphics/stm_eqn02470.gif)其中![](../graphics/stm_eqn02471.gif)任意、适当连续的标量场。

这个陈述可以重写为

![](../graphics/stm_eqn02472.gif)再次使用散度定理产生

![](../graphics/stm_eqn02473.gif)
### 本构行为

扩散被假定为由化学势梯度驱动，这给出了一般行为

![](../graphics/stm_eqn02474.gif)其中![](../graphics/stm_eqn02475.gif)扩散率；![](../graphics/stm_eqn02476.gif)溶解度；![](../graphics/stm_eqn02477.gif)"Soret效应"因子，提供由温度梯度引起的扩散；![](../graphics/stm_eqn01111.gif)温度；![](../graphics/stm_eqn02243.gif)所用温度标度的绝对零；![](../graphics/stm_eqn02478.gif)压力应力因子，提供由等效压力应力梯度![](../graphics/stm_eqn02479.gif)动的扩散；![](../graphics/stm_eqn00480.gif)任何预定义的场变量。

这个本构模型特定形式的一个例子是对金属中氢扩散的假设：

![](../graphics/stm_eqn02480.gif)其中化学势![](../graphics/stm_eqn02482.gif)![](../graphics/stm_eqn02483.gif)![](../graphics/stm_eqn02481.gif)其中![](../graphics/stm_eqn02483.gif)氢在固溶体中的偏摩尔体积。这个形式类似于[Sofronis和McMeeking（1989）](07s01a01-References.md)使用的，并导致形式为本构表达式

![](../graphics/stm_eqn02484.gif)为了实现这个特定形式，必须从方程

![](../graphics/stm_eqn02486.gif)计算数据和![](../graphics/stm_eqn02487.gif)改变变量（![](../graphics/stm_eqn02487))并将[方程2.13.1-3](02s13a49-Mass-diffusion-analysis.md)的本构假设引入[方程2.13.1-2](02s13a49-Mass-diffusion-analysis.md)产生

![](../graphics/stm_eqn02488.gif)其中

![](../graphics/stm_eqn02489.gif)是穿过*S*进入身体的浓度通量。
### 离散化和时间积分

![](../graphics/stm_eqn02490.gif)![](../graphics/stm_eqn00981.gif)![](../graphics/stm_eqn02491.gif)在有限元模型中，平衡通过引入适当的插值函数近似为有限组方程。离散量用大写上标表示（例如，![](../graphics/stm_eqn02490])。对上标采用求和约定。这些表示节点变量，节点在相邻单元之间共享，并选择适当的插值以提供假设变化的充分连续性。插值基于材料坐标![](../graphics/stm_eqn00981.gif)![](../graphics/stm_eqn02491.gif)2、3。

虚拟归一化浓度场通过以下方式插值

![](../graphics/stm_eqn02492.gif)其中![](../graphics/stm_eqn02493.gif)插值函数。然后，离散方程写为

![](../graphics/stm_eqn02494.gif)

![](../graphics/stm_eqn01842.gif)![](../graphics/stm_eqn01842.gif)瞬态问题中的时间积分使用向后Euler方法（改进的Crank-Nicholson算子）。采用任何未明确与时间点关联的量取在![](../graphics/stm_eqn01842.gif)约定，我们可以 drop 下标![](../graphics/stm_eqn02495.gif)
![](../graphics/stm_eqn01087.gif)![](../graphics/stm_eqn02480.gif)### Jacobian贡献

![](../graphics/stm_eqn00155.gif)![](../graphics/stm_eqn00438.gif)守恒方程的Jacobian贡献是从[方程2.13.1-6](02s13a49-Mass-diffusion-analysis.md)相对于![](../graphics/stm_eqn00155.gif)时间![](../graphics/stm_eqn00438.gif)变分获得的。这产生

![](../graphics/stm_eqn02496.gif)

![](../graphics/stm_eqn02497.gif)重新排列并使用插值![](../graphics/stm_eqn02498.gif)我们获得

![](../graphics/stm_eqn02499.gif)

![](../graphics/stm_eqn02500.gif)

![](../graphics/stm_eqn00424.gif)![](../graphics/stm_eqn01709.gif)![](../graphics/stm_eqn02485.gif)检查上述方程，我们观察到，每当扩散率![](../graphics/stm_eqn00424.gif)温度驱动扩散系数![](../graphics/stm_eqn01709.gif)压力驱动扩散系数![](../graphics/stm_eqn02468.gif)"Abaqus Analysis User's Guide"第6.9.1节"质量扩散分析"
