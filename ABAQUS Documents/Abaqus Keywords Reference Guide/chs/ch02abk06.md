# *BEAM SECTION





### *BEAM SECTION当需要对截面进行数值积分时，指定梁截面。

此选项用于在需要对截面进行数值积分时（通常由于截面中的非线性材料响应）定义梁单元的横截面。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**部件、部件实例

**Abaqus/CAE：**属性模块

##### **参考：**

- ["使用在分析期间积分的梁截面定义截面行为，" Abaqus Analysis User's Guide第29.3.6节](../usb/usb-link.md#usb-elm-eusingbeamsection)
- ["梁建模：概述，" Abaqus Analysis User's Guide第29.3.1节](../usb/usb-link.md#usb-elm-ebeamoverview)
- ["具有变形横截面的管道和弯头：弯头单元，" Abaqus Analysis User's Guide第29.5.1节](../usb/usb-link.md#usb-elm-eelbows)

### **必需参数：**

ELSET

将此参数设置为定义此截面的单元集的名称。

MATERIAL

将此参数设置为与此梁截面定义一起使用的材料名称。

SECTION

将此参数设置为截面类型的名称（请参阅["梁横截面库，" Abaqus Analysis User's Guide第29.3.9节](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)）。以下横截面可用于梁单元：
- ARBITRARY，用于任意截面。
- BOX，用于矩形空心箱截面。
- CIRC，用于实心圆截面。
- HEX，用于空心六边形截面。
- I，用于工字梁截面。
- L，用于L梁截面。
- PIPE，用于薄壁圆截面。
- RECT，用于实心矩形截面。
- THICK PIPE，用于厚壁圆截面（仅限Abaqus/Standard）。
- TRAPEZOID，用于梯形截面。

设置SECTION=ELBOW用于弯头单元，仅在Abaqus/Standard中可用。

### **可选参数：**

LUMPED

此参数仅与Abaqus/Standard中的线性Timoshenko梁单元相关。

设置LUMPED=YES（默认）以在频率提取和模态分析过程中使用集中质量矩阵。

设置LUMPED=NO以使用基于挠度的三次插值和旋转场的二次插值的质量矩阵进行频率提取和模态分析。

POISSON

将此参数设置为截面的有效泊松比，以提供由于梁轴应变而在截面上均匀应变（使得梁被拉伸时横截面积发生变化）。有效泊松比的值必须介于1.0和0.5之间。默认值为POISSON=0。值为0.5将强制元素的不可压缩行为。

此参数仅在大位移分析中使用。它不与弯头单元或元素类型B23、B33、PIPE21、PIPE22和等效的"混合"元素一起使用（仅在Abaqus/Standard中可用）。

ROTARY INERTIA

此参数仅与三维Timoshenko梁单元相关。

设置ROTARY INERTIA=EXACT（默认）以在动态和特征频率提取过程中使用与梁截面几何形状对应的精确转动惯性。

设置ROTARY INERTIA=ISOTROPIC以对横截面使用近似转动惯性。在Abaqus/Standard中，与扭转变形模式相关的转动惯性用于所有旋转自由度。在Abaqus/Explicit中，所有旋转自由度的转动惯性等于缩放的弯曲惯性，缩放因子选择为使稳定时间增量最大化。

TEMPERATURE

使用此参数选择[*FIELD](ch06abk07.md)、[*INITIAL CONDITIONS](ch09abk18.md)或[*TEMPERATURE](ch19abk01.md)选项上使用的温度和场变量输入模式。

对于梁单元，设置TEMPERATURE=GRADIENTS（默认）以指定横截面原点处的温度和场变量值，以及关于截面2方向（对于空间梁，还有1方向）的梯度。设置TEMPERATURE=VALUES以在梁截面描述中所示的点处给出温度和场变量（请参阅["梁横截面库，" Abaqus Analysis User's Guide第29.3.9节](../usb/usb-link.md#usb-elm-ebeamcrosssectlib)）。

对于弯头单元，设置TEMPERATURE=GRADIENTS（默认）以在管道壁中间指定温度和场变量以及通过管道厚度的梯度。设置TEMPERATURE=VALUES以在横截面上所示的点处给出温度和场变量，如["具有变形横截面的管道和弯头：弯头单元，" Abaqus Analysis User's Guide第29.5.1节](../usb/usb-link.md#usb-elm-eelbows)所示。

### **BOX、CIRC、HEX、I、L、PIPE、RECT、THICK PIPE和TRAPEZOID截面的数据行：**

**第一行：**

**第二行（可选；如果要使用默认值，则输入空行）：**

对于平面梁，此行上的条目必须为（0，0，1）。对于空间中的梁，如果第一梁截面轴未通过单元连接中的附加节点定义，则默认值为（0，0，1）。详见["梁单元横截面方向，" Abaqus Analysis User's Guide第29.3.4节](../usb/usb-link.md#usb-elm-ebeamcrosssection)。

**第三行（可选）：**

### **ARBITRARY截面的数据行：**

**第一行：**

**第二行：**

根据需要重复第二个数据行以定义ARBITRARY截面。

**第三行（可选）：**

对于平面梁，此行上的条目必须为（0，0，1）。对于空间中的梁，如果第一梁截面轴未通过单元连接中的附加节点定义，则默认值为（0，0，1）。详见["梁单元横截面方向，" Abaqus Analysis User's Guide第29.3.4节](../usb/usb-link.md#usb-elm-ebeamcrosssection)。

### **ELBOW截面的数据行：**

**第一行：**

**第二行：**

输入与连接弯头的直管段相切的交点坐标，或者，如果此截面与直管关联，则输入管道轴外的点坐标。第二横截面轴将位于如此定义的平面内，其正方向指向此轴外点。

**第三行：**


