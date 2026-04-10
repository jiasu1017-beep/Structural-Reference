# *CONNECTOR MOTION






### *CONNECTOR MOTION指定连接器单元中可用相对运动分量的运动。

此选项用于规定连接器单元中可用相对运动分量的运动。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据或历史数据  

**级别：**模型、步骤

**Abaqus/CAE: **载荷模块

##### **参考：**

- ["连接类型库，" Abaqus 分析用户指南第 31.1.5 节](../usb/usb-link.md#usb-elm-econnectortypelibrary)
- ["DISP，" Abaqus 用户子程序参考指南第 1.1.4 节](../sub/sub-link.md#sub-rtn-udisp)

### **可选参数（仅限历史数据）：**

AMPLITUDE

此参数仅在某些被规定的变量具有非零大小时才相关。将此参数设置为定义规定连接器运动大小的幅值曲线名称（["幅值曲线，" Abaqus 分析用户指南第 34.1.2 节](../usb/usb-link.md#usb-prc-pamplitude)）。

如果在 Abaqus/Standard 分析中省略此参数，则参考大小将在线性分布于整个步骤（RAMP 函数）或在步骤开始时立即应用并随后保持恒定（STEP 函数）。RAMP 或 STEP 函数的选择取决于 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数分配的值（["定义分析，" Abaqus 分析用户指南第 6.1.2 节](../usb/usb-link.md#usb-anl-aover)）。两个例外是使用 TYPE=DISPLACEMENT 给出的位移或旋转分量，其默认值始终为 RAMP 函数；以及在静态步骤中使用 TYPE=VELOCITY 给出的位移或旋转分量，其默认值始终为 STEP 函数。

如果在 Abaqus/Explicit 分析中省略此参数，参考大小将在步骤开始时立即应用并随后保持恒定（STEP 函数）。

在 Abaqus/Standard 动态过程中，为 TYPE=DISPLACEMENT 或 TYPE=VELOCITY 指定的幅值曲线将自动平滑。在使用 Abaqus/Explicit 的显式动态分析中，用户必须请求平滑此类幅值曲线。有关更多信息，请参阅 ["幅值曲线，" Abaqus 分析用户指南第 34.1.2 节](../usb/usb-link.md#usb-prc-pamplitude)。

LOAD CASE

此参数仅适用于 Abaqus/Standard 分析。

此参数在除 [*BUCKLE](ch02abk16.md) 之外的所有过程中被忽略。该参数可以设置为 1（默认）或 2。

LOAD CASE=1 可用于定义施加载荷的连接器运动，LOAD CASE=2 可用于为屈曲模式定义反对称连接器运动。

OP

设置 OP=MOD（默认）以修改现有的连接器运动或向以前未约束的可用相对运动分量添加连接器运动。

设置 OP=NEW 以移除当前生效的所有连接器运动。要仅移除选定的连接器运动，请使用 OP=NEW 并重新指定要保留的所有连接器运动。

如果在应力/位移分析中移除了连接器运动，它将被替换为等于在上一步结束时在约束自由度处计算的反作用力的集中力。如果步骤是通用非线性分析步骤，则此集中力将根据 [*STEP](ch18abk36.md) 选项上的 AMPLITUDE 参数移除。因此，默认情况下，在静态分析中集中力将在线性分布于整个步骤的过程中减少到零，在动态分析中则立即移除。

### **可选的互斥参数（仅限历史数据）：**

FIXED

包含此参数以指示使用此 [*CONNECTOR MOTION](ch03abk47.md) 选项规定的变量的值应在步骤开始时保持在其当前值不变。如果使用此参数，则数据行上给出的任何大小都将被忽略。

TYPE

此参数在应力/位移分析中使用，以指定大小是以位移历史、速度历史还是加速度历史的形式给出。

设置 TYPE=DISPLACEMENT（默认）以给出位移历史。

设置 TYPE=VELOCITY 以给出速度历史。速度历史可在静态分析中指定。在这种情况下，默认变化是 STEP。

设置 TYPE=ACCELERATION 以给出加速度历史。加速度历史不应在静态分析步骤中使用。

USER

此参数仅适用于 Abaqus/Standard 分析。

包含此参数以指示通过此选项规定的变量关联的任何非零大小将在用户子程序 [`DISP`](../sub/sub-link.md#sub-xsl-disp) 中定义。如果使用此参数，则此选项的数据行定义的大小（可能由 AMPLITUDE 参数修改）可在子程序 [`DISP`](../sub/sub-link.md#sub-xsl-disp) 中重新定义。使用此选项时，TYPE 参数的值将被忽略。

### **矩阵生成和直接解稳态动力学分析的可选互斥参数（仅限历史数据）：**

IMAGINARY

包含此参数以定义连接器运动的虚部（异相）部分。

REAL

包含此参数（默认）以定义连接器运动的实部（同相）部分。

### **用于规定连接器运动的数据行：**

**第一行：**

根据需要重复此数据行，以指定不同连接器单元和可用相对运动分量的连接器运动。




