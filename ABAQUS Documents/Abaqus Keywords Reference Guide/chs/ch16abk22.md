# *POROUS METAL PLASTICITY







### *POROUS METAL PLASTICITY指定多孔金属塑性模型。

此选项用于指定多孔金属塑性模型的多孔部分。

[*POROUS METAL PLASTICITY](ch16abk22.md)选项可与[*VOID NUCLEATION](ch21abk07.md)选项结合使用以定义孔洞的形核。在Abaqus/Explicit分析中，它还可以与[*POROUS FAILURE CRITERIA](ch16abk21.md)选项结合使用以指定材料失效准则。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["多孔金属塑性，" Abaqus Analysis User's Guide第23.2.9节](../usb/usb-link.md#usb-mat-cpormetalplas)
- [*VOID NUCLEATION](ch21abk07.md)
- [*POROUS FAILURE CRITERIA](ch16abk21.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为![](../graphics/key_eqn01005.gif)、![](../graphics/key_eqn01006.gif)和![](../graphics/key_eqn01007.gif)参数定义中包含的场变量依赖数量，不包括温度。如果省略此参数，则![](../graphics/key_eqn01005.gif)、![](../graphics/key_eqn01006.gif)和![](../graphics/key_eqn01007.gif)可能仅依赖于温度。有关更多信息，请参见["指定场变量依赖性"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中。

RELATIVE DENSITY

将此参数设置为![](../graphics/key_eqn01008.gif)，即材料的初始相对密度。如果省略此参数，则初始相对密度从[*INITIAL CONDITIONS](ch09abk18.md)，TYPE=RELATIVE DENSITY选项给出的值进行插值。

### **定义多孔金属塑性的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于4时需要）：**

根据需要重复此组数据行，以将![](../graphics/key_eqn01005.gif)、![](../graphics/key_eqn01006.gif)和![](../graphics/key_eqn01007.gif)定义为温度和其他预定义场变量的函数。
