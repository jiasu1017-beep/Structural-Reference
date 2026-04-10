# *FLUID EXCHANGE





### *FLUID EXCHANGE定义流体交换。

此选项用于定义两个流体腔之间或流体腔与其环境之间的流体交换。

**产品：**Abaqus/Standard   Abaqus/Explicit   Abaqus/CAE   

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["流体交换定义，" Abaqus Analysis User's Guide第11.5.3节](../usb/usb-link.md#usb-anl-afluidcavityexchange)
- [*FLUID EXCHANGE PROPERTY](ch06abk23.md)

### **必需参数：**

NAME

将此参数设置为用于引用流体交换定义的标签。

PROPERTY

将此参数设置为定义流体交换属性的[*FLUID EXCHANGE PROPERTY](ch06abk23.md)选项的名称。

### **可选参数：**

CAVITY PRESSURE

此参数仅适用于Abaqus/Explicit分析。

设置CAVITY PRESSURE=SURFACE（默认）以指示应将流体腔中的流体压力施加于用于流体交换的表面上。

设置CAVITY PRESSURE=PERIMETER以将流体交换表面标识为开放通风口，并将流体压力作为等效载荷施加在表面的周长上。

CONSTANTS

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为在用户子程序[`VUFLUIDEXCHEFFAREA`](../sub/sub-link.md#sub-xsl-vufluidexcheffarea)中定义流体交换有效面积所需的数据流体交换常数数量。默认值为CONSTANTS=0。

EFFECTIVE AREA

此参数仅适用于Abaqus/Explicit分析。

将EFFECTIVE AREA设置为交换的总面积。如果省略SURFACE参数，则默认值为1.0。否则，默认值等于表面的面积。如果同时指定了EFFECTIVE AREA和SURFACE参数，则表面的面积仅用于确定阻塞程度，有效面积会因表面被阻塞而减少。

设置EFFECTIVE AREA=USER以指示将使用Abaqus/Explicit中的用户子程序[`VUFLUIDEXCHEFFAREA`](../sub/sub-link.md#sub-xsl-vufluidexcheffarea)来定义考虑局部材料状态的表面有效面积。如果使用用户子程序[`VUFLUIDEXCHEFFAREA`](../sub/sub-link.md#sub-xsl-vufluidexcheffarea)，则需要SURFACE参数。

SURFACE

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为流体腔上可以进行流体和/或热能交换的表面名称。如果省略此参数，则使用EFFECTIVE AREA参数指定的值进行交换。如果EFFECTIVE AREA=USER，则需要此参数。

### **定义流体交换的数据行：**

**第一行：**

**第二行（仅在使用CONSTANTS参数时需要）：**

根据需要重复此数据行，以定义所有属性。
