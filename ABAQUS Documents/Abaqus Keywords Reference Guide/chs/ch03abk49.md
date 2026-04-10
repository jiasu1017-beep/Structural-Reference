# *CONNECTOR POTENTIAL






### *CONNECTOR POTENTIAL在连接器单元中指定用户定义的势函数。

此选项用于定义受限的数学函数集，以在连接器可用分量所张成的空间中表示屈服或极限面。它只能与以下选项结合使用：[*CONNECTOR DAMAGE EVOLUTION](ch03abk37.md)、[*CONNECTOR DAMAGE INITIATION](ch03abk38.md)、[*CONNECTOR FRICTION](ch03abk43.md) 或 [*CONNECTOR PLASTICITY](ch03abk48.md)。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["连接类型库，" Abaqus 分析用户指南第 31.1.5 节](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["连接器行为，" Abaqus 分析用户指南第 31.2.1 节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["耦合行为的连接器函数，" Abaqus 分析用户指南第 31.2.4 节](../usb/usb-link.md#usb-elm-econnderivedandpotential)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)
- [*CONNECTOR DAMAGE EVOLUTION](ch03abk37.md)
- [*CONNECTOR DAMAGE INITIATION](ch03abk38.md)
- [*CONNECTOR DERIVED COMPONENT](ch03abk40.md)
- [*CONNECTOR FRICTION](ch03abk43.md)
- [*CONNECTOR PLASTICITY](ch03abk48.md)

### **可选参数：**

EXPONENT

此参数仅在 OPERATOR=SUM 时才能使用。

将此参数设置为势定义中总体指数的倒数，![](../graphics/key_eqn00135.gif)。![](../graphics/key_eqn00135.gif) 必须是正数。默认值为 ![](../graphics/key_eqn00351.gif)。

OPERATOR

设置 OPERATOR=SUM（默认）以将势定义为每个数据行上定义的贡献之和。

设置 OPERATOR=MAX 以将势定义为产生最大值的数据行的贡献。在这种情况下，EXPONENT 参数将被忽略。

### **用于定义势的数据行：**

**第一行：**

根据需要重复此数据行以定义势函数。




