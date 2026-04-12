# 9.27 FluidCavityPressureBC 对象

FluidCavityPressureBC 对象存储流体腔压力边界条件的数据。

FluidCavityPressureBC 对象派生自 [BoundaryCondition](pt01ch09pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].boundaryConditions[*name*]
```

### 9.27.1 FluidCavityPressureBC(...)

此方法创建 FluidCavityPressureBC 对象。

**路径**

```
mdb.models[*name*].FluidCavityPressureBC
```

**必需参数**

*name*

String，指定边界条件存储库密钥。

*createStepName*

String，指定创建边界条件的步骤名称。

*fluidCavity*

String，指定流体腔交互的名称。

**可选参数**

*magnitude*

Float，指定流体腔压力大小。默认值为 0。

*amplitude*

String 或 SymbolicConstant UNSET，指定幅值引用的名称。如果边界条件没有幅值引用，应使用 UNSET。默认值为 UNSET。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

*fixed*

Boolean，指定边界条件是否应在步骤开始时保持在当前值。默认值为 OFF。

**返回值**

FluidCavityPressureBC 对象。

**异常**

无。

### 9.27.2 setValues(...)

此方法修改创建该对象的步骤中现有 FluidCavityPressureBC 对象的数据。

**必需参数**

无。

**可选参数**

`setValues` 的可选参数与 [FluidCavityPressureBC](pt01ch09pyo27.md#ker-fluidcavitypressurebc-fluidcavitypressurebc-pyc) 方法的参数相同，但 *name* 和 *createStepName* 参数除外。

**返回值**

无。

**异常**

无。

### 9.27.3 setValuesInStep(...)

此方法修改指定步骤中现有 FluidCavityPressureBC 对象的传播数据。

**必需参数**

*stepName*

String，指定修改边界条件的步骤名称。

**可选参数**

*magnitude*

Float 或 SymbolicConstant FREED，指定流体腔压力大小。

*amplitude*

String 或 SymbolicConstant，指定幅值引用的名称。SymbolicConstant 的可能值为 UNCHANGED 和 FREED。如果幅值从前一个分析步骤传播，应使用 UNCHANGED。如果边界条件更改为没有幅值引用，应使用 FREED。仅当该参数对指定步骤有效时，才应提供 *amplitude* 参数。

**返回值**

无。

**异常**

无。

### 9.27.4 成员

FluidCavityPressureBC 对象可以具有以下成员：

*name*

String，指定边界条件存储库密钥。

*fluidCavity*

String，指定流体腔交互的名称。

*category*

SymbolicConstant，指定边界条件的类别。可能的值为 MECHANICAL 和 THERMAL。

*region*

[Region](pt01ch45pyo03.md) 对象，指定边界条件所应用到的区域。

*localCsys*

`None` 或 [DatumCsys](pt01ch15pyo03.md) 对象，指定边界条件自由度的局部坐标系。如果 *localCsys*=`None`，则自由度在全局坐标系中定义。默认值为 `None`。
