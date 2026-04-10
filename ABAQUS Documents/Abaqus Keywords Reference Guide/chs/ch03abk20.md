# *CHARACTERISTIC LENGTH






### *CHARACTERISTIC LENGTH在材料点定义特征单元长度。

此选项用于定义 Abaqus 用于应变软化模型正则化的特征单元长度，或传递给在材料点调用的用户子程序。如果使用，它必须出现在 [*MATERIAL](ch13abk08.md) 定义内（["材料数据定义，" Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata)）。如果未指定此选项，Abaqus 使用基于几何平均的定义计算特征单元长度。

**产品：**Abaqus/Explicit  

**类型：**模型数据  

**级别：**模型  

##### **参考：**

- ["VUCHARLENGTH，" Abaqus 用户子程序参考指南第 1.2.11 节](../sub/sub-link.md#sub-rtn-uexpucharlength)

### **可选参数：**

DEFINITION

设置 DEFINITION=GEOMETRIC MEAN（默认）以使用基于几何平均的特征单元长度定义。

设置 DEFINITION=USER 以在用户子程序 [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength) 中指定特征单元长度。

### **与 DEFINITION=USER 结合使用的可选参数：**

COMPONENTS

将此参数设置为你正在输入的特征单元长度的分量数。

PROPERTIES

将此参数设置为你正在输入的属性数。这些属性可在用户子程序 [`VUCHARLENGTH`](../sub/sub-link.md#sub-xsl-vucharlength) 中使用。

### **DEFINITION=GEOMETRIC MEAN 时不需要数据行。**

### **指定了 PROPERTIES 参数时 DEFINITION=USER 的数据行：**

**第一行：**

根据需要重复此数据行以定义所有材料属性。




