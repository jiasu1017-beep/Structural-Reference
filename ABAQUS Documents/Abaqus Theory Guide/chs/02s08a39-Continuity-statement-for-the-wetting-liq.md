# 2.8.4 多孔介质中润湿液相的连续性方程

### 2.8.4 多孔介质中润湿液相的连续性方程

**产品：** Abaqus/Standard

Abaqus/Standard为通过多孔介质的特定流体流动情况提供了功能。这些情况与介质中存在相对不可压缩的润湿液体相关。介质可能完全或部分被该液体饱和。当介质仅部分饱和时，孔隙的其余部分被另一种流体填充。例子是岩土工程问题，土壤含有水和空气：连续性方程是为水相编写的。

润湿液体可以附着在介质中的某些固体颗粒上，从而被它们捕获：附着在固体颗粒上的这部分被困液体形成"凝胶"。

Abaqus通过将有限元网格附着在固相上来近似建模多孔介质。液体可以通过这个网格流动。因此，需要为液体编写连续性方程，将一点处储存的液体质量增长率等于时间增量内流入该点的液体质量率。本节定义了这个连续性方程。它以变分形式编写，作为有限元近近的基础。液体流动通过引入达西定律或替代地引入Forchheimer定律来描述。连续性方程在使用过量润湿液体压力作为节点变量（自由度8）在单元上插值来近似满足。方程通过使用向后Euler近似进行时间积分。需要这个积分连续性变分陈述关于节点变量的全导数用于求解非线性、耦合、平衡和连续性方程的Newton迭代。本节还推导了这个表达式。

考虑一个包含固定量固体物质的体积。在当前配置中，这个体积占据空间*V*，表面为*S*。在参考配置中，它占据空间![](../graphics/stm_eqn01828.gif)。润湿液体可以通过这个体积流动：在任何时候，这种"自由"液体（如果受到压力驱动可以流动的液体）的体积写为![](../graphics/stm_eqn01829.gif)。润湿液体也可以通过被凝胶吸收而被困在体积中。这种被困液体的体积写为![](../graphics/stm_eqn01830.gif)。

控制体积中润湿液体的总质量为

![](../graphics/stm_eqn01831.gif)其中![](../graphics/stm_eqn01748.gif)液体的质量密度。

润湿液体质量的时变率为

![](../graphics/stm_eqn01832.gif)

穿过表面进入体积的润湿液体质量除以时间为

![](../graphics/stm_eqn01833.gif)其中![](../graphics/stm_eqn01834.gif)润湿液体相对于固相的平均速度（渗流速度），![](../graphics/stm_eqn00483.gif)*S*的外法线。

将液体质量经表面*S*的增加与体积*V*内液体质量的变化率相等，得到润湿液体质量连续性方程

![](../graphics/stm_eqn01835.gif)使用散度定理，由于体积是任意的，这提供了逐点方程

![](../graphics/stm_eqn01836.gif)

等效的弱形式为

![](../graphics/stm_eqn01837.gif)其中![](../graphics/stm_eqn01838.gif)任意的、连续的变分场。这个陈述也可以写在参考体积上：

![](../graphics/stm_eqn01839.gif)

在Abaqus/Standard中，这个连续性陈述通过向后Euler公式近似进行时间积分，给出

![](../graphics/stm_eqn01840.gif)在当前体积上，这是

![](../graphics/stm_eqn01841.gif)我们现在通过采用约定 drop 下标![](../graphics/stm_eqn01842.gif)即任何未明确与时间点关联的量取在![](../graphics/stm_eqn01842.gif)

散度定理允许将方程重写为

![](../graphics/stm_eqn01843.gif)其中——为方便起见——我们通过参考配置中液体的密度![](../graphics/stm_eqn01777.gif)方程进行了归一化。

![](../graphics/stm_eqn01844.gif)由于![](../graphics/stm_eqn01844.gif)这与

![](../graphics/stm_eqn01845.gif)

相同。
![](../graphics/stm_eqn01846.gif)### 本构行为

![](../graphics/stm_eqn01847.gif)![](../graphics/stm_eqn01848.gif)![](../graphics/stm_eqn00155.gif)孔隙流体流动的本构行为由达西定律或Forchheimer定律控制。达西定律通常适用于低流体流速，而Forchheimer定律常用于涉及较高流速的情况。达西定律可以被认为是Forchheimer定律的线性化版本。达西定律指出，在均匀条件下，润湿液体通过介质单位面积的体积流率![](../graphics/stm_eqn01846.gif)测压水头梯度的负值成正比（[Bear，1972](07s01a01-References.md)）：

![](../graphics/stm_eqn01853.gif)![](../graphics/stm_eqn01854.gif)![](../graphics/stm_eqn01847.gif)其中![](../graphics/stm_eqn01848.gif)介质的渗透率，![](../graphics/stm_eqn00155.gif)测压水头，定义为

![](../graphics/stm_eqn01849.gif)其中*z*是相对于某个基准面的高程，*g*是重力加速度的大小，它沿与*z*相反的方向作用。另一方面，Forchheimer定律指出，测压水头梯度的负值与润湿液体通过介质单位面积的体积流率的二次函数相关（[Desai，1975](07s01a01-References.md)）：

![](../graphics/stm_eqn01851.gif)![](../graphics/stm_eqn01852.gif)![](../graphics/stm_eqn01850.gif)其中![](../graphics/stm_eqn01851.gif)一个"速度系数"（[Tariq，1987](07s01a01-References.md)）。这个非线性渗透率可以定义为孔隙比的函数。我们看到，当流体速度趋于零时，Forchheimer定律趋近于达西定律。此外，如果![](../graphics/stm_eqn01852.gif)两种流动定律是相同的。

![](../graphics/stm_eqn01848.gif)![](../graphics/stm_eqn01853.gif)![](../graphics/stm_eqn01854.gif)![](../graphics/stm_eqn01848.gif)以是各向异性的，是饱和度和材料孔隙比的函数。![](../graphics/stm_eqn01848.gif)有速度单位（长度/时间）。一些作者将![](../graphics/stm_eqn01848.gif)为水力传导率（[Bear，1972](07s01a01-References.md)），并将渗透率定义为

![](../graphics/stm_eqn01853.gif)其中![](../graphics/stm_eqn01854.gif)流体的运动粘度（流体动力粘度与其密度之比）。]

![](../graphics/stm_eqn01855.gif)![](../graphics/stm_eqn01856.gif)![](../graphics/stm_eqn01748.gif)我们假设*g*在大小和方向上是恒定的，所以

![](../graphics/stm_eqn01855.gif)其中![](../graphics/stm_eqn01856.gif)重力加速度（我们假设![](../graphics/stm_eqn01748.gif)位置缓慢变化）。

![](../graphics/stm_eqn01857.gif)![](../graphics/stm_eqn01858.gif)![](../graphics/stm_eqn01859.gif)![](../graphics/stm_eqn01860.gif)多相流动系统中特定流体的渗透率取决于所考虑相的饱和度和介质的孔隙率。我们假设这些依赖性是可分离的，所以

![](../graphics/stm_eqn01857.gif)其中![](../graphics/stm_eqn01858.gif)供了对饱和度的依赖性，![](../graphics/stm_eqn01859.gif)![](../graphics/stm_eqn01860.gif)完全饱和介质的渗透率。

![](../graphics/stm_eqn01861.gif)![](../graphics/stm_eqn01862.gif)![](../graphics/stm_eqn01863.gif)函数![](../graphics/stm_eqn01861.gif)以由用户定义。[Nguyen和Durso（1983）](07s01a01-References.md)观察到，在通过部分饱和介质的稳态流动中，渗透率随![](../graphics/stm_eqn01862.gif)化。因此，我们默认取![](../graphics/stm_eqn01863.gif)

![](../graphics/stm_eqn01864.gif)引入流动本构定律允许质量连续性方程（[方程2.8.4-1](02s08a39-Continuity-statement-for-the-wetting-liq.md)）被写为

![](../graphics/stm_eqn01864.gif)
### 液体和颗粒中的体积应变

![](../graphics/stm_eqn01865.gif)颗粒的体积行为在"多孔介质中的本构行为"第2.8.3节中讨论。从[方程2.8.3-2](02s08a38-Constitutive-behavior-in-a-porous-medium.md)，

![](../graphics/stm_eqn01865.gif)将其与[方程2.8.1-4](02s08a36-Effective-stress-principle-for-porous-me.md)结合并忽略除了小量中的一阶项之外的所有项，我们得到

![](../graphics/stm_eqn01866.gif)使用[方程2.8.3-1](02s08a38-Constitutive-behavior-in-a-porous-medium.md)，再次忽略二阶小量，我们得到

![](../graphics/stm_eqn01867.gif)将此结果与[方程2.8.3-4](02s08a38-Constitutive-behavior-in-a-porous-medium.md)结合，再次近似到一阶小量，

![](../graphics/stm_eqn01868.gif)
![](../graphics/stm_eqn01719.gif)![](../graphics/stm_eqn01869.gif)![](../graphics/stm_eqn01719.gif)![](../graphics/stm_eqn01870.gif)![](../graphics/stm_eqn01871.gif)### 饱和度

由于![](../graphics/stm_eqn01719.gif)量润湿液体中的压力，而我们忽略介质中另一流体相中的压力（见"多孔介质的有效应力原理"第2.8.1节），当![](../graphics/stm_eqn01869.gif)，介质完全饱和。![](../graphics/stm_eqn01719.gif)负值表示介质中的毛细管效应。对于![](../graphics/stm_eqn01870.gif)已知（例如，见[Nguyen和Durso，1983](07s01a01-References.md)），在给定的毛细管压力值下，![](../graphics/stm_eqn01871.gif)饱和度在某个范围内。图2.8.4-1显示了这些范围的典型形式。

![](../graphics/stm_eqn01872.gif)![](../graphics/stm_eqn01873.gif)![](../graphics/stm_eqn01874.gif)![](../graphics/stm_eqn01875.gif)![](../graphics/stm_eqn01876.gif)![](../graphics/stm_eqn01877.gif)![](../graphics/stm_eqn01878.gif)![](../graphics/stm_eqn01879.gif)图2.8.4-1 典型的液体吸收和解吸行为。

![](../graphics/stmliquid-absorp-exsorp-nls.png) 我们将这些范围写为![](../graphics/stm_eqn01872.gif)其中![](../graphics/stm_eqn01873.gif)发生吸收的限制（所以![](../graphics/stm_eqn01874.gif)，![](../graphics/stm_eqn01875.gif)发生解吸的限制，因此![](../graphics/stm_eqn01876.gif)我们假设这些关系是唯一可逆的，因此也可以在吸收期间写为![](../graphics/stm_eqn01877.gif)在解吸期间写为![](../graphics/stm_eqn01878.gif)我们还假设一些润湿液体将始终存在于介质中：![](../graphics/stm_eqn01879.gif)

![](../graphics/stm_eqn01880.gif)[Bear（1972）](07s01a01-References.md)建议，吸收和解吸之间的转换以及相反过程沿"扫描"曲线进行。我们用直线近似这些，如图2.8.4-1所示。

![](../graphics/stm_eqn01881.gif)![](../graphics/stm_eqn01882.gif)![](../graphics/stm_eqn01883.gif)![](../graphics/stm_eqn01884.gif)饱和度被视为状态变量，如果润湿液体压力超出根据与图2.8.4-1对应的实际数据其值可接受的范围，则可能必须改变。饱和度作为状态变量的演化定义如下。假设时间*t*的饱和度![](../graphics/stm_eqn01880.gif)已知的。它必须满足约束

![](../graphics/stm_eqn01881.gif)我们求解连续性方程得到![](../graphics/stm_eqn01882.gif)最初假设![](../graphics/stm_eqn01883.gif)然后我们通过以下规则获得![](../graphics/stm_eqn01884.gif)

![](../graphics/stm_eqn01885.gif)其中![](../graphics/stm_eqn01886.gif)扫描线的斜率。这些选择如图2.8.4-2所示。

图2.8.4-2 unsaturated情况下*s*的演化。

![](../graphics/stm_eqn01748.gif)![](../graphics/stm_eqn01831.gif)![](../graphics/stmunsat-s-evol.png)
![](../graphics/stm_eqn01887.gif)![](../graphics/stm_eqn01719.gif)![](../graphics/stm_eqn00438.gif)### Jacobian贡献

![](../graphics/stm_eqn01888.gif)![](../graphics/stm_eqn01719.gif)连续性方程的Jacobian贡献是从[方程2.8.4-2](02s08a39-Continuity-statement-for-the-wetting-liq.md)相对于![](../graphics/stm_eqn01887.gif)![](../graphics/stm_eqn01719.gif)时间![](../graphics/stm_eqn00438.gif)变分获得的。

首先考虑表面积分。表面分为液体质量流率![](../graphics/stm_eqn01888.gif)规定的那部分和润湿液体压力![](../graphics/stm_eqn01719.gif)规定的那部分。因此，这项对Jacobian的唯一贡献是由质量流率被规定的那部分表面积变化引起的积分变化。我们忽略这个贡献。

![](../graphics/stm_eqn01886.gif)![](../graphics/stm_eqn01885.gif)![](../graphics/stm_eqn01889.gif)[方程2.8.4-2](02s08a39-Continuity-statement-for-the-wetting-liq.md)变分的剩余部分是

![](../graphics/stm_eqn01889.gif)

![](../graphics/stm_eqn01884.gif)![](../graphics/stm_eqn01881.gif)![](../graphics/stm_eqn01882.gif)![](../graphics/stm_eqn01883.gif)![](../graphics/stm_eqn01837.gif)![](../graphics/stm_eqn01838.gif)![](../graphics/stm_eqn01890.gif)使用[方程2.8.4-3](02s08a39-Continuity-statement-for-the-wetting-liq.md)，我们有

![](../graphics/stm_eqn01890.gif)因此，忽略与1相比很小的项，

![](../graphics/stm_eqn01891.gif)

![](../graphics/stm_eqn01852.gif)[方程2.8.3-5](02s08a38-Constitutive-behavior-in-a-porous-medium.md)表明![](../graphics/stm_eqn01892.gif)它由"多孔介质中的本构行为"第2.8.3节中给出的演化方程定义，因此对Jacobian没有贡献。

![](../graphics/stm_eqn01893.gif)最后，渗透率项的Jacobian贡献在Forchheimer流动定律的一般情况下相当复杂。虽然我们在软件中包含了它，但这里我们只写反映达西定律（![](../graphics/stm_eqn01852.gif)的线性化流动版本：

![](../graphics/stm_eqn01893.gif)

![](../graphics/stm_eqn01894.gif)使用这些结果提供连续性方程的Jacobian为

![](../graphics/stm_eqn01894.gif)
### 参考文献

### 参考文献

"Abaqus Analysis User's Guide"第6.8.1节"耦合孔隙流体扩散与应力分析"

![](../graphics/stm_eqn01890.gif)"Abaqus Analysis User's Guide"第26.6.1节"孔隙流体流动特性"
