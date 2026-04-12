# AFXStringKeyword





此类专为具有文本字符串值的命令关键字设计。
![](../graphics/gui-afxstringkeyword.png)

### AFXStringKeyword(command, name, isRequired=False, defaultValue='')

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| command | AFXCommand |  | 宿主命令。 |
| name | String |  | 关键字名称。 |
| isRequired | Bool | False | 如果关键字是命令的必需参数，则为 True。 |
| defaultValue | String | '' | 默认值。 |

### getTypeName()

返回关键字类型的名称。

实现 AFXKeyword。

### getValue()

返回关键字的当前值。

### getValueAsString()

返回表示关键字当前值的文本字符串。

实现 AFXKeyword。

### isValueChanged()

如果关键字值与其之前的值不同则返回 True。

实现 AFXKeyword。

### setDefaultValue(defaultValue)

设置关键字的默认值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| defaultValue | String |  | 默认值。 |

### setValue(newValue)

设置关键字的当前值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| newValue | String |  | 新值。 |

### setValueToDefault(ignoreUnspecified=False)

将关键字值设置为其默认值。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| ignoreUnspecified | Bool | False | 如果默认值未指定，则忽略设置值。 |

### setValueToPrevious()

将关键字值设置为其之前的值。

实现 AFXKeyword。

### syncPreviousValue()

将关键字的之前的值设置为其当前值。

实现 AFXKeyword。





