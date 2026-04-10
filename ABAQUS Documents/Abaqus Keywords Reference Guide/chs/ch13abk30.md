# *MOTION









### *MOTION将运动指定为预定义场。

此选项用于在腔体辐射热传递分析期间指定节点集或单个节点的运动，在稳态传输分析中定义参考框架的运动，或在静态分析中定义通过网格传输的 材料的速度。它也可用于在涡流分析中指定通过网格传输的代表导体的单元集的速度。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**步骤

##### **参考：**

- ["腔体辐射，" Abaqus Analysis User's Guide第41.1.1节](../usb/usb-link.md#usb-cni-acavityradiation)
- ["稳态传输分析，" Abaqus Analysis User's Guide第6.4.1节](../usb/usb-link.md#usb-anl-asteadystatetransport)
- ["静态应力分析，" Abaqus Analysis User's Guide第6.2.2节](../usb/usb-link.md#usb-anl-astatic)
- ["涡流分析，" Abaqus Analysis User's Guide第6.7.5节](../usb/usb-link.md#usb-anl-aeddycurrent)
- ["UMOTION，" Abaqus User Subroutines Reference Guide第1.1.44节](../sub/sub-link.md#sub-rtn-umotion)

### 在腔体辐射热传递分析、稳态传输分析或静态分析期间指定运动

### **可选的互斥参数：**

ROTATION

包含此参数以定义关于轴的刚体旋转。

TRANSLATION

包含此参数以在全局坐标系中给出*x*-、*y*-和*z*-方向的平移分量，或者如果在这些节点处使用了[*TRANSFORM](ch19abk11.md)，则在局部坐标系中给出。平移运动是默认值。

USER

包含此参数以指示运动的大小将在用户子程序[`UMOTION`](../sub/sub-link.md#sub-xsl-umotion)中定义。如果使用此参数，则数据行定义的任何大小都可以在用户子程序中重新定义。当使用此参数时，TYPE参数的值不相关。此参数不能用于稳态传输分析。

### **可选参数：**

AMPLITUDE

将此参数设置为幅值曲线（在[*AMPLITUDE](ch01abk09.md)选项中定义）的名称，该曲线给出整个步骤中运动的时间变化。

如果省略此参数，并且使用TYPE=DISPLACEMENT给出平移或旋转运动，则默认值为RAMP函数。如果使用TYPE=VELOCITY给出平移或旋转运动，则对于腔体辐射分析默认值为STEP函数，对于稳态传输分析默认值为RAMP函数。

TYPE

此参数用于指定大小是以位移还是以速度的形式给出。

设置TYPE=DISPLACEMENT（腔体辐射分析的默认值）以给出平移或旋转位移值。

设置TYPE=VELOCITY（稳态传输和静态分析的唯一可用类型）以给出平移或旋转速度。可以在["腔体辐射"中关于指定大旋转的讨论中指定腔体辐射问题的速度历史。

### **定义平移运动的数据行（TRANSLATION）：**

**第一行：**

根据需要重复此数据行以为不同的节点和自由度定义平移运动。

### **定义旋转运动的数据行（ROTATION）：**

**第一行：**

根据需要重复此数据行以为不同的节点定义旋转运动。

### **在用户子程序[`UMOTION`](../sub/sub-link.md#sub-xsl-umotion)中定义运动的数据行（USER）：**

**第一行：**

根据需要重复此数据行以定义将具有由用户子程序[`UMOTION`](../sub/sub-link.md#sub-xsl-umotion)规定的运动的节点和自由度。

### 在涡流分析期间指定运动

### **必需参数：**

ELEMENT

包含此参数以指定单元集的运动。

### **可选的互斥参数：**

ROTATION

包含此参数以定义关于轴的刚体旋转。

TRANSLATION

包含此参数以在全局坐标系中给出*x*-、*y*-和*z*-方向的平移分量，或者如果在这些节点处使用了[*TRANSFORM](ch19abk11.md)，则在局部坐标系中给出。平移运动是默认值。

### **可选参数：**

AMPLITUDE

将此参数设置为幅值曲线（在[*AMPLITUDE](ch01abk09.md)选项中定义）的名称，该曲线给出整个步骤中运动的时间变化。

如果省略此参数，则默认值为STEP函数。

### **定义运动平移速度的数据行（TRANSLATION）：**

**第一行（也是唯一一行）：**

### **定义运动旋转速度的数据行（ROTATION）：**

**第一行（也是唯一一行）：**