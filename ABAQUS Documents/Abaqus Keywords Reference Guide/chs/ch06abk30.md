# *FLUID LEAKOFF





### *FLUID LEAKOFF为孔隙压力内聚单元定义流体泄漏系数。

此选项用于为孔隙压力内聚单元定义泄漏系数。

**产品：**Abaqus/Standard   Abaqus/CAE   

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["定义内聚单元间隙内流体的本构响应，" Abaqus Analysis User's Guide第32.5.7节](../usb/usb-link.md#usb-elm-ecohesivefluidbehavior)
- ["UFLUIDLEAKOFF，" Abaqus User Subroutines Reference Guide第1.1.34节](../sub/sub-link.md#sub-rtn-uufluidleakoff)

### **可选的互斥参数：**

DEPENDENCIES

将此参数设置为除温度外还包括在流体泄漏系数定义中的场变量依赖项数。如果省略此参数，则假定泄漏系数为常数或仅取决于温度。有关详细信息，请参见["指定场变量依赖"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

USER

包含此参数以指示将使用用户子程序[`UFLUIDLEAKOFF`](../sub/sub-link.md#sub-xsl-ufluidleakoff)来定义流体泄漏系数。

### **如果省略USER参数，则定义流体泄漏系数的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于六时才需要）：**

根据需要重复此组数据行，以将*K*定义为温度和场变量的函数。

### **当包含USER参数时，没有数据行。**
