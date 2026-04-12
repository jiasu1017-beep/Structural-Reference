# AFXNote





此类通过"Note:"或"Warning:"为给定的消息字符串添加前缀。
![](../graphics/gui-afxnote.png)

### AFXNote(p, message, opts=NOTE_INFORMATION, x=0, y=0)

构造函数。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| p | FXComposite |  | 父窗口部件。 |
| message | String |  | 笔记消息字符串。 |
| opts | Int | NOTE_INFORMATION | 选项和提示。 |
| x | Int | 0 | 原点的 X 坐标。 |
| y | Int | 0 | 原点的 Y 坐标。 |

### create()

创建笔记。

从 FXComposite 重新实现。

### detach()

分离笔记的服务器资源。

从 FXComposite 重新实现。

### disable()

禁用笔记。

从 FXWindow 重新实现。

### enable()

启用笔记。

从 FXWindow 重新实现。

### getText()

返回笔记的消息字符串。

### setText(message)

设置笔记的消息字符串。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| message | String |  | 消息。 |

### 全局标志

### **笔记样式的标志。**

| **NOTE_INFORMATION** | 信息笔记。 |
| --- | --- |
| **NOTE_WARNING** | 警告笔记。 |



