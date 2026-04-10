# *ANNEAL TEMPERATURE





### *ANNEAL TEMPERATURE指定用于模拟退火或熔化的材料属性。

此选项用于定义弹塑性材料的退火温度。它必须与[*PLASTIC](ch16abk14.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["退火或熔化，" Abaqus Analysis User's Guide第23.2.5节](../usb/usb-link.md#usb-mat-cannealmelt)
- [*PLASTIC](ch16abk14.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为包含在退火温度定义中的场变量依赖项数。如果省略此参数，则假定退火温度是常数。参见["在材料数据定义中指定场变量依赖性，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多信息。

### **定义退火温度的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于七时需要）：**

根据需要重复此组数据行，以将材料参数![](../graphics/key_eqn00076.gif)定义为场变量的函数。