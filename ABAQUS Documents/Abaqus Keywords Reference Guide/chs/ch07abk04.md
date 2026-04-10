# *GAP FLOW






### *GAP FLOW为孔隙压力内聚单元中的切向流动定义本构参数。

此选项用于为孔隙压力内聚单元定义切向流动本构参数。它通常用于水力驱动的断裂模型中。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Property 模块

##### **参考文献：**

- ["定义内聚单元间隙内流体的本构响应，" Abaqus Analysis User's Guide 第 32.5.7 节](../usb/usb-link.md#usb-elm-ecohesivefluidbehavior)

### **可选参数：**

DEPENDENCIES

将此参数设置为除温度外本构参数定义中包含的场变量数量。如果省略此参数，则假定本构参数是常量或仅取决于温度。请参阅 ["指定场变量依赖性" in "材料数据定义，" Abaqus Analysis User's Guide 第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，获取更多信息。

TYPE

设置 TYPE=NEWTONIAN（默认）以定义牛顿流体的粘度。

设置 TYPE=POWER LAW 以定义幂律流体的稠度和指数。

KMAX

将此参数设置为应使用的最大渗透率值。此参数仅在 TYPE=NEWTONIAN 时才有意义。如果省略此参数，Abaqus 假定渗透率没有界限。

### **定义孔隙流体粘度 ![](../graphics/key_eqn00760.gif) 的数据行（TYPE=NEWTONIAN）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于五时需要）：**

根据需要重复此组数据行以定义变化。

### **定义稠度 *K* 和指数 ![](../graphics/key_eqn00080.gif) 的数据行（TYPE=POWER LAW）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于三时需要）：**

根据需要重复此组数据行以定义变化。




