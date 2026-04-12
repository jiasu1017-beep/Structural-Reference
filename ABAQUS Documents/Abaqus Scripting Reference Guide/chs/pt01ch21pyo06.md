# 21.6 MappedField 对象





MappedField 对象定义一个空间变化场，其值从外部源数据计算。

MappedField 对象派生自 [AnalyticalField](pt01ch21pyo02.md) 对象。

**访问**

```
import fields
mdb.models[*name*].analyticalFields[*name*]
```

### 21.6.1 MappedField(...)

此方法创建 MappedField 对象。

**路径**

```
mdb.models[*name*].MappedField
```

**必需参数**

*name*

一个 String，指定存储库键。

**可选参数**

*regionType*

一个 SymbolicConstant，指定数据源区域类型。可以是 ODB 网格或点云。可能的值为 MESH 和 POINT。默认值为 POINT。

*partLevelData*

一个 Boolean，指定点云源数据是否以部件级坐标描述。如果使用部件级坐标，则 *localCsys* 中定义的局部坐标系将被忽略。默认值为 OFF。

*pointDataFormat*

一个 SymbolicConstant，指定点云源数据格式。可能的值为 GRID 和 XYZ。默认值为 XYZ。

*gridPointPlane*

一个 SymbolicConstant，指定网格格式点云源数据所在的平面。可能的值为 XYPLANE、YZPLANE 和 XZPLANE。默认值为 XYPLANE。

*defaultUnmappedValue*

一个 Float，指定目标模型区域在无法从数据源计算值时的默认参数（场）值。默认值为 0.0。

*mappingAlgorithm*

一个 SymbolicConstant，指定目标表面或网格目标模型（当参数值位于节点上时，例如节点温度）的映射算法。可能的值为 SURFACE 和 VOLUMETRIC。默认值为 SURFACE。

*searchTolType*

一个 SymbolicConstant，指定搜索容差类型，可以是绝对值或目标模型区域中所有单元特征长度的平均值。可能的值为 ABSOLUTE 和 RELATIVE。默认值为 RELATIVE。

*boundarySearchTol*

一个 Float，指定目标模型区域外边界上的搜索距离容差。源点在此距离内将参与目标区域参数值的计算。此容差适用于表面和体积映射。默认值为 0.01。

*neighborhoodSearchTol*

一个 Float，指定用于距离加权算法的搜索距离容差。源点在此距离内将参与目标区域参数值的计算。此容差仅适用于表面映射。默认值为 1000000.0。

*negativeNormalSearchTol*

一个 Float，指定目标表面区域负法向的搜索距离容差。源点在此距离内将参与目标区域参数值的计算。此容差仅适用于表面映射。默认值为 0.15。

*positiveNormalSearchTol*

一个 Float，指定目标表面区域正法向的搜索距离容差。源点在此距离内将参与目标区域参数值的计算。此容差仅适用于表面映射。默认值为 0.05。

*scaleCoordinates*

一个 Boolean，指定是否缩放从点云或指定 ODB 提供用户提供的坐标值。默认值为 OFF。

*gridPointData*

一个 Float 序列的序列，指定网格格式的点云源数据。默认值为空序列。

*xyzPointData*

一个 Float 序列的序列，指定 XYZ 格式的点云源数据。每个数据项定义一个点的 XYZ 坐标及其场值。默认值为空序列。

*coordinateScalingFactors*

一个 Float 序列，指定全局 1、2 和 3 方向的缩放因子。默认值为 (1.0, 1.0, 1.0)。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定场的局部坐标系。如果 *localCsys*=`None`，则场在全局坐标系中定义。默认值为 `None`。

*description*

一个 String，指定场的描述。默认值为空字符串。

**返回值**

一个 MappedField 对象。

**异常**

AbaqusException。

### 21.6.2 setValues(...)

此方法修改 MappedField 对象。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [MappedField](pt01ch21pyo06.md#ker-mappedfield-mappedfield-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 21.6.3 成员

MappedField 对象可以具有以下成员：

*name*

一个 String，指定存储库键。

*regionType*

一个 SymbolicConstant，指定数据源区域类型。可以是 ODB 网格或点云。可能的值为 MESH 和 POINT。默认值为 POINT。

*partLevelData*

一个 Boolean，指定点云源数据是否以部件级坐标描述。如果使用部件级坐标，则 *localCsys* 中定义的局部坐标系将被忽略。默认值为 OFF。

*pointDataFormat*

一个 SymbolicConstant，指定点云源数据格式。可能的值为 GRID 和 XYZ。默认值为 XYZ。

*gridPointPlane*

一个 SymbolicConstant，指定网格格式点云源数据所在的平面。可能的值为 XYPLANE、YZPLANE 和 XZPLANE。默认值为 XYPLANE。

*defaultUnmappedValue*

一个 Float，指定目标模型区域在无法从数据源计算值时的默认参数（场）值。默认值为 0.0。

*mappingAlgorithm*

一个 SymbolicConstant，指定目标表面或网格目标模型（当参数值位于节点上时，例如节点温度）的映射算法。可能的值为 SURFACE 和 VOLUMETRIC。默认值为 SURFACE。

*searchTolType*

一个 SymbolicConstant，指定搜索容差类型，可以是绝对值或目标模型区域中所有单元特征长度的平均值。可能的值为 ABSOLUTE 和 RELATIVE。默认值为 RELATIVE。

*boundarySearchTol*

一个 Float，指定目标模型区域外边界上的搜索距离容差。源点在此距离内将参与目标区域参数值的计算。此容差适用于表面和体积映射。默认值为 0.01。

*neighborhoodSearchTol*

一个 Float，指定用于距离加权算法的搜索距离容差。源点在此距离内将参与目标区域参数值的计算。此容差仅适用于表面映射。默认值为 1000000.0。

*negativeNormalSearchTol*

一个 Float，指定目标表面区域负法向的搜索距离容差。源点在此距离内将参与目标区域参数值的计算。此容差仅适用于表面映射。默认值为 0.15。

*positiveNormalSearchTol*

一个 Float，指定目标表面区域正法向的搜索距离容差。源点在此距离内将参与目标区域参数值的计算。此容差仅适用于表面映射。默认值为 0.05。

*scaleCoordinates*

一个 Boolean，指定是否缩放从点云或指定 ODB 提供用户提供的坐标值。默认值为 OFF。

*gridPointData*

一个 Float 元组的元组，指定网格格式的点云源数据。默认值为空序列。

*xyzPointData*

一个 Float 元组的元组，指定 XYZ 格式的点云源数据。每个数据项定义一个点的 XYZ 坐标及其场值。默认值为空序列。

*odbMeshRegionData*

一个 [OdbMeshRegionData](pt01ch21pyo07.md) 对象，指定来自 ODB 网格区域的外部源数据。

*coordinateScalingFactors*

一个 Float 元组，指定全局 1、2 和 3 方向的缩放因子。默认值为 (1.0, 1.0, 1.0)。

*localCsys*

`None` 或一个 [DatumCsys](pt01ch15pyo03.md) 对象，指定场的局部坐标系。如果 *localCsys*=`None`，则场在全局坐标系中定义。默认值为 `None`。

*description*

一个 String，指定场的描述。默认值为空字符串。





