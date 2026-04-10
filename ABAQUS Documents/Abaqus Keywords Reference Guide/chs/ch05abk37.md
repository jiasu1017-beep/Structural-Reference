# *EXTREME VALUE









### *EXTREME VALUE定义要监控的单元和节点变量。

此选项与[*EXTREME ELEMENT VALUE](ch05abk35.md)和/或[*EXTREME NODE VALUE](ch05abk36.md)选项结合使用，以指示要在当前步骤中监控节点和单元变量并与用户指定值进行比较。对于使用这些选项指定的每个变量，在分析过程中达到的最大值、最小值或绝对最大值以及相关的单元或节点编号将在步骤结束时写入状态（`.sta`）文件。在新步骤中使用不带[*EXTREME ELEMENT VALUE](ch05abk35.md)或[*EXTREME NODE VALUE](ch05abk36.md)选项且不带任何参数的[*EXTREME VALUE](ch05abk37.md)选项来停止监控变量。

**产品：**Abaqus/Explicit

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["显式动态分析，" Abaqus分析用户指南第6.3.3节](../usb/usb-link.md#usb-anl-aexpdynamic)
- [*EXTREME ELEMENT VALUE](ch05abk35.md)
- [*EXTREME NODE VALUE](ch05abk36.md)

### **可选参数：**

HALT

如果即使变量已超过用户指定的边界，分析仍应继续，则设置 HALT=NO（默认）。

设置 HALT=YES 以在变量首次超过其用户指定边界时停止分析。分析将在发生这种情况的增量之后的增量中停止。

**此选项没有关联的数据行。**



