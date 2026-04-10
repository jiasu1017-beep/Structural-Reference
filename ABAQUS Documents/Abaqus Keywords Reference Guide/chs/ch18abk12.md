# *SHEAR RETENTION





### *SHEAR RETENTION定义*CONCRETE模型中与裂纹表面相关的剪切模量降低，作为裂纹两侧拉伸应变的函数。

此选项用于给出一个乘数因子 ![](../graphics/key_eqn01059.gif)，它将裂纹剪切模量定义为未开裂混凝土弹性剪切模量的分数。如果使用此选项，它应跟在[*CONCRETE](ch03abk28.md)选项之后。[*SHEAR RETENTION](ch18abk12.md)选项也可以与[*FAILURE RATIOS](ch06abk04.md)选项配合使用。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["Concrete smeared cracking," Section 23.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcrete)
- [*CONCRETE](ch03abk28.md)
- [*FAILURE RATIOS](ch06abk04.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括剪切保持行为定义中的场变量依赖项数。如果省略此参数，则假定剪切保持行为仅取决于温度。有关更多信息，请参见["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

### **定义剪切保持行为的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于三时需要）：**

根据需要重复此组数据行以定义剪切保持行为对温度和其他预定义场变量的依赖性。




