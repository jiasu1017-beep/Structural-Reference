# *BRITTLE FAILURE





### *BRITTLE FAILURE指定脆性失效准则。

此选项与脆性开裂材料模型一起使用以指定材料的脆性失效。它必须与[*BRITTLE CRACKING](ch02abk13.md)和[*BRITTLE SHEAR](ch02abk15.md)选项配合使用。

**产品：**Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**属性模块

##### **参考：**

- ["混凝土开裂模型，" Abaqus Analysis User's Guide第23.6.2节](../usb/usb-link.md#usb-mat-ccracking)
- [*BRITTLE CRACKING](ch02abk13.md)
- [*BRITTLE SHEAR](ch02abk15.md)

### **可选参数：**

CRACKS

设置CRACKS=1（默认）以指示当任何局部直接开裂应变（或位移）分量达到失效值时，将移除单元。

设置CRACKS=2以指示当任何两个直接开裂应变（或位移）分量达到失效值时，将移除单元。

设置CRACKS=3以指示当所有三个可能的直接开裂应变（或位移）分量达到失效值时，将移除单元。

对于梁或桁架单元，CRACKS参数的值只能为1。对于平面应力和壳单元，它不能大于2；对于三维、平面应变和轴对称单元，它不能大于3。

DEPENDENCIES

将此参数设置为除了温度之外还包括在失效准则定义中的场变量依赖项数。如果省略此参数，则假定失效准则仅取决于温度。有关更多信息，请参阅["材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata)中的"使用DEPENDENCIES参数定义场变量依赖"。

### **在[*BRITTLE CRACKING](ch02abk13.md)选项上使用TYPE=STRAIN（默认）时的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时才需要）：**

根据需要重复此组数据行，以将开裂后行为定义为温度和其他预定义场变量的函数。

### **在[*BRITTLE CRACKING](ch02abk13.md)选项上包含TYPE=DISPLACEMENT或GFI时的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时才需要）：**

根据需要重复此组数据行，以将开裂后行为定义为温度和其他预定义场变量的函数。


