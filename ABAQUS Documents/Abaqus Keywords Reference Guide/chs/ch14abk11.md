# *NODE FILE









### *NODE FILE为节点数据定义结果文件请求。

此选项用于选择将在Abaqus/Standard分析的结果（.fil）文件中或Abaqus/Explicit分析的所选结果（.sel）文件中写入的节点变量。在Abaqus/Explicit分析中，它必须与[*FILE OUTPUT](ch06abk09.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**不支持；Abaqus/CAE仅从输出数据库文件读取输出。

##### **参考：**

- ["输出到数据和结果文件，" Abaqus Analysis User's Guide第4.1.2节](../usb/usb-link.md#usb-out-oprintfile)
- [*FILE OUTPUT](ch06abk09.md)

### **可选参数：**

FREQUENCY

此参数仅适用于Abaqus/Standard分析。

将此参数设置为输出频率，以增量计。除非FREQUENCY=0，否则输出将在每个步骤的最后一个增量写入结果文件。默认值为FREQUENCY=1。设置FREQUENCY=0以抑制输出。

GLOBAL

此参数仅适用于Abaqus/Standard分析。

此参数仅在与用于定义局部坐标系的[*TRANSFORM](ch19abk11.md)选项一起使用的节点处相关。

设置GLOBAL=NO以在局部方向写入向量值节点变量。

设置GLOBAL=YES（默认）以在全局方向写入向量值节点变量。此默认值为[*NODE PRINT](ch14abk12.md)选项上默认值的相反值，因为大多数后处理器假定分量在全局系统中给出。

LAST MODE

此参数仅适用于Abaqus/Standard分析。

此参数仅在自然频率提取和特征值 buckling 估计期间有用。将此参数设置为需要输出的最高模式号。

默认值为LAST MODE=*N*，其中*N*是提取的模式数。如果使用了MODE参数，则默认值为LAST MODE=*M*，其中*M*是MODE参数的值。

MODE

此参数仅适用于Abaqus/Standard分析。

此参数仅在自然频率提取和特征值 buckling 估计期间有用。将此参数设置为需要输出的第一个模式号。默认值为MODE=1。另请参见LAST MODE参数。执行[*FREQUENCY](ch06abk35.md)分析时，归一化将遵循NORMALIZATION参数设置的格式。否则，归一化使得模式中的最大位移分量具有1.0的大小。

NSET

将此参数设置为要向结果文件写入输出的节点集名称。如果省略此参数，将为模型中的所有节点写入输出。

### **在结果或所选结果文件中请求节点输出的数据行：**

**第一行：**

根据需要重复此数据行以定义要写入结果或所选结果文件的节点变量。