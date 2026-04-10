# *MONITOR









### *MONITOR定义要监控的自由度。

此选项用于选择节点和自由度以在状态文件中监控解决方案的进度。在Abaqus/Standard中，信息也将写入消息文件。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["输出，" Abaqus Analysis User's Guide第4.1.1节](../usb/usb-link.md#usb-out-ooutput)

### **必需参数：**

DOF

将此参数设置为要在节点处监控的自由度。在Abaqus/Explicit分析中，自由度将在全局坐标系中。如果在Abaqus/Standard分析中的节点处使用了[*TRANSFORM](ch19abk11.md)选项，则自由度在局部变换坐标系中。

NODE

将此参数设置为要监控的节点编号或包含要监控的节点的节点集名称。如果选择节点集的名称，则该节点集必须恰好包含一个节点。

### **可选参数：**

FREQUENCY

此参数仅适用于Abaqus/Standard分析。

此参数仅影响消息文件的输出。将其设置为输出频率，以增量计。除非FREQUENCY=0，否则输出将在每个步骤的最后一个增量打印。默认值为FREQUENCY=1。设置FREQUENCY=0以抑制输出。

**此选项没有关联的数据行。**