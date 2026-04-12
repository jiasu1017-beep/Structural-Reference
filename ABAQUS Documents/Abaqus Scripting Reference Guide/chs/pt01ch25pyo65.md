# 25.65 StabilizationAssignment 对象

StabilizationAssignment 对象存储 [ContactStd](pt01ch25pyo24.md) 对象中域对的接触稳定化分配定义。StabilizationAssignment 对象没有构造函数或成员。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*].stabilizationAssignments
```

### 25.65.1 changeValuesInStep(...)

此方法允许修改已在给定步骤中定义的域对的接触稳定化分配。

**必需参数**

*stepName*

字符串，指定要修改接触稳定化分配的步骤名称。

*index*

整数，指定要修改其值的接触稳定化分配的位置。

*value*

字符串，指定要分配给索引引用的域对的接触稳定化的值。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.65.2 appendInStep(...)

此方法允许在给定步骤中向新域对添加接触稳定化分配。

**必需参数**

*stepName*

字符串，指定要定义新接触稳定化分配的步骤名称。

*assignments*

元组序列，指定每个表面对的稳定化。每个元组包含三个条目：
- 区域对象或 SymbolicConstant GLOBAL。
- 区域对象或 SymbolicConstant SELF。
- 字符串，指定与此域对关联的 [StdStabilization](pt01ch25pyo68.md) 对象。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.65.3 delete(...)

`delete` 方法允许您从 [ContactStd](pt01ch25pyo24.md) 对象中删除现有的接触稳定化分配。

**必需参数**

*indices*

整数序列，指定要删除的每个接触稳定化分配的索引。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.65.4 成员

StabilizationAssignment 对象没有成员。

### 25.65.5 对应的分析关键字

| [*CONTACT STABILIZATION](../key/key-link.md#usb-kws-hcontactstab) |
| --- |



