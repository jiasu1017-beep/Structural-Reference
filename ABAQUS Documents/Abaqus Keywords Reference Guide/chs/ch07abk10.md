# *GASKET ELASTICITY






### *GASKET ELASTICITY指定垫片的膜和横向剪切行为弹性特性。

此选项用于定义垫片的膜和横向剪切行为的弹性参数。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Property 模块

##### **参考文献：**

- ["使用垫片行为模型直接定义垫片行为，" Abaqus Analysis User's Guide 第 32.6.6 节](../usb/usb-link.md#usb-elm-egasketbehavior)

### **可选参数：**

COMPONENT

设置 COMPONENT=MEMBRANE 以定义垫片的膜行为。

设置 COMPONENT=TRANSVERSE SHEAR（默认）以定义垫片的横向剪切行为。

DEPENDENCIES

将此参数设置为除温度外弹性参数定义中包含的场变量依赖数量。如果省略此参数，则假定弹性参数仅取决于温度。请参阅 ["指定场变量依赖性" in "材料数据定义，" Abaqus Analysis User's Guide 第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，获取更多信息。

VARIABLE

此参数仅与 COMPONENT=TRANSVERSE SHEAR 一起使用，以指定定义横向剪切行为的单位制。

设置 VARIABLE=FORCE 以按每单位位移的力或每单位长度每单位位移的力来定义横向剪切刚度，具体取决于此行为所指的单元类型。

设置 VARIABLE=STRESS（默认）以按每单位位移的应力来定义横向剪切刚度。

### **COMPONENT=TRANSVERSE SHEAR 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于六时需要）：**

根据需要重复此组数据行，以将剪切刚度定义为温度和场变量的函数。

### **COMPONENT=MEMBRANE 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于五时需要）：**

根据需要重复此组数据行，以将杨氏模量和泊松比定义为温度和场变量的函数。




