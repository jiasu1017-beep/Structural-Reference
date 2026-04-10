# *CYCLIC HARDENING







### *CYCLIC HARDENING指定组合硬化模型的弹性范围大小。

此选项用于定义非线性各向同性/运动硬化模型弹性域的演化。此选项只能与[*PLASTIC](ch16abk14.md)选项结合使用。如果不使用此选项，弹性域在分析过程中保持不变。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **属性模块

##### **参考：**

- ["承受循环载荷的金属模型，" Abaqus 分析用户指南第 23.2.2 节](../usb/usb-link.md#usb-mat-chardening)
- [*PLASTIC](ch16abk14.md)
- ["UHARD，" Abaqus 用户子程序参考指南第 1.1.36 节](../sub/sub-link.md#sub-rtn-uuhard)
- ["VUHARD，" Abaqus 用户子程序参考指南第 1.2.17 节](../sub/sub-link.md#sub-rtn-uexphard)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在循环硬化行为定义中的场变量依赖项数。如果省略此参数，则此行为不依赖于场变量。请参阅["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

PARAMETERS

包含此参数以直接提供材料参数![](../graphics/key_eqn00542.gif)和*b*。

USER

在Abaqus/Standard分析中包含此参数以在用户子程序[`UHARD`](../sub/sub-link.md#sub-xsl-uhard)中定义弹性范围，在Abaqus/Explicit分析中在用户子程序[`VUHARD`](../sub/sub-link.md#sub-xsl-vuhard)中定义。如果通过在关联的[*PLASTIC](ch16abk14.md)选项上使用DATA TYPE=HALF CYCLE指定半循环试验数据来指定运动硬化分量，则不能包含此参数。

### **与USER参数一起使用的可选参数：**

PROPERTIES

将此参数设置为在用户子程序[`UHARD`](../sub/sub-link.md#sub-xsl-uhard)（Abaqus/Standard分析）或[`VUHARD`](../sub/sub-link.md#sub-xsl-vuhard)（Abaqus/Explicit分析）中需要作为数据的属性值数量。默认值为PROPERTIES=0。

### **如果未包含PARAMETERS或USER时的可选参数：**

RATE

将此参数设置为等效塑性应变率![](../graphics/key_eqn00543.gif)，该应力-应变曲线适用于此应变率。

### **用于给出表格化材料数据的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于五时需要）：**

根据需要重复此数据行集，以定义各向同性分量作为塑性应变、温度和其他预定义变量的函数值。

### **用于直接定义材料参数的数据行（PARAMETERS）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于四时需要）：**

根据需要重复此数据行集，以定义材料参数对温度和其他预定义场变量的依赖性。

### **用于带PROPERTIES的USER的数据行：**

**第一行：**

根据需要重复此数据行，以定义所有硬化属性。





