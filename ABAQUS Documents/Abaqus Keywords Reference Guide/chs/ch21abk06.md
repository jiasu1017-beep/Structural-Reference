# *VOID NUCLEATION





### *VOID NUCLEATION定义多孔材料中孔洞的形核。

此选项用于对多孔材料中孔洞的形核进行建模。它只能与[*POROUS METAL PLASTICITY](ch16abk22.md)选项一起使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["多孔金属塑性," Section 23.2.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cpormetalplas)
- [*POROUS METAL PLASTICITY](ch16abk22.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外定义形核应变正态分布的场变量依赖项数。如果省略此参数，则定义正态分布的常数可能仅取决于温度。请参见["材料数据定义," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

### **定义孔洞形核的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将![](../graphics/key_eqn01182.gif)、![](../graphics/key_eqn01183.gif)和![](../graphics/key_eqn01184.gif)定义为温度和其他预定义场变量的函数。





