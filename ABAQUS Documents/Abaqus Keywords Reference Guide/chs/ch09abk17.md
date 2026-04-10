# *INERTIA RELIEF






### *INERTIA RELIEF应用基于惯性的载荷平衡。

此选项用于在自由或部分约束的物体上施加基于惯性的载荷。

**产品：** Abaqus/Standard  Abaqus/CAE  

**类型：** 历史数据  

**级别：** 步骤  

**Abaqus/CAE：** Load 模块

##### **参考文献：**

- ["惯性释放，" Abaqus Analysis User's Guide 第 11.1.1 节](../usb/usb-link.md#usb-anl-ainertiarelief)
- ["分布载荷，" Abaqus Analysis User's Guide 第 34.4.3 节](../usb/usb-link.md#usb-prc-ploaddistributed)

### **可选参数：**

ORIENTATION

将此参数设置为给 [*ORIENTATION](ch15abk01.md) 定义（["方向，" Abaqus Analysis User's Guide 第 2.2.5 节](../usb/usb-link.md#usb-int-corientation)）的名称，该定义指定刚性体自由度局部系统的方向。

### **可选的、互斥的参数：**

FIXED

包含此参数（默认）以指示先前步骤中的惯性释放载荷应保持在其从当前步骤开始时的值。

REMOVE

包含此参数以指示先前步骤中的惯性释放载荷应在当前步骤中移除。

### **指定全局（或局部，如果使用了 ORIENTATION 参数）自由度的可选数据行，这些自由度定义了应用惯性释放载荷的自由方向：**

**第一行：**

**第二行（仅在用户选择的自由方向组合需要参考点以定义刚性体方向向量时需要）：**

这些数据行仅在某些方向上约束了刚性体运动时需要。

### **当指定了 FIXED 或 REMOVE 参数时，没有数据行。**




