# *DAMPING CONTROLS





### *DAMPING CONTROLS指定阻尼控制。

此选项用于在Abaqus/Standard中以下分析类型的步骤定义内控制阻尼的类型（粘性、结构）和来源（材料、全局）：
- [*STEADY STATE DYNAMICS](ch18abk34.md)，DIRECT
- [*STEADY STATE DYNAMICS](ch18abk34.md)，SUBSPACE PROJECTION
- [*STEADY STATE DYNAMICS](ch18abk34.md) 支持非对角阻尼
- [*MODAL DYNAMIC](ch13abk18.md) 支持非对角阻尼
- [*MATRIX GENERATE](ch13abk12.md)
- [*SUBSTRUCTURE GENERATE](ch18abk42.md)

阻尼可以在材料级别使用 [*DAMPING](ch04abk06.md) 定义；在单元级别使用 [*SPRING](ch18abk29.md)、COMPLEX STIFFNESS 或 [*CONNECTOR DAMPING](ch03abk39.md) 定义；对于声学单元使用 [*ACOUSTIC MEDIUM](ch01abk02.md)、VOLUMETRIC DRAG；或使用声阻抗定义（[*IMPEDANCE](ch09abk01.md) 和 [*SIMPEDANCE](ch18abk17.md)）。阻尼使用 [*GLOBAL DAMPING](ch07abk15.md) 选项在全局级别定义。[*DAMPING CONTROLS](ch04abk07.md) 选项控制哪些提供的阻尼选项将在当前步骤或子结构内参与。

[*DAMPING CONTROLS](ch04abk07.md) 选项还用于在使用考虑阻尼的子结构的所有分析程序中的 [*SUBSTRUCTURE PROPERTY](ch18abk46.md) 选项下定义子结构阻尼的类型和来源。在子结构属性定义中使用此选项的规则与在步骤定义中使用它的规则相同（有关详细信息，请参见Abaqus分析用户指南第10.1.1节中的["定义子结构阻尼"](../usb/usb-link.md#usb-anl-asuperelements-damping)）。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据或历史数据  

**级别：**部件、部件实例  

**Abaqus/CAE：**仅在子结构生成的步骤模块中支持。

##### **参考：**

- ["材料阻尼，" Abaqus分析用户指南第26.1.1节](../usb/usb-link.md#usb-mat-cdampingopt)
- ["动态分析中的阻尼" 位于 "动态分析程序：概述，" 第6.3.1节](../usb/usb-link.md#usb-anl-adynamicproc-damp)
- [*FREQUENCY](ch06abk35.md)

### **可选参数：**

STRUCTURAL

将此参数设置为 ELEMENT 以请求仅包含材料和/或单元阻尼属性的结构阻尼矩阵。

将此参数设置为 FACTOR 以请求仅包含全局阻尼因子的结构阻尼矩阵。

将此参数设置为 COMBINED 以请求包含 ELEMENT 和 FACTOR 组合的结构阻尼矩阵。

将此参数设置为 NONE 以在此步骤中排除结构阻尼矩阵。

如果省略此参数或此选项未在步骤定义中使用，则默认使用模型和步骤级别指定的所有结构阻尼。如果同时指定了材料和全局结构阻尼，则使用 COMBINED 阻尼。

如果省略此参数或此选项未作为 [*SUBSTRUCTURE PROPERTY](ch18abk46.md) 的子选项使用，则子结构属性使用 COMBINED 作为默认值，并使用 [*DAMPING](ch04abk06.md)、STRUCTURAL 选项下指定的结构因子。

VISCOUS

将此参数设置为 ELEMENT 以请求仅包含材料和/或单元阻尼属性的粘性阻尼矩阵。

将此参数设置为 FACTOR 以请求仅包含全局阻尼因子的粘性阻尼矩阵。

将此参数设置为 COMBINED 以请求包含 ELEMENT 和 FACTOR 组合的粘性阻尼矩阵。

将此参数设置为 NONE 以在此步骤中排除粘性阻尼矩阵。

如果省略此参数或此选项未在步骤定义中使用，则默认使用模型和步骤级别指定的所有粘性阻尼。如果同时指定了材料和全局阻尼，则使用 COMBINED 阻尼。

如果省略此参数或此选项未作为 [*SUBSTRUCTURE PROPERTY](ch18abk46.md) 的子选项使用，则子结构属性使用 COMBINED 作为默认值，并使用 [*DAMPING](ch04abk06.md)、ALPHA 或 BETA 选项下指定的质量和刚度比例Rayleigh阻尼因子。

**此选项没有关联的数据行。**




