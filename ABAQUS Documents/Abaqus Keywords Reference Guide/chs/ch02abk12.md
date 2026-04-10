# *BOUNDARY





### *BOUNDARY指定边界条件。

此选项用于在节点上指定边界条件，或在子模型分析中指定驱动节点。在Abaqus/Standard中，它还用于为模态叠加过程定义主基和次级基，以及为扩展单元在幻节点上指定边界条件。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**模型或历史数据

**级别：**模型、步骤

**Abaqus/CAE：**载荷模块；不支持流体腔压力和广义平面应变边界条件。

##### **参考：**

- ["在Abaqus中定义模型，" Abaqus Analysis User's Guide第1.3.1节](../usb/usb-link.md#usb-int-imodel)
- ["Abaqus/Standard和Abaqus/Explicit中的边界条件，" Abaqus Analysis User's Guide第34.3.1节](../usb/usb-link.md#usb-prc-pboundary)
- ["Abaqus/CFD中的边界条件，" Abaqus Analysis User's Guide第34.3.2节](../usb/usb-link.md#usb-prc-pboundarycfd)
- ["DISP，" Abaqus User Subroutines Reference Guide第1.1.4节](../sub/sub-link.md#sub-rtn-udisp)
- ["VDISP，" Abaqus User Subroutines Reference Guide第1.2.1节](../sub/sub-link.md#sub-rtn-uexpdisp)
- ["自然频率提取，" Abaqus Analysis User's Guide第6.3.5节](../usb/usb-link.md#usb-anl-afreqextraction)
- ["基于节点的子模型，" Abaqus Analysis User's Guide第10.2.2节](../usb/usb-link.md#usb-anl-asubmodeldisp)
- ["使用扩展有限元方法将不连续性建模为 enrichment特征，" Abaqus Analysis User's Guide第10.7.1节](../usb/usb-link.md#usb-anl-aenrichment)
- ["在Abaqus/Explicit中定义ALE自适应网格域，" Abaqus Analysis User's Guide第12.2.2节](../usb/usb-link.md#usb-anl-aaledomains)

### 在节点上指定边界条件

### **当固定边界条件被指定为模型数据时，不使用参数。**

### **可选参数（仅限历史数据）：**

AMPLITUDE

此参数仅与一些具有非零大小的被指定变量相关。将此参数设置为定义指定边界条件大小的振幅曲线名称（["振幅曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)）。

如果在Abaqus/Standard分析中省略此参数，则参考大小将在步骤上线性应用（RAMP函数），或者在步骤开始时立即应用并随后保持恒定（STEP函数）。RAMP或STEP函数的选择取决于分配给[*STEP](ch18abk36.md)选项上AMPLITUDE参数的值（["定义分析，" Abaqus Analysis User's Guide第6.1.2节](../usb/usb-link.md#usb-anl-aover)）。有两个例外。第一个是当使用TYPE=DISPLACEMENT给出位移或旋转分量时，默认值始终是RAMP函数。第二个是当在静态步骤或具有APPLICATION=QUASI-STATIC的动态步骤中使用TYPE=VELOCITY给出位移或旋转分量时，默认值始终是STEP函数。

如果在Abaqus/Explicit或Abaqus/CFD分析中省略此参数，则参考大小将在步骤开始时立即应用并随后保持恒定（STEP函数）。

在Abaqus/Standard动态或模态动态过程中，为TYPE=DISPLACEMENT或TYPE=VELOCITY指定的振幅曲线将被自动平滑。在Abaqus/Explicit分析中，用户必须请求平滑此类振幅曲线。有关更多信息，请参阅["振幅曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)。

BLOCKING

此参数仅适用于指定了USER参数的Abaqus/Explicit分析。

设置BLOCKING=YES（默认）以为给定的节点集启用阻塞。阻塞大小将在Abaqus/Explicit中设置为预定义值。

设置BLOCKING=NO以禁用阻塞。

FIXED

此参数仅适用于Abaqus/Standard分析，不能与TYPE和USER参数一起使用。

包含此参数以指示使用此[*BOUNDARY](ch02abk12.md)选项指定的变量值应在步骤开始时保持固定在其当前值。如果使用此参数，则数据行上给出的任何大小都将被忽略。如果在分析的第一步中使用此参数，则它将被忽略。

LOAD CASE

此参数仅适用于Abaqus/Standard分析。它在除[*BUCKLE](ch02abk16.md)之外的所有过程中被忽略。

将此参数设置为1（默认）或2。LOAD CASE=1可用于定义施加载荷的边界条件，LOAD CASE=2可用于为屈曲模式定义反对称边界条件。

NAME

此参数仅适用于指定了USER参数的Abaqus/Explicit分析。

将此参数设置为将用于在用户子程序[`VDISP`](../sub/sub-link.md#sub-xsl-vdisp)中引用边界条件的名称。在Abaqus/Explicit分析中出现的边界条件名称必须唯一。它们不能以数字开头，必须遵守标签的命名约定。请参阅["输入语法规则，" Abaqus Analysis User's Guide第1.2.1节](../usb/usb-link.md#usb-int-iinputsyntax)，了解此类名称的语法。

OP

设置OP=MOD（默认）以修改现有边界条件或向以前未约束的自由度添加边界条件。

设置OP=NEW如果应该删除当前生效的所有边界条件。要仅删除选定的边界条件，请使用OP=NEW并重新指定要保留的所有边界条件。

如果在Abaqus/Standard的应力/位移分析中删除了边界条件，它将被等于在上一步骤结束时在约束自由度处计算的反作用力的集中力替换。如果该步骤是通用非线性分析步骤，则此集中力将根据[*STEP](ch18abk36.md)选项上的AMPLITUDE参数被移除。因此，如果使用默认振幅，则集中力将在静态分析中随步骤期间线性减小到零，在动态分析中立即减小为零。

OP参数在同一步骤中所有[*BOUNDARY](ch02abk12.md)选项使用中必须相同，除了在[*BUCKLE](ch02abk16.md)步骤中，即使OP=MOD与LOAD CASE=1一起使用，OP=NEW也可以与LOAD CASE=2一起使用。

PHANTOM

此参数仅适用于Abaqus/Standard中的扩展单元。

设置PHANTOM=NODE以将边界条件应用到最初与扩展单元中指定实节点重合的幻节点。

设置PHANTOM=EDGE以将边界条件应用到位于扩展单元中两个指定实角节点之间的单元边缘处的幻节点。此设置仅适用于具有孔隙压力自由度的节点。

REGION TYPE

此参数仅适用于Abaqus/Explicit分析。

此参数仅与应用于自适应网格域边界上的节点的边界条件相关。如果边界条件应用于自适应网格域内部的节点，这些节点将始终跟随材料。Abaqus/Explicit自动为表面类型约束（对称平面、移动边界平面和完全夹紧边界）创建拉格朗日边界区域。

设置REGION TYPE=LAGRANGIAN（默认）以将边界条件应用到拉格朗日边界区域。拉格朗日边界区域的边缘将跟随材料，同时允许沿边缘和区域内部进行自适应网格划分。

设置REGION TYPE=SLIDING以定义滑动边界区域。滑动边界区域的边缘将在材料上滑动。自适应网格划分将发生在边缘和区域内部。通常在滑动边界区域的边缘上应用网格约束以将其空间固定。

设置REGION TYPE=EULERIAN以将边界条件应用到欧拉边界区域。此选项用于创建材料可以流过的边界区域，通常与速度边界条件一起使用。必须垂直于欧拉边界区域使用网格约束，以允许材料流过该区域。如果未应用网格约束，则欧拉边界区域的行为将与滑动边界区域相同。

TYPE

此参数不能与FIXED参数一起使用。

此参数在应力/位移分析中使用，以指定大小是以位移历史、速度历史还是加速度历史的形式给出。在Abaqus/Standard分析中，TYPE=VELOCITY通常应用于指定有限旋转。

设置TYPE=DISPLACEMENT（默认）以给出位移历史。Abaqus/Explicit不允许位移跳跃。如果未指定振幅，Abaqus/Explicit将忽略用户提供的位移值并强制执行零位移边界条件。详见["Abaqus/Standard和Abaqus/Explicit中的边界条件，" Abaqus Analysis User's Guide第34.3.1节](../usb/usb-link.md#usb-prc-pboundary)。在Abaqus/CFD中，此类型用于指定网格位移。

设置TYPE=VELOCITY以给出速度历史。速度历史可以在Abaqus/Standard的静态分析中指定，如["Abaqus/Standard和Abaqus/Explicit中的边界条件，" Abaqus Analysis User's Guide第34.3.1节](../usb/usb-link.md#usb-prc-pboundary)中的"指定大旋转"所述。在这种情况下，默认变化是STEP。速度历史不在Abaqus/CFD中使用。

设置TYPE=ACCELERATION以给出加速度历史。加速度历史不应在Abaqus/CFD或Abaqus/Standard的静态分析步骤中使用。

如果在Abaqus/Explicit中将振幅函数指定为分段线性函数并使用位移历史，则在曲线改变斜率的点处，速度会有跳跃，加速度会有尖峰。这将导致"嘈杂"的解决方案。如果可能，请使用[*AMPLITUDE](ch01abk09.md)，DEFINITION=SMOOTH STEP；[*AMPLITUDE](ch01abk09.md)，SMOOTH；或[*BOUNDARY](ch02abk12.md)，TYPE=VELOCITY或TYPE=ACCELERATION。对于TYPE=ACCELERATION，必须指定初始速度的值（给定于[*INITIAL CONDITIONS](ch09abk18.md)，TYPE=VELOCITY）以获得正确的位移历史。

USER

此参数仅适用于Abaqus/Standard和Abaqus/Explicit分析，不能与FIXED参数一起使用。

对于Abaqus/Standard，包含此参数以指示可以通过用户子程序[`DISP`](../sub/sub-link.md#sub-xsl-disp)重新定义与此选项指定的变量关联的任何非零大小。在此选项的数据行上定义的任何大小（可能由AMPLITUDE参数修改）将被传递到用户子程序[`DISP`](../sub/sub-link.md#sub-xsl-disp)，可以在子程序[`DISP`](../sub/sub-link.md#sub-xsl-disp)中重新定义。当使用此选项时，TYPE参数的值被忽略。

对于Abaqus/Explicit，包含此参数以指示与此选项指定的变量关联的边界值将在用户子程序[`VDISP`](../sub/sub-link.md#sub-xsl-vdisp)中定义。在此选项的数据行上定义的任何大小都将被忽略，如果包含了AMPLITUDE参数，则振幅被传递到[`VDISP`](../sub/sub-link.md#sub-xsl-vdisp)例程供您使用。用户子程序[`VDISP`](../sub/sub-link.md#sub-xsl-vdisp)中用户指定变量的类型由TYPE参数确定。NAME参数可在用户子程序[`VDISP`](../sub/sub-link.md#sub-xsl-vdisp)中使用以区分多个边界条件。用户指定的边界条件仅支持平移和旋转自由度。

### **矩阵生成和直接解稳态动力学分析的可选、互斥参数（仅限历史数据）：**

IMAGINARY

包含此参数以定义边界条件的虚部（异相）部分。

REAL

包含此参数（默认）以定义边界条件实部（同相）部分。

### **使用"类型"格式定义零值边界条件的数据行（仅限模型数据）：**

**第一行：**

根据需要重复此数据行以在不同节点和自由度处指定固定边界条件。

### **当未使用PHANTOM参数时，使用"直接"格式指定边界条件的数据行：**

**第一行：**

根据需要重复此数据行以在不同节点和自由度处指定边界条件。

### **当PHANTOM=NODE时，使用"直接"格式指定边界条件的数据行：**

**第一行：**

根据需要重复此数据行以在不同节点和自由度处指定边界条件。

### **当PHANTOM=EDGE时，使用"直接"格式指定边界条件的数据行：**

**第一行：**

根据需要重复此数据行以在不同节点和自由度处指定边界条件。

### 为模态叠加过程定义主基和次级基

### **可选参数：**

BASE NAME

此参数用于定义次级基，只能在频率提取步骤中使用（["自然频率提取，" Abaqus Analysis User's Guide第6.3.5节](../usb/usb-link.md#usb-anl-afreqextraction)）。将此参数设置为您选择的库截面名称（["动态分析过程：概述，" Abaqus Analysis User's Guide第6.3.1节](../usb/usb-link.md#usb-anl-adynamicproc)）。在后续模态叠加步骤中，此基将按照引用相同基名的[*BASE MOTION](ch02abk01.md)选项的规定被激发。如果在频率提取步骤中未使用此参数，则节点将被分配给主基。

### **在[*FREQUENCY](ch06abk35.md)过程中定义主基或次级基的数据行：**

**第一行：**

根据需要重复此数据行以在不同节点和自由度处指定边界条件。

### 子模型边界条件

### **必需参数：**

STEP

将此参数设置为全局分析中的步骤编号，在该步骤的子模型分析期间将读取驱动变量的值。

SUBMODEL

包含此参数以指定边界条件是子模型分析中的"驱动变量"。在此选项中使用的节点必须在[*SUBMODEL](ch18abk38.md)模型定义选项中列出。

### **可选参数：**

INC

此参数仅可用于静态线性扰动步骤（["通用和线性扰动过程，" Abaqus Analysis User's Guide第6.1.3节](../usb/usb-link.md#usb-anl-alinearnonlinear)）。将此参数设置为全局分析选定步骤中的增量号，在该增量处将使用解决方案指定驱动变量的值。默认情况下，Abaqus/Standard将使用所选步骤最后一步的解决方案。

OP

设置OP=MOD（默认）以保留现有[*BOUNDARY](ch02abk12.md)条件，并由此选项添加或修改边界条件。

设置OP=NEW如果应该删除当前生效的所有边界条件。要仅删除选定的边界条件，请使用OP=NEW并重新指定要保留的所有边界条件。

如果在应力/位移分析中删除了边界条件，它将被等于在上一步骤结束时在约束自由度处计算的反作用力的集中力替换。如果该步骤是通用非线性分析步骤，则此集中力将根据[*STEP](ch18abk36.md)选项上的AMPLITUDE参数被移除。因此，默认情况下，集中力将在静态分析中随步骤期间线性减小到零，在动态分析中立即减小为零。

OP参数在步骤中所有[*BOUNDARY](ch02abk12.md)选项使用中必须相同。

SCALE

将此参数设置为要用于缩放从全局分析读取的驱动变量的值。默认值为SCALE=1.0。

TIMESCALE

如果子模型分析步骤时间与全局分析步骤时间不同，请使用TIMESCALE参数调整驱动节点振幅函数的时间变量。每个驱动节点振幅函数的时间变量被缩放以匹配子模型分析步骤时间。如果省略此参数，则时间变量不被缩放。

### **壳到壳或实体到实体子模型的数据行：**

**第一行：**

根据需要重复此数据行以在不同节点和自由度处指定子模型边界条件。

### **壳到实体子模型的数据行：**

**第一行：**

根据需要重复此数据行以在不同节点处指定子模型边界条件。

### **声学到结构子模型的数据行：**

**第一行：**

根据需要重复此数据行以在不同节点处指定子模型边界条件。


