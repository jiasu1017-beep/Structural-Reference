# 3.7.1 二维中的钢筋建模

### 3.7.1 二维中的钢筋建模

**产品：** Abaqus/Standard  Abaqus/Explicit

设![](../graphics/stm_eqn04949.gif)为单元的 usual等参坐标。设*r*为沿着单元面与增强平面相交线的等参坐标，在单元中![](../graphics/stm_eqn04950.gif)（参见[图3.7.1-1](03s07a88-Rebar-modeling-in-two-dimensions.md)）。

图3.7.1-1 实体二维单元中的钢筋。

![](../graphics/stm2drebar.png)增强平面始终垂直于单元面。

钢筋将在一个或两个点进行积分，取决于底层单元的插值阶次。积分体积![](../graphics/stm_eqn04951.gif)、位置、钢筋应变![](../graphics/stm_eqn04952.gif)以及每个点处钢筋应变的一阶和二阶变分![](../graphics/stm_eqn04953.gif)和![](../graphics/stm_eqn04954.gif)计算为

![](../graphics/stm_eqn04955.gif)其中

![](../graphics/stm_eqn00945.gif)

是平面单元的原始厚度，轴对称单元为![](../graphics/stm_eqn04956.gif)；

![](../graphics/stm_eqn04957.gif)

是钢筋横截面面积；

![](../graphics/stm_eqn04958.gif)

是钢筋间距（对于轴对称单元![](../graphics/stm_eqn04959.gif)，其中![](../graphics/stm_eqn04960.gif)是给定间距![](../graphics/stm_eqn04961.gif)的半径）；

![](../graphics/stm_eqn04962.gif)

是与沿![](../graphics/stm_eqn04963.gif)线的积分点相关的高斯权重；

![](../graphics/stm_eqn04964.gif)

是位置；和

![](../graphics/stm_eqn04965.gif)

应变是

![](../graphics/stm_eqn04966.gif)其中![](../graphics/stm_eqn04967.gif)和![](../graphics/stm_eqn04968.gif)分别测量当前和初始构型中沿钢筋的长度。

对于这些单元允许的变形，

![](../graphics/stm_eqn04969.gif)其中![](../graphics/stm_eqn00904.gif)是钢筋相对于模型平面的方向，

![](../graphics/stm_eqn04970.gif)是*r*方向的平方拉伸比，![](../graphics/stm_eqn04027.gif)是厚度方向的拉伸比：

![](../graphics/stm_eqn04971.gif)

对于平面应力或平面应变；

![](../graphics/stm_eqn04972.gif)

对于广义平面应变，其中*t*在"广义平面应变单元"第3.2.7节中给出；和

![](../graphics/stm_eqn04973.gif)

对于轴对称单元。

从这些结果得到应变的一阶变分为

![](../graphics/stm_eqn04974.gif)其中

![](../graphics/stm_eqn04975.gif)

对于平面应力和平面应变，

![](../graphics/stm_eqn04976.gif)

对于广义平面应变，和

![](../graphics/stm_eqn04977.gif)

对于轴对称情况。然后是应变的二阶变分

![](../graphics/stm_eqn04978.gif)
### 参考

### 参考

"Defining rebar as an element property," Section 2.2.4 of the Abaqus Analysis User's Guide
