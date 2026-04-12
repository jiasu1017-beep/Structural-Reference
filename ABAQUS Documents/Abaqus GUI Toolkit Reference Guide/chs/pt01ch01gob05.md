# AFXColumnItems






该类将 AFXTable 单列中的选定项目连接到关键字（通常是元组关键字）。
![](../graphics/gui-afxcolumnitems.png)

### AFXColumnItems(table, referenceColumn, opts=0)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| table | AFXTable |  | 要使用的表格。 |
| referenceColumn | Int |  | 参考列的索引。 |
| opts | Int | 0 | 选择选项（未使用）。 |

### AFXColumnItems(referenceColumn, tgt=None, sel=0, opts=0)

用于关键字的构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| referenceColumn | Int |  | 参考列的索引。 |
| tgt | FXObject | None | 消息目标。 |
| sel | Int | 0 | 消息 ID。 |
| opts | Int | 0 | 选择选项（未使用）。 |

### getReferenceColumn()

返回表格参考列的索引。

### getSelector()

返回消息 ID。

### getTarget()

返回消息目标。

### setReferenceColumn(index)

设置表格参考列，其选定项目将被发送到目标。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 表格列索引。 |

### setSelector(sel)

设置消息 ID。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| sel | Int |  | 新消息 ID。 |

### setTarget(tgt)

设置消息目标。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| tgt | FXObject |  | 新消息目标。 |

### 类标志

### **消息 ID。**

| **ID_TABLE** | 表格 ID。 |
| --- | --- |




