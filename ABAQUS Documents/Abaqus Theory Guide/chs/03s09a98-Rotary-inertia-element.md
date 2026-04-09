# 3.9.7 旋转惯性单元

### 3.9.7 旋转惯性单元

**产品：** Abaqus/Standard  Abaqus/Explicit

MASS和ROTARYI单元允许在节点处引入刚体的惯性。本节定义与这些单元一起使用的公式。

假定引入质量和旋转惯性的节点是物体的质心。我们称该节点为刚体参考节点*C*。设物体的局部主惯性轴为![](../graphics/stm_eqn00008.gif)、![](../graphics/stm_eqn00338.gif)。设![](../graphics/stm_eqn03949.gif)是*C*与刚体中具有当前坐标![](../graphics/stm_eqn00117.gif)的某点之间的向量，使得

![](../graphics/stm_eqn05473.gif)其中![](../graphics/stm_eqn05474.gif)是刚体中的局部坐标。刚体质量是质量密度![](../graphics/stm_eqn05475.gif)在物体上的积分

![](../graphics/stm_eqn05476.gif)由于假定*C*是物体的质心，

![](../graphics/stm_eqn05477.gif)由于![](../graphics/stm_eqn00008.gif)是物体的主轴，

![](../graphics/stm_eqn05478.gif)设![](../graphics/stm_eqn03733.gif)、![](../graphics/stm_eqn03734.gif)和![](../graphics/stm_eqn05479.gif)是物体关于其主轴![](../graphics/stm_eqn00014.gif)、![](../graphics/stm_eqn00015.gif)和![](../graphics/stm_eqn00016.gif)的二阶惯性矩；则

![](../graphics/stm_eqn05480.gif)旋转惯性张量写为

![](../graphics/stm_eqn05481.gif)

对于刚体，物体中任意点的速度由

![](../graphics/stm_eqn05482.gif)给出，其中![](../graphics/stm_eqn03952.gif)是物体的角速度。取二阶时间导数，加速度为

![](../graphics/stm_eqn05483.gif)

平衡方程的局部或强形式表示线性动量平衡和角动量平衡；这两个平衡方程是

![](../graphics/stm_eqn05484.gif)平衡的变分或弱形式为

![](../graphics/stm_eqn05485.gif)内部或d'Alembert力贡献为

![](../graphics/stm_eqn05486.gif)其中![](../graphics/stm_eqn05487.gif)是物体中一点位置的变分。这里![](../graphics/stm_eqn05488.gif)是刚体参考节点位置的变分，![](../graphics/stm_eqn03959.gif)是刚体参考节点旋转的变分。外部载荷贡献为

![](../graphics/stm_eqn05489.gif)引入关于惯性主轴的分量表达式，弱形式的旋转贡献变为

![](../graphics/stm_eqn05490.gif)

当刚体惯性用于隐式时间积分时，需要![](../graphics/stm_eqn05491.gif)的Jacobian贡献：这是

![](../graphics/stm_eqn05492.gif)
### 参考

### 参考

"Rotary inertia," Section 30.2.1 of the Abaqus Analysis User's Guide
