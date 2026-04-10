# *GLOBAL DAMPING






### *GLOBAL DAMPING指定全局阻尼。

此选项用于为 Abaqus/Standard 中的以下分析步骤提供全局阻尼系数：
- [*COMPLEX FREQUENCY](ch03abk26.md)
- [*MODAL DYNAMIC](ch13abk18.md)
- [*RANDOM RESPONSE](ch17abk07.md)
- [*RESPONSE SPECTRUM](ch17abk15.md)
- [*STEADY STATE DYNAMICS](ch18abk34.md)
- [*STEADY STATE DYNAMICS](ch18abk34.md), DIRECT
- [*STEADY STATE DYNAMICS](ch18abk34.md), SUBSPACE PROJECTION
- [*MATRIX GENERATE](ch13abk12.md)
- [*SUBSTRUCTURE GENERATE](ch18abk42.md)

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 历史数据  

**级别：** 步骤  

**Abaqus/CAE：** 仅在子结构生成时在 Step 模块中支持。

##### **参考文献：**

- ["材料阻尼，" Abaqus Analysis User's Guide 第 26.1.1 节](../usb/usb-link.md#usb-mat-cdampingopt)
- ["动态分析中的阻尼" in "动态分析步骤概述，" Abaqus Analysis User's Guide 第 6.3.1 节](../usb/usb-link.md#usb-anl-adynamicproc-damp)
- ["声学、冲击和耦合声-结构分析，" Abaqus Analysis User's Guide 第 6.10.1 节](../usb/usb-link.md#usb-anl-aacoustic)

### **可选参数：**

ALPHA

将此参数设置为 ![](../graphics/key_eqn00768.gif) 因子，以创建全局 Rayleigh 质量比例阻尼 ![](../graphics/key_eqn00769.gif)，其中 ![](../graphics/key_eqn00770.gif) 表示模型质量矩阵。默认值为 ALPHA=0。（单位为 [T1](../popups/usb-int-iconventions-unitsym.md)。）

BETA

将此参数设置为 ![](../graphics/key_eqn00771.gif) 因子，以创建全局 Rayleigh 刚度比例阻尼 ![](../graphics/key_eqn00772.gif)，其中 ![](../graphics/key_eqn00773.gif) 表示模型刚度矩阵。默认值为 BETA=0。（单位为 [T](../popups/usb-int-iconventions-unitsym.md)。）

FIELD

设置 FIELD=ACOUSTIC 以仅将全局阻尼应用于模型中的声学场。

设置 FIELD=ALL（默认）以将全局阻尼应用于模型中所有有效的位移、旋转和声学场。

设置 FIELD=MECHANICAL 以仅将全局阻尼应用于模型中有效的位移和旋转场。

此参数在使用耦合声-结构模态的基于模态的稳态动态分析中不支持。

STRUCTURAL

将此参数设置为 ![](../graphics/key_eqn00774.gif) 因子，以创建与频率无关的刚度比例结构阻尼 ![](../graphics/key_eqn00775.gif)，其中 ![](../graphics/key_eqn00776.gif) 表示模型刚度矩阵。默认值为 STRUCTURAL=0。

**此选项没有关联的数据行。**




