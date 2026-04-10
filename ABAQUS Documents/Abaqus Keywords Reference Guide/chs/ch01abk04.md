# *ACOUSTIC FLOW VELOCITY





### *ACOUSTIC FLOW VELOCITY为声学元素指定流速度作为预定义场。

此选项用于为声学分析指定节点集或单个节点的流体流速度。此选项定义了一个基础流，声学分析是关于该基础流的线性扰动。

**产品：**Abaqus/Standard  

**类型：**历史数据

**级别：**Step

##### **参考：**

- ["声学、冲击和耦合声学-结构分析，" Abaqus Analysis User's Guide第6.10.1节](../usb/usb-link.md#usb-anl-aacoustic)

### **必需的、互斥的参数：**

ROTATION

包含此参数以定义由于刚体绕轴旋转而产生的流速度场。

TRANSLATION

包含此参数以在全局坐标系中或在如果在这些节点处使用了[*TRANSFORM](ch19abk11.md)时的局部坐标系中给出x-、y-和z-方向的平移流速度分量。平移流速度是默认值。

### **可选参数：**

AMPLITUDE

将此参数设置为振幅曲线（在[*AMPLITUDE](ch01abk09.md)选项中定义）的名称，该曲线给出整个step中流速度的时间变化（["振幅曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)）。

如果省略此参数，默认值为STEP函数。

### **定义平移流速度的数据行（TRANSLATION）：**

**第一行：**

根据需要重复此数据行，以定义不同节点和自由度的平移流速度。

### **定义旋转流速度的数据行（ROTATION）：**

**第一行：**

根据需要重复此数据行，以定义不同节点的旋转流速度。