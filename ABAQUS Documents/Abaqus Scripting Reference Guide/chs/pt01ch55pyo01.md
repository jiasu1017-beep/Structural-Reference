# 55.1 XYData 对象







XYData 对象用于存储与 XYData 类型对象关联的值和属性。

可以使用下面描述的方法创建 XYData 对象。通过 Session 对象访问的方法会将 XYData 对象添加到 `session.xyData` repository。

如果未提供名称，将创建临时 XYData 对象。临时 XYData 对象将被添加到 `session.xyData` repository，但在不再使用时自动删除。临时 XYData 对象也会作为 `abaqusMath` 模块中找到的数学运算的结果创建。

**访问**

```
import visualization
session.charts[*name*].axes1[*i*].axisData.curves[*i*].data
session.charts[*name*].axes2[*i*].axisData.curves[*i*].data
session.charts[*name*].curves[*name*].data
session.curves[*name*].data
session.defaultChartOptions.defaultAxis1Options.axisData.curves[*i*]\
.data
session.defaultChartOptions.defaultAxis2Options.axisData.curves[*i*]\
.data
import odbAccess
session.odbs[*name*].userData.xyDataObjects[*name*]
session.xyDataObjects[*name*]
session.xyPlots[*name*].charts[*name*].axes1[*i*].axisData.curves[*i*].data
session.xyPlots[*name*].charts[*name*].axes2[*i*].axisData.curves[*i*].data
session.xyPlots[*name*].charts[*name*].curves[*name*].data
session.xyPlots[*name*].curves[*name*].data
```

### 55.1.1 XYData(...)

此方法从 *X–Y* 数据对序列创建 XYData 对象。

**路径**

```
session.XYData
```

```
xyPlot.XYData
```

**必需参数**

*data*

一个 Float 对的序列，指定 *X–Y* 数据对。

**可选参数**

*name*

repository 键。如果未提供名称，则生成形式为 _temp#_ 的默认名称，并且 XYData 对象是临时的。

*sourceDescription*

一个 String，指定 *X–Y* 数据的来源（例如，"从键盘输入"、"从 ASCII 文件获取"、"从 ODB 读取"等）。默认值为空字符串。

*contentDescription*

一个 String，指定 *X–Y* 数据的内容（例如，"field 1 vs. field 2"）。默认值为空字符串。

*positionDescription*

一个 String，指定关于 *X–Y* 数据的其他信息（例如，"for whole model"）。默认值为空字符串。

*legendLabel*

一个 String，指定要在图例中使用的标签。默认值为 XYData 对象的名称。

*xValuesLabel*

一个 String，指定 X 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能被覆盖。默认值为空字符串。

*yValuesLabel*

一个 String，指定 Y 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能被覆盖。默认值为空字符串。

*axis1QuantityType*

一个 [QuantityType](pt01ch55pyo11.md) 对象，指定与 X 轴1值关联的 [QuantityType](pt01ch55pyo11.md) 对象。

*axis2QuantityType*

一个 [QuantityType](pt01ch55pyo11.md) 对象，指定与 Y 轴2值关联的 [QuantityType](pt01ch55pyo11.md) 对象。

**返回值**

一个 XYData 对象。

**异常**

InvalidNameError。

### 55.1.2 XYData(...)

此方法通过复制现有 XYData 对象来创建 XYData 对象。

**路径**

```
session.odbs[*name*].userData.XYData
```

```
session.XYData
```

```
xyPlot.XYData
```

**必需参数**

*objectToCopy*

要复制的 XYData 对象。

**可选参数**

可选参数与 [XYData](pt01ch55pyo01.md#ker-xydata-xydata-pyc) 方法的可选参数相同。
None。

**返回值**

一个 XYData 对象。

**异常**

InvalidNameError。

### 55.1.3 XYDataFromFile(...)

此方法从 ASCII 文件中的数据创建 XYData 对象。

**路径**

```
session.XYDataFromFile
```

```
xyPlot.XYDataFromFile
```

**必需参数**

*fileName*

一个 String，指定要从中读取 *X–Y* 数据的文件名。

**可选参数**

*name*

repository 键。如果未提供名称，则生成形式为 _temp#_ 的默认名称，并且 XYData 对象是临时的。

*sourceDescription*

一个 String，指定 *X–Y* 数据的来源（例如，"从键盘输入"、"从 ASCII 文件获取"、"从 ODB 读取"等）。默认值为空字符串。

*contentDescription*

一个 String，指定 *X–Y* 数据的内容（例如，"field 1 vs. field 2"）。默认值为空字符串。

*positionDescription*

一个 String，指定关于 *X–Y* 数据的其他信息（例如，"for whole model"）。默认值为空字符串。

*legendLabel*

一个 String，指定要在图例中使用的标签。默认值为 XYData 对象的名称。

*xValuesLabel*

一个 String，指定 X 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能被覆盖。默认值为空字符串。

*yValuesLabel*

一个 String，指定 Y 值的标签。如果 *X–Y* 数据与其他 *X–Y* 数据组合，此值可能被覆盖。默认值为空字符串。

*axis1QuantityType*

一个 [QuantityType](pt01ch55pyo11.md) 对象，指定与 X 轴1值关联的 [QuantityType](pt01ch55pyo11.md) 对象。

*axis2QuantityType*

一个 [QuantityType](pt01ch55pyo11.md) 对象，指定与 Y 轴2值关联的 [QuantityType](pt01ch55pyo11.md) 对象。

*xField*

一个 Int，指定要从中读取 *X* 数据的字段。字段由空格、制表符或逗号分隔。默认值为 1。

*yField*

一个 Int，指定要从中读取 *Y* 数据的字段。字段由空格、制表符或逗号分隔。默认值为 2。

*skipFrequency*

一个 Int，指定跳过数据行的频率。*skipFrequency* 为 1 表示每隔一行跳过一行。始终读取第一行。可能的值为 *skipFrequency* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0（从每一行读取数据）。

**返回值**

一个 XYData 对象。

**异常**

InvalidNameError 和 RangeError。

### 55.1.4 XYDataFromHistory(...)

此方法通过从 Odb 对象读取历史数据来创建 XYData 对象。

**路径**

```
session.XYDataFromHistory
```

```
xyPlot.XYDataFromHistory
```

**必需参数**

*odb*

一个 Odb 对象，指定要从中读取数据的输出数据库。

*outputVariableName*

一个 String，指定要从中读取 *X–Y* 数据的输出变量。

*steps*

一个 String 序列，指定要从中提取数据的步骤名称。

**可选参数**

*name*

repository 键。如果未提供名称，则生成形式为 _temp#_ 的默认名称，并且 XYData 对象是临时的（如果从 `session` 对象访问方法，则需要此参数）。

*sourceDescription*

一个 String，指定 *X–Y* 数据的来源（例如，"从键盘输入"、"从 ASCII 文件获取"、"从 ODB 读取"等）。默认值为空字符串。

*contentDescription*

一个 String，指定 *X–Y* 数据的内容（例如，"field 1 vs. field 2"）。默认值为空字符串。

*positionDescription*

一个 String，指定关于 *X–Y* 数据的其他信息（例如，"for whole model"）。默认值为空字符串。

*legendLabel*

一个 String，指定要在图例中使用的标签。默认值为 XYData 对象的名称。

*skipFrequency*

一个 Int，指定跳过数据帧的频率。如果 *skipFrequency*=1，Abaqus 将跳过每隔一帧。始终读取第一帧。可能的值为 *skipFrequency* ![](../graphics/ker_eqn00407.gif) 0。默认值为 0（从每一帧读取数据）。

*numericForm*

一个 SymbolicConstant，指定显示包含复数的結果的数字形式。可能的值为 COMPLEX_MAGNITUDE、COMPLEX_PHASE、REAL、IMAGINARY 和 COMPLEX_VAL_AT_ANGLE。默认值为 REAL。

*complexAngle*

一个 Float，指定当 *numericForm*=COMPLEX_VAL_AT_ANGLE 时显示包含复数的結果的角度（度）。默认值为 0。

*stepTuple*

一个 Integer 元组，指定要包含在提取数据中的步骤。

**返回值**

一个 XYData 对象。

**异常**

InvalidNameError 和 RangeError。

### 55.1.5 xyDataListFromField(...)

此方法通过从 Odb 对象读取场数据来创建 XYData 对象列表。

**路径**

```
session.xyDataListFromField
```

```
xyPlot.xyDataListFromField
```

**必需参数**

*odb*

一个 Odb 对象，指定要从中读取数据的输出数据库。

*outputPosition*

一个 SymbolicConstant，指定要从中读取输出的位置。可能的值为 ELEMENT_CENTROID、ELEMENT_NODAL、INTEGRATION_POINT 和 NODAL。

*variable*

一个元组的元组，包含要从中提取数据的变量的描述。每个元组指定以下内容：
- 变量标签：一个 String，指定变量；例如，'U'。
- 变量输出位置：一个 SymbolicConstant，指定输出位置。可能的值为 ELEMENT_CENTROID、ELEMENT_FACE、ELEMENT_NODAL、GENERAL_PARTICLE、INTEGRATION_POINT、NODAL、WHOLE_ELEMENT、WHOLE_MODEL、WHOLE_PART_INSTANCE 和 WHOLE_REGION。
- 细化：一个元组，指定细化。如果省略细化元组，则为所有分量和不变量（如适用）写入数据。如果包含位置字典（元组中的下一个元素），则需要此元素。细化元组包含以下内容：
  - 类型：一个 SymbolicConstant，指定细化的类型。可能的值为 INVARIANT 和 COMPONENT。
  - 标签：一个 String，指定不变量或分量；例如，'Mises' 或 'S22'。
- 位置：一个可选 Dictionary，指定位置。字典包含以下对的配对：
  - 一个 String，指定类别选择标签。
  - 一个 String，指定截面点标签。

例如：

```
variable= ('S',INTEGRATION_POINT, ( (COMPONENT, 'S22' ), ), )
variable= (('S',INTEGRATION_POINT, ((COMPONENT, 'S11' ), ), ),
           ('U',NODAL,((COMPONENT, 'U1'),)),)
variable= (('S', INTEGRATION_POINT, ((INVARIANT, 'Mises' ), ),
           {'shell < STEEL > < 3 section points >':'SNEG,
                                    (fraction = -1.0)', }), )

```

**可选参数**

必须提供以下参数中的至少一个：*elementSets*、*elementLabels*、*nodeSets* 和 *nodeLabels*。

*elementSets*

一个 String 序列，指定元素集或指定单个元素集的 String。

*elementLabels*

一个表达式序列，指定模型中每个零件实例的元素标签。每个零件实例元素表达式是一个 String（指定零件实例名称）和元素表达式序列的序列；例如，`(('partInstance1',(1,'7','3:15;3'),), ('partInstance2','8'),))`。元素表达式可以是以下任何一种：
- 一个 Int，指定单个元素标签；例如，`1`。
- 一个 String，指定单个元素标签；例如，`'7'`。
- 一个 String，指定元素标签序列；例如，`'3:5'` 和 `'3:15:3'`。

*nodeSets*

一个 String 序列，指定节点集或指定单个节点集的 String。

*nodeLabels*

一个表达式序列，指定模型中每个零件实例的节点标签。每个零件实例节点表达式是一个 String（指定零件实例名称）和节点表达式序列的序列；例如，`(('partInstance1',(1,'7','3:15;3'),), ('partInstance2','8'),))`。节点表达式可以是以下任何一种：
- 一个 Int，指定单个节点标签；例如，`1`。
- 一个 String，指定单个节点标签；例如，`'7'`。
- 一个 String，指定节点标签序列；例如，`'3:5'` 和 `'3:15:3'`。

*numericForm*

一个 SymbolicConstant，指定显示包含复数的結果的数字形式。可能的值为 COMPLEX_MAGNITUDE、COMPLEX_PHASE、REAL、IMAGINARY 和 COMPLEX_VAL_AT_ANGLE。默认值为 REAL。

*complexAngle*

一个 Float，指定当 *numericForm*=COMPLEX_VAL_AT_ANGLE 时显示包含复数的結果的角度（度）。默认值为 0。

**返回值**

一个 XYData 对象列表。

**异常**

InvalidNameError 和 RangeError。

### 55.1.6 XYDataFromFreeBody(...)

此方法通过从 Odb 对象计算自由体数据来创建 XYData 对象列表。

**路径**

```
session.XYDataFromFreeBody
```

```
xyPlot.XYDataFromFreeBody
```

**必需参数**

*odb*

一个 Odb 对象，指定要从中读取数据的输出数据库。

*force*

一个布尔值，指定是否计算力。

*moment*

一个布尔值，指定是否计算力矩。

*resultant*

一个布尔值，指定是否计算合量。

*comp1*

一个布尔值，指定是否计算第一个分量。

*comp2*

一个布尔值，指定是否计算第二个分量。

*comp3*

一个布尔值，指定是否计算第三个分量。

**可选参数**

None。

**返回值**

一个 XYData 对象列表。

**异常**

InvalidNameError 和 RangeError。

### 55.1.7 XYDataFromShellThickness(...)

此方法通过从 Odb 对象读取厚度场数据来创建 XYData 对象列表。

**路径**

```
xyPlot.XYDataFromShellThickness
```

**必需参数**

*odb*

一个 Odb 对象，指定要从中读取数据的输出数据库。

*outputPosition*

一个 SymbolicConstant，指定要从中读取输出的位置。可能的值为 ELEMENT_CENTROID、ELEMENT_NODAL、INTEGRATION_POINT 和 NODAL。

*variable*

一个元组的元组，包含要从中提取数据的变量的描述。每个元组指定以下内容：
- 变量标签：一个 String，指定变量；例如，'U'。
- 变量输出位置：一个 SymbolicConstant，指定输出位置。可能的值为 ELEMENT_CENTROID、ELEMENT_FACE、ELEMENT_NODAL、GENERAL_PARTICLE、INTEGRATION_POINT、NODAL、WHOLE_ELEMENT、WHOLE_MODEL、WHOLE_PART_INSTANCE 和 WHOLE_REGION。
- 细化：一个元组，指定细化。如果省略细化元组，则为所有分量和不变量（如适用）写入数据。如果包含位置字典（元组中的下一个元素），则需要此元素。细化元组包含以下内容：
  - 类型：一个 SymbolicConstant，指定细化的类型。可能的值为 INVARIANT 和 COMPONENT。
  - 标签：一个 String，指定不变量或分量；例如，'Mises' 或 'S22'。
- 位置：一个可选 Dictionary，指定位置。字典包含以下对的配对：
  - 一个 String，指定类别选择标签。
  - 一个 String，指定截面点标签。

例如：

```
variable= ('S',INTEGRATION_POINT, ( (COMPONENT, 'S22' ), ), )
variable= (('S',INTEGRATION_POINT, ((COMPONENT, 'S11' ), ), ),
           ('U',NODAL,((COMPONENT, 'U1'),)),)
variable= (('S', INTEGRATION_POINT, ((INVARIANT, 'Mises' ), ),
           {'shell < STEEL > < 3 section points >':'SNEG,
                                    (fraction = -1.0)', }), )
```

**可选参数**

必须提供以下参数中的至少一个：*elementSets*、*elementLabels*、*nodeSets* 和 *nodeLabels*。

*elementSets*

一个 String 序列，指定元素集或指定单个元素集的 String。

*elementLabels*

一个表达式序列，指定模型中每个零件实例的元素标签。每个零件实例元素表达式是一个 String（指定零件实例名称）和元素表达式序列的序列；例如，`(('partInstance1',(1,'7','3:15;3'),), ('partInstance2','8'),))`。元素表达式可以是以下任何一种：
- 一个 Int，指定单个元素标签；例如，`1`。
- 一个 String，指定单个元素标签；例如，`'7'`。
- 一个 String，指定元素标签序列；例如，`'3:5'` 和 `'3:15:3'`。

*nodeSets*

一个 String 序列，指定节点集或指定单个节点集的 String。

*nodeLabels*

一个表达式序列，指定模型中每个零件实例的节点标签。每个零件实例节点表达式是一个 String（指定零件实例名称）和节点表达式序列的序列；例如，`(('partInstance1',(1,'7','3:15;3'),), ('partInstance2','8'),))`。节点表达式可以是以下任何一种：
- 一个 Int，指定单个节点标签；例如，`1`。
- 一个 String，指定单个节点标签；例如，`'7'`。
- 一个 String，指定节点标签序列；例如，`'3:5'` 和 `'3:15:3'`。

*numericForm*

一个 SymbolicConstant，指定显示包含复数的結果的数字形式。可能的值为 COMPLEX_MAGNITUDE、COMPLEX_PHASE、REAL、IMAGINARY 和 COMPLEX_VAL_AT_ANGLE。默认值为 REAL。

*complexAngle*

一个 Float，指定当 *numericForm*=COMPLEX_VAL_AT_ANGLE 时显示包含复数的結果的角度（度）。默认值为 0。

**返回值**

一个 XYData 对象列表。

**异常**

InvalidNameError 和 RangeError。

### 55.1.8 XYDataFromPath(...)

此方法从路径信息创建 XYData 对象。

**路径**

```
session.XYDataFromPath
```

```
xyPlot.XYDataFromPath
```

**必需参数**

*path*

一个 Path 对象，用于 *X–Y* 数据生成。

*name*

一个 String，指定 repository 键：
- 对于 *session*，'name' 是必需参数；对于 *xyPlot*，'name' 是可选参数。

*includeIntersections*

一个 Boolean，指定是否为路径与元素面或边的交点包含 *X–Y* 数据。默认值为 False。

*shape*

一个 SymbolicConstant，指定要使用的模型形状。可能的值为 UNDEFORMED 和 DEFORMED。

*pathStyle*

一个 SymbolicConstant，指定路径样式。可能的值为 PATH_POINTS 和 UNIFORM_SPACING。

*numIntervals*

一个 Int，指定均匀间隔间隔的数量。默认值为 10。

*labelType*

一个 SymbolicConstant，指定要使用的 *X* 标签类型。可能的值为 NORM_DISTANCE、SEQ_ID、TRUE_DISTANCE、TRUE_DISTANCE_X、TRUE_DISTANCE_Y 和 TRUE_DISTANCE_Z。

**可选参数**

*viewport*

一个 String，标识要从中获取值的视口。默认值为当前视口。

*step*

一个 Int，标识要从中获取值的步骤。默认值为当前步骤。

*frame*

一个 Int，标识要从中获取值的帧。默认值为当前帧。

*variable*

一个元组的元组，包含要沿路径提取数据的变量的描述。默认值为当前变量。每个元组指定以下内容：
- 变量标签：一个 String，指定变量；例如，'U'。
- 变量输出位置：一个 SymbolicConstant，指定输出位置。可能的值为 ELEMENT_CENTROID、ELEMENT_FACE、ELEMENT_NODAL、GENERAL_PARTICLE、INTEGRATION_POINT、NODAL、WHOLE_ELEMENT、WHOLE_MODEL、WHOLE_PART_INSTANCE 和 WHOLE_REGION。
- 细化：一个元组，指定细化。如果省略细化元组，则为所有分量和不变量（如适用）写入数据。如果包含位置字典（元组中的下一个元素），则需要此元素。细化元组包含以下内容：
  - 类型：一个 SymbolicConstant，指定细化的类型。可能的值为 INVARIANT 和 COMPONENT。
  - 标签：一个 String，指定不变量或分量；例如，'Mises' 或 'S22'。
- 位置：一个可选 Dictionary，指定位置。字典包含以下对的配对：
  - 一个 String，指定类别选择标签。
  - 一个 String，指定截面点标签。

例如：

```
variable= ('S',INTEGRATION_POINT, ( (COMPONENT, 'S22' ), ), )
variable= (('S',INTEGRATION_POINT, ((COMPONENT, 'S11' ), ), ),
           ('U',NODAL,((COMPONENT, 'U1'),)),)
variable= (('S', INTEGRATION_POINT, ((INVARIANT, 'Mises' ), ),
           {'shell < STEEL > < 3 section points >':'SNEG,
                                    (fraction = -1.0)', }), )
```

*deformedMag*

三个 Float 的元组，指定 *X*、*Y* 和 *Z* 平面中的变形幅度。默认值为 (1, 1, 1)。

*numericForm*

一个 SymbolicConstant，指定显示包含复数的結果的数字形式。可能的值为 COMPLEX_MAGNITUDE、COMPLEX_PHASE、REAL、IMAGINARY 和 COMPLEX_VAL_AT_ANGLE。默认值为 REAL。

*complexAngle*

一个 Float，指定当 *numericForm*=COMPLEX_VAL_AT_ANGLE 时显示包含复数的結果的角度（度）。默认值为 0。

**返回值**

如果 *variable* 指定有一个 fieldoutput：返回 XYData 对象。

如果 *variable* 指定有多个 fieldoutputs：返回 XYData 对象列表。

**异常**

如果 *path* 无效：

```
ErrorPathNotFound: Path not found.
```

如果 *viewport* 无效：

```
ErrorCurrentVPNotFound: Current viewport not found.
```

如果 *step* 和/或 *frame* 无效：

```
ErrorInvalidUserStepAndFrame: The user step and frame specified have not been defined.
```

如果 *variable* 参数为空：

```
ErrorNoVarInPathExtract: No variable selection for XY data extraction from path.
```

如果指定的输出变量在输出数据库中不可用：

```
ErrorUnavailableSelectedVariable: The selected variable is not available for the current frame.
```

如果指定的输出变量不能用于获取 *X–Y* 数据：

```
ErrorUnusableVarInPathExtract: Specified variable cannot be used in XY data extraction from path.
```

如果指定细化的 SymbolicConstant 无效：

```
ErrorUnsupportedRefinementType: Unsupported refinement type.
```

如果指定细化的不变量或分量的标签无效：

```
ErrorInvalidRefinementSpecification: Invalid refinement specification.
```

如果 *deformedMag* 不包含三个 Float：

```
ErrorDeformedMagTupleInPathExtract: Deformed magnification tuple must contain X, Y and Z values.
```

### 55.1.9 save()

此方法保存临时 XYData。XYData 的名称更改为 "XYData-#"。如果 XYData 已保存，则不执行任何操作。

**参数**

None。

**返回值**

None

**异常**

None。

### 55.1.10 setValues(...)

此方法修改 XYData 对象。

**必需参数**

None。

**可选参数**

`setValues` 的可选参数与 [XYData](pt01ch55pyo01.md#ker-xydata-xydata-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

None

**异常**

None。

### 55.1.11 成员

XYData 对象具有与 [XYData](pt01ch55pyo01.md#ker-xydata-xydata-pyc) 方法的参数具有相同名称和描述的成员。

此外，XYData 对象具有以下成员：

*sourceType*

一个 SymbolicConstant，指定 XYData 对象的来源类型。可能的值为 FROM_ODB、FROM_KEYBOARD、FROM_ASCII_FILE、FROM_OPERATION 和 FROM_USER_DEFINED。

*fileName*

一个 String，指定 XYData 对象的源文件名。

*description*

一个 String，指定 XYData 对象的完整描述。

