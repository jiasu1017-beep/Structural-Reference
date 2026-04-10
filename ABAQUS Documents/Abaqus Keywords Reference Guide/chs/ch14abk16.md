# *NORMAL









### *NORMAL指定特定的法线方向。

此选项用于定义单元的替代节点法线。在Abaqus/Standard分析中，它也可用于定义接触表面的替代法线。

**产品：**Abaqus/Standard  Abaqus/Explicit  

**类型：**模型数据  

**级别：**部件、部件实例、装配  

##### **参考：**

- ["节点处的法线定义，" Abaqus Analysis User's Guide第2.1.4节](../usb/usb-link.md#usb-int-inodalnormals)

### **可选参数：**

TYPE

设置TYPE=ELEMENT（默认）以允许单元的替代法线定义。

设置TYPE=CONTACT SURFACE以允许Abaqus/Standard分析中接触表面的替代法线定义。

### **为单元定义法线的数据行（TYPE=ELEMENT）：**

**第一行：**

根据需要重复此数据行以定义法线。

### **为接触表面定义法线的数据行（TYPE=CONTACT SURFACE）：**

**第一行：**

根据需要重复此数据行以定义法线。