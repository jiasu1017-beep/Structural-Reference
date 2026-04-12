# AFXBoolKeyword






该类专为具有布尔值的命令关键字设计。
![](../graphics/gui-afxboolkeyword.png)

### AFXBoolKeyword(command, name, booleanType=ON_OFF, isRequired=False, defaultValue=False)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| command | AFXCommand |  | 宿主命令。 |
| name | String |  | 关键字名称。 |
| booleanType | Type | ON_OFF | 命令中使用的布尔类型。 |
| isRequired | Bool | False | 如果该关键字是命令的必需参数，则为 True。 |
| defaultValue | Bool | False | 默认值。 |

### getTypeName()

返回关键字类型的名称。

实现 AFXKeyword。

### getValue()

返回关键字的当前值。

### getValueAsString()

返回表示关键字当前值的文本字符串。

实现 AFXKeyword。

### isValueChanged()

如果关键字值与其之前的值不同，则返回 True。

实现 AFXKeyword。

### setDefaultValue(defaultValue)

设置关键字的默认值。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| defaultValue | Bool |  | 默认值。 |

### setDefaultValueByString(defaultValueString)

设置关键字的默认值（如果给定的文本字符串有效则返回 True）。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| defaultValueString | String |  | 文本字符串形式的默认值。 |

### setDefaultValueByString(defaultValueString)

设置关键字的默认值（如果给定的文本字符串有效则返回 True）。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| defaultValueString | String |  | 文本字符串形式的默认值。 |

### setValue(newValue)

设置关键字的当前值。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| newValue | Bool |  | 新值。 |

### setValueByString(newValueString)

设置关键字的当前值（如果给定的文本字符串有效则返回 True）。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| newValueString | String |  | 文本字符串形式的新值。 |

### setValueByString(newValueString)

设置关键字的当前值（如果给定的文本字符串有效则返回 True）。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| newValueString | String |  | 文本字符串形式的新值。 |

### setValueToDefault(ignoreUnspecified=False)

将关键字值设置为其默认值。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| ignoreUnspecified | Bool | False | 未使用。 |

### setValueToPrevious()

将关键字值设置为其之前的值。

实现 AFXKeyword。

### syncPreviousValue()

将关键字之前的值设置为其当前值。

实现 AFXKeyword。

### 类标志

### **布尔类型的标志。**

| **ON_OFF** | 关键字值为 ON 或 OFF。 |
| --- | --- |
| **TRUE_FALSE** | 关键字值为 True 或 False。 |




