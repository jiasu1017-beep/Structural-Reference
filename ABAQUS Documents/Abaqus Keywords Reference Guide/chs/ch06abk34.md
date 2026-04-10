# *FRAME SECTION





### *FRAME SECTION指定框架截面。

此选项用于定义框架单元的横截面。由于框架截面几何和材料描述相结合，因此此选项没有关联的[*MATERIAL](ch13abk08.md)参考。

**产品：**Abaqus/Standard   

**类型：**模型数据  

**级别：**部件，部件实例  

##### **参考：**

- ["框架单元，" Abaqus Analysis User's Guide第29.4.1节](../usb/usb-link.md#usb-elm-eframe)
- ["框架截面行为，" Abaqus Analysis User's Guide第29.4.2节](../usb/usb-link.md#usb-elm-eusingframesection)

### **必需参数：**

ELSET

将此参数设置为定义截面的单元集名称。

### **可选参数：**

BUCKLING

包含此参数以指示允许这些单元产生屈曲 strut 响应，并使用默认屈曲包络线。当包含此参数时，需要YIELD STRESS参数以确定屈曲包络线上的![](../graphics/key_eqn00138.gif)和![](../graphics/key_eqn00730.gif)。

要包含具有非默认屈曲包络线的屈曲 strut 响应，请将[*BUCKLING ENVELOPE](ch02abk17.md)选项与[*FRAME SECTION](ch06abk34.md)选项和YIELD STRESS参数结合使用。如果同时存在BUCKLING参数和[*BUCKLING ENVELOPE](ch02abk17.md)选项，则用户定义的屈曲包络线优先。

要使用默认或非默认屈曲包络线为第一和第二截面方向定义有效长度因子和附加长度，请将[*BUCKLING LENGTH](ch02abk18.md)选项与[*FRAME SECTION](ch06abk34.md)选项结合使用。要使用默认或非默认屈曲包络线为第一和第二截面方向定义屈曲折减因子，请将[*BUCKLING REDUCTION FACTORS](ch02abk19.md)选项与[*FRAME SECTION](ch06abk34.md)选项结合使用。

DENSITY

将此参数设置为框架单元材料每单位体积的质量密度。只有当需要单元的质量时（例如在动态分析中或重力载荷下）才需要此参数。

DEPENDENCIES

将此参数设置为除温度外还包括在材料属性定义中的场变量依赖项数。如果省略此参数，则假定属性为常数或仅取决于温度。有关详细信息，请参见["指定场变量依赖"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

PINNED

包含此参数以指示这些单元仅具有单轴响应；即端部具有铰接连接。

如果使用此参数且不存在BUCKLING参数和[*BUCKLING ENVELOPE](ch02abk17.md)选项，则这些单元从分析开始就具有线性弹性单轴响应。如果使用此参数且存在BUCKLING参数或[*BUCKLING ENVELOPE](ch02abk17.md)选项，则这些单元具有单轴响应，在压缩中具有屈曲和后屈曲行为，在拉伸中具有各向同性硬化塑性，如从分析开始时屈曲包络线选项所述。当存在BUCKLING参数或[*BUCKLING ENVELOPE](ch02abk17.md)选项时，[*BUCKLING LENGTH](ch02abk18.md)选项可与此参数结合使用。

此参数不能与PLASTIC DEFAULTS参数或任何[*PLASTIC](ch16abk14.md)选项一起使用。

PLASTIC DEFAULTS

包含此参数以指示包含弹塑性材料响应，并使用基于YIELD STRESS参数定义的屈服应力的默认值创建所有塑性选项。使用此参数时需要YIELD STRESS参数。

要包含具有用户定义塑性材料响应的弹塑性材料响应，请将适当的[*PLASTIC AXIAL](ch16abk15.md)、[*PLASTIC M1](ch16abk16.md)、[*PLASTIC M2](ch16abk17.md)和[*PLASTIC TORQUE](ch16abk18.md)选项中的一个或多个（视情况而定）与[*FRAME SECTION](ch06abk34.md)选项结合使用。如果省略PLASTIC DEFAULTS和YIELD STRESS参数，则仅将指定的那些塑性选项包含在弹塑性材料响应中。

此参数不能与PINNED参数一起使用。

SECTION

将此参数设置为您选择的标准库截面的库截面名称（参见["梁截面库，" Abaqus Analysis User's Guide第29.3.9节](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)）。以下横截面可用于弹性框架单元（当省略弹塑性和屈曲 strut 响应时）：

- BOX，用于矩形空心箱形截面。
- CIRC，用于实心圆形截面。
- GENERAL，用于通用横截面（默认）。
- I，用于工字梁截面。
- PIPE，用于空心圆形截面。
- RECT，用于实心矩形截面。

对于弹塑性材料响应，唯一可用的塑性相互作用表面是椭球体，仅建议用于PIPE截面。其他截面类型（除GENERAL截面外）可根据用户判断使用。

对于屈曲 strut 响应，仅PIPE截面可用。

YIELD STRESS

将此参数设置为构成截面的材料的屈服应力。

当使用PLASTIC DEFAULTS参数定义默认弹塑性材料响应时，以及当使用[*BUCKLING ENVELOPE](ch02abk17.md)选项或BUCKLING参数对屈曲 strut 响应进行建模时，需要此参数。

ZERO

如果需要，则将此参数设置为热膨胀的参考温度（![](../graphics/key_eqn00086.gif)）。默认值为ZERO=0。

### **SECTION=GENERAL的数据行：**

**第一行：**

**第二行（可选；如果要使用默认值，请输入空行）：**

对于FRAME2D单元，此行上的条目必须为（0, 0, 1）。对于FRAME3D单元，如果第一个单元截面轴不是由单元连接中的附加节点定义的，则默认值为（0, 0, 1）。有关详细信息，请参见["框架单元，" Abaqus Analysis User's Guide第29.4.1节](../usb/usb-link.md#usb-elm-eframe)。

**第三行：**

**后续行（仅当DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将属性定义为温度和其他预定义场变量的函数。

### **BOX、CIRC、I、PIPE和RECT截面的数据行：**

**第一数据行：**

**第二数据行（可选；如果要使用默认值，请输入空行）：**

对于FRAME2D单元，此行上的条目必须为（0, 0, 1）。对于FRAME3D单元，如果第一个单元截面轴不是由单元连接中的附加节点定义的，则默认值为（0, 0, -1）。有关详细信息，请参见["框架单元，" Abaqus Analysis User's Guide第29.4.1节](../usb/usb-link.md#usb-elm-eframe)。

**第三数据行：**

**后续行（仅当DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将属性定义为温度和其他预定义场变量的函数。
