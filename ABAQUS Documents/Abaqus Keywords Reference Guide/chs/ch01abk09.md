# *AMPLITUDE





### *AMPLITUDE定义振幅曲线。

此选项允许在整个step中给出载荷、位移和其他规定变量大小的任意时间（在Abaqus/Standard分析中为频率）变化。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**模型或历史数据

**级别：**模型、Step

**Abaqus/CAE：**Amplitude工具集；不支持气泡载荷。类似功能在Interaction模块中可用。

##### **参考：**

- ["振幅曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此振幅曲线。

### **可选参数：**

DEFINITION

设置DEFINITION=TABULAR（默认值）以表格形式给出振幅-时间（或振幅-频率）定义。

设置DEFINITION=EQUALLY SPACED、PERIODIC、MODULATED、DECAY、SMOOTH STEP、SOLUTION DEPENDENT或BUBBLE以根据["振幅曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)中给出的定义来定义振幅。

设置DEFINITION=USER以通过用户子程序[`UAMP`](../sub/sub-link.md#sub-xsl-uamp)和[`VUAMP`](../sub/sub-link.md#sub-xsl-vuamp)定义振幅。

设置DEFINITION=ACTUATOR以通过与逻辑建模程序的协同仿真定义振幅。

BUBBLE、SOLUTION DEPENDENT、USER和ACTUATOR的参数设置在Abaqus/CFD分析中不可用。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。参见["输入语法规则，" Abaqus Analysis User's Guide第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类文件名的语法。如果省略此参数，则假定数据跟在关键字行之后。

如果DEFINITION=USER或DEFINITION=ACTUATOR，则不能使用此参数。

SCALEX

将此参数设置为时间值要缩放的值。默认值为1。

如果DEFINITION=SOLUTION DEPENDENT、BUBBLE、USER或ACTUATOR，则不能使用此参数。

SCALEY

将此参数设置为振幅值要缩放的值。默认值为1。

如果DEFINITION=SOLUTION DEPENDENT、BUBBLE或USER，则不能使用此参数。

SHIFTX

将此参数设置为时间值要偏移的值。默认值为0。

如果DEFINITION=SOLUTION DEPENDENT、BUBBLE、USER或ACTUATOR，则不能使用此参数。

SHIFTY

将此参数设置为振幅值要偏移的值。默认值为0。

如果DEFINITION=SOLUTION DEPENDENT、BUBBLE或USER，则不能使用此参数。

TIME

设置TIME=STEP TIME（默认值）表示step时间。如果振幅被引用的step在频域中，STEP TIME对应于频率。

设置TIME=TOTAL TIME表示在所有非扰动分析step中累积的总时间。

参见["约定，" Abaqus Analysis User's Guide第1.2.2节](../usb/usb-link.md#usb-int-iconventions)，了解这些时间度量的讨论。

VALUE

设置VALUE=RELATIVE（默认值）表示相对大小定义。

设置VALUE=ABSOLUTE表示直接输入绝对大小。在这种情况下，载荷选项中的数据行值将被忽略。由于场定义中给出的值被忽略， absolute振幅值将用于定义温度和梯度。因此，当为连接到梁和壳元素的节点指定温度或预定义场变量时，不应使用VALUE=ABSOLUTE，其截面定义包括TEMPERATURE=GRADIENTS（默认值）。

### **DEFINITION=EQUALLY SPACED时的必需参数：**

FIXED INTERVAL

将此参数设置为将给出振幅数据的固定时间（或频率）间隔。

### **DEFINITION=EQUALLY SPACED时的可选参数：**

BEGIN

将此参数设置为给出第一个振幅的时间（或最低频率）。默认值为BEGIN=0.0。

### **DEFINITION=TABULAR或DEFINITION=EQUALLY SPACED时的可选参数：**

SMOOTH

将此参数设置为在每个时间点前后的一部分时间间隔的值，在需要振幅定义的时间导数的情况下，将分段线性时间变化替换为平滑二次时间变化。默认值为Abaqus/Standard中SMOOTH=0.25，Abaqus/Explicit中SMOOTH=0.0。允许范围为0.0 ![](../graphics/key_eqn00016.gif) SMOOTH ![](../graphics/key_eqn00017.gif) 0.5。对于包含大时间间隔的振幅定义，建议值为0.05，以避免与给定定义的严重偏差。此参数仅在需要时间导数时适用（用于直接积分动态分析中的位移或速度边界条件），并对此选项的所有其他用途忽略。此参数在Abaqus/CFD中不可用。

### **DEFINITION=USER时的可选参数：**

PROPERTIES

将此参数设置为输入的属性数量。这些属性可用于用户子程序[`UAMP`](../sub/sub-link.md#sub-xsl-uamp)和[`VUAMP`](../sub/sub-link.md#sub-xsl-vuamp)。可以在数据行上或直接在用户子程序中定义属性。默认值为PROPERTIES=0。

VARIABLES

将此参数设置为必须与此振幅定义一起存储的解决方案相关状态变量的数量。其值必须大于0。默认值为VARIABLES=1。

### **DEFINITION=TABULAR或DEFINITION=SMOOTH STEP的数据行，每行四个数据点（每行八个条目）：**

**第一行：**

根据需要重复此数据行。每行（最后一行除外）必须正好有四个时间/大小或频率/大小数据对。

### **DEFINITION=TABULAR或DEFINITION=SMOOTH STEP的数据行，每行一个数据对（每行两个条目）：**

**第一行：**

根据需要重复此数据行。每行必须正好有一个时间/大小或频率/大小数据对。

### **DEFINITION=EQUALLY SPACED的数据行，每行八个值：**

**第一行：**

根据需要重复此数据行。每行（最后一行除外）必须正好有八个振幅值。

### **DEFINITION=EQUALLY SPACED的数据行，每行一个值：**

**第一行：**

根据需要重复此数据行。每行必须正好有一个振幅值。

### **定义周期数据的数据行（DEFINITION=PERIODIC）：**

**第一行：**

**第二行：**

根据需要重复此数据行。每行（最后一行除外）必须正好有八个条目，总共2*N个条目。

### **定义调制数据的数据行（DEFINITION=MODULATED）：**

**第一行（也是唯一一行）：**

### **定义指数衰减的数据行（DEFINITION=DECAY）：**

**第一行（也是唯一一行）：**

### **定义解决方案相关振幅的数据行（DEFINITION=SOLUTION DEPENDENT）：**

**第一行（也是唯一一行）：**

### **定义气泡载荷的数据行（DEFINITION=BUBBLE）：**

**第一行：**

**第二行：**

**第三行：**

**第四行：**

### **当PROPERTIES与DEFINITION=USER一起指定时，定义用户振幅属性的数据行：**

**第一行：**

根据需要重复此数据行以定义所有振幅属性。

### **如果DEFINITION=ACTUATOR，则没有数据行。**