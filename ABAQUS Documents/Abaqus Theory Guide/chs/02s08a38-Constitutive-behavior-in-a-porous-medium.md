# 2.8.3 多孔介质中的本构行为

![](../graphics/stm_eqn01813.gif)### 2.8.3 多孔介质中的本构行为

**产品：** Abaqus/Standard

Abaqus/Standard中的多孔介质被认为是固体物质、含有液体和气体的孔隙以及附着在固体物质上的被困液体的混合物。多孔介质的力学行为包括液体和固体物质对局部压力的响应，以及整体材料对有效应力的响应。本节讨论对这些响应的假设。
### 液体响应

对于系统中的液体（孔隙中的自由液体和被困液体），我们假设

![](../graphics/stm_eqn01776.gif)其中![](../graphics/stm_eqn01748.gif)液体的密度，![](../graphics/stm_eqn01777.gif)液体在参考配置中的密度，![](../graphics/stm_eqn01778.gif)液体的体积模量，

![](../graphics/stm_eqn01779.gif)是由温度变化引起的液体体积膨胀。这里![](../graphics/stm_eqn01780.gif)液体的热膨胀系数，![](../graphics/stm_eqn01111.gif)当前温度，![](../graphics/stm_eqn01781.gif)介质中该点的初始温度，![](../graphics/stm_eqn01782.gif)热膨胀的参考温度。![](../graphics/stm_eqn01783.gif)![](../graphics/stm_eqn01784.gif)被假设为很小。
![](../graphics/stm_eqn01799.gif)### 颗粒响应
![](../graphics/stm_eqn01793.gif)![](../graphics/stm_eqn01794.gif)![](../graphics/stm_eqn01795.gif)![](../graphics/stm_eqn01796.gif)![](../graphics/stm_eqn01797.gif)
多孔介质中的固体物质假设在压力下具有局部力学响应

![](../graphics/stm_eqn01785.gif)其中![](../graphics/stm_eqn01786.gif)固体物质的体积模量，*s*是润湿流体中的饱和度，

![](../graphics/stm_eqn01787.gif)是其体积热应变。这里![](../graphics/stm_eqn01788.gif)固体物质的热膨胀系数，![](../graphics/stm_eqn01789.gif)此膨胀的参考温度。![](../graphics/stm_eqn01790.gif)假设为很小。

![](../graphics/stm_eqn01791.gif)![](../graphics/stm_eqn01591.gif)![](../graphics/stm_eqn01791.gif)重要的是将![](../graphics/stm_eqn01791.gif)![](../graphics/stm_eqn01591.gif)分为固体颗粒材料的属性。整个多孔介质将表现出比![](../graphics/stm_eqn01791.gif)指示的更软（通常不可恢复）的整体体积行为，并且还将显示不同的热膨胀。这些效应部分是结构性的，由介质由部分接触的不规则颗粒组成引起。它们也可能是由系统仅部分饱和引起的，孔隙中含有相对可压缩的气体和相对不可压缩的液体。
### 液体捕获

![](../graphics/stm_eqn01792.gif)液体捕获与吸收液体并膨胀成"凝胶"的特定材料相关。这种行为的简单模型基于将该凝胶理想化为等半径![](../graphics/stm_eqn01792.gif)单个球形颗粒的体积。[Tanaka和Fillmore（1979）](07s01a01-References.md)表明，当这种材料的单个球体完全暴露于液体时，其半径变化可以建模为

![](../graphics/stm_eqn01793.gif)其中![](../graphics/stm_eqn01794.gif)当![](../graphics/stm_eqn01795.gif)趋近的完全膨胀半径，*N*、![](../graphics/stm_eqn01796.gif)![](../graphics/stm_eqn01797.gif)材料参数。Tanaka和Fillmore还表明，级数中的第一项占主导地位，因此模型可以简化为

![](../graphics/stm_eqn01798.gif)这提供了速率形式
![](../graphics/stm_eqn01808.gif)
![](../graphics/stm_eqn01799.gif)

![](../graphics/stm_eqn01800.gif)![](../graphics/stm_eqn01801.gif)当凝胶颗粒仅部分暴露于液体时（在 unsaturated 系统中），可以合理地假设膨胀速率将根据饱和度水平而降低。此外，我们假设凝胶仅在周围介质的饱和度超过凝胶的有效饱和度![](../graphics/stm_eqn01800.gif)膨胀，其中![](../graphics/stm_eqn01801.gif)完全干燥的凝胶颗粒的半径。我们将这些组合成一个简单的线性效应：

![](../graphics/stm_eqn01802.gif)其中如果![](../graphics/stm_eqn01804.gif)则![](../graphics/stm_eqn01803.gif)否则为![](../graphics/stm_eqn01805.gif)

![](../graphics/stm_eqn01806.gif)堆积密度和膨胀可能导致凝胶颗粒接触。在这种情况下，可用于吸收和捕获液体的表面积减少，直到如果凝胶颗粒占据除固体材料外的整个体积，液体捕获必须完全停止。每单位参考体积有![](../graphics/stm_eqn01806.gif)凝胶颗粒，在它们必须接触之前（以面心立方排列）凝胶颗粒可以达到的最大半径为
![](../graphics/stm_eqn01827.gif)
![](../graphics/stm_eqn01807.gif)当有效凝胶半径为
![](../graphics/stm_eqn01776.gif)![](../graphics/stm_eqn01748.gif)![](../graphics/stm_eqn01777.gif)![](../graphics/stm_eqn01778.gif)
![](../graphics/stm_eqn01808.gif)时，体积完全被凝胶和固体物质占据。因此，凝胶膨胀行为进一步修改为

![](../graphics/stm_eqn01809.gif)因此，在无应力介质中，被困液体体积假设为

![](../graphics/stm_eqn01810.gif)其中

![](../graphics/stm_eqn01811.gif)其中![](../graphics/stm_eqn01812.gif)[方程2.8.3-3](02s08a38-Constitutive-behavior-in-a-porous-medium.md)的积分定义。这个被困液体可以被压力压缩，因此，当多孔介质处于应力下时，我们假设

![](../graphics/stm_eqn01813.gif)因此

![](../graphics/stm_eqn01812.gif)![](../graphics/stm_eqn01811.gif)![](../graphics/stm_eqn01814.gif)将其与[方程2.8.3-1](02s08a38-Constitutive-behavior-in-a-porous-medium.md)结合并忽略与1相比很小的项，然后提供

![](../graphics/stm_eqn01815.gif)

我们假设，在初始状态下，凝胶的有效饱和度与周围介质的饱和度相同：

![](../graphics/stm_eqn01816.gif)

含有被困流体的凝胶的本构行为由弹性体积关系给出

![](../graphics/stm_eqn01817.gif)其中![](../graphics/stm_eqn01728.gif)凝胶流体中的平均压力应力，![](../graphics/stm_eqn01818.gif)其体积有效应变。
### 有效应变

![](../graphics/stm_eqn01819.gif)从[方程2.8.3-2](02s08a38-Constitutive-behavior-in-a-porous-medium.md)，我们看到体积应变![](../graphics/stm_eqn01819.gif)示由作用于多孔介质中固体物质上的孔隙压力和该固体物质的热膨胀引起的总体积应变的一部分。此外，介质中液体的捕获可能导致额外的体积变化比：

![](../graphics/stm_eqn01821.gif)![](../graphics/stm_eqn01820.gif)最后，![](../graphics/stm_eqn01821.gif)饱和驱动 moisture swelling strain，表示在部分饱和流动条件下固体骨架的体积膨胀。这个 moisture swelling 可以是各向同性或各向异性的。介质中应变的其余部分，

![](../graphics/stm_eqn01822.gif)![](../graphics/stm_eqn01822.gif)假定改变介质中有效应力的应变。也就是说，我们假设

![](../graphics/stm_eqn01823.gif)这种特定类型的本构模型在第4章"机械本构理论"中讨论。从此假设，并使用[方程2.8.3-5](02s08a38-Constitutive-behavior-in-a-porous-medium.md)，我们可以将有效应力的Jaumann率写为运动学和孔隙液体压力变量变化率的函数为

![](../graphics/stm_eqn01824.gif)其中![](../graphics/stm_eqn01825.gif)第4章"机械本构理论"中为每个特定模型定义。

同样，对于被困在凝胶中的流体的有效压力应力，

![](../graphics/stm_eqn01826.gif)

![](../graphics/stm_eqn01798.gif)然后，从[方程2.8.2-3](02s08a37-Discretized-equilibrium-statement-for-a-.md)，

![](../graphics/stm_eqn01827.gif)
### 参考

### 参考

"Abaqus Analysis User's Guide"第26.6节"孔隙流体流动特性"
