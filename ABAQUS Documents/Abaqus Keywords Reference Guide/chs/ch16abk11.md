# *PIEZOELECTRIC







### *PIEZOELECTRIC指定压电材料属性。

此选项用于定义材料的压电特性。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["压电行为，" Abaqus Analysis User's Guide第26.5.2节](../usb/usb-link.md#usb-mat-cpiezoelect)

### **可选参数：**

DEPENDENCIES

将此参数设置为压电特性定义中包含的场变量数量。如果省略此参数，则假定压电特性不依赖于任何场变量，但仍可能依赖于温度。有关更多信息，请参见["指定场变量依赖性"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中。

TYPE

设置TYPE=S（默认）以指定压电特性的应力材料系数。设置TYPE=E以指定压电特性的应变材料系数。

### **定义压电应力系数矩阵的数据行（TYPE=S）：**

**第一行：**

**第二行：**

**第三行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将压电特性定义为温度和其他预定义场变量的函数。

### **定义压电应变系数矩阵的数据行（TYPE=E；对于剪切分量，这些系数将工程剪切应变分量（而非张量剪切应变分量）与势梯度向量的分量相关联）：**

**第一行：**

**第二行：**

**第三行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将压电特性定义为温度和其他预定义场变量的函数。
