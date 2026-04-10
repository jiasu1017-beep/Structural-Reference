# *GAP ELECTRICAL CONDUCTANCE






### *GAP ELECTRICAL CONDUCTANCE指定表面之间的电导。

此选项用于在耦合热-电或耦合热-电-结构模拟的表面相互作用模型中引入间隙电导。它必须与 [*SURFACE INTERACTION](ch18abk50.md) 选项一起使用。

**产品：** Abaqus/Standard  

**类型：** 模型数据  

**级别：** 模型  

##### **参考文献：**

- ["完全耦合热应力分析，" Abaqus Analysis User's Guide 第 6.5.3 节](../usb/usb-link.md#usb-anl-acouptempdisp)
- ["完全耦合热-电-结构分析，" Abaqus Analysis User's Guide 第 6.7.4 节](../usb/usb-link.md#usb-anl-acoupthermalelecstruct)
- ["电接触特性，" Abaqus Analysis User's Guide 第 37.3.1 节](../usb/usb-link.md#usb-cni-ajouleheatinteraction)
- [*SURFACE INTERACTION](ch18abk50.md)
- ["GAPELECTR，" Abaqus User Subroutines Reference Guide 第 1.1.11 节](../sub/sub-link.md#sub-rtn-ugapelectr)

### **可选参数：**

DEPENDENCIES

将此参数设置为 ![](../graphics/key_eqn00759.gif) 所依赖的场变量数量。

PRESSURE

包含此参数以指示 ![](../graphics/key_eqn00759.gif) 是表面之间接触压力 *p* 的函数。省略此参数以将 ![](../graphics/key_eqn00759.gif) 定义为表面之间间隙 *d* 的函数。

USER

包含此参数以在用户子程序 [`GAPELECTR`](../sub/sub-link.md#sub-xsl-gapelectr) 中定义 ![](../graphics/key_eqn00759.gif)。在这种情况下，DEPENDENCIES 参数和任何数据行都被忽略。

### **直接定义间隙电导的数据行：**

**第一行：**

根据需要重复此数据行，以定义间隙电导对表面分离、平均表面温度以及表面上任何预定义场变量的平均值的依赖关系。




