# *JOINT ELASTICITY






### *JOINT ELASTICITY为弹塑性关节单元指定弹性特性。

此选项用于为弹塑性关节单元定义线性弹性模量。它只能与 [*EPJOINT](ch05abk29.md) 选项一起使用。

**产品：** Abaqus/Standard  

**类型：** 模型数据  

**级别：** 零件、零件实例  

##### **参考文献：**

- ["弹塑性关节，" Abaqus Analysis User's Guide 第 32.10.1 节](../usb/usb-link.md#usb-elm-eepjoint)
- [*EPJOINT](ch05abk29.md)

### **必需参数：**

MODULI

设置 MODULI=SPUD CAN 以定义桩靴模量。设置 MODULI=GENERAL 以输入通用弹性模量。

NDIM

设置 NDIM=2 以输入二维问题的值。设置 NDIM=3 以输入三维问题的值。

### **可选参数：**

DEPENDENCIES

将此参数设置为模量定义中包含的场变量依赖数量。如果省略此参数，则假定模量是常量或仅取决于温度。请参阅 ["指定场变量依赖性" in "材料数据定义，" Abaqus Analysis User's Guide 第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，获取更多信息。

### **MODULI=SPUD CAN 和 NDIM=2 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于三时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **MODULI=SPUD CAN 和 NDIM=3 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于二时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **MODULI=GENERAL 和 NDIM=2 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于一时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。

### **MODULI=GENERAL 和 NDIM=3 的数据行：**

**第一行：**

**第二行：**

**第三行：**

**后续行（仅在 DEPENDENCIES 参数的值大于二时需要）：**

根据需要重复此组数据行，以将弹性行为定义为温度和其他预定义场变量的函数。




