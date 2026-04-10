# *RADIATION PRINT







### *RADIATION PRINT定义腔体辐射热传递的打印请求。

此选项用于打印腔体辐射变量（辐射通量、视角因子总和和小平面温度）的表格输出。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**步骤  

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

将此参数设置为输出频率，以增量为单位。除非FREQUENCY=0，否则输出始终在每个步骤的最后一个增量打印。默认为FREQUENCY=1。设置FREQUENCY=0以抑制输出。

SUMMARY

设置SUMMARY=YES（默认）以获取表中每列最大值和最小值及其位置的摘要。

设置SUMMARY=NO以抑制此摘要。

TOTALS

设置TOTALS=YES以打印表中每列的总和。例如，这对于汇总构成辐射表面的所有小平面上的辐射通量很有用。默认为TOTALS=NO。

### **请求打印输出的数据行：**

**第一行：**

根据需要重复此数据行：每行定义一个表（如果请求是针对由多个表面组成的腔体，则可能不止一个表）。如果省略此行，则将使用默认变量。
