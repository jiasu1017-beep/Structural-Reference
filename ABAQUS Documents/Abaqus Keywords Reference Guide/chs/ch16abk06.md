# *PERMANENT MAGNETIZATION









### *PERMANENT MAGNETIZATION指定永久磁化。

此选项用于通过永磁体的矫顽力为瞬态电磁或静磁分析中的电磁单元定义永久磁化。此选项只能与[*MAGNETIC PERMEABILITY](ch13abk01.md)选项结合使用，并可选择与[*NONLINEAR BH](ch14abk14.md)选项结合使用。

**产品：**Abaqus/Standard  

**类型：**模型数据  

**级别：**模型  

##### **参考：**

- ["磁导率，" Abaqus Analysis User's Guide第26.5.3节](../usb/usb-link.md#usb-mat-cmagpermeability)
- ["涡流分析，" Abaqus Analysis User's Guide第6.7.5节](../usb/usb-link.md#usb-anl-aeddycurrent)
- ["静磁分析，" Abaqus Analysis User's Guide第6.7.6节](../usb/usb-link.md#usb-anl-amagnetostatic)

### **可选参数：**

DEPENDENCIES

将此参数设置为永磁体矫顽力定义中包含的场变量数量。如果省略此参数，则假定矫顽力不依赖于任何场变量，但可能仍依赖于温度。

### **定义矫顽力向量的数据行：**

**第一行：**

**第二行：**

**后续行（仅在DEPENDENCIES参数值大于6时需要）：**

不要重复第一数据行。根据需要重复第二和后续数据行，以将矫顽力大小定义为温度和场变量的函数。