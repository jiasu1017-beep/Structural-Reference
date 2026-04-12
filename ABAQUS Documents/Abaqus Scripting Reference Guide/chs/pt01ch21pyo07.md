# 21.7 OdbMeshRegionData 对象





OdbMeshRegionData 对象定义 [MappedField](pt01ch21pyo06.md) 的外部源数据，来自 ODB 文件。

**访问**

```
import field
mdb.models[*name*].analyticalFields[*name*].odbMeshRegionData
```

### 21.7.1 OdbMeshRegionData(...)

此方法创建 OdbMeshRegionData 对象。

**路径**

```
mdb.models[*name*].analyticalFields[*name*].OdbMeshRegionData
```

**必需参数**

*odbFileName*

一个 String，指定要读取作为源数据的输出数据库文件名（包括 .odb 扩展名）。如果该文件位于其他目录，此 String 也可以是输出数据库文件的完整路径。

*variableLabel*

一个 String，指定场输出变量。

**可选参数**

*stepIndex*

一个 Int，指定步骤索引。可能的值为 0 ≤ *stepIndex* ≤ (*numSteps * 1)。默认值为 0。

*frameIndex*

一个 Int，指定指定步骤中的帧。有效值为 0 ≤ *frameIndex* ≤ (*numFramesInStep * 1)。默认值为 0。

*outputPosition*

一个 SymbolicConstant，指定获取数据的位置。数据只能从分析过程中写入输出数据库的位置获取。此位置应与场输出变量对齐。可能的值为：
- UNDEFINED_POSITION
- NODAL
- INTEGRATION_POINT
- ELEMENT_FACE
- ELEMENT_NODAL
- ELEMENT_CENTROID
- WHOLE_ELEMENT
- WHOLE_REGION
- WHOLE_PART_INSTANCE
- WHOLE_MODEL
- GENERAL_PARTICLE

默认值为 UNDEFINED_POSITION。

*dataType*

一个 SymbolicConstant，指定场输出变量的数据类型，应与变量对齐。当前仅支持 SCALAR。可能的值为：
- ENUMERATION
- BOOLEAN
- INTEGER
- SCALAR
- VECTOR
- QUATERNION_2D
- QUATERNION_3D
- TENSOR
- TENSOR_3D_FULL
- TENSOR_3D_PLANAR
- TENSOR_3D_SURFACE
- TENSOR_2D_PLANAR
- TENSOR_2D_SURFACE

默认值为 SCALAR。

*storageType*

一个 SymbolicConstant，指定场输出变量的存储类型，应与变量对齐。可能的值为 FLOAT、DOUBLE、INTEGER 和 BOOLEAN。默认值为 FLOAT。

*quantityToPlot*

一个 SymbolicConstant，指定要绘制的数量。当前仅支持 FIELD_OUTPUT。可能的值为 FIELD_OUTPUT 和 DISCONTINUITIES。默认值为 FIELD_OUTPUT。

*averageElementOutput*

一个 Boolean，指定是否对单元输出求平均。默认值为 OFF。

*useRegionBoundaries*

一个 Boolean，指定求平均时是否使用区域边界。默认值为 OFF。

*regionBoundaries*

一个 SymbolicConstant，指定平均区域边界的类型。当前仅支持 NONE 和 ODB_REGIONS。可能的值为 NONE、ODB_REGIONS、ELEMENT_SET 和 DISPLAY_GROUPS。默认值为 NONE。

*includeFeatureBoundaries*

一个 Boolean，指定是否基于特征边为壳和膜包含额外的平均边界。默认值为 ON。

*featureAngle*

一个 Float，指定当 *includeFeatureBoundaries*=ON 时使用的特征角度。默认值为 20.0。

*averageOnlyDisplayed*

一个 Boolean，指定是否仅对显示的单元上的值求平均。默认值为 OFF。

*averagingThreshold*

一个 Float，指定节点平均阈值百分比。0 ≤ *averagingThreshold* ≤ 100。默认值为 75.0。

*computeOrder*

一个 SymbolicConstant，指定对感兴趣的场输出变量执行的计算顺序。可能的值为 EXTRAPOLATE_AVERAGE_COMPUTE、EXTRAPOLATE_COMPUTE_AVERAGE、EXTRAPOLATE_COMPUTE、EXTRAPOLATE_COMPUTE_DISCONTINUITIES 和 RAW_DATA。默认值为 EXTRAPOLATE_COMPUTE_AVERAGE。

*numericForm*

一个 SymbolicConstant，指定显示包含复数的结果时使用的数字形式。可能的值为 COMPLEX_MAGNITUDE、COMPLEX_PHASE、REAL、IMAGINARY 和 COMPLEX_MAG_AT_ANGLE。默认值为 REAL。

*complexAngle*

一个 Float，指定当 *numericForm=COMPLEX_MAG_AT_ANGLE* 时显示包含复数的结果的角度（度）。默认值为 0.0。

**返回值**

一个 OdbMeshRegionData 对象。

**异常**

TextException。

### 21.7.2 setValues(...)

此方法修改 OdbMeshRegionData 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [OdbMeshRegionData](pt01ch21pyo07.md#ker-odbmeshregiondata-odbmeshregiondata-pyc) 方法的参数相同。

**返回值**

无

**异常**

无。

### 21.7.3 成员

OdbMeshRegionData 对象具有以下成员：

*stepIndex*

一个 Int，指定步骤索引。可能的值为 0 ≤ *stepIndex* ≤ (*numSteps * 1)。默认值为 0。

*frameIndex*

一个 Int，指定指定步骤中的帧。有效值为 0 ≤ *frameIndex* ≤ (*numFramesInStep * 1)。默认值为 0。

*outputPosition*

一个 SymbolicConstant，指定获取数据的位置。数据只能从分析过程中写入输出数据库的位置获取。此位置应与场输出变量对齐。可能的值为：
- UNDEFINED_POSITION
- NODAL
- INTEGRATION_POINT
- ELEMENT_FACE
- ELEMENT_NODAL
- ELEMENT_CENTROID
- WHOLE_ELEMENT
- WHOLE_REGION
- WHOLE_PART_INSTANCE
- WHOLE_MODEL
- GENERAL_PARTICLE

默认值为 UNDEFINED_POSITION。

*dataType*

一个 SymbolicConstant，指定场输出变量的数据类型，应与变量对齐。当前仅支持 SCALAR。可能的值为：
- ENUMERATION
- BOOLEAN
- INTEGER
- SCALAR
- VECTOR
- QUATERNION_2D
- QUATERNION_3D
- TENSOR
- TENSOR_3D_FULL
- TENSOR_3D_PLANAR
- TENSOR_3D_SURFACE
- TENSOR_2D_PLANAR
- TENSOR_2D_SURFACE

默认值为 SCALAR。

*storageType*

一个 SymbolicConstant，指定场输出变量的存储类型，应与变量对齐。可能的值为 FLOAT、DOUBLE、INTEGER 和 BOOLEAN。默认值为 FLOAT。

*quantityToPlot*

一个 SymbolicConstant，指定要绘制的数量。当前仅支持 FIELD_OUTPUT。可能的值为 FIELD_OUTPUT 和 DISCONTINUITIES。默认值为 FIELD_OUTPUT。

*averageElementOutput*

一个 Boolean，指定是否对单元输出求平均。默认值为 OFF。

*useRegionBoundaries*

一个 Boolean，指定求平均时是否使用区域边界。默认值为 OFF。

*regionBoundaries*

一个 SymbolicConstant，指定平均区域边界的类型。当前仅支持 NONE 和 ODB_REGIONS。可能的值为 NONE、ODB_REGIONS、ELEMENT_SET 和 DISPLAY_GROUPS。默认值为 NONE。

*includeFeatureBoundaries*

一个 Boolean，指定是否基于特征边为壳和膜包含额外的平均边界。默认值为 ON。

*featureAngle*

一个 Float，指定当 *includeFeatureBoundaries*=ON 时使用的特征角度。默认值为 20.0。

*averageOnlyDisplayed*

一个 Boolean，指定是否仅对显示的单元上的值求平均。默认值为 OFF。

*averagingThreshold*

一个 Float，指定节点平均阈值百分比。0 ≤ *averagingThreshold* ≤ 100。默认值为 75.0。

*computeOrder*

一个 SymbolicConstant，指定对感兴趣的场输出变量执行的计算顺序。可能的值为 EXTRAPOLATE_AVERAGE_COMPUTE、EXTRAPOLATE_COMPUTE_AVERAGE、EXTRAPOLATE_COMPUTE、EXTRAPOLATE_COMPUTE_DISCONTINUITIES 和 RAW_DATA。默认值为 EXTRAPOLATE_COMPUTE_AVERAGE。

*numericForm*

一个 SymbolicConstant，指定显示包含复数的结果时使用的数字形式。可能的值为 COMPLEX_MAGNITUDE、COMPLEX_PHASE、REAL、IMAGINARY 和 COMPLEX_MAG_AT_ANGLE。默认值为 REAL。

*complexAngle*

一个 Float，指定当 *numericForm=COMPLEX_MAG_AT_ANGLE* 时显示包含复数的结果的角度（度）。默认值为 0.0。

*odbFileName*

一个 String，指定要读取作为源数据的输出数据库文件名（包括 .odb 扩展名）。如果该文件位于其他目录，此 String 也可以是输出数据库文件的完整路径。

*variableLabel*

一个 String，指定场输出变量。





