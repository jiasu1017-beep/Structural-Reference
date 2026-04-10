# *GASKET THICKNESS BEHAVIOR






### *GASKET THICKNESS BEHAVIOR指定垫片厚度方向行为。

此选项用于定义垫片在厚度方向上的行为。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Property 模块

##### **参考文献：**

- ["使用垫片行为模型直接定义垫片行为，" Abaqus Analysis User's Guide 第 32.6.6 节](../usb/usb-link.md#usb-elm-egasketbehavior)

### **可选参数：**

DEPENDENCIES

将此参数设置为除温度外数据定义中包含的场变量依赖数量。如果省略此参数，则假定数据仅取决于温度。请参阅 ["指定场变量依赖性" in "材料数据定义，" Abaqus Analysis User's Guide 第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，获取更多信息。

DIRECTION

设置 DIRECTION=LOADING（默认）以指定用于定义垫片厚度方向行为的模型的加载曲线。

设置 DIRECTION=UNLOADING 以指定用于定义垫片厚度方向行为的模型的卸载曲线。

TENSILE STIFFNESS FACTOR

将此参数设置为定义拉伸刚度的初始压缩刚度分数。默认值为 103。此参数只能与 DIRECTION=LOADING 一起使用。

TYPE

设置 TYPE=DAMAGE 以定义垫片厚度方向行为的损伤弹性模型。

设置 TYPE=ELASTIC-PLASTIC（默认）以定义垫片厚度方向行为的弹塑性模型。

VARIABLE

设置 VARIABLE=FORCE 以按力与闭合的关系或每单位长度力与闭合的关系来定义行为，具体取决于使用此行为的单元类型。

设置 VARIABLE=STRESS（默认）以按压力与闭合的关系来定义行为。

### **以下参数是可选的、互斥的，只能与 DIRECTION=LOADING 一起使用：**

SLOPE DROP

将此参数设置为加载曲线上定义塑性变形开始的斜率相对下降。默认值为 0.1。

YIELD ONSET

将此参数设置为发生屈服的闭合值。指定值必须对应于加载曲线上斜率减小的点。

### **以压力与闭合的关系定义加载的数据行（DIRECTION=LOADING 和 VARIABLE=STRESS）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于五时需要）：**

根据需要重复此组数据行，以将加载曲线定义为温度和场变量的函数。

### **以力或每单位长度力与闭合的关系定义加载的数据行（DIRECTION=LOADING 和 VARIABLE=FORCE）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于五时需要）：**

根据需要重复此组数据行，以将加载曲线定义为温度和场变量的函数。

### **对于弹塑性模型，以压力与闭合的关系定义卸载的数据行（TYPE=ELASTIC-PLASTIC, DIRECTION=UNLOADING 和 VARIABLE=STRESS）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于四时需要）：**

根据需要重复此组数据行，以将弹塑性模型的卸载曲线定义为温度和场变量的函数。

### **对于弹塑性模型，以力或每单位长度力与闭合的关系定义卸载的数据行（TYPE=ELASTIC-PLASTIC, DIRECTION=UNLOADING 和 VARIABLE=FORCE）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于四时需要）：**

根据需要重复此组数据行，以将弹塑性模型的卸载曲线定义为温度和场变量的函数。

### **对于损伤模型，以压力与闭合的关系定义卸载的数据行（TYPE=DAMAGE, DIRECTION=UNLOADING 和 VARIABLE=STRESS）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于四时需要）：**

根据需要重复此组数据行，以将损伤模型的卸载曲线定义为温度和场变量的函数。

### **对于损伤模型，以力或每单位长度力与闭合的关系定义卸载的数据行（TYPE=DAMAGE, DIRECTION=UNLOADING 和 VARIABLE=FORCE）：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于四时需要）：**

根据需要重复此组数据行，以将损伤模型的卸载曲线定义为温度和场变量的函数。




