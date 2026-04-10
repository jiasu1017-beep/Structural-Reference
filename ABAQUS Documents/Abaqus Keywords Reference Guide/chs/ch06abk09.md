# *FILE OUTPUT









### *FILE OUTPUT定义写入结果文件的输出。

**警告：**此选项可能创建非常大的文件。

[*FILE OUTPUT](ch06abk09.md)选项提供节点、单元或全局数据到所选结果文件的输出。[*EL FILE](ch05abk01.md)、[*ENERGY FILE](ch05abk22.md)和/或[*NODE FILE](ch14abk10.md)选项必须与[*FILE OUTPUT](ch06abk09.md)选项结合使用。

**产品：**Abaqus/Explicit  Abaqus/CAE

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**不支持；Abaqus/CAE仅从输出数据库文件读取输出。

##### **参考：**

- ["输出到数据和结果文件，" Abaqus分析用户指南第4.1.2节](../usb/usb-link.md#usb-out-oprintfile)
- [*EL FILE](ch05abk01.md)
- [*ENERGY FILE](ch05abk22.md)
- [*NODE FILE](ch14abk10.md)

### **必需参数：**

NUMBER INTERVAL

将此参数设置为步骤中间隔的编号，在这些间隔时写入文件输出状态。Abaqus/Explicit始终在步骤开始时写入结果。例如，如果NUMBER INTERVAL=10，Abaqus/Explicit将写入11个结果状态，包括步骤开始时的值和整个步骤中10个间隔结束时的值。此参数的值必须是正整数。

### **可选参数：**

TIME MARKS

设置 TIME MARKS=NO（默认）以在由NUMBER INTERVAL参数决定的时间之后立即结束的增量处写入结果。

设置 TIME MARKS=YES 以在由NUMBER INTERVAL参数决定的确切时间写入结果。当在[*DYNAMIC](ch04abk43.md)选项上包含了FIXED TIME INCREMENTATION或DIRECT USER CONTROL参数时，不能使用TIME MARKS=YES。

**此选项没有关联的数据行。**



