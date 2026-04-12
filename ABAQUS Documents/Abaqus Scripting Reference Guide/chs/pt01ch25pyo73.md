# 25.73 SurfaceThicknessAssignment 对象

SurfaceThicknessAssignment 对象存储 [ContactExp](pt01ch25pyo19.md) 和 [ContactStd](pt01ch25pyo24.md) 对象中表面的表面厚度分配定义。SurfaceThicknessAssignment 对象没有构造函数或成员。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*].surfaceThicknessAssignments
```

### 25.73.1 changeValuesInStep(...)

此方法允许修改已在给定步骤中表面上定义的表面厚度分配。

**必需参数**

*stepName*

字符串，指定要修改表面厚度分配的步骤名称。

*index*

整数，指定要修改其值的表面厚度分配的位置。

*value*

元组，指定索引引用的表面的表面厚度分配值。每个元组包含两个条目：
- 浮点数或 SymbolicConstant，指定在接触定义中使用的覆盖厚度值。 SymbolicConstants 的可能值为 ORIGINAL 和 THINNING。SymbolicConstant THINNING 仅在 Abaqus/Explicit 分析中可以指定。
- 浮点数，指定乘以第二条目中指定厚度值的比例因子。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.73.2 appendInStep(...)

此方法允许在给定步骤中向新表面添加表面厚度分配。

**必需参数**

*stepName*

字符串，指定要定义新表面厚度分配的步骤名称。

*assignments*

元组序列，指定表面厚度分配。每个元组包含三个条目：
- 指定厚度被分配的表面的区域对象或 SymbolicConstant GLOBAL。
- 浮点数或 SymbolicConstant，指定在接触定义中使用的覆盖厚度值。 SymbolicConstants 的可能值为 ORIGINAL 和 THINNING。SymbolicConstant THINNING 仅在 Abaqus/Explicit 分析中可以指定。
- 浮点数，指定乘以第二条目中指定厚度值的比例因子。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.73.3 delete(...)

`delete` 方法允许您删除现有的表面厚度分配。

**必需参数**

*indices*

整数序列，指定要删除的每个表面厚度分配的索引。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.73.4 成员

SurfaceThicknessAssignment 对象没有成员。

### 25.73.5 对应的分析关键字

| [*SURFACE PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hsurfpropassign), PROPERTY=THICKNESS |
| --- |



