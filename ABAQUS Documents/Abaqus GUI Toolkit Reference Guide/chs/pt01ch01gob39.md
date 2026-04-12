# AFXNote





此类通过"Note:"或"Warning:"作为前缀来标记给定的消息字符串。
![](../graphics/gui-afxnote.png)

### AFXNote(p, message, opts=NOTE_INFORMATION, x=0, y=0)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父组件。 |
| message | String |  | 注释消息字符串。 |
| opts | Int | NOTE_INFORMATION | 选项和提示。 |
| x | Int | 0 | 起点X坐标。 |
| y | Int | 0 | 起点Y坐标。 |

### create()

创建注释。

从 FXComposite 重实现。

### detach()

分离注释的服务器资源。

从 FXComposite 重实现。

### disable()

禁用注释。

从 FXWindow 重实现。

### enable()

启用注释。

从 FXWindow 重实现。

### getText()

返回注释的消息字符串。

### setText(message)

设置注释的消息字符串。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| message | String |  | 消息。 |

### 全局标志

### **注释样式的标志。**

| **NOTE_INFORMATION** | 信息注释。 |
| --- | --- |
| **NOTE_WARNING** | 警告注释。 |


