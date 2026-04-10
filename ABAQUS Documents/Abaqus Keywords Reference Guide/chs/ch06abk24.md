# *FLUID EXPANSION





### *FLUID EXPANSION指定液压流体的热膨胀系数。

此选项用于为液压流体模型定义热膨胀系数。它只能与[*FLUID BEHAVIOR](ch06abk16.md)选项一起使用。

**产品：**Abaqus/Standard   Abaqus/Explicit   Abaqus/CAE   

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["流体腔定义，" Abaqus Analysis User's Guide第11.5.2节](../usb/usb-link.md#usb-anl-afluidcavities)
- [*FLUID BEHAVIOR](ch06abk16.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除温度外还包括在热膨胀系数定义中的场变量依赖项数。如果省略此参数，则假定热膨胀系数仅取决于温度。有关详细信息，请参见["指定场变量依赖"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

ZERO

将此参数设置为![](../graphics/key_eqn00714.gif)的值。默认值为ZERO=0。

### **定义热膨胀系数的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于六时才需要）：**

根据需要重复此组数据行，以将![](../graphics/key_eqn00080.gif)定义为![](../graphics/key_eqn00075.gif)和场变量的函数。
