# AFXMode





此类是模式的基类。
![](../graphics/gui-afxmode.png)

### AFXMode()

构造函数。

### getCommand(index)

返回给定索引处的命令（如果索引越界则返回 0）。
| **参数** | **类型** | **默认值** | **说明** |
| --- | --- | --- | --- |
| index | Int |  | 命令索引（从零开始）。 |

### getNumCommands()

返回与模式关联的命令数量。

### isActive()

如果模式处于活动状态则返回 True。

### 类标志

### **消息ID。**

| **ID_ACTIVATE** | 激活模式。 |
| --- | --- |
| **ID_COMMIT** | 提交模式。 |
| **ID_CANCEL** | 取消模式。 |
| **ID_DEACTIVATE** | 停用模式。 |
| **ID_GET_NEXT** | 获取下一步/对话框。 |
| **ID_RESUME** | 恢复模式。 |
| **ID_SET_DEFAULTS** | 设置默认值。 |
| **ID_SUSPEND** | 暂停模式。 |
| **ID_CMD_ACTIVATED** | 指示命令被激活。 |
| **ID_CMD_DEACTIVATED** | 指示命令被停用。 |
| **ID_CMD_MODIFIED** | 指示命令被修改。 |


