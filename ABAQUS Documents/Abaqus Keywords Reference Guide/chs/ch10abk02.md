# *JOINT






### *JOINT为 JOINTC 单元定义特性。

此选项用于为 JOINTC 单元定义特性。[*DASHPOT](ch04abk08.md) 和 [*SPRING](ch18abk29.md) 选项必须紧跟此选项。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 零件、零件实例  

**Abaqus/CAE：** 不支持；通过建模连接器可以提供类似功能。

##### **参考文献：**

- ["柔性关节单元，" Abaqus Analysis User's Guide 第 32.3.1 节](../usb/usb-link.md#usb-elm-ejoint)
- [*DASHPOT](ch04abk08.md)
- [*SPRING](ch18abk29.md)

### **必需参数：**

ELSET

将此参数设置为包含正在定义其特性的 JOINTC 单元的单元集名称。

### **可选参数：**

ORIENTATION

将此参数设置为给 [*ORIENTATION](ch15abk01.md) 定义（["方向，" Abaqus Analysis User's Guide 第 2.2.5 节](../usb/usb-link.md#usb-int-corientation)）的名称，该定义指定关节中局部系统的初始方向。

**此选项没有关联的数据行；相反，根据需要包含 [*SPRING](ch18abk29.md) 和 [*DASHPOT](ch04abk08.md) 选项以定义关节行为。**




