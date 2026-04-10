# *BRITTLE CRACKING





### *BRITTLE CRACKING定义脆性开裂属性。

此选项用于为脆性开裂材料模型定义开裂和开裂后属性。[*BRITTLE CRACKING](ch02abk13.md)选项必须与[*BRITTLE SHEAR](ch02abk15.md)选项配合使用，必须紧接在其之前。[*BRITTLE CRACKING](ch02abk13.md)选项可与[*BRITTLE FAILURE](ch02abk14.md)选项配合使用以指定脆性失效准则。

**产品：**Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**属性模块

##### **参考：**

- ["混凝土开裂模型，" Abaqus Analysis User's Guide第23.6.2节](../usb/usb-link.md#usb-mat-ccracking)
- [*BRITTLE FAILURE](ch02abk14.md)
- [*BRITTLE SHEAR](ch02abk15.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在开裂后行为定义中的场变量依赖项数。如果省略此参数，则假定开裂后行为仅取决于温度。有关更多信息，请参阅["材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata)中的"使用DEPENDENCIES参数定义场变量依赖"。

TYPE

设置TYPE=STRAIN（默认）以通过直接输入失效后应力-应变关系来指定开裂后行为。

设置TYPE=DISPLACEMENT以通过直接输入失效后应力/位移关系来定义开裂后行为。

设置TYPE=GFI以通过输入失效应力![](../graphics/key_eqn00117.gif)和I型断裂能![](../graphics/key_eqn00118.gif)来定义开裂后行为。

### **包含TYPE=STRAIN参数时的数据行（默认）：**

**第一行：**

每个温度值的第一点必须具有0.0的开裂应变，并给出失效应力值。

**后续行（仅在DEPENDENCIES参数的值大于五时才需要）：**

根据需要重复此组数据行，以将开裂后行为定义为温度和其他预定义场变量的函数。

### **包含TYPE=DISPLACEMENT参数时的数据行：**

**第一行：**

每个温度值的第一点必须具有0.0的开裂位移，并给出失效应力值。

**后续行（仅在DEPENDENCIES参数的值大于五时才需要）：**

根据需要重复此组数据行，以将开裂后行为定义为温度和其他预定义场变量的函数。

### **包含TYPE=GFI参数时的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时才需要）：**

根据需要重复此组数据行，以将开裂后行为定义为温度和其他预定义场变量的函数。


