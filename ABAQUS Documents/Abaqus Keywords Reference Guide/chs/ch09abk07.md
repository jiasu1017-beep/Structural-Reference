# *IMPORT NSET






### *IMPORT NSET从先前的 Abaqus/Explicit 或 Abaqus/Standard 分析导入节点集定义。

此选项用于导入在先前的 Abaqus/Explicit 或 Abaqus/Standard 分析中定义的节点集定义。如果使用了 [*IMPORT NSET](ch09abk07.md) 选项，它必须出现在 [*IMPORT](ch09abk04.md) 选项之后。如果省略此选项或指定时没有任何数据行，则将导入与分析相关的所有节点集。

**产品：** Abaqus/Standard  Abaqus/Explicit  

**类型：** 模型数据  

**级别：** 模型  

##### **参考文献：**

- ["在 Abaqus/Explicit 和 Abaqus/Standard 之间传输结果，" Abaqus Analysis User's Guide 第 9.2.2 节](../usb/usb-link.md#usb-anl-aexptostd)
- [*IMPORT](ch09abk04.md)

**此选项没有关联的参数。**

### **指定要导入的节点集定义的数据行：**

**第一行：**

根据需要重复此数据行，以指定要导入的节点集定义。每行最多可列出 16 个节点集。




