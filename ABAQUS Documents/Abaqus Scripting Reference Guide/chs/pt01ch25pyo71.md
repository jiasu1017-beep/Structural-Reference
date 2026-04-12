# 25.71 SurfaceFeatureAssignment 对象

SurfaceFeatureAssignment 对象存储 [ContactExp](pt01ch25pyo19.md) 或 [ContactStd](pt01ch25pyo24.md) 对象中表面的表面特征角度分配定义。SurfaceFeatureAssignment 对象没有构造函数或成员。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*].surfaceFeatureAssignments
```

### 25.71.1 changeValuesInStep(...)

此方法允许修改已在给定步骤中表面上定义的表面特征角度分配。

**必需参数**

*stepName*

字符串，指定要修改表面特征分配的步骤名称。

*index*

整数，指定要修改其值的表面特征角度分配的位置。

*value*

元组，指定索引引用的表面的表面特征分配值。每个元组包含一个条目：
- 浮点数或 SymbolicConstant，指定用于表面的覆盖表面特征角度值。 SymbolicConstants 的可能值为 PERIMETER、ALL、PICKED 或 NONE。ALL 和 PICKED 值不能与 GLOBAL 区域常量一起指定，只能在 Explicit 版本的一般接触中使用。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.71.2 appendInStep(...)

此方法允许在给定步骤中向新表面添加表面特征角度分配。

**必需参数**

*stepName*

字符串，指定要定义新表面特征角度分配的步骤名称。

*assignments*

元组序列，指定表面特征角度分配。每个元组包含两个条目：
- 指定特征角度被分配的表面的区域对象或 SymbolicConstant GLOBAL。
- 浮点数或 SymbolicConstant，指定用于表面的覆盖表面特征角度值。 SymbolicConstants 的可能值为 PERIMETER、ALL、PICKED 或 NONE。ALL 和 PICKED 值不能与 GLOBAL 区域常量一起指定，只能在 Explicit 版本的一般接触中使用。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.71.3 delete(...)

`delete` 方法允许您从 [ContactExp](pt01ch25pyo19.md) 对象中删除现有的表面特征角度分配。

**必需参数**

*indices*

整数序列，指定要删除的每个表面特征角度分配的索引。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.71.4 成员

SurfaceFeatureAssignment 对象没有成员。

### 25.71.5 对应的分析关键字

| [*SURFACE PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hsurfpropassign), PROPERTY=FEATURE EDGE CRITERIA |
| --- |



