# 61.8 FieldValue 对象

FieldValue 对象表示某一点的场数据。FieldValue 对象没有构造函数；当使用 `addData` 方法将数据添加到 [FieldOutput](pt02ch61pyo07.md) 对象时，数据由 [Odb](pt02ch61pyo01.md) 对象自动创建。如需更快地批量访问数据，请参阅"Abaqus Scripting User's Guide"第 10.10.7 节"Using bulk data access to an output database"（[cmd-link](../cmd/cmd-link.md#cmd-odb-intro-bulkdata-cpp)）。

**访问**

```
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*].values(*i*)
```

### 61.8.1 成员

FieldValue 对象具有以下成员：

**原型**

```
odb_Enum::odb_ResultPositionEnum position() const;
const odb_Instance& instance() const;
int elementLabel() const;
int nodeLabel() const;
int integrationPoint() const;
odb_Enum::odb_ElementFaceEnum face() const;
odb_SectionPoint sectionPoint() const;
odb_Enum::odb_PrecisionEnum precision() const;
odb_Enum::odb_DataTypeEnum type() const;
const float* data(int& numVal) const;
odb_SequenceFloat data() const;
const float* conjugateData(int& numVal) const;
odb_SequenceFloat conjugateData() const;
const double* dataDouble(int& numVal) const;
odb_SequenceDouble dataDouble() const;
const double* conjugateDataDouble(int& numVal) const;
odb_SequenceDouble conjugateDataDouble() const;
odb_SequenceSequenceFloat localCoordSystem() const;
odb_SequenceSequenceDouble localCoordSystemDouble() const;
float magnitude() const;
float mises() const;
float tresca() const;
float press() const;
float inv3() const;
float maxPrincipal() const;
float midPrincipal() const;
float minPrincipal() const;
float maxInPlanePrincipal() const;
float minInPlanePrincipal() const;
float outOfPlanePrincipal() const;
```

*position*

一个 odb_Enum::odb_ResultPositionEnum，指定输出在元素中的位置。可能的值为：
- odb_Enum::NODAL，指定在节点处计算的值。
- odb_Enum::INTEGRATION_POINT，指定在积分点处计算的值。
- odb_Enum::ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- odb_Enum::ELEMENT_FACE，指定为诸如空腔辐射等针对元素表面面定义的面变量获得的结果。
- odb_Enum::CENTROID，指定通过外推在积分点处计算的结果获得的质心处的值。

*precision*

一个 odb_Enum::odb_PrecisionEnum，指定输出的精度。可能的值为：
- odb_Enum::SINGLE_PRECISION，指定输出为单精度。
- odb_Enum::DOUBLE_PRECISION，指定输出为双精度。

*elementLabel*

一个 Int，指定包含该位置的元素的元素标签。*elementLabel* 仅在 *position*=odb_Enum::INTEGRATION_POINT、odb_Enum::CENTROID、odb_Enum::ELEMENT_NODAL 或 odb_Enum::ELEMENT_FACE 时可用。

*nodeLabel*

一个 Int，指定包含该位置的节点的节点标签。*nodeLabel* 仅在 *position*=odb_Enum::ELEMENT_NODAL 或 odb_Enum::NODAL 时可用。

*integrationPoint*

一个 Int，指定元素中的积分点。*integrationPoint* 仅在 *position*=odb_Enum::INTEGRATION_POINT 时可用。

*face*

一个 odb_Enum::odb_ElementFaceEnum，指定元素的面。*face* 仅在 *position*=odb_Enum::ELEMENT_FACE 时可用。

*type*

一个 odb_Enum::odb_DataTypeEnum，指定输出类型。可能的值为 odb_Enum::SCALAR、odb_Enum::VECTOR、odb_Enum::TENSOR_3D_FULL、odb_Enum::TENSOR_3D_PLANAR、odb_Enum::TENSOR_3D_SURFACE、odb_Enum::TENSOR_2D_PLANAR 和 odb_Enum::TENSOR_2D_SURFACE。

*magnitude*

一个 Float，指定向量的长度或大小。*magnitude* 仅在 *type*=odb_Enum::VECTOR 时有效。

*mises*

一个 Float，指定计算的 von Mises 应力。仅当 *validInvariants* 成员包含 odb_Enum::MISES 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*tresca*

一个 Float，指定计算的 Tresca 应力。仅当 *validInvariants* 成员包含 odb_Enum::TRESCA 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*press*

一个 Float，指定计算的压力应力。仅当 *validInvariants* 成员包含 odb_Enum::PRESS 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*inv3*

一个 Float，指定计算的第三应力不变量。仅当 *validInvariants* 成员包含 odb_Enum::INV3 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*maxPrincipal*

一个 Float，指定计算的最大主应力。仅当 *validInvariants* 成员包含 odb_Enum::MAX_PRINCIPAL 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*midPrincipal*

一个 Float，指定计算的中间主应力。仅当 *validInvariants* 成员包含 odb_Enum::MID_PRINCIPAL 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*minPrincipal*

一个 Float，指定最小主应力。仅当 *validInvariants* 成员包含 odb_Enum::MIN_PRINCIPAL 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*maxInPlanePrincipal*

一个 Float，指定最大主平面内应力。仅当 *validInvariants* 成员包含 odb_Enum::MAX_INPLANE_PRINCIPAL 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*minInPlanePrincipal*

一个 Float，指定计算的最小主平面内应力。仅当 *validInvariants* 成员包含 odb_Enum::MIN_INPLANE_PRINCIPAL 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*outOfPlanePrincipal*

一个 Float，指定计算的主平面外应力。仅当 *validInvariants* 成员包含 odb_Enum::OUTOFPLANE_PRINCIPAL 时该值才有效；否则该值不确定。在不变量计算中忽略共轭数据。

*instance*

一个 [OdbInstance](pt02ch61pyo16.md) 对象，指定标签所属的部件。

*sectionPoint*

一个 [SectionPoint](pt02ch61pyo28.md) 对象。

*localCoordSystem*

一个 odb_SequenceSequenceFloat，指定表示局部坐标系方向余弦的 3×3 Float 矩阵。每个序列表示方向余弦矩阵中的一行。*localCoordSystem* 仅对以局部坐标系编写的 odb_Enum::TENSOR 数据可用。如果底层数据为双精度，将抛出异常。

*localCoordSystemDouble*

一个 odb_SequenceSequenceDouble，指定表示局部坐标系方向余弦的 3×3 Double 矩阵。每个序列表示方向余弦矩阵中的一行。*localCoordSystemDouble* 仅对以局部坐标系编写的 odb_Enum::TENSOR 数据可用。如果底层数据为单精度，将抛出异常。

*data*

一个指向 Float 数组的指针，以 *type* 描述的形式指定数据。如果 *type*=odb_Enum::TENSOR 或 odb_Enum::VECTOR，*data* 是一个包含分量的序列。如果底层数据为双精度，将抛出异常。

*dataDouble*

一个指向 Double 数组的指针，以 *type* 描述的形式指定数据。如果 *type*=odb_Enum::TENSOR 或 odb_Enum::VECTOR，*data* 是一个包含分量的序列。如果底层数据为单精度，将抛出异常。

*conjugateData*

一个指向 Float 数组的指针，以 *type* 描述的形式指定数据。如果 *type*=odb_Enum::TENSOR 或 odb_Enum::VECTOR，*conjugateData* 是一个包含分量的序列。如果底层数据为双精度，将抛出异常。

*conjugateDataDouble*

一个指向 Double 数组的指针，以 *type* 描述的形式指定数据。如果 *type*=odb_Enum::TENSOR 或 odb_Enum::VECTOR，*conjugateData* 是一个包含分量的序列。如果底层数据为单精度，将抛出异常。
