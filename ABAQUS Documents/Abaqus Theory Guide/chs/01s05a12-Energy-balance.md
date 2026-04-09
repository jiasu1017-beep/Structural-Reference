# 1.5.5 能量平衡

### 1.5.5 能量平衡

**产品：** Abaqus/Standard  Abaqus/Explicit

热力学第一定律所隐含的能量守恒表明，固定材料体的动能和内能的时间变化率等于表面力和体力所做的功的功率率之和。这可以表示为

![](../graphics/stm_eqn00592.gif)其中

![](../graphics/stm_eqn00593.gif)

是当前质量密度，

![](../graphics/stm_eqn00427.gif)

是速度场向量，

*U*

是每单位质量的内能，

![](../graphics/stm_eqn00479.gif)

是表面牵引力向量，

![](../graphics/stm_eqn00480.gif)

是体力向量，和

![](../graphics/stm_eqn00483.gif)

是边界 *S* 上的法线方向向量。

利用高斯定理和在边界 *S* 上 ![](../graphics/stm_eqn00594.gif) 的恒等式，[方程 1.5.5-1](01s05a12.md) 右边第一项可以重写为

![](../graphics/stm_eqn00595.gif) 其中我们使用了 ![](../graphics/stm_eqn00596.gif) 是对称的事实，我们也知道（见"平衡与虚功"第1.5.1节）

![](../graphics/stm_eqn00597.gif)其中 ![](../graphics/stm_eqn00598.gif) 是应变率张量（见"变形率与应变增量"第1.4.3节）。 将 [方程 1.5.5-2](01s05a12.md) 代入 [方程 1.5.5-1](01s05a12.md) 得到

![](../graphics/stm_eqn00599.gif)

从Cauchy运动方程我们有

![](../graphics/stm_eqn00600.gif) 将其代入 [方程 1.5.5-3](01s05a12.md) 给出

![](../graphics/stm_eqn00601.gif)由此得到能量方程

![](../graphics/stm_eqn00602.gif)积分此方程我们发现

![](../graphics/stm_eqn00603.gif)其中 ![](../graphics/stm_eqn00604.gif) 是时间 ![](../graphics/stm_eqn00605.gif) 时的能量。为了使能量平衡（[方程 1.5.5-1](01s05a12.md)）更方便使用，我们对其进行时间积分：

![](../graphics/stm_eqn00606.gif)或

![](../graphics/stm_eqn00607.gif)其中

![](../graphics/stm_eqn00608.gif) 定义为外力和接触表面之间摩擦力对物体所做的功的功率率。![](../graphics/stm_eqn00609.gif)，动能，由下式给出

![](../graphics/stm_eqn00610.gif)而 ![](../graphics/stm_eqn00611.gif) 定义为

![](../graphics/stm_eqn00612.gif)为了更精确地跟踪物理上可区分的工程现象，我们引入了应力、应变和牵引力的分解。

我们可以将牵引力 ![](../graphics/stm_eqn00479.gif) 分解为表面分布载荷 ![](../graphics/stm_eqn00613.gif)、固体无限元辐射牵引力 ![](../graphics/stm_eqn00614.gif) 和摩擦牵引力 ![](../graphics/stm_eqn00615.gif)。然后 ![](../graphics/stm_eqn00616.gif) 可以写成

![](../graphics/stm_eqn00617.gif)其中 ![](../graphics/stm_eqn00618.gif) 是外力对物体所做的功的功率率，![](../graphics/stm_eqn00619.gif) 是固体介质无限元阻尼效应消耗的能量率，![](../graphics/stm_eqn00620.gif) 是接触表面之间摩擦力消耗的能量率。整个模型的能量平衡可以写成

![](../graphics/stm_eqn00621.gif)为方便起见，内能的耗散部分被分离出来：

![](../graphics/stm_eqn00622.gif) 其中 ![](../graphics/stm_eqn00623.gif) 是从用户指定的本构方程推导的应力，不包括黏性耗散效应；![](../graphics/stm_eqn00624.gif) 是弹性应力；![](../graphics/stm_eqn00625.gif) 是黏性应力（为体积黏性、材料阻尼和阻尼器定义）；![](../graphics/stm_eqn00626.gif) 是黏性效应消耗的能量；![](../graphics/stm_eqn00627.gif) 是剩余的能量，我们继续称之为内能。 如果我们引入应变分解，![](../graphics/stm_eqn00628.gif)（其中 ![](../graphics/stm_eqn00629.gif)、![](../graphics/stm_eqn00630.gif) 和 ![](../graphics/stm_eqn00631.gif) 分别是弹性、塑性和蠕变应变率），内能 ![](../graphics/stm_eqn00627.gif) 可以表示为

![](../graphics/stm_eqn00632.gif)其中 ![](../graphics/stm_eqn00633.gif) 是施加的弹性应变能，![](../graphics/stm_eqn00634.gif) 是塑性消耗的能量，![](../graphics/stm_eqn00635.gif) 是时间依赖变形（蠕变、膨胀和黏弹性）消耗的能量。

如果材料中发生损伤，不是所有施加的弹性应变能都可以恢复。在任何给定时间，应力 ![](../graphics/stm_eqn00623.gif) 可以用"无损伤"应力 ![](../graphics/stm_eqn00636.gif) 和连续损伤参数 *d* 表示：

![](../graphics/stm_eqn00637.gif)损伤参数 *d* 从零（未损伤材料）开始，增加到不超过一（完全损伤材料）的最大值。因此，我们可以写成

![](../graphics/stm_eqn00638.gif)我们假设，在卸载时，损伤参数保持在时间 *t* 时达到的值。因此，可恢复的应变能等于

![](../graphics/stm_eqn00639.gif)通过损伤消耗的能量等于

![](../graphics/stm_eqn00640.gif)如果我们定义

![](../graphics/stm_eqn00641.gif)为无损伤弹性能函数，我们可以写成

![](../graphics/stm_eqn00642.gif)和

![](../graphics/stm_eqn00643.gif)交换积分顺序得到

![](../graphics/stm_eqn00644.gif)和

![](../graphics/stm_eqn00645.gif)最后表达式的第一项消失了，因为在时间 *t* 时 ![](../graphics/stm_eqn00646.gif)，在时间零时 ![](../graphics/stm_eqn00647.gif)。如果我们现在定义损伤应变能函数

![](../graphics/stm_eqn00648.gif)那么

![](../graphics/stm_eqn00649.gif)对于线性弹性能函数

![](../graphics/stm_eqn00650.gif)因此，

![](../graphics/stm_eqn00651.gif)
### 参考文献

### 参考文献

"Abaqus Analysis User's Guide" 第4.2.1节"Abaqus/Standard输出变量标识符"

"Abaqus Analysis User's Guide" 第4.2.2节"Abaqus/Explicit输出变量标识符"