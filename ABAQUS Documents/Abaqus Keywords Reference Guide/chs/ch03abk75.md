# *CONTROLS






### *CONTROLS重置求解控制。

**警告：**此选项在大多数非线性分析中不需要，除了与参数 ANALYSIS=DISCONTINUOUS 结合使用的情况。但是，如果发生极端非线性，可能需要此选项来获得求解。["常用控制参数，" Abaqus 分析用户指南第 7.2.2 节](../usb/usb-link.md#usb-anl-aconvergecontrol) 包含对可能发生的问题类型以及使用 [*CONTROLS](ch03abk75.md) 选项克服这些问题的方法的讨论。在某些情况下，此选项也可用于以更有效的方式获得求解。此后一目的的使用仅适用于有经验的用户。

**产品：**Abaqus/Standard  Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **步骤模块

##### **参考：**

- ["收敛和时间积分准则：概述，" Abaqus 分析用户指南第 7.2.1 节](../usb/usb-link.md#usb-anl-aconvergeintro)
- ["常用控制参数，" Abaqus 分析用户指南第 7.2.2 节](../usb/usb-link.md#usb-anl-aconvergecontrol)
- ["非线性问题的收敛准则，" Abaqus 分析用户指南第 7.2.3 节](../usb/usb-link.md#usb-anl-aconvergcriteria)
- ["瞬态问题中的时间积分精度，" Abaqus 分析用户指南第 7.2.4 节](../usb/usb-link.md#usb-anl-aautomaticinc)

### **必需的互斥参数：**

ANALYSIS

此参数仅适用于 Abaqus/Standard 分析。

设置 ANALYSIS=DISCONTINUOUS 以设置通常会提高严重不连续行为（如摩擦滑动或混凝土开裂）效率的参数，方法是在开始任何收敛率检查之前允许相对较多的迭代。当与 PARAMETERS=TIME INCREMENTATION 数据行关联的变量 ![](../graphics/key_eqn00390.gif) 和 ![](../graphics/key_eqn00391.gif) 设置了值时，此参数将覆盖这些值。如果在不表现出严重不连续行为的问题中设置此参数，则可能导致求解效率较低。

PARAMETERS

此参数仅适用于 Abaqus/Standard 分析。

设置 PARAMETERS=FIELD 以设置满足场方程的参数。在这种情况下，FIELD 参数可用于定义正在为其提供参数的场。如果省略 FIELD 参数，则为问题中所有活动场设置参数。

设置 PARAMETERS=CONSTRAINTS 以设置约束方程的容差。

设置 PARAMETERS=LINE SEARCH 以设置线搜索控制参数。

设置 PARAMETERS=TIME INCREMENTATION 以设置时间增量控制参数。

RESET

包含此参数以将所有值重置为默认值。当使用此参数时，选项不应有数据行。

TYPE

设置 TYPE=FSI 以设置将用于 Abaqus/CFD 中涉及移动边界或变形几何的变形网格问题的参数，以及 Abaqus/CFD 到 Abaqus/Standard 或 Abaqus/Explicit 联合仿真的参数。此参数设置仅能用于 Abaqus/CFD 分析。

设置 TYPE=DIRECT CYCLIC 以设置将用于控制稳定状态和塑性棘轮检测的参数，并指定何时对直接循环分析施加周期性条件。

设置 TYPE=VCCT LINEAR SCALING 以设置将用于 VCCT 分层分析的 ![](../graphics/key_eqn00135.gif) 参数。

### **可选参数：**

DISTORTION CONTROL

此参数仅在 TYPE=FSI、MESH SMOOTHING=EXPLICIT 时适用于 Abaqus/CFD 分析。

设置 DISTORTION CONTROL=OFF（默认）以停用在 CFD 网格移动中阻止负单元体积的约束。

设置 DISTORTION CONTROL=ON 以激活在 CFD 网格移动中阻止负单元体积的约束。DISTORTION CONTROL 参数无法阻止由于时间不稳定性和物理上不真实的变形导致的单元变形。

FIELD

此参数仅在 Abaqus/Standard 中与 PARAMETERS=FIELD 结合使用时才能使用。

设置 FIELD=CONCENTRATION 以设置质量浓度场平衡方程的参数。

设置 FIELD=DISPLACEMENT 以设置位移场和翘曲自由度平衡方程的参数。

设置 FIELD=ELECTRICAL POTENTIAL 以设置电位场平衡方程的参数。

设置 FIELD=GLOBAL（默认）以定义一组用于所有活动场的参数。

设置 FIELD=HYDROSTATIC FLUID PRESSURE 以设置静水流体单元体积约束的参数。

设置 FIELD=MATERIAL FLOW 以设置连接单元材料流自由度的参数。

设置 FIELD=PORE FLUID PRESSURE 以设置孔隙液体积连续性方程的参数。

设置 FIELD=PRESSURE LAGRANGE MULTIPLIER 以设置压力拉格朗日乘子场方程的参数。

设置 FIELD=ROTATION 以设置旋转场平衡方程的参数。

设置 FIELD=TEMPERATURE 以设置温度场平衡方程的参数。

设置 FIELD=VOLUMETRIC LAGRANGE MULTIPLIER 以设置体积拉格朗日乘子场方程的参数。

MESH SMOOTHING

此参数仅在 TYPE=FSI 时适用于 Abaqus/CFD 分析。

设置 MESH SMOOTHING=IMPLICIT（默认）以选择隐式算法来控制网格平滑。

设置 MESH SMOOTHING=EXPLICIT 以选择显式算法来控制网格平滑。

### **TYPE=FSI、MESH SMOOTHING=IMPLICIT 的数据行：**

**第一行（也是唯一一行）：**

### **TYPE=FSI、MESH SMOOTHING=EXPLICIT 的数据行：**

**第一行（也是唯一一行）：**

### **PARAMETERS=FIELD 的数据行：**

**第一行：**

**第二行：**

这些项目很少需要从其默认值重置。

### **PARAMETERS=CONSTRAINTS 的数据行：**

**第一行（也是唯一一行）：**

这些项目很少需要从其默认值重置。某些参数的相关性取决于 [*STEP](ch18abk36.md) 选项上 CONVERT SDI 参数的值。

### **PARAMETERS=LINE SEARCH 的数据行：**

**第一行（也是唯一一行）：**

### **PARAMETERS=TIME INCREMENTATION 的数据行：**

**第一行：**

某些参数的相关性取决于 [*STEP](ch18abk36.md) 选项上 CONVERT SDI 参数的值。

**第二行：**

这些项目很少需要从其默认值重置。

**第三行：**

这些项目很少需要从其默认值重置。

**第四行：**

这些项目很少需要从其默认值重置。

### **TYPE=DIRECT CYCLIC 的数据行：**

**第一行（也是唯一一行）：**

### **TYPE=VCCT LINEAR SCALING 的数据行：**

**第一行（也是唯一一行）：**




