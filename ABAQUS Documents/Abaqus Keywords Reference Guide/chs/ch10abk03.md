# *JOINT PLASTICITY






### *JOINT PLASTICITY为弹塑性关节单元指定塑性特性。

此选项用于为弹塑性关节单元定义塑性行为。它只能与 [*EPJOINT](ch05abk29.md) 选项一起使用。

**产品：** Abaqus/Standard  

**类型：** 模型数据  

**级别：** 零件、零件实例  

##### **参考文献：**

- ["弹塑性关节，" Abaqus Analysis User's Guide 第 32.10.1 节](../usb/usb-link.md#usb-elm-eepjoint)
- [*EPJOINT](ch05abk29.md)

### **必需参数：**

TYPE

设置 TYPE=SAND 以指定桩靴与沙子相互作用的模型。设置 TYPE=CLAY 以指定桩靴与粘土相互作用的模型。设置 TYPE=MEMBER 以指定结构构件的抛物线模型。

### **可选参数：**

DEPENDENCIES

将此参数设置为塑性特性值定义中包含的场变量依赖数量。如果省略此参数，则假定塑性特性值是常量或仅取决于温度。请参阅 ["指定场变量依赖性" in "材料数据定义，" Abaqus Analysis User's Guide 第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，获取更多信息。

### **TYPE=SAND 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于二时需要）：**

根据需要重复此组数据行，以将塑性行为定义为温度和其他预定义场变量的函数。

### **TYPE=CLAY 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于三时需要）：**

根据需要重复此组数据行，以将塑性行为定义为温度和其他预定义场变量的函数。

### **TYPE=MEMBER 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于三时需要）：**

根据需要重复此组数据行，以将塑性行为定义为温度和其他预定义场变量的函数。




