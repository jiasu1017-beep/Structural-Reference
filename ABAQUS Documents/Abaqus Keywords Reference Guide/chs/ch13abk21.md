# *MODAL PRINT









### *MODAL PRINT在基于模式的动力学程序期间打印广义坐标（模态幅度）数据。

此选项用于在基于模式的动力学程序期间控制广义坐标（模态幅度和相位）值的打印输出。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**步骤

##### **参考：**

- ["输出到数据和结果文件，" Abaqus Analysis User's Guide第4.1.2节](../usb/usb-link.md#usb-out-oprintfile)

### **可选参数：**

FREQUENCY

将此参数设置为输出频率，以增量计。除非FREQUENCY=0，否则输出将在每个步骤的最后一个增量打印。默认值为FREQUENCY=1。设置FREQUENCY=0以抑制输出。

### **在数据文件中请求模态输出的数据行：**

**第一行：**

根据需要重复此数据行：每一行定义一个表。