# 9.41 SubmodelBC 对象

SubmodelBC 对象存储子模型边界条件的数据。

SubmodelBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.41.1 SubmodelBC(...)

此方法创建 SubmodelBC 对象。

**路径**

```
mdb.models[*name*].SubmodelBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*dof*

Int 的序列，指定边界条件所应用到的自由度。

*globalStep*

String，指定全局模型中的步骤，Abaqus 从该步骤读取将驱动子模型分析的变量值。String 表示分析步骤序列中的位置。例如，*globalStep*='1' 表示第一个步骤。

*timeScale*

Boolean，指定是否缩放驱动节点幅值函数的时间变量以匹配子模型分析步骤时间。默认值为 OFF。

*shellThickness*

Float，指定全局模型中壳的厚度。此参数对于壳到实体子模型是必需的，且不适用于其他子模型。默认值为 0.0。

**可选参数**

*globalDrivingRegion*

String，指定全局模型中将被搜索的元素集，其响应将用于驱动子模型。空字符串表示将搜索整个全局模型。默认值为空字符串。

*absoluteExteriorTolerance*

`None` 或 Float，指定子模型的驱动节点可以位于全局模型元素区域外部的绝对值。默认值为 `None`。

*exteriorTolerance*

`None` 或 Float，指定子模型的驱动节点可以位于全局模型元素区域外部的平均元素大小的分数。默认值为 0.05。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。

*globalIncrement*

Int，指定全局模型步骤中的增量号，其解将用于指定驱动变量的值。如果 *globalIncrement*=0，则使用最后一步的解。*globalIncrement* 参数仅适用于线性扰动步骤。默认值为 0。

*centerZoneSize*

Float，指定壳中面周围中心区域厚度。默认值为 `None`。

**返回值**

SubmodelBC 对象。

**异常**

无。

### 9.41.2 setValues(...)

此方法修改创建该对象的步骤中现有 SubmodelBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SubmodelBC](pt01ch09pyo41.md#ker-submodelbc-submodelbc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.41.3 setValuesInStep(...)

此方法修改指定步骤中现有 SubmodelBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*fixed*

Boolean，指定边界条件是否应在步骤开始时保持在当前值。默认值为 ON。

*dof*

Int 的序列，指定边界条件所应用到的自由度。*dof* 参数仅在 *fixed*=OFF 时适用。

*globalStep*

String，指定全局模型中的步骤，Abaqus 从该步骤读取将驱动子模型分析的变量值。String 表示分析步骤序列中的位置。例如，*globalStep*='1' 表示第一个步骤。*globalStep* 参数仅在 *fixed*=OFF 时适用。

*globalIncrement*

Int，指定全局模型步骤中其解将用于指定驱动变量的值的增量号。如果 *globalIncrement*=0，则使用最后一步的解。*globalIncrement* 参数仅适用于线性扰动步骤，且仅在 *fixed*=OFF 时适用。默认值为 0。

*centerZoneSize*

Float，指定壳中面周围中心区域厚度。默认值为 `None`。

*centerZoneSize* 参数仅在 *fixed*=OFF 时适用。

**返回值**

无。

**异常**

无。

### 9.41.4 成员

SubmodelBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*shellThickness*

Float，指定全局模型中壳的厚度。此参数对于壳到实体子模型是必需的，且不适用于其他子模型。默认值为 0.0。

*absoluteExteriorTolerance*

`None` 或 Float，指定子模型的驱动节点可以位于全局模型元素区域外部的绝对值。默认值为 `None`。

*exteriorTolerance*

`None` 或 Float，指定子模型的驱动节点可以位于全局模型元素区域外部的平均元素大小的分数。默认值为 0.05。

*globalDrivingRegion*

String，指定全局模型中将被搜索的元素集，其响应将用于驱动子模型。空字符串表示将搜索整个全局