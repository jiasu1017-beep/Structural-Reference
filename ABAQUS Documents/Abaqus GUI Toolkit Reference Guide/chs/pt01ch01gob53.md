# AFXTableKeyword





此类专为具有表值的命令关键字而设计。
![](../graphics/gui-afxtablekeyword.png)

### AFXTableKeyword(command, name, isRequired=False, minLength=0, maxLength=-1, opts=0)

构造函数。
| **参数** | **类型** | **默认值** | **描述** |
| --- | --- | --- | --- |
| command | AFXGuiCommand |  | 宿主命令。 |
| name | String |  | 关键字名称。 |
| isRequired | Bool | False | 如果此关键字是必需参数，则为 True。 |
| minLength | Int | 0 | 最小（和默认）行长度。 |
| maxLength | Int | -1 | 最大行长度（-1 表示无限制）。 |
| opts | Int | 0 | 选项。 |

### getTypeName()

返回表关键字类型的名称。

从 AFXComTableKeyword 重新实现。





