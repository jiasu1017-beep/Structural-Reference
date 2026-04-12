# 42.11 MaterialAssignment 对象

MaterialAssignment 对象存储初始材料分配预定义场的数据，用于欧拉分析。

MaterialAssignment 对象派生自 [PredefinedField](pt01ch42pyo01.md) 对象。

**访问**

```
import load
mdb.models[*name*].predefinedFields[*name*]
```

### 42.11.1 MaterialAssignment(...)

此方法创建 MaterialAssignment 预定义场对象。

**Path**

```
mdb.models[*name*].MaterialAssignment
```

**必需参数**

*name*

 String，指定存储库键。

*instanceList*

 [PartInstanceArray](pt01ch06pyo04.md) 对象，指定应用预定义场的零件实例。所有实例必须分配相同的欧拉截面。

**可选参数**

*useFields*

 Boolean，指定体积分数数据是均匀的还是由离散字段定义。默认值为 OFF。

*assignmentList*

元组序列，指定要分配的均匀体积分数。此参数仅在 *useFields*=FALSE 时有效。每个元组包含两个条目：
- [Region](pt01ch45pyo03.md) 对象。
- Float 元组，指定均匀体积分数值。元组的长度必须与分配给 *instanceList* 指定的零件实例的欧拉截面中指定的材料实例名称的数量匹配。

*fieldList*

元组序列，指定要分配的离散体积分数。此参数仅在 *useFields*=TRUE 时有效。每个元组包含两个条目：
- [Region](pt01ch45pyo03.md) 对象。
- String 元组，指定离散字段名称。元组的长度必须与分配给 *instanceList* 指定的零件实例的欧拉截面中指定的材料实例名称的数量匹配。

*colorList*

三个 Int 的序列，指定用于显示材料实例分配的颜色。这是 R,G,B 颜色序列，其中值用 0 到 255 之间的整数表示。默认值为空序列。

**返回值**

MaterialAssignment 对象。

**异常**

无。

### 42.11.2 setValues(...)

此方法修改 MaterialAssignment 对象。

**必需参数**

无。

**可选参数**

 `setValues` 的可选参数与 [MaterialAssignment](pt01ch42pyo11.md#ker-materialassignment-materialassignment-pyc) 方法的参数相同，但 *name* 参数除外。

**返回值**

无

**异常**

无。

### 42.11.3 成员

MaterialAssignment 对象的成员与 [MaterialAssignment](pt01ch42pyo11.md#ker-materialassignment-materialassignment-pyc) 方法的参数具有相同的名称和描述。

此外，MaterialAssignment 对象可以具有以下成员：

*region*

 [Region](pt01ch45pyo03.md) 对象，指定应用预定义场的区域。如果预定义场有可用的 *instances* 成员，则忽略 *Region*。如果预定义场有可用的 *distributionType* 成员，并且 *distributionType*=FROM_FILE 或 FROM_FILE_AND_USER_DEFINED，则也忽略 *Region*。

### 42.11.4 对应分析关键字

| [*INITIAL CONDITIONS*](../key/key-link.md#usb-kws-minitialcond), TYPE=EULERIAN MATERIAL |
| --- |

