# *HYPOELASTIC






### *HYPOELASTIC指定亚弹性材料特性。

此选项用于定义非线性小应变弹性材料。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Property 模块

##### **参考文献：**

- ["亚弹性行为，" Abaqus Analysis User's Guide 第 22.4.1 节](../usb/usb-link.md#usb-mat-chypoelastic)
- ["UHYPEL，" Abaqus User Subroutines Reference Guide 第 1.1.37 节](../sub/sub-link.md#sub-rtn-uuhypel)

### **可选参数：**

USER

如果模量在用户子程序 [`UHYPEL`](../sub/sub-link.md#sub-xsl-uhypel) 中定义，则包含此参数。如果模量在数据行上定义，则省略此参数。

### **通过直接指定材料常数来定义亚弹性的数据行：**

**第一行：**

根据需要重复此数据行，以将模量定义为应变不变量的函数。

### **通过用户子程序定义亚弹性：**

当指定了 USER 参数时，此选项不使用数据行。相反，必须使用用户子程序 [`UHYPEL`](../sub/sub-link.md#sub-xsl-uhypel) 来定义亚弹性。




