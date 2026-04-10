# *DENSITY





### *DENSITY指定材料质量密度。

此选项用于定义材料的质量密度。在Abaqus/Standard分析中，可以使用分布为实体连续单元定义空间变化的质量密度（["分布定义，" Abaqus分析用户指南第2.8.1节](../usb/usb-link.md#usb-int-adefiningdistributions)）。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["密度，" Abaqus分析用户指南第21.2.1节](../usb/usb-link.md#usb-mat-cdensity)

### **可选参数：**

DEPENDENCIES

除了温度之外，将此参数设置为密度定义中包含的场变量数量。如果省略此参数，则假定密度是常数或仅取决于温度。请参见Abaqus分析用户指南第21.1.2节中的["指定场变量依赖性"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

如果使用分布定义空间变化密度，则此参数在Abaqus/Standard分析中不相关。请参见Abaqus分析用户指南第2.8.1节中的["分布定义"](../usb/usb-link.md#usb-int-adefiningdistributions)。

在Abaqus/CFD分析中，假定密度为常数。

PORE FLUID

此参数仅适用于Abaqus/Standard分析。

如果正在定义多孔介质中孔隙流体的密度，请包含此参数。

### **定义质量密度的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于六时需要）：**

根据需要重复此组数据行，以将密度定义为温度和其他预定义场变量的函数。

### **使用分布在Abaqus/Standard分析中为实体连续单元定义空间变化质量密度的数据行：**

**第一行（也是唯一一行）：**




