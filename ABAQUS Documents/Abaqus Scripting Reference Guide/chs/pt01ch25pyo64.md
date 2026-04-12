# 25.64 SmoothingAssignment 对象

SmoothingAssignment 对象存储 [ContactExp](pt01ch25pyo19.md) 和 [ContactStd](pt01ch25pyo24.md) 对象中表面的表面平滑分配定义。SmoothingAssignment 对象没有构造函数或成员。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*].smoothingAssignments
```

### 25.64.1 changeValuesInStep(...)

此方法允许修改已在给定步骤中表面上定义的表面平滑分配。

**必需参数**

*stepName*

字符串，指定要修改表面平滑分配的步骤名称。

*index*

整数，指定要修改其值的表面平滑分配的位置。

*value*

元组，指定索引引用的表面的表面平滑分配值。每个元组包含一个条目：
- SymbolicConstant，指定用于表面的表面平滑值。 SymbolicConstants 的可能值为 NONE、REVOLUTION、SPHERICAL 和 TOROIDAL。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.64.2 appendInStep(...)

此方法允许在给定步骤中向新表面添加表面平滑分配。

**必需参数**

*stepName*

字符串，指定要定义新表面平滑分配的步骤名称。

*assignments*

元组序列，指定表面平滑分配。每个元组包含两个条目：
- 指定平滑被分配的表面的区域对象。
- SymbolicConstant，指定用于表面的表面平滑值。 SymbolicConstants 的可能值为 NONE、REVOLUTION、SPHERICAL 和 TOROIDAL。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.64.3 delete(...)

`delete` 方法允许您从 [ContactExp](pt01ch25pyo19.md) 和 [ContactStd](pt01ch25pyo24.md) 对象中删除现有的表面平滑分配。

**必需参数**

*indices*

整数序列，指定要删除的每个表面平滑分配的索引。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.64.4 成员

SmoothingAssignment 对象没有成员。

### 25.64.5 对应的分析关键字

| [*SURFACE PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hsurfpropassign), PROPERTY=GEOMETRIC CORRECTION |
| --- |



