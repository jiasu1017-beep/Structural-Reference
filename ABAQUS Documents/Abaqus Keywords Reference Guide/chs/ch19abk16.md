# *TRS





### *TRS用于定义时间历史粘弹性分析的温度-时间偏移。

此选项只能与[*VISCOELASTIC](ch21abk04.md)选项结合使用，在Abaqus/Explicit中，还要与[*VISCOSITY](ch21abk05.md)选项结合使用。

在Abaqus/Standard分析中，必须通过使用[*VISCOELASTIC](ch21abk04.md)、NONLINEAR选项定义非线性粘弹性，或者必须通过使用[*VISCOELASTIC](ch21abk04.md)、TIME选项在时域中定义粘弹性。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["时域粘弹性," Section 22.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ctimevisco)
- ["并行流变框架," Section 22.8.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cnonlinvisco)
- ["UTRS," Section 1.1.53 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uutrs)
- ["UTRSNETWORK," Section 1.1.54 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uutrsnetwork)
- ["VUTRS," Section 1.2.23 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexputrs)
- [*VISCOELASTIC](ch21abk04.md)
- [*VISCOSITY](ch21abk05.md)

### **可选参数：**

DEFINITION

设置DEFINITION=WLF（默认）以使用Williams-Landel-Ferry近似定义偏移函数。

设置DEFINITION=ARRHENIUS以使用Arrhenius近似定义偏移函数。

设置DEFINITION=USER以在用户子程序中定义偏移函数。在Abaqus/Standard分析中，对于线性粘弹性模型在用户子程序[`UTRS`](../sub/sub-link.md#sub-xsl-utrs)中定义偏移函数（参见["时域粘弹性," Section 22.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ctimevisco)），或者对于使用并行流变框架定义的非线性粘弹性模型在用户子程序[`UTRSNETWORK`](../sub/sub-link.md#sub-xsl-utrsnetwork)中定义（参见["并行流变框架," Section 22.8.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cnonlinvisco)）。在Abaqus/Explicit分析中，对于线性粘弹性模型在用户子程序[`VUTRS`](../sub/sub-link.md#sub-xsl-vutrs)中定义偏移函数。

PROPERTIES

此参数仅适用于Abaqus/Explicit分析和Abaqus/Standard分析（如果使用用户子程序[`UTRSNETWORK`](../sub/sub-link.md#sub-xsl-utrsnetwork)定义偏移函数）。

将此参数设置为正在输入的属性数量。这些属性可用于用户子程序[`VUTRS`](../sub/sub-link.md#sub-xsl-vutrs)或[`UTRSNETWORK`](../sub/sub-link.md#sub-xsl-utrsnetwork)。

### **使用Williams-Landel-Ferry近似定义偏移函数的数据行：**

**第一行（也是唯一行）：**

### **使用Arrhenius近似定义偏移函数的数据行：**

**第一行（也是唯一行）：**

此外，您需要使用[*PHYSICAL CONSTANTS](ch16abk09.md)选项指定通用气体常数和绝对零度。

### **为用户定义的偏移函数（DEFINITION=USER）定义材料属性的数据行：**

**如果PROPERTIES参数被省略或设置为0，则不需要数据行。否则，第一行：**

根据需要重复此数据行，以定义所有材料属性。





