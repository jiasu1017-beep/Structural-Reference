# *INCLUDE






### *INCLUDE引用包含 Abaqus 输入数据的外部文件。

此选项用于引用包含部分 Abaqus 输入文件的外部文件。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：** 模型或历史数据  

**级别：** 零件、零件实例、装配、模型、步骤  

**Abaqus/CAE：** Abaqus/CAE 中的多个输入数据选项提供了引用外部文件的功能；例如，材料编辑器可以从 ASCII 文件读取材料特性。

##### **参考文献：**

- ["在 Abaqus 中定义模型，" Abaqus Analysis User's Guide 第 1.3.1 节](../usb/usb-link.md#usb-int-imodel)

### **必需参数：**

INPUT

将此参数设置为包含输入数据的文件名。请参阅 ["输入语法规则，" Abaqus Analysis User's Guide 第 1.2.1 节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。

### **可选参数：**

PASSWORD

当外部文件已加密时，将此参数设置为文件的密码。密码区分大小写。

**此选项没有关联的数据行。**




