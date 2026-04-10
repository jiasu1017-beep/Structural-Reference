# *SUBSTRUCTURE COPY





### *SUBSTRUCTURE COPY复制子结构定义。

此选项用于将子结构定义从一个库复制到另一个库，或在同一库内从一个子结构标识符复制到另一个。

**产品：**Abaqus/Standard

**类型：**模型数据

**级别：**此选项在以部件实例装配定义的模型中不受支持。

##### **参考：**

- ["Using substructures," Section 10.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asuperelements)

### **必需参数：**

NEW TYPE

将此参数设置为正在创建的子结构的TYPE标识符。

OLD TYPE

将此参数设置为正在复制的子结构的TYPE标识符。

### **可选参数：**

NEW LIBRARY

将此参数设置为存储子结构的子结构库名称。默认库名称为*jobname*。

OLD LIBRARY

将此参数设置为正在从中复制子结构的子结构库名称。默认库名称为*jobname*。

**此选项没有关联的数据行。**




