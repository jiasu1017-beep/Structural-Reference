# *EXPANSION









### *EXPANSION指定热膨胀或场膨胀。

此选项用于为材料或垫片行为定义Abaqus/Standard中的热膨胀或场膨胀。在Abaqus/Standard分析中，可以使用分布（["分布定义，" Abaqus分析用户指南第2.8.1节](../usb/usb-link.md#usb-int-adefiningdistributions)）为实体连续体单元定义空间变化的热膨胀。在Abaqus/CFD分析中，此选项用于定义热膨胀以计算浮力。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**属性模块

##### **参考：**

- ["热膨胀，" Abaqus分析用户指南第26.1.2节](../usb/usb-link.md#usb-mat-cthermalexpan)
- ["场膨胀，" Abaqus分析用户指南第26.1.3节](../usb/usb-link.md#usb-mat-cfieldexpansion)
- ["UEXPAN，" Abaqus用户子程序参考指南第1.1.30节](../sub/sub-link.md#sub-rtn-uuexpan)

### **可选参数：**

DEPENDENCIES

此参数仅适用于Abaqus/Standard和Abaqus/Explicit分析。

将此参数设置为除温度外系数所依赖的场变量数。如果省略此参数，则假定热膨胀是常数或仅取决于温度。

如果包含了USER参数，或者在Abaqus/Standard分析中使用分布定义空间变化的热膨胀，则此参数不相关（请参见["分布定义，" Abaqus分析用户指南第2.8.1节](../usb/usb-link.md#usb-int-adefiningdistributions)）。

FIELD

此参数仅适用于Abaqus/Standard分析。

将此参数设置为正在为其定义场膨胀的预定义场变量编号。

PORE FLUID

此参数仅适用于Abaqus/Standard分析。

如果正在定义多孔介质中孔隙流体的热膨胀，则包含此参数。流体的热膨胀必须是各向同性的，因此如果包含此参数，则不能使用TYPE=ORTHO和TYPE=ANISO。

TYPE

设置 TYPE=ISO（默认）来定义各向同性膨胀。在Abaqus/CFD分析中唯一可用的选项是TYPE=ISO。

设置 TYPE=ORTHO 来定义正交各向异性膨胀。

设置 TYPE=ANISO 在Abaqus/Standard分析中定义完全各向异性膨胀。

设置 TYPE=SHORT FIBER 来为每个壳单元中的每一层定义层合板材料属性。此参数设置仅在使用Abaqus/Standard与**abaqus moldflow**执行程序结合时适用。任何数据行都将被忽略。材料属性将从标识为*jobid*`.shf`的ASCII中性文件读取。请参见["将Moldflow数据转换到Abaqus输入文件，" Abaqus分析用户指南第3.2.37节](../usb/usb-link.md#usb-int-dmflabaproc)，获取更多信息。

在Abaqus/Standard分析中，可以使用分布定义空间变化的各向同性、正交各向异性或各向异性膨胀。使用分布时，必须使用TYPE参数来指示热膨胀的各向异性水平。各向异性水平必须与分布中定义的一致。请参见["分布定义，" Abaqus分析用户指南第2.8.1节](../usb/usb-link.md#usb-int-adefiningdistributions)。

USER

此参数仅适用于Abaqus/Standard分析。

包含此参数以指示将使用用户子程序[`UEXPAN`](../sub/sub-link.md#sub-xsl-uexpan)来定义热应变增量。应使用TYPE参数来指示热膨胀的各向异性水平。PORE FLUID参数也可用于指示正在定义孔隙流体的热膨胀。

如果使用此参数，则DEPENDENCIES和ZERO参数不相关。

ZERO

如果热膨胀取决于温度或场变量，则将此参数设置为 ![](../graphics/key_eqn00086.gif) 的值。默认值为 ZERO=0。

如果包含USER参数，则此参数不相关。

在Abaqus/CFD中，此参数应设置为用于浮力Boussinesq近似的参考温度。

### **定义各向同性热膨胀系数的数据行（省略USER参数的TYPE=ISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将热膨胀系数定义为温度和其他预定义场变量的函数。

### **定义正交各向异性热膨胀系数的数据行（省略USER参数的TYPE=ORTHO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将热膨胀系数定义为温度和其他预定义场变量的函数。

### **定义各向异性热膨胀系数的数据行（省略USER参数的TYPE=ANISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于一时需要）：**

根据需要重复此组数据行，以将热膨胀系数定义为温度和其他预定义场变量的函数。

### **在Abaqus/Standard分析中使用分布定义空间变化热膨胀的数据行：**

**第一行（也是唯一一行）：**

### **通过用户子程序定义热膨胀（包含USER参数）：**

当指定USER参数时，此选项不使用数据行。相反，必须使用用户子程序[`UEXPAN`](../sub/sub-link.md#sub-xsl-uexpan)来定义热膨胀。

### **定义各向同性场膨胀系数的数据行（省略USER参数的TYPE=ISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将场膨胀系数定义为温度和其他预定义场变量的函数。

### **定义正交各向异性场膨胀系数的数据行（省略USER参数的TYPE=ORTHO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将场膨胀系数定义为温度和其他预定义场变量的函数。

### **定义各向异性场膨胀系数的数据行（省略USER参数的TYPE=ANISO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于一时需要）：**

根据需要重复此组数据行，以将场膨胀系数定义为温度和其他预定义场变量的函数。

### **通过用户子程序定义场膨胀（包含USER参数）：**

当指定USER参数时，此选项不使用数据行。相反，必须使用用户子程序[`UEXPAN`](../sub/sub-link.md#sub-xsl-uexpan)来定义场膨胀。




