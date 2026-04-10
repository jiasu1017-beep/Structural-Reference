# *SLOAD





### *SLOAD将载荷施加到子结构。

此选项用于激活由[*SUBSTRUCTURE LOAD CASE](ch18abk43.md)选项定义的子结构载荷情况。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步

##### **参考：**

- ["Using substructures," Section 10.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelements)
- [*SUBSTRUCTURE LOAD CASE](ch18abk43.md)

### **可选参数：**

AMPLITUDE

将此参数设置为由[*AMPLITUDE](ch01abk09.md)选项（["Amplitude curves," Section 34.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pamplitude)）定义的幅值名称。此幅值定义了整个步中载荷情况（[*SUBSTRUCTURE LOAD CASE](ch18abk43.md)）幅值的时间变化。如果省略此参数，则默认幅值为["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)中为步中使用的特定过程定义的幅值。

OP

设置OP=MOD（默认）以修改或添加到当前活动的[*SLOAD](ch18abk20.md)s。

如果应删除应用于模型的所有现有[*SLOAD](ch18abk20.md)s并可能定义新的，则设置OP=NEW。

### **定义载荷的数据行：**

**第一行：**

根据需要重复此数据行以定义子结构上的载荷。




