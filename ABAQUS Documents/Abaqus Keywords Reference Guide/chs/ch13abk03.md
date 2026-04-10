# *MAGNETOSTATIC









### *MAGNETOSTATIC静磁分析。

此选项用于指示该步骤应作为静磁荷载步骤进行分析。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**步骤

##### **参考：**

- ["电磁分析程序，" Abaqus Analysis User's Guide第6.7.1节](../usb/usb-link.md#usb-anl-aelectricproc)
- ["静磁分析，" Abaqus Analysis User's Guide第6.7.6节](../usb/usb-link.md#usb-anl-amagnetostatic)

### **可选参数：**

DIRECT

此参数选择用户对步骤增量的直接控制。如果使用此参数，则使用数据行定义的恒定增量。如果省略，Abaqus将选择增量（在第一次尝试第一个增量时尝试用户的初始时间增量之后）。

STABILIZATION

包含此参数以激活在某些情况下获得静磁解决方案所需的稳定方案。它定义了Abaqus在稳定计算中使用的因子。如果包含此参数时没有指定值，则假定默认值为1.0。该参数可以设置为较高值以增加稳定性，或设置为较低值以减少稳定性。

### **静磁分析的数据行：**

**第一行（也是唯一一行）：**



