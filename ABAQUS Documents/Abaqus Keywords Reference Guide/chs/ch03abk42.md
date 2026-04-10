# *CONNECTOR FAILURE






### *CONNECTOR FAILURE定义连接器单元的失效准则。

此选项用于定义连接器单元的失效准则。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["连接器行为，" Abaqus 分析用户指南第 31.2.1 节](../usb/usb-link.md#usb-elm-econnectorbehavior)
- ["连接类型库，" Abaqus 分析用户指南第 31.1.5 节](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- [*CONNECTOR BEHAVIOR](ch03abk35.md)

### **必需参数：**

COMPONENT

将此参数设置为在 Abaqus/Standard 中定义失效准则的连接器分量号；只能选择可用的相对运动分量。在 Abaqus/Explicit 中可以指定任何连接器分量号。请参阅 ["连接类型库，" Abaqus 分析用户指南第 31.1.5 节](../usb/usb-link.md#usb-elm-econnectortypelibrary)，了解相对运动分量的连接器分量定义。

### **可选参数：**

RELEASE

在 Abaqus/Standard 中，当失效准则满足时，将此参数设置为 ALL（默认）以释放所有可用的相对运动分量。在 Abaqus/Explicit 中，当失效准则满足时，将此参数设置为 ALL（默认）以释放所有分量（可用的或约束的）。

在 Abaqus/Standard 中，当失效准则满足时，将此参数设置为相对运动分量号，以仅释放该分量。在 Abaqus/Explicit 中，当失效准则满足时，将此参数设置为一个分量号，以仅释放该分量。

### **用于定义失效准则的数据行：**

**第一行（也是唯一一行）：**




