# *CAST IRON PLASTICITY






### *CAST IRON PLASTICITY指定灰铸铁的塑性材料属性。

此选项用于定义灰铸铁的塑性属性。必须与 [*CAST IRON COMPRESSION HARDENING](ch03abk06.md) 和 [*CAST IRON TENSION HARDENING](ch03abk08.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **属性模块

##### **参考：**

- ["铸铁塑性，" Abaqus 分析用户指南第 23.2.10 节](../usb/usb-link.md#usb-mat-ccastironplasticity)
- [*CAST IRON COMPRESSION HARDENING](ch03abk06.md)
- [*CAST IRON TENSION HARDENING](ch03abk08.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在材料属性定义中的场变量依赖项数。如果省略此参数，则假定材料属性仅依赖于温度。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

### **用于定义塑性"泊松比"的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于六时需要）：**

根据需要重复此数据行集，以定义材料参数 ![](../graphics/key_eqn00164.gif) 对温度和场变量的依赖性。




