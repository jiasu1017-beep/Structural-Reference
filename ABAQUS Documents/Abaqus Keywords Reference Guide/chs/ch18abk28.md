# *SPECIFIC HEAT





### *SPECIFIC HEAT定义比热容。

此选项用于指定材料的比热容。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["Specific heat," Section 26.2.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cspecificheat)

### **可选参数：**

DEPENDENCIES

此参数仅适用于Abaqus/Standard和Abaqus/Explicit分析。

将此参数设置为比热容定义中包含的场变量数量。如果省略此参数，则假定比热容是常数或仅取决于温度。有关更多信息，请参见["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

PORE FLUID

此参数仅适用于Abaqus/Standard分析。

如果正在定义多孔介质中孔隙流体的比热容，则包含此参数。

TYPE

此参数仅适用于Abaqus/CFD分析。

设置TYPE=CONSTANT VOLUME（默认）以定义定容比热容。

设置TYPE=CONSTANT PRESSURE以在为热流问题使用能量方程时定义定压比热容。

### **指定材料比热容的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于六时需要）：**

根据需要重复此组数据行，以将比热容定义为温度和其他预定义场变量的函数。




