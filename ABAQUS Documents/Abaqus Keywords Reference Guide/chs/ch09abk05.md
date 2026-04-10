# *IMPORT CONTROLS






### *IMPORT CONTROLS指定导入模型和结果数据时使用的容差。

此选项用于在使用 [*IMPORT](ch09abk04.md), UPDATE=YES 选项时指定 Abaqus/Standard 或 Abaqus/Explicit 中壳法线误差检查的容差。如果使用了 [*IMPORT CONTROLS](ch09abk05.md) 选项，它必须出现在 [*IMPORT](ch09abk04.md) 选项之后。

**产品：** Abaqus/Standard  Abaqus/Explicit  

**类型：** 模型数据  

**级别：** 模型  

##### **参考文献：**

- ["在 Abaqus/Explicit 和 Abaqus/Standard 之间传输结果，" Abaqus Analysis User's Guide 第 9.2.2 节](../usb/usb-link.md#usb-anl-aexptostd)
- [*IMPORT](ch09abk04.md)

### **必需参数：**

NORMAL TOL

将此参数设置为壳法线误差检查所需的容差。默认值为 0.1。

**此选项没有关联的数据行。**




