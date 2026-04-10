# *CONTACT PRINT






### *CONTACT PRINT定义接触变量的打印请求。

此选项用于提供接触表面对的接触变量的表格打印输出。

**产品：**Abaqus/Standard  

**类型：**历史数据 

**级别：**步骤

##### **参考：**

- ["输出到数据和结果文件，" Abaqus 分析用户指南第 4.1.2 节](../usb/usb-link.md#usb-out-oprintfile)

### **可选参数：**

FREQUENCY

将此参数设置为输出频率（以增量为单位）。除非 FREQUENCY=0，否则输出将始终在每个步骤的最后增量打印。默认值为 FREQUENCY=1。设置 FREQUENCY=0 以禁止输出。

MASTER

将此参数设置为主表面的名称，为其发出此输出请求。

NSET

将此参数设置为节点集的名称，为其发出此输出请求。

SLAVE

将此参数设置为从表面的名称，为其发出此输出请求。

SUMMARY

设置 SUMMARY=YES（默认）以获取表中每列最大值和最小值及其位置的摘要。设置 SUMMARY=NO 以禁止此摘要。

TOTALS

设置 TOTALS=YES 以打印表中每列的总和。默认值为 TOTALS=NO。

### **用于在数据文件中请求接触变量输出的数据行：**

**第一行：**

根据需要重复此数据行：每一行定义一个表。如果省略此行，则将输出默认变量。




