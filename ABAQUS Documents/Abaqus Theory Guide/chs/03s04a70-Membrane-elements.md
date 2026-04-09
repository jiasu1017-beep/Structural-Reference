# 3.4.1 薄膜单元

### 3.4.1 薄膜单元

**产品：** Abaqus/Standard  Abaqus/Explicit

薄膜单元是空间中的薄片，能够承受薄膜力但不具有任何弯曲或横向剪切刚度，因此薄膜中唯一的非零应力分量是平行于薄膜中面的那些分量：薄膜处于平面应力状态。

在任何时候，我们使用局部正交基系统![](../graphics/stm_eqn00022.gif)，其中![](../graphics/stm_eqn00014.gif)和![](../graphics/stm_eqn00015.gif)在薄膜表面内，![](../graphics/stm_eqn00016.gif)垂直于薄膜。该基系统由Abaqus用于空间表面上的基的标准约定定义。在本节中，希腊指标取范围1、2，拉丁指标取范围1、2、3。希腊指标用于引用局部正交基前两个方向（薄膜表面内）中的分量。
### 平衡

薄膜单元内部力的虚功贡献为

![](../graphics/stm_eqn03395.gif)其中![](../graphics/stm_eqn00033.gif)是柯西应力，![](../graphics/stm_eqn03396.gif)是虚变形率（![](../graphics/stm_eqn03397.gif)，其中![](../graphics/stm_eqn01597.gif)是虚速度场），*V*是薄膜的当前体积。

我们假定薄膜表面内的薄膜应力分量唯一非零：![](../graphics/stm_eqn03398.gif)。然后[公式3.4.1-1](03s04a70-Membrane-elements.md)简化为

![](../graphics/stm_eqn03399.gif)其中

![](../graphics/stm_eqn03400.gif)和![](../graphics/stm_eqn03401.gif)，其中*t*是单元的当前厚度，*A*是其当前面积。
### Jacobian矩阵

来自单元的一致Jacobian贡献为

![](../graphics/stm_eqn03402.gif)由于我们假定![](../graphics/stm_eqn03398.gif)，被积函数的第一项为

![](../graphics/stm_eqn03403.gif)我们还假定没有单元的横向剪切应变：![](../graphics/stm_eqn03404.gif)，因此，![](../graphics/stm_eqn03405.gif)。因此，被积函数的第二项为

![](../graphics/stm_eqn03406.gif)我们可以写成

![](../graphics/stm_eqn03407.gif)
### 厚度变化

在几何非线性分析中，横截面厚度作为薄膜应变的函数变化，具有用户定义的"有效截面泊松比"，![](../graphics/stm_eqn01854.gif)。

在平面应力![](../graphics/stm_eqn03408.gif)中；线弹性给出

![](../graphics/stm_eqn03409.gif)将这些视为对数应变，

![](../graphics/stm_eqn03410.gif)其中*A*是薄膜参考表面上的面积。这种与线弹性的非线性类比导致厚度变化关系：

![](../graphics/stm_eqn03411.gif)对于![](../graphics/stm_eqn03412.gif)，材料是不可压缩的；对于![](../graphics/stm_eqn03413.gif)，截面厚度不变化。
### 总变形

变形梯度为![](../graphics/stm_eqn03414.gif)。由于我们取![](../graphics/stm_eqn00016.gif)垂直于当前薄膜表面并假定薄膜没有横向剪切，

![](../graphics/stm_eqn03415.gif)通过上述厚度变化假设，变形梯度的直接面外分量为

![](../graphics/stm_eqn03416.gif)

为了计算增量结束时的变形梯度，首先我们计算由位置相对于参考坐标的导数定义的增量结束时的两个切向量：

![](../graphics/stm_eqn03417.gif)其中![](../graphics/stm_eqn03418.gif)通过从节点坐标的形函数导数进行插值获得，坐标变换的变化![](../graphics/stm_eqn03419.gif)基于参考几何。变形梯度分量定义为

![](../graphics/stm_eqn03420.gif)

为了选择单元基方向![](../graphics/stm_eqn03421.gif)，我们执行以下操作。找到任何一对面内正交向量![](../graphics/stm_eqn03422.gif)（通过标准Abaqus投影）。然后找到角度![](../graphics/stm_eqn03423.gif)，使得单元基向量![](../graphics/stm_eqn03421.gif)，定义为

![](../graphics/stm_eqn03424.gif)满足对称条件

![](../graphics/stm_eqn03425.gif)利用上述方程中![](../graphics/stm_eqn03421.gif)相对于![](../graphics/stm_eqn03426.gif)的定义，发现旋转角度![](../graphics/stm_eqn03423.gif)为

![](../graphics/stm_eqn03427.gif)其中

![](../graphics/stm_eqn03428.gif)然后立即获得变形梯度。

对于弹性体，我们直接使用![](../graphics/stm_eqn03429.gif)和![](../graphics/stm_eqn03430.gif)。对于非弹性材料模型，我们需要增量应变和平均材料旋转的度量，我们从由![](../graphics/stm_eqn03431.gif)定义的![](../graphics/stm_eqn00434.gif)计算，其中![](../graphics/stm_eqn03432.gif)是当前增量开始时的变形梯度（在增量"*n*"处）：

![](../graphics/stm_eqn03433.gif)我们可以定义![](../graphics/stm_eqn03434.gif)的分量

![](../graphics/stm_eqn03435.gif)因此，通过求逆定义![](../graphics/stm_eqn03436.gif)。

然后从极分解![](../graphics/stm_eqn03437.gif)定义增量应变和旋转，其中![](../graphics/stm_eqn00433.gif)是旋转矩阵，![](../graphics/stm_eqn00572.gif)是纯拉伸：

![](../graphics/stm_eqn03438.gif)（参见"变形，" 第1.4.1节）。我们通过求解以下特征值问题找到![](../graphics/stm_eqn00574.gif)和相应的特征向量![](../graphics/stm_eqn03439.gif)

![](../graphics/stm_eqn03440.gif)由于我们假定薄膜没有横向剪切，法线方向（沿![](../graphics/stm_eqn00016.gif)）始终是主方向，因此特征值问题是![](../graphics/stm_eqn03441.gif)问题

![](../graphics/stm_eqn03442.gif)然后对数应变增量为

![](../graphics/stm_eqn03443.gif)平均材料旋转增量从增量的极分解定义：

![](../graphics/stm_eqn03444.gif)由于单元基方向的选择，我们可以假定

![](../graphics/stm_eqn03445.gif)
### 参考

### 参考

"Abaqus Analysis User's Guide"第29.1.1节"薄膜单元"
