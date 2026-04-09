# 3.3.1 实体无限单元

### 3.3.1 实体无限单元

**产品：** Abaqus/Standard  Abaqus/Explicit

应力分析师经常面临在无界域中定义的问题，或者感兴趣区域相对于周围介质较小的问题。无界或无限介质可以通过将有限元网格扩展到很远距离来近似，在那里周围介质对感兴趣区域的影响被认为是足够小以至于可以忽略。这种方法需要用网格大小的实验和在网格截断边缘处假设边界条件来验证，并不总是可靠的。在动态分析中尤其值得关注，当网格的边界可能将能量反射回正在建模的区域时。更好的方法是使用"无限单元"：在具有适当选择衰减函数的半无限域上定义的单元。Abaqus提供了一阶和二阶无限单元，它们基于[Zienkiewicz等人（1983）](07s01a01-References.md)的静态响应工作和[Lysmer和Kuhlemeyer（1969）](07s01a01-References.md)的动态响应工作。这些单元与标准有限单元一起使用，标准有限单元对感兴趣区域周围的区域建模，无限单元对远场区域建模。
### 静态分析

远场中的解假定是线性的，因此无限单元中仅提供线性行为。无限单元的静态行为基于对基本解变量*u*（在应力分析中*u*是位移分量）相对于从解的"极点"测量的空间距离*r*的建模，使得当![](../graphics/stm_eqn03275.gif)时，![](../graphics/stm_eqn03274.gif)，当![](../graphics/stm_eqn01414.gif)时，![](../graphics/stm_eqn03276.gif)。插值提供阶数为![](../graphics/stm_eqn03277.gif)、![](../graphics/stm_eqn03278.gif)的项，当解变量是类应力变量（如多孔介质流动分析中的孔隙液体压力）时，当![](../graphics/stm_eqn01414.gif)时，![](../graphics/stm_eqn03279.gif)。许多常见情况的远场行为，如半空间上的点载荷，因此被包括。通过在*s*方向上以乘积形式组合这种插值与映射空间中正交方向上的标准线性或二次插值，获得达到无穷远的三维和二维域模型。

对于静态分析使用无限单元时，必须定位极点，以为正在建模的特定问题提供合理的远场解。Abaqus中的无限单元编写时，在有限和无限单元之间的界面以及在每个延伸到无穷远的边上有一个节点，该节点必须放置在无限方向上，使得从该节点通过相应界面节点的直线在界面另一侧距离无限单元等于这些节点之间距离的位置穿过该射线的极点（[图3.3.1-1](03s03a68-Solid-infinite-elements.md)）。

图3.3.1-1 无限单元的极点节点位置。

![](../graphics/stm_eqn03291.gif)![](../graphics/stm_eqn03292.gif)![](../graphics/stm_eqn03294.gif)![](../graphics/stm_eqn03293.gif)![](../graphics/stm_eqn03275.gif)![](../graphics/stm_eqn03289.gif)![](../graphics/stminf-pole-node.png)

因此，一维概念基于有限和无限单元之间界面上的节点（节点1），距离极点![](../graphics/stm_eqn03284.gif)，在映射空间中位于![](../graphics/stm_eqn03285.gif)，以及节点2，距离极点![](../graphics/stm_eqn03286.gif)（极点在![](../graphics/stm_eqn01415.gif)），在映射空间中位于![](../graphics/stm_eqn03287.gif)。选择![](../graphics/stm_eqn03282.gif)映射为

![](../graphics/stm_eqn03288.gif)以便

![](../graphics/stm_eqn03289.gif)其逆转为

![](../graphics/stm_eqn03290.gif)

当需要具有![](../graphics/stm_eqn03277.gif)和![](../graphics/stm_eqn03278.gif)（这在![](../graphics/stm_eqn03293.gif)处给出![](../graphics/stm_eqn03292.gif)，其中![](../graphics/stm_eqn03275.gif)）。使用反转几何映射定义![](../graphics/stm_eqn03294.gif)然后给出

![](../graphics/stm_eqn03295.gif)这提供了所需的行为。类似地，当还需要![](../graphics/stm_eqn03279.gif)行为时，我们使用相对于*s*的*u*的三次插值，用其在节点1和节点2处的值以及我们选择放置在![](../graphics/stm_eqn03296.gif)的第三个节点的值写成：

![](../graphics/stm_eqn03297.gif)反转几何映射然后提供

![](../graphics/stm_eqn03298.gif)Abaqus中的无限单元包括用于解耦应力分析的二维和三维单元，这些单元对位移分量使用二次插值，以及用于耦合应力-孔隙液体压力单元的二维和三维单元，其中位移使用二次插值，孔隙液体压力在无限方向使用三次插值。位移按![](../graphics/stm_eqn03278.gif)变化，因此应变（从而应力）可能按![](../graphics/stm_eqn03279.gif)变化，所以对孔隙液体压力使用更高阶插值以保证兼容性。
### 动态响应

无限单元的动态响应基于垂直于边界传播的平面体波的考虑。同样，我们假定邻近边界的响应振幅足够小，使得介质以线性弹性方式响应。

平衡方程是

![](../graphics/stm_eqn03299.gif)其中![](../graphics/stm_eqn00593.gif)是材料密度，![](../graphics/stm_eqn00890.gif)是材料粒子加速度，![](../graphics/stm_eqn00033.gif)是应力，![](../graphics/stm_eqn00117.gif)是位置。

我们假定材料响应是各向同性、线性弹性的——因此可以写成

![](../graphics/stm_eqn03300.gif)其中![](../graphics/stm_eqn00399.gif)是应变，

![](../graphics/stm_eqn03301.gif)

![](../graphics/stm_eqn03302.gif)

是Lam常数（*E*是杨氏模量，![](../graphics/stm_eqn01854.gif)是泊松比）。在平衡方程中引入这种材料响应，并假定小应变：

![](../graphics/stm_eqn03303.gif)提供运动控制方程

![](../graphics/stm_eqn03304.gif)这里为简单起见使用了指标符号。

![](../graphics/stm_eqn03305.gif)![](../graphics/stm_eqn03306.gif)我们考虑沿*x*轴传播的平面波。这个方程存在这种形式的两种体波解。一种描述平面纵向（"推动"）波，其形式为

![](../graphics/stm_eqn03305.gif)其中，通过代入上面的控制方程，我们发现波速，![](../graphics/stm_eqn03306.gif)，是

![](../graphics/stm_eqn03307.gif)这种形式的另一个解是"剪切"波解

![](../graphics/stm_eqn03308.gif)或

![](../graphics/stm_eqn03309.gif)其中——再次通过代入控制方程——我们获得

![](../graphics/stm_eqn03310.gif)在每种情况下，解![](../graphics/stm_eqn03311.gif)表示沿*x*增加方向传播的波，而![](../graphics/stm_eqn03312.gif)表示沿*x*减小方向传播的波。

现在考虑在![](../graphics/stm_eqn03313.gif)处，由有限元在![](../graphics/stm_eqn03314.gif)中建模的介质的边界。我们在这个边界上引入分布阻尼，使得

![](../graphics/stm_eqn03315.gif)

![](../graphics/stm_eqn03316.gif)其中我们现在选择阻尼常数![](../graphics/stm_eqn03317.gif)和![](../graphics/stm_eqn03318.gif)以避免纵向和剪切波能量反射回![](../graphics/stm_eqn03314.gif)中的介质。接近边界的平面纵向波具有形式![](../graphics/stm_eqn03319.gif)、![](../graphics/stm_eqn03320.gif)。如果它们作为平面纵向波被完全反射，它们的反射将以某种形式![](../graphics/stm_eqn03321.gif)、![](../graphics/stm_eqn03320.gif)离开边界传播。由于问题是线性的，叠加提供总位移![](../graphics/stm_eqn03322.gif)，相应的应力![](../graphics/stm_eqn03323.gif)，所有其他![](../graphics/stm_eqn00540.gif)和速度![](../graphics/stm_eqn03324.gif)。对于这个解，为了满足在![](../graphics/stm_eqn03313.gif)处引入的边界阻尼行为，需要

![](../graphics/stm_eqn03325.gif)因此，我们可以通过选择

![](../graphics/stm_eqn03329.gif)来确保对于任何![](../graphics/stm_eqn03328.gif)，![](../graphics/stm_eqn03326.gif)（所以![](../graphics/stm_eqn03327.gif)）。对于剪切波的类似论证提供

![](../graphics/stm_eqn03330.gif)

这些边界阻尼值内置于Abaqus的无限单元中。从上面的讨论我们看到，它们精确传输所有正入射平面体波（只要边界附近的材料行为是线性弹性的）。一般问题涉及非平面体波，这些波不是正交方向入射到边界上，也可能涉及Rayleigh表面波和Love波。尽管如此，这些"安静"边界即使对于这种一般情况也工作得相当好，只要它们被安排成使得波传播的主要方向垂直于边界，或者在自由表面和界面上（当涉及Rayleigh或Love波时），它们垂直于表面（参见，例如，[Cohen和Jennings，1983](07s01a01-References.md)）。因为边界是"安静"而不是沉默的（所有波形的完美发射器），并且因为边界依赖于邻近它们的线性弹性解，它们应该放置在离主要感兴趣区域合理距离的地方。

在静态预载后的动态响应分析中（如同岩土工程应用中常见的那样），无限单元提供给有限元网格边界的牵引力由从静态响应获得的恒定应力加上安静边界阻尼应力组成。因为单元在动态分析期间没有刚度，它们允许发生净刚体运动，这通常不是一个显著的影响。
### 参考

### 参考

![](../graphics/stm_eqn03284.gif)![](../graphics/stm_eqn03286.gif)![](../graphics/stm_eqn03285.gif)![](../graphics/stm_eqn03287.gif)![](../graphics/stm_eqn01415.gif)![](../graphics/stm_eqn03282.gif)![](../graphics/stm_eqn03297.gif)"Infinite elements," Section 28.3.1 of the Abaqus Analysis User's Guide
