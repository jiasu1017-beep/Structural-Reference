# *CONTACT INCLUSIONS






### *CONTACT INCLUSIONS指定要包含在通用接触域中的自接触表面或表面配对。

此选项用于指定应由通用接触算法考虑的自接触表面和表面配对。应与 [*CONTACT](ch03abk54.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**Abaqus/Standard 中的模型数据；Abaqus/Explicit 中的模型数据或历史数据  

**级别：**Abaqus/Standard 中的模型；Abaqus/Explicit 中的模型或步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["在 Abaqus/Standard 中定义通用接触相互作用，" Abaqus 分析用户指南第 36.2.1 节](../usb/usb-link.md#usb-cni-acontactgeneralstd)
- ["在 Abaqus/Explicit 中定义通用接触相互作用，" Abaqus 分析用户指南第 36.4.1 节](../usb/usb-link.md#usb-cni-acontactgeneral)
- [*CONTACT](ch03abk54.md)

### **可选参数：**

ALL EXTERIOR

包含此参数以为默认未命名的全包容表面指定自接触，该表面包含所有基于单元的表面小平面，并且在 Abaqus/Explicit 中仅包含所有解析刚性表面。这是定义接触域最简单的方法。使用此参数时，选项不应有数据行。

如果省略此参数，则必须在数据行上指定接触表面。

### **如果省略了 ALL EXTERIOR 参数，则用于指定接触包含的数据行：**

**第一行：**

根据需要重复此数据行。




