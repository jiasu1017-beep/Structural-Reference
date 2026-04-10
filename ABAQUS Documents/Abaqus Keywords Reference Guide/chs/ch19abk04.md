# *TENSION STIFFENING





### *TENSION STIFFENING定义*CONCRETE模型中裂纹法向的保留拉应力。

此选项用于定义裂纹法向的保留拉应力，作为裂纹法向方向变形函数的函数。它必须与[*CONCRETE](ch03abk28.md)选项一起使用并出现在其后。[*TENSION STIFFENING](ch19abk04.md)选项也可以与[*SHEAR RETENTION](ch18abk12.md)和[*FAILURE RATIOS](ch06abk04.md)选项一起使用。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["混凝土弥散开裂," Section 23.6.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cconcrete)
- [*CONCRETE](ch03abk28.md)
- [*FAILURE RATIOS](ch06abk04.md)
- [*SHEAR RETENTION](ch18abk12.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括开裂后行为定义中的场变量依赖项数。如果省略此参数，则假定开裂后行为仅取决于温度。有关详细信息，请参见["材料数据定义," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

TYPE

设置TYPE=DISPLACEMENT以通过输入位移来定义开裂后行为，![](../graphics/key_eqn01103.gif)，即开裂后线性强度损失给出零应力。

设置TYPE=STRAIN（默认）以通过直接输入失效后应力-应变关系来指定开裂后行为。

### **如果包含参数TYPE=STRAIN（默认）的数据行：**

**第一行：**

每个温度值下的第一个点必须是在应变为0.0时应力分数为1.0。

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以定义开裂后行为对温度和其他预定义场变量的依赖性。

### **如果包含参数TYPE=DISPLACEMENT的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以定义开裂后行为对温度和其他预定义场变量的依赖性。





