# 25.22 ContactPropertyAssignment 对象

ContactPropertyAssignment 对象存储 [ContactExp](pt01ch25pyo19.md) 和 [ContactStd](pt01ch25pyo24.md) 对象中域对的接触属性分配定义。ContactPropertyAssignment 对象没有构造函数或成员。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*].contactPropertyAssignments
```

### 25.22.1 changeValuesInStep(...)

此方法允许修改已在给定步骤中定义的域对的接触属性分配。

**必需参数**

*stepName*

String，指定要修改接触属性分配的步骤名称。

*index*

Int，指定要修改其值的接触属性分配的位置。

*value*

String，指定要分配给索引引用的域对的接触属性值。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.22.2 appendInStep(...)

此方法允许在给定步骤中添加新域对的接触属性分配。

**必需参数**

*stepName*

String，指定要定义新接触属性分配的步骤名称。

*assignments*

元组序列，指定分配给每个表面对的属性。每个元组包含三个条目：
- 区域对象或 SymbolicConstant GLOBAL。
- 区域对象或 SymbolicConstant SELF。当与 [ContactExp](pt01ch25pyo19.md) 对象一起使用时，此参数也可以是引用欧拉材料表面的字符串。
- String，指定与这对区域关联的 [ContactProperty](pt01ch25pyo21.md) 对象。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.22.3 delete(...)

`delete` 方法允许您删除现有的接触属性分配。

**必需参数**

*indices*

Int 序列，指定要删除的每个接触属性分配的索引。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.22.4 成员

ContactPropertyAssignment 对象没有成员。

### 25.22.5 对应的分析关键字

| [*CONTACT PROPERTY ASSIGNMENT](../key/key-link.md#usb-kws-hcontpropassign) |
| --- |
