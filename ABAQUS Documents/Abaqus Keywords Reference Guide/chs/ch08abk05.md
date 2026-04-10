# *HEATCAP






### *HEATCAP指定点热容。

此选项用于定义与 HEATCAP 单元相关的集中热容值。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 零件、零件实例、装配  

**Abaqus/CAE：** Property 模块和 Interaction 模块。

##### **参考文献：**

- ["点热容，" Abaqus Analysis User's Guide 第 30.4.1 节](../usb/usb-link.md#usb-elm-ecapacitance)

### **必需参数：**

DEPENDENCIES

将此参数设置为您正在定义点热容的场变量数量。如果省略此参数，则假定点热容是常量或仅取决于温度。请参阅 ["指定场变量依赖性" in "材料数据定义，" Abaqus Analysis User's Guide 第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，获取更多信息。

ELSET

将此参数设置为包含正在给出其值的 HEATCAP 单元的单元集名称。

### **定义热容大小的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于六时需要）：**

根据需要重复此组数据行，以将点热容定义为温度和其他预定义场变量的函数。Abaqus 不使用任何特定的物理单位，因此用户的选择必须一致。




