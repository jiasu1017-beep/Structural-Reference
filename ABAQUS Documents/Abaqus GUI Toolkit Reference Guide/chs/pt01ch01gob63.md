# AFXTupleKeyword





此类管理在命令中作为元组发送的值。

用于编辑整个元组的 widget 应将其消息 ID 设置为 0。也可以编辑元组的各个元素。要编辑第 N 个元组元素，widget 的消息 ID 应设置为 N（N 从 1 开始）。
![](../graphics/gui-afxtuplekeyword.png)

### AFXTupleKeyword(command, name, isRequired=False, minLength=0, maxLength=-1, opts=0)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| command | AFXCommand |  | 宿主命令。 |
| name | String |  | 关键字名称。 |
| isRequired | Bool | False | 如果此关键字是必需参数，则为 True。 |
| minLength | Int | 0 | 最小（和默认）元组长度。 |
| maxLength | Int | -1 | 最大元组长度（-1 表示无限制）。 |
| opts | Int | 0 | 选项。 |

### equal(index, a, b)

如果两个元组元素值比较相等则返回 True（index 未使用）。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引（未使用）。 |
| a | String |  | 第一个值。 |
| b | String |  | 第二个值。 |

### getDefaultStyle()

返回元素的默认样式。

### getDefaultType()

返回元素的默认类型。

### getDefaultValues()

返回此元组的默认值。

### getElementStyle(index)

返回一个元素的样式。永远不会返回 AFXTUPLE_STYLE_DEFAULT！
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |

### getElementType(index)

返回一个元素的类型。永远不会返回 AFXTUPLE_TYPE_DEFAULT！
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |

### getFormattedValue(index)

返回适合放在命令中的元组元素的格式化值。如果元素具有 AFXTUPLE_EVALUATE 样式且其内容无效，则将抛出异常。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |

### getLength()

返回元组的长度。

### getMaxLength()

返回此元组的最大长度，或 -1 表示无界长度。

### getMinLength()

返回元组的最小长度。

### getTypeName()

返回元组关键字类型的名称。

实现 AFXKeyword。

### getValue(index)

返回元组元素的值。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |

### getValueAsDouble()

以浮点数返回关键字的值；失败时返回 False。

### getValueAsInt()

以整数返回关键字的值；失败时返回 False。

### getValueAsString()

返回表示命令中当前关键字值的格式化字符串。

实现 AFXKeyword。

### getValueForBlank(index)

返回用于空元组元素的替换值。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |

### getValues()

返回包含元组元素值（用逗号分隔）的字符串。

### getValuesForBlanks()

返回包含元组元素空值替换值的字符串。

### insertElements(index, numCols)

从给定索引开始插入元素。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 起始索引。 |
| numCols | Int |  | 要插入的元素数。 |

### isValueChanged()

如果关键字值与其先前的值不同，则返回 True。

实现 AFXKeyword。

### removeElements(index, numCols)

从给定索引开始移除元素。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 起始索引。 |
| numCols | Int |  | 要移除的元素数。 |

### setDefaultStyle(style)

设置元素的默认样式。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| style | Int |  | 新的默认元素样式。 |

### setDefaultType(type)

设置元素的默认类型。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| type | Int |  | 新的默认类型。 |

### setDefaultValues(values)

设置此元组的默认值。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| values | String |  | 带默认值的序列字符串。 |

### setElementStyle(index, style)

设置一个元素的样式。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |
| style | Int |  | 新的元素样式。 |

### setElementType(index, type)

设置一个元素的类型。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |
| type | Int |  | 新的元素类型。 |

### setLengthRange(minLength, maxLength)

设置允许的元组长度范围。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| minLength | Int |  | 新的最小长度。 |
| maxLength | Int |  | 新的最大长度，或 -1 表示无界长度。 |

### setMaxLength(length)

设置此元组的最大长度。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| length | Int |  | 新的最大长度，或 -1 表示无界长度。 |

### setMinLength(length)

设置此元组的最小长度。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| length | Int |  | 新的最小长度。 |

### setValue(index, value)

设置元组元素的值；失败时返回 False。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |
| value | String |  | 新值。 |

### setValueForBlank(index, value)

设置用于空元组元素的替换值。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| index | Int |  | 元素索引。 |
| value | String |  | 新值。 |

### setValues(values)

设置所有元组元素的值（使用逗号分隔字符串中的值）。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| values | String |  | 带新值的元组字符串。 |

### setValuesForBlanks(values)

设置用于元组元素空值的替换值。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| values | String |  | 带值的元组字符串。 |

### setValueToDefault(ignoreUnspecified=False)

将关键字值设置为其默认值。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| ignoreUnspecified | Bool | False | 如果默认值为 unspecified，是否忽略。 |

### setValueToPrevious()

将关键字值设置为其先前的值。

实现 AFXKeyword。

### syncPreviousValue()

将关键字的先前值设置为其当前值。

实现 AFXKeyword。

### 类标志

### **消息 ID。**

| **ID_PRINTSNIPPET** | 用于调试。 |
| --- | --- |

### 全局标志

### **元组关键字选项的标志。**

| **AFXTUPLE_TYPE_ANY** | 接受任何类型。 |
| --- | --- |
| **AFXTUPLE_TYPE_DEFAULT** | 元素类型与元组默认类型相同。 |
| **AFXTUPLE_TYPE_INT** | 元素是整数。 |
| **AFXTUPLE_TYPE_FLOAT** | 元素是浮点数。 |
| **AFXTUPLE_TYPE_STRING** | 元素是字符串。 |
| **AFXTUPLE_TYPE_BOOL** | 元素是 True 或 False。 |
| **AFXTUPLE_TYPE_MASK** | 元素类型的掩码。 |
| **AFXTUPLE_ALLOW_EMPTY** | 允许元素为空值。 |
| **AFXTUPLE_DEFAULT_IF_EMPTY** | 始终用默认值替换空值。 |
| **AFXTUPLE_EVALUATE** | 求值整数和浮点元素。 |
| **AFXTUPLE_STYLE_DEFAULT** | 使用元组默认元素样式。 |
| **AFXTUPLE_STYLE_MASK** | 元素样式的掩码。 |





