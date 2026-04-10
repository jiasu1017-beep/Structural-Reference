# *RATIOS







### *RATIOS定义各向异性膨胀。

此选项用于指定定义各向异性膨胀的比值。[*RATIOS](ch17abk09.md)选项只能与[*MOISTURE SWELLING](ch13abk25.md)选项或[*SWELLING](ch18abk56.md)选项结合使用，并且应紧接在其中一个选项之后。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["湿度膨胀，" Abaqus Analysis User's Guide第26.6.6节](../usb/usb-link.md#usb-mat-cmoistureswell)
- ["率相关塑性：蠕变和膨胀，" Abaqus Analysis User's Guide第23.2.4节](../usb/usb-link.md#usb-mat-cratedepcreep)
- [*MOISTURE SWELLING](ch13abk25.md)
- [*SWELLING](ch18abk56.md)

### **当[*RATIOS](ch17abk09.md)选项与[*SWELLING](ch18abk56.md)选项结合使用时的可选参数：**

DEPENDENCIES

将此参数设置为各向异性比定义中包含的场变量依赖数量，不包括温度。如果省略此参数，则假定比值仅依赖于温度。有关更多信息，请参见["指定场变量依赖性"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中。

### **定义各向异性膨胀比的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于4时需要）：**

根据需要重复此组数据行，以将各向异性膨胀比定义为温度和其他场变量的函数。
