# 61.7 FieldOutput 对象





FieldOutput 对象包含特定输出变量的场数据。

**访问**

```
odb.steps()[*name*].frames(*i*).fieldOutputs()[*name*]
```

### 61.7.1 FieldOutput(...)

此方法创建一个 FieldOutput 对象。

**路径**

```
odb.steps()[*name*].frames(*i*).FieldOutput
```

**原型**

```
odb_FieldOutput&
FieldOutput(const odb_String& name,
            const odb_String& description,
            odb_Enum::odb_DataTypeEnum type,
            const odb_SequenceString& componentLabels,
            const odb_SequenceInvariant& validInvariants,
            bool isEngineeringTensor);
```

**必需参数**

*name*

一个 odb_String，指定输出变量名称。

*description*

一个 odb_String，指定输出变量。冒号（:）不应作为场输出描述的一部分使用。

*type*

一个 odb_Enum::odb_DataTypeEnum，指定输出类型。可能的值为 odb_Enum::SCALAR、odb_Enum::VECTOR、odb_Enum::TENSOR_3D_FULL、odb_Enum::TENSOR_3D_PLANAR、odb_Enum::TENSOR_3D_SURFACE、odb_Enum::TENSOR_2D_PLANAR 和 odb_Enum::TENSOR_2D_SURFACE。

**可选参数**

*componentLabels*

一个 odb_SequenceString，指定值每个分量的标签。序列的长度必须与类型匹配。如果 *type*=odb_Enum::TENSOR，默认值为带有后缀（'11'、'22'、'33'、'12'、'13'、'23'）的 *name*。如果 *type*=odb_Enum::VECTOR，默认值为带有后缀（'1'、'2'、'3'）的 *name*。如果 *type*=odb_Enum::SCALAR，默认值为空序列。

*validInvariants*

一个 odb_SequenceInvariant，指定应该为此场计算的不变量。空序列表示没有不变量对此场有效。可能的值为：
- odb_Enum::MAGNITUDE
- odb_Enum::MISES
- odb_Enum::TRESCA
- odb_Enum::PRESS
- odb_Enum::INV3
- odb_Enum::MAX_PRINCIPAL
- odb_Enum::MID_PRINCIPAL
- odb_Enum::MIN_PRINCIPAL
- odb_Enum::MAX_INPLANE_PRINCIPAL
- odb_Enum::MIN_INPLANE_PRINCIPAL
- odb_Enum::OUTOFPLANE_PRINCIPAL

默认值为空序列。

*isEngineeringTensor*

一个布尔值，指定场是否是工程张量。将 isEngineeringTensor 设置为 true 会使张量场表现为类似应变的量，其中张量的非对角分量在计算不变量时减半。此参数仅适用于张量场输出。默认值为 false。

**返回值**

一个 FieldOutput 对象。

**异常**

无。

### 61.7.2 FieldOutput(...)

此方法从现有 FieldOutput 对象创建一个 FieldOutput 对象。

**路径**

```
odb.steps()[*name*].frames(*i*).FieldOutput
```

**原型**

```
odb_FieldOutput&
FieldOutput(const odb_FieldOutput& field,
            const odb_String& name,
            const odb_String& description);
```

**必需参数**

*field*

一个 FieldOutput 对象。

**可选参数**

*name*

一个 String，指定 FieldOutput 对象的名称。

*description*

一个 odb_String，指定输出变量。冒号（:）不应作为场输出描述的一部分使用。

**返回值**

一个 FieldOutput 对象。

**异常**

无。

### 61.7.3 VectorOutput(...)

此方法创建一个 FieldOutput 对象。

**路径**

```
odb.steps()[*name*].frames(*i*).VectorOutput
```

**原型**

```
odb_FieldOutput&
VectorOutput(const odb_String& name,
             const odb_String& description,
             int width);
```

**必需参数**

*name*

一个 odb_String，指定输出变量名称。

*description*

一个 odb_String，指定输出变量。冒号（:）不应作为场输出描述的一部分使用。

*width*

一个 Int，指定向量的宽度。

**可选参数**

无。

**返回值**

一个 FieldOutput 对象。

**异常**

无。

### 61.7.4 MatrixOutput(...)

此方法创建一个 FieldOutput 对象。

**路径**

```
odb.steps()[*name*].frames(*i*).MatrixOutput
```

**原型**

```
odb_FieldOutput&
MatrixOutput(const odb_String& name,
             const odb_String& description,
             int rows,
             int cols);
```

**必需参数**

*name*

一个 odb_String，指定输出变量名称。

*description*

一个 odb_String，指定输出变量。冒号（:）不应作为场输出描述的一部分使用。

*rows*

一个 Int，指定矩阵的行数。

*cols*

一个 Int，指定矩阵的列数。

**可选参数**

无。

**返回值**

一个 FieldOutput 对象。

**异常**

无。

### 61.7.5 SymmetricMatrixOutput(...)

此方法创建一个 FieldOutput 对象。

**路径**

```
odb.steps()[*name*].frames(*i*).SymmetricMatrixOutput
```

**原型**

```
odb_FieldOutput&
SymmetricMatrixOutput(const odb_String& name,
                      const odb_String& description,
                      int dim);
```

**必需参数**

*name*

一个 odb_String，指定输出变量名称。

*description*

一个 odb_String，指定输出变量。冒号（:）不应作为场输出描述的一部分使用。

*dim*

一个 Int，指定对称矩阵的维数。

**可选参数**

无。

**返回值**

一个 FieldOutput 对象。

**异常**

无。

### 61.7.6 addData(...)

此方法向 FieldOutput 对象添加数据。

**原型**

```
void
addData(odb_Enum::odb_ResultPositionEnum position,
        const odb_Instance& instance,
        const odb_SequenceInt& labels,
        const odb_SequenceSequenceFloat& data,
        const odb_SectionPoint& sectionPoint,
        const odb_SequenceSequenceFloat& localCoordSystem,
        const odb_SequenceSequenceFloat& conjugateData);
```

**必需参数**

*position*

一个 odb_Enum::odb_ResultPositionEnum，指定输出的位置。可能的值为：
- odb_Enum::NODAL，指定在节点处计算的值。
- odb_Enum::INTEGRATION_POINT，指定在积分点处计算的值。
- odb_Enum::ELEMENT_NODAL，指定通过外推在积分点处计算的结果获得的值。
- odb_Enum::CENTROID，指定通过外推在积分点处计算的结果获得的质心处的值。

*instance*

一个 [OdbInstance](pt02ch61pyo16.md) 对象，指定标签的命名空间。

*labels*

一个 odb_SequenceInt，指定 *data* 中值所在节点或元素的标签。节点或元素标签必须按升序排序，并且必须与为 *data* 参数提供的值顺序相同。

*data*

一个 odb_SequenceSequenceFloat，指定指定 *position*、*instance* 和 *labels* 的数据值。必须以正确顺序给出值。元素节点数据遵循 Abaqus 文档中定义的节点连通性顺序。积分点数据遵循 Abaqus 文档中定义的顺序。梁和壳的截面点数据遵循 Abaqus 文档中给出的约定。

**可选参数**

*sectionPoint*

一个 [SectionPoint](pt02ch61pyo28.md) 对象，指定截面中的位置。虽然 *sectionPoint* 是 `addData` 方法的可选参数，但省略此参数会影响可视化。如果在为壳或梁写入场输出数据时省略此参数，则在使用可视化模块显示场输出数据时，您将无法选择要显示的截面点。

*localCoordSystem*

一个 odb_SequenceSequenceFloat，指定局部坐标系的 3×3 方向余弦矩阵。此参数仅对 type=odb_Enum::TENSOR 或 odb_Enum::VECTOR 的场可用。

用户提供的 localCoordSystem 值在存储到数据库之前会被转置。

*conjugateData*

一个 odb_SequenceSequenceFloat，指定指定位置、实例和标签的虚数数据值。当向输出数据库添加复数场时，必须提供此数据。值的顺序遵循"Abaqus Analysis User's Guide"第六部分"Elements"中定义的约定。

**返回值**

无

**异常**

`addData` 方法会抛出多种类型的 odbException 异常。例如，如果为标量数据指定了局部坐标系：

```
odbException: Transformation not allowed for scalar data.
```

### 61.7.7 addData(...)

此方法将从使用 `getSubset` 方法和数学运算符创建的场的数据添加到数据库。用户必须创建一个场来包含新数据，然后使用 `addData` 方法从场分配数据。

**原型**

```
void
addData(const odb_FieldOutput& field);
```

**必需参数**

*field*

一个 FieldOutput 对象，指定要添加的数据。

**可选参数**

无。

**返回值**

无

**异常**

`addData` 方法会抛出多种类型的 odbException 异常。

### 61.7.8 addData(...)

此方法向 FieldOutput 对象添加数据。

**原型**

```
void
addData(odb_Enum::odb_ResultPositionEnum position,
        const odb_Set& set,
        const odb_SequenceSequenceFloat& data,
        const odb_SectionPoint& sectionPoint,
        const odb_SequenceSequenceFloat& conjugateData);
```

**必需参数**

*position*

一个 odb_Enum::odb_ResultPositionEnum，指定输出的位置。可能的值为：
- odb_Enum::NODAL
- odb_Enum::INTEGRATION_POINT
- odb_Enum::ELEMENT_NODAL
- odb_Enum::CENTROID
- odb_Enum::ELEMENT_FACE_INTEGRATION_POINT
- odb_Enum::SURFACE_INTEGRATION_POINT

*set*

一个 [OdbSet](pt02ch61pyo24.md) 对象，指定为 `addData` 定义区域的在实例级别的集。

*data*

一个 odb_SequenceSequenceFloat，指定为指定位置和集中标签的数据值。每一行数据提供一个唯一位置的值。每行的宽度应与数据所需分量数匹配。

**可选参数**

*sectionPoint*

一个 [SectionPoint](pt02ch61pyo28.md) 对象。

*conjugateData*

一个 odb_SequenceSequenceFloat，指定复数数据的虚部。

**返回值**

无

**异常**

如果指定的 odbSet 包含来自多个实例的实体：

```
odbException: Entities from multiple instances present in set.
```

### 61.7.9 addData(...)

此方法向 FieldOutput 对象添加数据。

### 61.7.10 addData(...)

此方法向 FieldOutput 对象添加双精度数据。

### 61.7.11 getScalarField(...)

此方法生成一个包含提取分量或计算不变量值的标量场。

### 61.7.12 getScalarField(...)

此方法生成一个包含提取分量或计算不变量值的标量场。

### 61.7.13 getSubset(...)

具有场值子集的 FieldOutput 对象。

### 61.7.14 getSubset(...)

具有场值子集的 FieldOutput 对象。

### 61.7.15 getSubset(...)

具有场值子集的 FieldOutput 对象。

### 61.7.16 getSubset(...)

具有场值子集的 FieldOutput 对象。

### 61.7.17 getSubset(...)

具有场值子集的 FieldOutput 对象。

### 61.7.18 getSubset(...)

具有场值子集的 FieldOutput 对象。

### 61.7.19 getSubset(...)

具有场值子集的 FieldOutput 对象。

### 61.7.20 getSubset(...)

具有场值子集的 FieldOutput 对象。

### 61.7.21 getSubset(...)

具有场值子集的 FieldOutput 对象。

### 61.7.22 getTransformedField(...)

此方法生成一个包含父场转换后分量值的新向量或张量场。

### 61.7.23 getTransformedField(...)

此方法生成一个包含父场转换后分量值的新向量或张量场。

### 61.7.24 getTransformedField(...)

此方法生成一个包含父场转换后分量值的新向量或张量场。

### 61.7.25 成员

FieldOutput 对象具有与 [FieldOutput](pt02ch61pyo07.md#ker-fieldoutput-fieldoutput-cpp) 方法参数相同名称和描述的成员。

此外，FieldOutput 对象可以具有以下成员：

**原型**

```
odb_String name() const;
               odb_String description() const;
               odb_Enum::odb_DataTypeEnum type() const;
               odb_Enum::odb_DataSubtypeEnum subtype() const;
               int dim() const;
               int dim2() const;
               bool isComplex() const;
               odb_SequenceInvariant validInvariants() const;
               odb_SequenceString componentLabels() const;
               odb_SequenceString baseElementTypes() const;
               const odb_SequenceFieldLocation& locations() const;
               odb_FieldLocation locations(int index) const;
               const odb_FieldValue values(int i);
               odb_SequenceFieldValue values();
               const odb_FieldBulkData& bulkDataBlocks(int i);
               odb_SequenceFieldBulkData& bulkDataBlocks();
```

*dim*

一个 Int，指定向量的维数或矩阵的第一维（行数）。

*dim2*

一个 Int，指定矩阵的第二维（列数）。

*isComplex*

一个布尔值，指定数据是否为复数。

*locations*

[FieldLocation](pt02ch61pyo06.md) 对象的序列。

*values*

[FieldValue](pt02ch61pyo08.md) 对象的序列，数组中对象的顺序由 Abaqus Scripting Interface 确定。

*bulkDataBlocks*

[FieldBulkData](pt02ch61pyo05.md) 对象的序列。





