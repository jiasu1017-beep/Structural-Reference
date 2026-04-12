# 9.38 RetainedNodalDofsBC 对象

RetainedNodalDofsBC 对象存储保留节点自由度边界条件的数据。

RetainedNodalDofsBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.38.1 RetainedNodalDofsBC(...)

此方法创建 RetainedNodalDofsBC 对象。

**路径**

```
mdb.models[*name*].RetainedNodalDofsBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

**可选参数**

*u1*

Boolean，指定是否保留 1 方向上的自由度。默认值为 OFF，表示不保留该自由度。

*u2*

Boolean，指定是否保留 2 方向上的自由度。默认值为 OFF，表示不保留该自由度。

*u3*

Boolean，指定是否保留 3 方向上的自由度。默认值为 OFF，表示不保留该自由度。

*ur1*

Boolean，指定是否保留关于 1 方向的旋转自由度。默认值为 OFF，表示不保留该自由度。

*ur2*

Boolean，指定是否保留关于 2 方向的旋转自由度。默认值为 OFF，表示不保留该自由度。

*ur3*

Boolean，指定是否保留关于 3 方向的旋转自由度。默认值为 OFF，表示不保留该自由度。

**返回值**

RetainedNodalDofsBC 对象。

**异常**

无。

### 9.38.2 setValues(...)

此方法修改创建该对象的步骤中现有 RetainedNodalDofsBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [RetainedNodalDofsBC](pt01ch09pyo38.md#ker-retainednodaldofsbc-retainednodaldofsbc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.38.3 setValuesInStep(...)

此方法修改指定步骤中现有 RetainedNodalDofsBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*u1*

Boolean，指定是否保留 1 方向上的自由度。

*u2*

Boolean，指定是否保留 2 方向上的自由度。

*u3*

Boolean，指定是否保留 3 方向上的自由度。

*ur1*

Boolean，指定是否保留关于 1 方向的旋转自由度。

*ur2*

Boolean，指定是否保留关于 2 方向的旋转自由度。

*ur3*

Boolean，指定是否保留关于 3 方向的旋转自由度。

**返回值**

无。

**异常**

无。

### 9.38.4 成员

RetainedNodalDofsBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*category*

SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
