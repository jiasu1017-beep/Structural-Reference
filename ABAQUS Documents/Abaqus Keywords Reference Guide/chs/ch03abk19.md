# *CLAY PLASTICITY






### *CLAY PLASTICITY指定扩展 Cam-clay 塑性模型。

此选项用于为使用扩展 Cam-clay 塑性模型的弹塑性材料指定材料行为的塑性部分。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **属性模块

##### **参考：**

- ["临界状态（粘土）塑性模型，" Abaqus 分析用户指南第 23.3.4 节](../usb/usb-link.md#usb-mat-cclayplastic)
- [*CLAY HARDENING](ch03abk19.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在 Cam-clay 参数定义中的场变量依赖项数。如果省略此参数，则 Cam-clay 参数可能仅依赖于温度。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

HARDENING

设置 HARDENING=EXPONENTIAL（Abaqus/Standard 默认）以指定指数硬化/软化定律。此硬化定律在 Abaqus/Explicit 中不受支持。

设置 HARDENING=TABULAR（Abaqus/Explicit 的默认和唯一选项）以指定分段线性硬化/软化关系。在这种情况下必须使用 [*CLAY HARDENING](ch03abk19.md) 选项。HARDENING=TABULAR 与 INTERCEPT 参数的使用互斥。

INTERCEPT

此参数仅适用于 Abaqus/Standard 分析。

当指定指数硬化定律时，它用作直接指定初始屈服面大小 ![](../graphics/key_eqn00172.gif) 的替代方法。将此参数设置为 ![](../graphics/key_eqn00173.gif)，即在孔隙比与压力应力对数的图中，默认压缩曲线与孔隙比轴的截距。如果包含此参数，则数据行上给出的 ![](../graphics/key_eqn00172.gif) 值将被忽略。当使用 HARDENING=TABULAR 参数时，此参数不能使用。

### **用于定义 Cam-clay 塑性的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于二时需要）：**

根据需要重复此数据行集，以定义 Cam-clay 参数对温度和其他预定义场变量的依赖性。




