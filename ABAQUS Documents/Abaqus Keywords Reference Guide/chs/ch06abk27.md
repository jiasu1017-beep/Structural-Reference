# *FLUID INFLATOR ACTIVATION





### *FLUID INFLATOR ACTIVATION激活流体充气机定义。

此选项用于激活流体充气机定义。

**产品：**Abaqus/Explicit   

**类型：**历史数据  

**级别：**步骤  

##### **参考：**

- ["充气机定义，" Abaqus Analysis User's Guide第11.5.4节](../usb/usb-link.md#usb-anl-afluidinflator)
- [*FLUID INFLATOR](ch06abk26.md)

### **可选参数：**

INFLATION TIME AMPLITUDE

将此参数设置为定义充气时间与实际时间之间映射关系的幅值曲线名称。如果省略此参数，则充气时间将等于自激活以来经过的实际时间。

MASS FLOW AMPLITUDE

将此参数设置为用于修改质量流率的幅值曲线名称。此参数仅在质量流率在充气机属性定义中直接规定时有效。如果质量流率是通过使用罐体测试数据或双压力方法计算的，则此参数将被忽略。

OP

对于现有[*FLUID INFLATOR ACTIVATION](ch06abk27.md)定义保持不变，将OP=MOD（默认）设置为此选项定义要添加或修改的流体充气机激活。

如果应该删除所有当前生效的流体充气机激活，则设置OP=NEW。要仅删除选定的流体充气机激活，请使用OP=NEW并重新指定要保留的所有流体充气机激活。

### **定义流体充气机激活的数据行：**

**第一行：**

根据需要重复此数据行。每行最多允许8个条目。
