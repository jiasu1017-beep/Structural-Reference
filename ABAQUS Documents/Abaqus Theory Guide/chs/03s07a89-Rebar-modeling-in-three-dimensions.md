# 3.7.2 三维中的钢筋建模

### 3.7.2 三维中的钢筋建模

**产品：** Abaqus/Standard  Abaqus/Explicit

设![](../graphics/stm_eqn04979.gif)为放置钢筋的基本有限单元的等参坐标。设![](../graphics/stm_eqn04980.gif)为增强表面上的等参坐标，![](../graphics/stm_eqn04981.gif)。设*t*为沿钢筋方向的材料坐标。见[图3.7.2-1](03s07a89-Rebar-modeling-in-three-dimensions.md)。

图3.7.2-1 实体三维单元中的钢筋。

![](../graphics/stm3drebar.png)

钢筋使用![](../graphics/stm_eqn03441.gif)或![](../graphics/stm_eqn04982.gif)个高斯点进行积分，取决于底层单元的阶次。积分点处的积分体积为

![](../graphics/stm_eqn04983.gif)其中![](../graphics/stm_eqn04957.gif)是每根钢筋的横截面面积，![](../graphics/stm_eqn04958.gif)是钢筋间距，![](../graphics/stm_eqn04962.gif)是与积分点相关的高斯权重，![](../graphics/stm_eqn00141.gif)是积分点的位置，

![](../graphics/stm_eqn04984.gif)在这些表达式中，所有量都在参考构型中获取，因此Abaqus忽略由钢筋应变引起的钢筋横截面面积的变化，以及由钢筋所在有限单元应变引起的钢筋间距的变化。

钢筋的应变是

![](../graphics/stm_eqn04985.gif)其中

![](../graphics/stm_eqn04986.gif)*G*是原始构型中*g*的值。

为方便起见，我们定义*s*，这是一个材料坐标，沿当前构型中的钢筋方向测量距离：

![](../graphics/stm_eqn04987.gif)应变的一阶变分为

![](../graphics/stm_eqn04988.gif)应变的一阶变分为

![](../graphics/stm_eqn04989.gif)
### 参考

### 参考

"Defining rebar as an element property," Section 2.2.4 of the Abaqus Analysis User's Guide
