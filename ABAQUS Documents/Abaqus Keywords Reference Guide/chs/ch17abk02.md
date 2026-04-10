# *RADIATION FILE







### *RADIATION FILE为腔体辐射热传递定义结果文件请求。

此选项用于将腔体辐射变量写入Abaqus/Standard结果文件。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**不支持；Abaqus/CAE仅从输出数据库文件读取输出。

##### **参考：**

- ["腔体辐射，" Abaqus Analysis User's Guide第41.1.1节](../usb/usb-link.md#usb-cni-acavityradiation)
- ["输出，" Abaqus Analysis User's Guide第4.1.1节](../usb/usb-link.md#usb-out-ooutput)

### **可选的互斥参数（如果未指定，将为模型中的所有腔体提供输出）：**

CAVITY

将此参数设置为此输出请求所针对的腔体名称。

ELSET

将此参数设置为此输出请求所针对的元素集名称。

SURFACE

将此参数设置为此输出请求所针对的表面名称。

### **可选参数：**

FREQUENCY

将此参数设置为输出频率，以增量为单位。除非FREQUENCY=0，否则输出始终在每个步骤的最后一个增量写入结果文件。默认为FREQUENCY=1。设置FREQUENCY=0以抑制输出。

### **请求结果文件输出的数据行：**

**第一行：**

根据需要重复此数据行，以定义要写入指定腔体、表面或元素集的结果文件的表面变量。如果省略此行，则将使用默认变量。
