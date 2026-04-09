# 3.5.5 Timoshenko梁的质量和惯性

### 3.5.5 Timoshenko梁的质量和惯性

**产品：** Abaqus/Standard  Abaqus/Explicit

Abaqus中Timoshenko梁（包括PIPE单元）的质量和惯性属性可能来自两个独立的来源。第一个来源是梁本身的密度和横截面几何。第二个来源来自可能施加在梁横截面上指定位置的任何额外质量和每单元长度的惯性属性。当质量和惯性仅从第一个来源给出时，用户可以选择请求各向同性近似或梁质量矩阵的精确旋转惯性公式。当使用各向同性公式时，每长度的梁质量被施加到位于横截面轴原点的梁节点，并且质量矩阵公式中忽略梁节点与横截面质量中心之间的偏移（如果非零）。

设![](../graphics/stm_eqn03942.gif)是梁密度。梁横截面坐标系中关于质量中心质量和旋转惯性定义为

![](../graphics/stm_eqn03943.gif)这里，![](../graphics/stm_eqn01412.gif)和![](../graphics/stm_eqn01413.gif)是相对于横截面质量中心测量的。

对于各向同性（近似）公式，单元的质量矩阵取形式

![](../graphics/stm_eqn03944.gif)在二维中![](../graphics/stm_eqn03945.gif)。

在本节所有表达式中，适用于平移自由度的质量矩阵![](../graphics/stm_eqn03946.gif)对于2节点梁是集中的，对于3节点梁是一致的。

当使用精确公式时，梁节点与横截面质量中心之间的任何偏移将在单元的质量矩阵中产生平移自由度与旋转自由度之间的耦合。

设![](../graphics/stm_eqn03947.gif)定义每梁长度的附加质量。组合梁质量定义为

![](../graphics/stm_eqn03948.gif)

设![](../graphics/stm_eqn03949.gif)是质量中心*C*与具有当前坐标![](../graphics/stm_eqn00117.gif)的某个点之间的向量，

![](../graphics/stm_eqn03950.gif)

对于刚体，物体中任何点的速度由以下给出

![](../graphics/stm_eqn03951.gif)其中![](../graphics/stm_eqn03952.gif)是物体的角速度。对这个表达式取时间导数，加速度为

![](../graphics/stm_eqn03953.gif)

平衡方程的局部或强形式表示线性动量守恒和角动量守恒；这两个平衡方程是

![](../graphics/stm_eqn03954.gif)其中![](../graphics/stm_eqn03955.gif)和![](../graphics/stm_eqn03956.gif)是作用在质量中心处的外力和外部力矩，![](../graphics/stm_eqn00064.gif)是旋转惯性张量。

平衡的变分或弱形式为

![](../graphics/stm_eqn03957.gif)取平衡方程中的时间导数，内部或d'Alembert力贡献为

![](../graphics/stm_eqn03958.gif)其中![](../graphics/stm_eqn01597.gif)是物体中一点位置的变分，![](../graphics/stm_eqn03959.gif)是刚体参考节点旋转的变分。外部载荷贡献为

![](../graphics/stm_eqn03960.gif)对于线性理论，所有非线性项被忽略，因此内部力贡献简化为

![](../graphics/stm_eqn03961.gif)并导致以下所有线和线性扰动分析的质量矩阵：

![](../graphics/stm_eqn03962.gif)其中![](../graphics/stm_eqn03963.gif)表示斜对称矩阵，![](../graphics/stm_eqn03964.gif)。

当刚性体的惯性用于隐式时间积分时，需要![](../graphics/stm_eqn03965.gif)的Jacobian贡献。它可以写成形式

![](../graphics/stm_eqn03966.gif)其中使用了以下符号

![](../graphics/stm_eqn03967.gif)

![](../graphics/stm_eqn03968.gif)

![](../graphics/stm_eqn03969.gif)在3节点梁的Jacobian公式中，平移自由度使用一致质量矩阵，旋转自由度以及耦合平移和旋转自由度的项使用集中质量矩阵。
