# 5.2.6 由电流引起的热生成

### 5.2.6 由电流引起的热生成

**产品：** Abaqus/Standard

![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn03328.gif)![](../graphics/stm_eqn07791.gif)对于Abaqus/Standard中的耦合热-电和耦合热-电-结构分析，用户可以引入一个因子，定义在接触区因电耗散转化为热量的分数。生成热量进入第一和第二表面的分数也可以定义。

![](../graphics/stm_eqn02098.gif)![](../graphics/stm_eqn03328.gif)![](../graphics/stm_eqn07791.gif)热分数确定了因电流而耗散的能量中进入接触体作为热量的部分。热量瞬间传导到每个接触体，取决于和的值。接触界面假定没有热容量，可能具有用于通过传导和辐射交换热量的属性。

![](../graphics/stm_eqn05787.gif)![](../graphics/stm_eqn05788.gif)热通量密度，从第一侧表面流出，和，从第二侧表面流出，由给出

![](../graphics/stm_eqn07793.gif)和

![](../graphics/stm_eqn07794.gif)![](../graphics/stm_eqn07795.gif)![](../graphics/stm_eqn07796.gif)![](../graphics/stm_eqn07797.gif)其中是由电流引起的界面元素生成的热通量密度，是由传导引起的热通量，是由辐射引起的热通量。

由传导引起的热通量假定为形式

![](../graphics/stm_eqn07824.gif)![](../graphics/stm_eqn07825.gif)![](../graphics/stm_eqn07802.gif)![](../graphics/stm_eqn07404.gif)![](../graphics/stm_eqn07803.gif)![](../graphics/stm_eqn07804.gif)其中热传递系数是接触点平均温度和过盈的函数。和分别是第一侧和第二侧的温度。

由辐射引起的热通量假定为形式

![](../graphics/stm_eqn07826.gif)![](../graphics/stm_eqn07783.gif)![](../graphics/stm_eqn02243.gif)其中是间隙辐射常数（从两个表面的发射率导出），是所用温标上的绝对零。

![](../graphics/stm_eqn02113.gif)![](../graphics/stm_eqn07827.gif)界面元素中的电通量密度以跨界面的电势差的形式给出：

![](../graphics/stm_eqn07828.gif)![](../graphics/stm_eqn07829.gif)![](../graphics/stm_eqn07404.gif)![](../graphics/stm_eqn07830.gif)![](../graphics/stm_eqn07831.gif)![](../graphics/stm_eqn07832.gif)其中间隙电导是过盈和接触点平均温度的函数。和分别是第一侧和第二侧的电势。

在稳态分析中，由电流引起的界面元素生成的热通量密度为

![](../graphics/stm_eqn07833.gif)![](../graphics/stm_eqn02098.gif)其中是将耗散能量转化为热量的分数。在瞬态分析中，平均热通量密度为

![](../graphics/stm_eqn07834.gif)![](../graphics/stm_eqn02391.gif)![](../graphics/stm_eqn00883.gif)其中是增量开始时的时间，是时间增量。

使用Galerkin方法，方程的弱形式可以写成

![](../graphics/stm_eqn07806.gif)热平衡变分陈述的贡献为

![](../graphics/stm_eqn07807.gif)![](../graphics/stm_eqn07808.gif)其中。牛顿求解器Jacobian矩阵的贡献为

![](../graphics/stm_eqn07835.gif)在接触点，温度可以用

![](../graphics/stm_eqn07836.gif)![](../graphics/stm_eqn02247.gif)![](../graphics/stm_eqn06990.gif)插值，其中是与之关联的界面元素第个节点的温度。注意对所有上标使用求和约定。因此，温度变量可以写成如下：

![](../graphics/stm_eqn07811.gif)![](../graphics/stm_eqn07812.gif)![](../graphics/stm_eqn07813.gif)将上述表达式代入方程得

![](../graphics/stm_eqn07837.gif)![](../graphics/stm_eqn07797.gif)![](../graphics/stm_eqn07796.gif)![](../graphics/stm_eqn07795.gif)、和的导数如下：

![](../graphics/stm_eqn07817.gif)在稳态分析中

![](../graphics/stm_eqn07838.gif)而在瞬态分析中

![](../graphics/stm_eqn07839.gif)类似地，电平衡变分陈述的贡献为

![](../graphics/stm_eqn07840.gif)牛顿求解器Jacobian矩阵的贡献为

的导数为

![](../graphics/stm_eqn07841.gif)### 参考

![](../graphics/stm_eqn07842.gif)![](../graphics/stm_eqn02113.gif)### 参考

![](../graphics/stm_eqn07843.gif)"Abaqus Analysis User's Guide"第6.7.3节"耦合热-电分析"

"Abaqus Analysis User's Guide"第6.7.4节"完全耦合热-电-结构分析"

"Abaqus Analysis User's Guide"第37.3.1节"电接触属性"
