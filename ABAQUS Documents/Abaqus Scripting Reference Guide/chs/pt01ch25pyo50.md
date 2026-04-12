# 25.50 MasterSlaveAssignment 对象

MasterSlaveAssignment 对象存储 [ContactExp](pt01ch25pyo19.md) 和 [ContactStd](pt01ch25pyo24.md) 对象中表面的主-从分配定义。MasterSlaveAssignment 对象没有构造函数或成员。

**访问**

```
import interaction
mdb.models[*name*].interactions[*name*].masterSlaveAssignments
```

### 25.50.1 changeValuesInStep(...)

此方法允许修改已在给定步骤中表面表对上定义的主-从分配。

**必需参数**

*stepName*

字符串，指定要修改主-从分配的步骤名称。

*index*

整数，指定要修改其值的主-从分配的位置。

*value*

 SymbolicConstant，指定要分配给索引引用的表面的主-从角色值。可能的值为 MASTER、SLAVE 和 BALANCED。SymbolicConstant BALANCED 仅在 Abaqus/Standard 分析中可以指定。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.50.2 appendInStep(...)

此方法允许在给定步骤中向新表面表对添加主-从分配。

**必需参数**

*stepName*

字符串，指定要定义新主-从分配的步骤名称。

*assignments*

元组序列，指定主-从分配。每个元组包含两个条目：
- 指定主-从属性被分配的表面的区域对象或 SymbolicConstant GLOBAL。
- SymbolicConstant，指定要用于第一个表面的覆盖主-从值。 SymbolicConstants 的可能值为 MASTER、SLAVE 和 BALANCED。SymbolicConstant BALANCED 仅在 Abaqus/Standard 分析中可以指定。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.50.3 delete(...)

`delete` 方法允许您删除现有的主-从分配。

**必需参数**

*indices*

整数序列，指定要删除的每个主-从分配的索引。

**可选参数**

无。

**返回值**

无。

**异常**

无。

### 25.50.4 成员

MasterSlaveAssignment 对象没有成员。

### 25.50.5 对应的分析关键字

| [*CONTACT FORMULATION](../key/key-link.md#usb-kws-hcontformulation), TYPE=PURE MASTER-SLAVE |
| --- |
| [*CONTACT FORMULATION](../key/key-link.md#usb-kws-hcontformulation), TYPE=MASTER SLAVE ROLES |



