# *FLUID BULK MODULUS





### *FLUID BULK MODULUS定义液压流体的可压缩性。

此选项用于定义液压流体模型的可压缩性。它只能与[*FLUID BEHAVIOR](ch06abk16.md)选项一起使用。

**产品：**Abaqus/Standard   Abaqus/Explicit   Abaqus/CAE   

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["流体腔定义，" Abaqus Analysis User's Guide第11.5.2节](../usb/usb-link.md#usb-anl-afluidcavities)
- [*FLUID BEHAVIOR](ch06abk16.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除温度外还包括在流体体积模量定义中的场变量依赖项数。如果省略此参数，则假定流体体积模量仅取决于温度。有关详细信息，请参见["指定场变量依赖"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

### **定义液压流体可压缩性的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于六时才需要）：**

根据需要重复此组数据行，以将*K*定义为温度和场变量的函数。
