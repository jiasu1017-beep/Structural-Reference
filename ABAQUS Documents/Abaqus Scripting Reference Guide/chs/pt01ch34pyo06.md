# 34.6 FieldOutput 对象

FieldOutput 对象包含特定输出变量的场数据。

**访问**

```
import odbAccess
session.odbs[*name*].steps[*name*].frames[*i*].fieldOutputs[*name*]
```

### 34.6.1 FieldOutput(...)

此方法创建一个 FieldOutput 对象。

**路径**

```
session.odbs[*name*].steps[*name*].frames[*i*].FieldOutput
```

**必要参数**

*name*

一个字符串，指定输出变量名称。

*description*

一个字符串，指定输出变量。冒号（:）不应作为场输出描述的一部分使用。

*type*

一个 SymbolicConstant，指定输出类型。可能的值为 SCALAR、VECTOR、TENSOR_3D_FULL、TENSOR_3D_PLANAR、TENSOR_3D_SURFACE、TENSOR_2D_PLANAR 和 TENSOR_2D_SURFACE。

**可选参数**

*componentLabels*

字符串序列，指定值的每个分量的标签。序列的长度必须与类型匹配。如果 *type*=TENSOR，默认值为带有后缀（'11'、'22'、'33'、'12'、'13'、'23'）的 *name*。如果 *type*=VECTOR，默认值为带有后缀（'1'、'2'、'3'）的 *name*。如果 *type*=SCALAR，默认值为空序列。

*validInvariants*

SymbolicConstant 序列，指定应该为此场计算的不变量。空序列表示此场没有有效的任何不变量。可能的值为：
- MAGNITUDE
- MISES
- TRESCA
- PRESS
- INV3
- MAX_PRINCIPAL
- MID_PRINCIPAL
- MIN_PRINCIPAL
- MAX_INPLANE_PRINCIPAL
- MIN_INPLANE_PRINCIPAL
- OUTOFPLANE_PRINCIPAL

默认值为空序列。

*isEngineeringTensor*

一个布尔值，指定该场是否是工程张量。将 isEngineeringTensor 设置为 true 会使张量场表现为类似应变的量，其中张量的非对角分量在计算不变量时被减半。此参数仅适用于张量场输出。默认值为 OFF。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.2 FieldOutput(...)

此方法从现有 FieldOutput 对象创建一个 FieldOutput 对象。

**路径**

```
session.odbs[*name*].steps[*name*].frames[*i*].FieldOutput
```

**必要参数**

*field*

一个 FieldOutput 对象。

**可选参数**

*name*

一个字符串，指定 FieldOutput 对象的名称。

*description*

一个字符串，指定输出变量。冒号（:）不应作为场输出描述的一部分使用。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.3 addData(...)

此方法向 FieldOutput 对象添加数据。

**必要参数**

*position*

一个 SymbolicConstant，指定输出的位置。可能的值为：
- NODAL，指定在节点处计算的值。
- INTEGRATION_POINT，指定在积分点处计算的值。
- ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- CENTROID，指定通过外推在积分点处计算的结果获得的质心处的值。

*instance*

一个 [OdbInstance](pt01ch34pyo15.md) 对象，指定标签的命名空间。

*labels*

整数序列，指定 *data* 中值所在的节点或元素的标签。节点或元素标签必须按升序排序，并且必须与为 *data* 参数提供的值顺序相同。

*data*

浮点数序列的序列，指定指定 *position*、*instance* 和 *labels* 的数据值。值必须以正确的顺序给出。元素节点数据遵循 Abaqus 文档中定义的节点连接顺序。积分点数据遵循 Abaqus 文档中定义的顺序。梁和壳的截面点数据遵循 Abaqus 文档中给出的约定。有关更多信息，请参阅《Abaqus Analysis User's Guide》的"Part VI, Elements"。这些数据在内部创建 [FieldValue](pt01ch34pyo07.md) 对象。

**可选参数**

*sectionPoint*

一个 [SectionPoint](pt01ch34pyo28.md) 对象，指定截面中的位置。虽然 *sectionPoint* 是 `addData` 方法的可选参数，但省略此参数对可视化有影响。如果在为壳或梁写入场输出数据时省略此参数，则在使用 Visualization 模块显示场输出数据时，您将无法随后选择要显示的截面点。

*localCoordSystem*

*localCoordSystem* 参数可以通过以下任一方式指定：
- 浮点数序列的序列，指定局部坐标系的方向余弦的 3×3 矩阵。此参数仅适用于 type=TENSOR 或 VECTOR 的场。
- 浮点数矩阵的序列，指定局部坐标系的方向余弦，其中序列长度与 *data* 相同。如果 *localCoordSystem* 是一个矩阵，则每个数据值适用不同的局部坐标系。

用户提供的 localCoordSystem 值在存储到数据库之前被转置。

**返回值**

无

**异常**

`addData` 方法会抛出多种类型的 odbException 异常。例如，如果为标量数据指定了局部坐标系：

```
odbException: Transformation not allowed for scalar data.
```

### 34.6.4 addData(...)

此方法将从使用 `getSubset` 方法创建的场和数学运算符的数据添加到数据库。用户必须创建一个场来包含新数据，然后使用 `addData` 方法从场分配数据。

**必要参数**

*field*

一个 FieldOutput 对象，指定要添加的数据。

**可选参数**

无。

**返回值**

无

**异常**

`addData` 方法会抛出多种类型的 odbException 异常。例如，如果为标量数据指定了局部坐标系：

```
odbException: Transformation not allowed for scalar data.
```

### 34.6.5 addData(...)

此方法向 FieldOutput 对象添加数据。

**必要参数**

*position*

一个 SymbolicConstant，指定输出的位置。可能的值为：
- NODAL，指定在节点处计算的值。
- INTEGRATION_POINT，指定在积分点处计算的值。
- ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- CENTROID，指定通过外推在积分点处计算的结果获得的质心处的值。
- ELEMENT_FACE_INTEGRATION_POINT，指定在元素面积分点处计算的值。
- SURFACE_INTEGRATION_POINT，指定在表面积分点处计算的值。选择此值会提示 Visualization 模块计算多个表面上 ELEMENT_FACE_INTEGRATION_POINT 位置处的值之和。

*set*

一个 [OdbSet](pt01ch34pyo23.md) 对象，指定定义 `addData` 区域的实例级集合。集合必须在与写入新场输出数据的输出数据库相同的输出数据库中定义。集合中的节点或元素标签必须按升序排序，并且必须与为 *data* 参数提供的值顺序相同。

*data*

浮点数序列的序列，指定指定位置和集合中标签的数据值。每一行数据提供一个唯一位置的值。每行的宽度应与所需的数据分量数量匹配。值必须按照与集合中标签顺序匹配的顺序给出。

元素节点数据、积分点数据以及梁和壳的截面点数据的顺序遵循《Abaqus Analysis User's Guide》"Part VI, Elements"中定义的约定。

**可选参数**

*sectionPoint*

一个 [SectionPoint](pt01ch34pyo28.md) 对象，指定截面中的位置。虽然 *sectionPoint* 是 `addData` 方法的可选参数，但省略此参数对可视化有影响。如果在为壳或梁写入场输出数据时省略此参数，则在使用 Visualization 模块显示场输出数据时，您将无法随后选择要显示的截面点。

*conjugateData*

一个 odb_SequenceSequenceFloat 对象，指定指定位置、实例和标签的虚数据值。当向输出数据库添加复数场时，必须提供此数据。值的顺序遵循《Abaqus Analysis User's Guide》"Part VI, Elements"中定义的约定。

**返回值**

无

**异常**

如果指定的 odbSet 包含来自多个实例的实体：

```
odbException: Entities from multiple instances present in set.
```

`addData` 方法会抛出多种类型的 odbException 异常。例如，如果为标量数据指定了局部坐标系：

```
odbException: Transformation not allowed for scalar data.
```

### 34.6.6 getScalarField(...)

此方法生成一个包含提取的分量或计算的不变量值的标量场。新场将保持与父场相同的节点或元素的值。Abaqus 仅对 FieldOutput 对象的实部执行此操作。该操作不在共轭数据（复数结果的虚部）上执行。

**必要参数**

*invariant*

一个 SymbolicConstant，指定不变量。可能的值为 MAGNITUDE、MISES、TRESCA、PRESS、INV3、MAX_PRINCIPAL、MID_PRINCIPAL、MIN_PRINCIPAL、MAX_INPLANE_PRINCIPAL、MIN_INPLANE_PRINCIPAL 和 OUTOFPLANE_PRINCIPAL。

**可选参数**

无。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.7 getScalarField(...)

此方法生成一个包含提取的分量或计算的不变量值的标量场。新场将保持与父场相同的节点或元素的值。Abaqus 仅对 FieldOutput 对象的实部执行此操作。该操作不在共轭数据（复数结果的虚部）上执行。

**必要参数**

*componentLabel*

一个字符串，指定分量标签，例如"S11"。

**可选参数**

无。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.8 getSubset(...)

具有场值子集的 FieldOutput 对象。

**必要参数**

无。

**可选参数**

*position*

一个 SymbolicConstant，指定输出在元素中的位置。可能的值为：
- NODAL，指定在节点处计算的值。
- INTEGRATION_POINT，指定在积分点处计算的值。
- ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- CENTROID，指定通过外推在积分点处计算的结果获得的质心处的值。

如果请求的场值在指定的 ELEMENT_NODAL 或 CENTROID 位置的输出数据库中找不到，则从 INTEGRATION_POINT 位置的场数据外推。

*readOnly*

一个布尔值，指定此调用返回的外推数据是否写入输出数据库。默认值为 OFF。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.9 getSubset(...)

具有场值子集的 FieldOutput 对象。

**必要参数**

无。

**可选参数**

*region*

一个 [OdbSet](pt01ch34pyo23.md)，指定要提取值的区域。集合中的节点或元素必须排序并按升序排列。不支持使用未排序的集合。对于通过多域运行分析获得的 Abaqus 输出数据库中的集合尤其如此。在这种情况下，必须创建新的排序集合，然后才能在 getSubset 方法中使用它。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.10 getSubset(...)

具有场值子集的 FieldOutput 对象。

**必要参数**

无。

**可选参数**

*localCoordSystem*

浮点数序列的序列，指定方向余弦的 3×3 矩阵。将提取与所提供坐标系关联的场值。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.11 getSubset(...)

具有场值子集的 FieldOutput 对象。

**必要参数**

无。

**可选参数**

*sectionPoint*

一个 [SectionPoint](pt01ch34pyo28.md) 对象。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.12 getSubset(...)

具有场值子集的 FieldOutput 对象。

**必要参数**

无。

**可选参数**

*location*

一个 [FieldLocation](pt01ch34pyo05.md) 对象。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.13 getSubset(...)

具有场值子集的 FieldOutput 对象。

**必要参数**

无。

**可选参数**

*region*

一个 [OdbMeshElement](pt01ch34pyo17.md)，指定要提取值的区域。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.14 getSubset(...)

具有场值子集的 FieldOutput 对象。

**必要参数**

无。

**可选参数**

*region*

一个 [OdbMeshNode](pt01ch34pyo18.md)，指定要提取值的区域。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.15 getSubset(...)

具有场值子集的 FieldOutput 对象。

**必要参数**

无。

**可选参数**

*region*

一个 [OdbInstance](pt01ch34pyo15.md)，指定要提取值的区域。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.16 getSubset(...)

具有场值子集的 FieldOutput 对象。

**必要参数**

无。

**可选参数**

*elementType*

一个字符串，指定要提取值的单元类型。该字符串必须对应于有效的 Abaqus 单元类型。

**返回值**

FieldOutput 对象。

**异常**

无。

### 34.6.17 getTransformedField(...)

此方法生成一个包含父场转换分量值的新向量或张量场。新场将保持与父场相同的节点或元素的值。结果将根据输入 [DatumCsys](pt01ch15pyo03.md) 对象指定的方向进行转换。Abaqus 仅对 FieldOutput 对象的实部执行此操作。该操作不在共轭数据（复数结果的虚部）上执行。

**必要参数**

*datumCsys*

一个有效的 [DatumCsys](pt01ch15pyo03.md) 对象，指定坐标系。有效的系统可以是固定的或相对于模型上的节点定位的，可以是笛卡尔、圆柱或球形。

**可选参数**

*projected22Axis*

一个整数，指定坐标系的哪个轴将作为局部结果方向的第二个分量投影。有效值为 1、2 或 3；默认值为 2。

*projectionTol*

一个 Double，指定指定投影轴与元素法线之间的最小允许角度（弧度）。如果此容差测试失败，将使用下一个轴进行投影。

**返回值**

FieldOutput 对象。

**异常**

如果场包含任何装配级节点，`getTransformedField` 方法会抛出异常。

```
odbException: Cannot apply transformation to field containing assembly level nodes.
```

### 34.6.18 getTransformedField(...)

此方法生成一个包含父场转换分量值的新向量或张量场。新场将保持与父场相同的节点或元素的值。结果将根据输入 [DatumCsys](pt01ch15pyo03.md) 对象指定的方向进行转换。Abaqus 仅对 FieldOutput 对象的实部执行此操作。该操作不在共轭数据（复数结果的虚部）上执行。

**必要参数**

*datumCsys*

一个有效的 [DatumCsys](pt01ch15pyo03.md) 对象，指定坐标系。有效的系统可以是固定的或相对于模型上的节点定位的，可以是笛卡尔、圆柱或球形。

**可选参数**

*deformationField*

一个 FieldOutput 对象，指定移动坐标系确定瞬时配置所需的节点位移向量。

*projected22Axis*

一个整数，指定坐标系的哪个轴将作为局部结果方向的第二个分量投影。有效值为 1、2 或 3；默认值为 2。

*projectionTol*

一个 Double，指定指定投影轴与元素法线之间的最小允许角度（弧度）。如果此容差测试失败，将使用下一个轴进行投影。

**返回值**

FieldOutput 对象。

**异常**

如果场包含任何装配级节点，`getTransformedField` 方法会抛出异常。

```
odbException: Cannot apply transformation to field containing assembly level nodes.
```

### 34.6.19 getTransformedField(...)

此方法生成一个包含父场转换分量值的新向量或张量场。新场将保持与父场相同的节点或元素的值。结果将根据输入 [DatumCsys](pt01ch15pyo03.md) 对象指定的方向进行转换。Abaqus 仅对 FieldOutput 对象的实部执行此操作。该操作不在共轭数据（复数结果的虚部）上执行。

**必要参数**

*datumCsys*

一个有效的 [DatumCsys](pt01ch15pyo03.md) 对象，指定坐标系。有效的系统可以是固定的或相对于模型上的节点定位的，可以是笛卡尔、圆柱或球形。

**可选参数**

*deformationField*

一个 FieldOutput 对象，指定移动坐标系确定瞬时配置所需的节点位移向量。

*rotationField*

一个 FieldOutput 对象，指定跟随 6-dof 节点的移动坐标系确定瞬时配置所需的节点旋转位移向量。

*projected22Axis*

一个整数，指定坐标系的哪个轴将作为局部结果方向的第二个分量投影。有效值为 1、2 或 3；默认值为 2。

*projectionTol*

一个 Double，指定指定投影轴与元素法线之间的最小允许角度（弧度）。如果此容差测试失败，将使用下一个轴进行投影。

**返回值**

FieldOutput 对象。

**异常**

如果场包含任何装配级节点，`getTransformedField` 方法会抛出异常。

```
odbException: Cannot apply transformation to field containing assembly level nodes.
```

### 34.6.20 成员

FieldOutput 对象具有与 [FieldOutput](pt01ch34pyo06.md#ker-fieldoutput-fieldoutput-pyc) 方法的参数名称和描述相同的成员。

此外，FieldOutput 对象可以具有以下成员：

*dim*

一个整数，指定向量的维度或矩阵的第一维（行数）。

*dim2*

一个整数，指定矩阵的第二维（列数）。

*isComplex*

一个布尔值，指定数据是否为复数。

*locations*

一个 [FieldLocationArray](pt01ch34pyo05.md) 对象。

*values*

一个 [FieldValueArray](pt01ch34pyo07.md) 对象，指定数组中对象的顺序由 Abaqus Scripting Interface 确定；有关描述顺序，请参阅 `addData` 方法的 *data* 参数。
