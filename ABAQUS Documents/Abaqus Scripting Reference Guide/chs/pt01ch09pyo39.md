# 9.39 SecondaryBaseBC 对象

SecondaryBaseBC 对象存储次级基准边界条件的数据。

SecondaryBaseBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.39.1 SecondaryBaseBC(...)

此方法创建 SecondaryBaseBC 对象。

**路径**

```
mdb.models[*name*].SecondaryBaseBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*regions*

[RegionArray](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。请注意，常规 *region* 被忽略。默认值为 MODEL。

*dofs*

Int 的序列的序列，指定要约束的自由度。

**可选参数**

无。

**返回值**

SecondaryBaseBC 对象。

**异常**

无。

### 9.39.2 setValues(...)

此方法修改创建该对象的步骤中现有 SecondaryBaseBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [SecondaryBaseBC](pt01ch09pyo39.md#ker-secondarybasebc-secondarybasebc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.39.3 setValuesInStep(...)

此方法修改指定步骤中现有 SecondaryBaseBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 9.39.4 成员

SecondaryBaseBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*dofs*

Int 的元组的元组，指定要约束的自由度。

*regions*

[RegionArray](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。请注意，常规 *region* 被忽略。默认值为 MODEL。

*category*

SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
