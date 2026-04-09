# 2.11.2 壳体热传导

### 2.11.2 壳体热传导

**产品：** Abaqus/Standard

本节描述Abaqus/Standard中壳体热传导单元所使用的公式。单元的基础是通过壳体厚度的分段二次温度插值与在壳体参考表面上的一次插值（DS3和DS4单元）或二次插值（DS6和DS8单元）的组合。壳体参考表面的等参插值函数形式与用于实体四边形和三角形单元的函数相同，可在"实体等参四边形和六面体"第3.2.4节和"三角形、四面体和楔形单元"第3.2.6节中找到。节点温度值存储在单元每个节点（下面节点*N*）的厚度方向上的一组点（下面点*P*）处。用于有限元方程的数值积分，对于四边形单元DS4使用2×2高斯积分方案和2×2节点积分方案用于内部能量和比热项，对于四边形单元DS8使用3×3高斯积分方案。三角形单元DS3和DS6分别使用三点和六点积分方案，详细信息可在"三角形、四面体和楔形单元"第3.2.6节中找到。

设![](../graphics/stm_eqn02279)是壳体参考表面一点材料坐标，![](../graphics/stm_eqn02280)测量壳体厚度方向的位置，使得![](../graphics/stm_eqn02281)，其中*h*是壳体厚度，![](../graphics/stm_eqn02282)是参考表面相对于中面的偏移，如"复合壳体中的横向剪切刚度和中面偏移"第3.6.8节所述。壳体中任何一点的位置由下式给出

![](../graphics/stm_eqn02283.gif)其中

![](../graphics/stm_eqn02284.gif)

是参考表面中一点的位置，

![](../graphics/stm_eqn00483.gif)

是壳体参考表面的单位法线。温度插值可以写为

![](../graphics/stm_eqn02285.gif)其中

![](../graphics/stm_eqn02286.gif)

是分段抛物线插值，

![](../graphics/stm_eqn02287.gif)

是参考表面中的插值器，

![](../graphics/stm_eqn02288.gif)

是节点温度值（在节点*N*，厚度方向点*P*处）。

基本热能量平衡为[方程2.11.1-3](02s11a43.md)，具有基于

![](../graphics/stm_eqn02289.gif)的Newton方法的近似Jacobian矩阵，其中![](../graphics/stm_eqn02290)是时间![](../graphics/stm_eqn00438)处温度解的修正。这种形式的发展在"非耦合热传递分析"第2.11.1节中讨论。壳体热传导单元这些项的形式通过引入插值器[方程2.11.2-1](02s11a44.md)获得，并忽略与参考表面平行的表面面积相对于![](../graphics/stm_eqn02280)的变化。

内部能量率项（[方程2.11.1-3](02s11a43.md)的第一项）对残差贡献

![](../graphics/stm_eqn02291.gif)对Jacobian贡献

![](../graphics/stm_eqn02292.gif)

对于第二项，温度导数相对于局部正交系统![](../graphics/stm_eqn02293)取，其中![](../graphics/stm_eqn02294)和![](../graphics/stm_eqn02295)测量沿壳体参考表面中局部基向量![](../graphics/stm_eqn00014)和![](../graphics/stm_eqn00015)方向的距离，根据Abaqus中此类壳体局部系统的标准约定设置。该项的形成首先引入一组中间温度值，

![](../graphics/stm_eqn02296.gif)对应于厚度方向每个温度值点，在执行厚度方向积分的每个截面处。由于截面上温度值点的数量与积分点的数量相同，![](../graphics/stm_eqn02297)在适当位置为1，在其他所有地方为0。然后我们可以通过

![](../graphics/stm_eqn02298.gif)插值到截面，其中

![](../graphics/stm_eqn02299.gif)然后厚度方向的分段二次插值给出

![](../graphics/stm_eqn02300.gif)其中

![](../graphics/stm_eqn02301.gif)Jacobian中的电导率项为

![](../graphics/stm_eqn02302.gif)其中![](../graphics/stm_eqn02303)是局部电导率矩阵，相同项乘以![](../graphics/stm_eqn02304)出现在残差中。

最后，外部通量项对残差贡献

![](../graphics/stm_eqn02305.gif)

![](../graphics/stm_eqn02306.gif)对Jacobian贡献，其中

![](../graphics/stm_eqn02307.gif)

在厚度方向点*A*处

![](../graphics/stm_eqn02308.gif)

在厚度方向所有其他点处，点*A*和*B*在壳体的上表面和下表面上。
### 参考

### 参考

"Abaqus Analysis User's Guide"第29.6.7节"三维常规壳单元库"
