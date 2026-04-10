# *BEAM GENERAL SECTION





### *BEAM GENERAL SECTION当不需要对截面进行数值积分时，指定梁截面。

此选项用于在线性或非线性梁截面响应不需要对截面进行数值积分时进行定义。在这种情况下，梁截面几何和材料描述被组合；此选项不关联[*MATERIAL](ch13abk08.md)引用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例

**Abaqus/CAE：**属性模块支持线性响应的通用梁截面。

##### **参考：**

- ["使用通用梁截面定义截面行为，" Abaqus Analysis User's Guide第29.3.7节](../usb/usb-link.md#usb-elm-eusingbeamgensect)
- ["梁建模：概述，" Abaqus Analysis User's Guide第29.3.1节](../usb/usb-link.md#usb-elm-ebeamoverview)

### **必需参数：**

ELSET

将此参数设置为定义截面的单元集的名称。

### **Abaqus/Explicit中的必需参数，Abaqus/Standard中的可选参数：**

DENSITY

将此参数设置为梁材料的质量密度（单位体积质量）。在Abaqus/Standard分析中，仅在需要单元质量时（如动态分析或重力载荷）才需要此参数。当SECTION=MESHED时不能使用此参数。

### **可选参数：**

DEPENDENCIES

当SECTION=NONLINEAR GENERAL或SECTION=MESHED时，不能使用此参数。

将此参数设置为除了温度之外还包括在材料模量定义中的场变量依赖项数。如果省略此参数，则假定模量是常数或仅取决于温度。

LUMPED

此参数仅与Abaqus/Standard中的线性Timoshenko梁单元相关。

设置LUMPED=YES（默认）以在频率提取和模态分析过程中使用集中质量矩阵。

设置LUMPED=NO以使用基于挠度的三次插值和旋转场的二次插值的质量矩阵进行频率提取和模态分析。

POISSON

将此参数设置为截面的有效泊松比，以提供由于梁轴应变而在截面上均匀应变（使得梁被拉伸时横截面积发生变化）。有效泊松比的值必须介于1.0和0.5之间。默认值为POISSON=0。值为0.5将强制元素的不可压缩行为。

对于具有SECTION=PIPE的PIPE元素，此参数还将与第三数据行上给出的杨氏模量一起使用，以计算由周向应变引起的轴向应变。

此参数仅在大位移分析中使用。它不与元素类型B23、B33或等效的"混合"元素一起使用（仅在Abaqus/Standard中可用）。

ROTARY INERTIA

此参数仅与三维Timoshenko梁单元相关。

设置ROTARY INERTIA=EXACT（默认）以在动态和特征频率提取过程中使用与梁截面几何形状对应的精确转动惯性。

设置ROTARY INERTIA=ISOTROPIC以对横截面使用近似转动惯性。在Abaqus/Standard中，与扭转变形模式相关的转动惯性用于所有旋转自由度。在Abaqus/Explicit中，所有旋转自由度的转动惯性等于缩放的弯曲惯性，缩放因子选择为使稳定时间增量最大化。当SECTION=MESHED时，ROTARY INERTIA=ISOTROPIC不相关且不能使用；对于网格化截面，默认值EXACT始终适用。

SECTION

设置SECTION=GENERAL（默认）以定义具有线性响应的通用梁截面。

设置SECTION=NONLINEAR GENERAL以定义横截面的通用非线性行为。

设置SECTION=MESHED以定义具有翘曲单元网格化的任意形状实心横截面。

将此参数设置为您选择的库截面名称（请参阅["梁横截面库，" Abaqus Analysis User's Guide第29.3.9节](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)）。以下横截面可用：
- ARBITRARY，用于任意截面。
- BOX，用于矩形空心箱截面。
- CIRC，用于实心圆截面。
- HEX，用于空心六边形截面。
- I，用于工字梁截面。
- L，用于L梁截面。
- PIPE，用于空心圆截面。
- RECT，用于实心矩形截面。
- TRAPEZOID，用于梯形截面。

TAPER

此参数仅与Abaqus/Standard分析相关。

包含此参数以定义具有锥形横截面的通用梁截面。

ZERO

当SECTION=MESHED时不能使用此参数。

将此参数设置为热膨胀的参考温度（![](../graphics/key_eqn00086.gif)），如果需要的话。默认值为ZERO=0。

### **SECTION=GENERAL的数据行：**

**第一行：**

**第二行（可选；如果要使用默认值，则输入空行）：**

对于平面梁，此行上的条目必须为（0，0，![](../graphics/key_eqn00089.gif)）。对于空间中的梁，如果第一梁截面轴未通过单元连接中的附加节点定义，则默认值为（0，0，![](../graphics/key_eqn00089.gif)）。详见["梁单元横截面方向，" Abaqus Analysis User's Guide第29.3.4节](../usb/usb-link.md#usb-elm-ebeamcrosssection)。

**第三行：**

**后续行（仅在DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将属性定义为温度和其他预定义场变量的函数。

### **包含TAPER参数时SECTION=GENERAL的数据行：**

**第一行（节点A的属性）：**

**第二行（节点B的属性）：**

**第三行（可选；如果要使用默认值，则输入空行）：**

对于平面梁，此行上的条目必须为（0，0，![](../graphics/key_eqn00089.gif)）。对于空间中的梁，如果第一梁截面轴未通过单元连接中的附加节点定义，则默认值为（0，0，![](../graphics/key_eqn00089.gif)）。详见["梁单元横截面方向，" Abaqus Analysis User's Guide第29.3.4节](../usb/usb-link.md#usb-elm-ebeamcrosssection)。

**第四行：**

**后续行（仅在DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将属性定义为温度和其他预定义场变量的函数。

### **SECTION=NONLINEAR GENERAL的数据行：**

**第一行：**

截面的轴向和弯曲行为通过使用[*AXIAL](ch01abk16.md)、[*M1](ch13abk32.md)、[*M2](ch13abk33.md)、[*TORQUE](ch19abk08.md)和[*THERMAL EXPANSION](ch19abk05.md)选项来定义。

**第二行（可选）：**

对于平面梁，此行上的条目必须为（0，0，![](../graphics/key_eqn00089.gif)）。对于空间中的梁，如果第一梁截面轴未通过单元连接中的附加节点定义，则默认值为（0，0，![](../graphics/key_eqn00089.gif)）。详见["梁单元横截面方向，" Abaqus Analysis User's Guide第29.3.4节](../usb/usb-link.md#usb-elm-ebeamcrosssection)。

### **SECTION=MESHED的数据行：**

**第一行：**

对于平面梁，此行上的条目必须为（0，0，1）。对于空间中的梁，如果第一梁截面轴未通过单元连接中的附加节点定义，则默认值为（0，0，1）。详见["梁单元横截面方向，" Abaqus Analysis User's Guide第29.3.4节](../usb/usb-link.md#usb-elm-ebeamcrosssection)。

**第二行：**

此行和后续行上的条目包括二维网格化横截面生成过程产生的梁截面属性。这些属性在横截面生成期间写入文件`*jobname*.bsp`，通常使用[*INCLUDE](ch09abk14.md)选项读入后续梁分析。详见["网格化梁横截面，" Abaqus Analysis User's Guide第10.6.1节](../usb/usb-link.md#usb-anl-ameshedsection)。

**第三行：**

### **BOX、CIRC、HEX、I、L、PIPE、RECT和TRAPEZOID截面的数据行：**

**第一行：**

**第二行（可选；如果要使用默认值，则输入空行）：**

对于平面梁，此行上的条目必须为（0，0，![](../graphics/key_eqn00089.gif)）。对于空间中的梁，如果第一梁截面轴未通过单元连接中的附加节点定义，则默认值为（0，0，![](../graphics/key_eqn00089.gif)）。详见["梁单元横截面方向，" Abaqus Analysis User's Guide第29.3.4节](../usb/usb-link.md#usb-elm-ebeamcrosssection)。

**第三行：**

**后续行（仅在DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将属性定义为温度和其他预定义场变量的函数。

### **包含TAPER参数时BOX、CIRC、HEX、I、L、PIPE、RECT和TRAPEZOID截面的数据行：**

**第一行（节点A的属性）：**

**第二行（节点B的属性）：**

**第三行（可选；如果要使用默认值，则输入空行）：**

对于平面梁，此行上的条目必须为（0，0，![](../graphics/key_eqn00089.gif)）。对于空间中的梁，如果第一梁截面轴未通过单元连接中的附加节点定义，则默认值为（0，0，![](../graphics/key_eqn00089.gif)）。详见["梁单元横截面方向，" Abaqus Analysis User's Guide第29.3.4节](../usb/usb-link.md#usb-elm-ebeamcrosssection)。

**第四行：**

**后续行（仅在DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将属性定义为温度和其他预定义场变量的函数。

### **SECTION=ARBITRARY的数据行：**

**第一行：**

**第二行：**

根据需要重复第二个数据行以定义ARBITRARY截面。

**第三行（可选；如果要使用默认值，则输入空行）：**

对于平面梁，此行上的条目必须为（0，0，![](../graphics/key_eqn00089.gif)）。对于空间中的梁，如果第一梁截面轴未通过单元连接中的附加节点定义，则默认值为（0，0，![](../graphics/key_eqn00089.gif)）。详见["梁单元横截面方向，" Abaqus Analysis User's Guide第29.3.4节](../usb/usb-link.md#usb-elm-ebeamcrosssection)。

**第四行：**

**后续行（仅在DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将属性定义为温度和其他预定义场变量的函数。

