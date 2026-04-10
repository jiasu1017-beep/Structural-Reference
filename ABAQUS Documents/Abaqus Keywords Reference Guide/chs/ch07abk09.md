# *GASKET CONTACT AREA






### *GASKET CONTACT AREA为平均压力输出指定垫片接触面积或接触宽度。

此选项用于定义接触面积或接触宽度与闭合的关系曲线，以通过变量 CS11 输出平均压力。它只能与垫片链接单元和三维线垫片单元一起使用，这些单元的厚度方向行为以力或每单位长度力来定义。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Property 模块

##### **参考文献：**

- ["使用垫片行为模型直接定义垫片行为，" Abaqus Analysis User's Guide 第 32.6.6 节](../usb/usb-link.md#usb-elm-egasketbehavior)

### **可选参数：**

DEPENDENCIES

将此参数设置为除温度外数据定义中包含的场变量依赖数量。如果省略此参数，则假定数据仅取决于温度。请参阅 ["指定场变量依赖性" in "材料数据定义，" Abaqus Analysis User's Guide 第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，获取更多信息。

### **为平均压力输出定义接触面积的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数的值大于五时需要）：**

根据需要重复此组数据行，以将接触面积或宽度与闭合的关系曲线定义为温度和场变量的函数。




