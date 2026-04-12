# 34.7 FieldValue 对象

FieldValue 对象表示一点的场数据。FieldValue 对象没有构造函数；当使用 `addData` 方法将数据添加到 [FieldOutput](pt01ch34pyo06.md) 对象时，它由 [Odb](pt01ch34pyo01.md) 对象创建。有关更快的大容量数据访问，请参阅《Abaqus Scripting User's Guide》第 10.10.7 节"使用输出数据库的大容量数据访问"。

**访问**

```
import odbAccess
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*].values[*i*]
```

### 34.7.1 成员

FieldValue 对象具有以下成员：

*position*

一个 SymbolicConstant，指定输出在元素中的位置。可能的值为：
- NODAL，指定在节点处计算的值。
- INTEGRATION_POINT，指定在积分点处计算的值。
- ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- ELEMENT_FACE，指定为元素表面定义的表面变量（如空腔辐射）的结果。
- CENTROID，指定通过外推在积分点处计算的结果获得的质心处的值。

*precision*

一个 SymbolicConstant，指定输出在元素中的精度。可能的值为：
- SINGLE_PRECISION，指定输出值为单精度。
- DOUBLE_PRECISION，指定输出值为双精度。

*elementLabel*

一个整数，指定包含该位置的元素的元素标签。*elementLabel* 仅在 *position*=INTEGRATION_POINT、CENTROID、ELEMENT_NODAL 或 ELEMENT_FACE 时可用。

*nodeLabel*

一个整数，指定包含该位置的节点的节点标签。*nodelabel* 仅在 *position*=ELEMENT_NODAL 或 NODAL 时可用。

*integrationPoint*

一个整数，指定元素中的积分点。*integrationPoint* 仅在 *position*=INTEGRATION_POINT 时可用。

*face*

一个 SymbolicConstant，指定元素的面。*face* 仅在 *position*=ELEMENT_FACE 时可用。

*type*

一个 SymbolicConstant，指定输出类型。可能的值为 SCALAR、VECTOR、TENSOR_3D_FULL、TENSOR_3D_PLANAR、TENSOR_3D_SURFACE、TENSOR_2D_PLANAR 和 TENSOR_2D_SURFACE。

*magnitude*

一个 Float，指定向量的长度或大小。*magnitude* 仅在 *type*=VECTOR 时有效。

*mises*

一个 Float，指定计算的 von Mises 应力。仅当 *validInvariants* 成员包含 MISES 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*tresca*

一个 Float，指定计算的 Tresca 应力。仅当 *validInvariants* 成员包含 TRESCA 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*press*

一个 Float，指定计算的压力应力。仅当 *validInvariants* 成员包含 PRESS 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*inv3*

一个 Float，指定计算的第三应力不变量。仅当 *validInvariants* 成员包含 INV3 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*maxPrincipal*

一个 Float，指定计算的最大主应力。仅当 *validInvariants* 成员包含 MAX_PRINCIPAL 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*midPrincipal*

一个 Float，指定计算的中间主应力。仅当 *validInvariants* 成员包含 MID_PRINCIPAL 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*minPrincipal*

一个 Float，指定最小主应力。仅当 *validInvariants* 成员包含 MIN_PRINCIPAL 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*maxInPlanePrincipal*

一个 Float，指定计算的最大平面内主应力。仅当 *validInvariants* 成员包含 MAX_INPLANE_PRINCIPAL 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*minInPlanePrincipal*

一个 Float，指定计算的最小平面内主应力。仅当 *validInvariants* 成员包含 MIN_INPLANE_PRINCIPAL 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*outOfPlanePrincipal*

一个 Float，指定计算的平面外主应力。仅当 *validInvariants* 成员包含 OUTOFPLANE_PRINCIPAL 时该值才有效；否则，该值不确定。在不变量计算中将忽略共轭数据。

*instance*

一个 [OdbInstance](pt01ch34pyo15.md) 对象，指定标签所属的部件。

*sectionPoint*

一个 [SectionPoint](pt01ch34pyo28.md) 对象。

*localCoordSystem*

浮点数元组的元组，指定局部坐标系方向余弦的 3×3 浮点数矩阵。每个序列表示方向余弦矩阵中的一行。*localCoordSystem* 仅适用于以局部坐标系写入的 TENSOR 数据。如果底层数据为双精度，则会抛出异常。

*localCoordSystemDouble*

浮点数元组的元组，指定局部坐标系方向余弦的 3×3 Double 矩阵。每个序列表示方向余弦矩阵中的一行。*localCoordSystemDouble* 仅适用于以局部坐标系写入的 TENSOR 数据。如果底层数据为单精度，则会抛出异常。

*data*

浮点数元组，以 *type* 描述的形式指定数据。如果 *type*=TENSOR 或 VECTOR，则 *data* 是包含分量的序列。如果底层数据为双精度，则会抛出异常。

*dataDouble*

浮点数元组，以 *type* 描述的形式指定数据。如果 *type*=TENSOR 或 VECTOR，则 *dataDouble* 是包含分量的序列。如果底层数据为单精度，则会抛出异常。

*conjugateData*

浮点数元组，以 *type* 描述的形式指定数据。如果 *type*=TENSOR 或 VECTOR，则 *conjugateData* 是包含分量的序列。如果底层数据为双精度，则会抛出异常。

*conjugateDataDouble*

浮点数元组，以 *type* 描述的形式指定数据。如果 *type*=TENSOR 或 VECTOR，则 *conjugateDataDouble* 是包含分量的序列。如果底层数据为单精度，则会抛出异常。
