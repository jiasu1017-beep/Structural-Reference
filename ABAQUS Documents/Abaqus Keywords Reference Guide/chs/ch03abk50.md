# *CONNECTOR SECTION






### *CONNECTOR SECTION为连接器单元指定连接属性。

此选项用于定义连接器单元的属性。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例、装配  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["连接器单元，" Abaqus 分析用户指南第 31.1.2 节](../usb/usb-link.md#usb-elm-econnectorelem)
- ["连接类型库，" Abaqus 分析用户指南第 31.1.5 节](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)

### **必需参数：**

ELSET

将此参数设置为包含正在为其定义连接属性的连接器单元的单元集名称。

### **可选参数：**

BEHAVIOR

将此参数设置为定义这些连接器单元的连接器行为名称。如果省略此参数，则连接器单元的行为仅由运动约束决定。

CONTROLS

此参数仅适用于 Abaqus/Standard 分析。

将此参数设置为截面控制定义的名称（请参阅 ["截面控制，" Abaqus 分析用户指南第 27.1.4 节](../usb/usb-link.md#usb-elm-esectioncontrol)），用于连接器单元。

截面控制可用于指定连接器单元完全失效后是否应将其删除。如果省略此参数，失效的单元将不会被删除。截面控制还可用于指定标量退化（损伤）参数 ![](../graphics/key_eqn00358.gif) 的最大值，并可指定粘性阻尼或正则化的粘性系数 ![](../graphics/key_eqn00195.gif)。

ELIMINATION

此参数仅适用于 Abaqus/Explicit 分析。

如果关联连接器单元的约束或动力 forces/moments 将直接在 Abaqus/Explicit 的隐式约束求解器中求解，则设置 ELIMINATION=NO（默认）。

如果关联连接器单元的约束或动力 forces/moments 将使用缩聚技术求解，则设置 ELIMINATION=YES。

### **用于定义连接属性的数据行：**

**第一行：**

**第二行（可选）：**

如果未指定两个方向中的任何一个且省略了第三行，则省略第二行。如果未指定两个方向中的任何一个且包含了第三行，则保留空白。

**SLIPRING 连接类型的第三行（可选）：**

如果未指定任何数据，则省略第三行。

**RETRACTOR 或 FLOW-CONVERTER 连接类型的第三行（可选）：**

如果未指定任何数据，则省略第三行。




