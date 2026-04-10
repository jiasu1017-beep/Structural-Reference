# *USER DEFINED FIELD





### *USER DEFINED FIELD在材料点重新定义场变量。

此材料选项用于允许通过用户子程序[`USDFLD`](../sub/sub-link.md#sub-xsl-usdfld)（Abaqus/Standard分析）或用户子程序[`VUSDFLD`](../sub/sub-link.md#sub-xsl-vusdfld)（Abaqus/Explicit分析）在增量内重新定义材料点处的场变量值。如果使用[*USER DEFINED FIELD](ch20abk06.md)选项，它必须出现在[*MATERIAL](ch13abk08.md)定义中（["材料数据定义," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)）。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["USDFLD," Section 1.1.50 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uusdfld)
- ["VUSDFLD," Section 1.2.22 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uexpusdfld)

### **可选参数：**

PROPERTIES

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为正在输入的属性数量。这些属性可用于用户子程序[`VUSDFLD`](../sub/sub-link.md#sub-xsl-vusdfld)。

### **指定PROPERTIES时定义材料属性的数据行：**

**第一行：**

根据需要重复此数据行，以定义所有材料属性。





