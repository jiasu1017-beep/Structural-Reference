# *ADAPTIVE MESH CONTROLS





### *ADAPTIVE MESH CONTROLS指定自适应网格划分和对流算法的控制。

此选项用于控制应用于自适应网格域的自适应网格划分和对流算法的各个方面。它只能与[*ADAPTIVE MESH](ch01abk04.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据

**级别：**Step

**Abaqus/CAE：**Step模块

##### **参考：**

- ["在Abaqus/Explicit中定义ALE自适应网格域，" Abaqus Analysis User's Guide第12.2.2节](../usb/usb-link.md#usb-anl-aaledomains)
- ["在Abaqus/Explicit中进行ALE自适应网格划分和重映射，" Abaqus Analysis User's Guide第12.2.3节](../usb/usb-link.md#usb-anl-aaleremesh)
- ["在Abaqus/Standard中定义ALE自适应网格域，" Abaqus Analysis User's Guide第12.2.6节](../usb/usb-link.md#usb-anl-aalestd)
- ["在Abaqus/Standard中进行ALE自适应网格划分和重映射，" Abaqus Analysis User's Guide第12.2.7节](../usb/usb-link.md#usb-anl-aalestdremesh)
- [*ADAPTIVE MESH](ch01abk04.md)

### **必需参数：**

NAME

将此参数设置为一个标签，用于引用此自适应网格控制定义。同一输入文件中的自适应网格控制名称必须唯一。

### **可选参数：**

ADVECTION

此参数仅适用于Abaqus/Explicit分析。

设置ADVECTION=SECOND ORDER（默认值）以使用二阶算法在执行自适应网格划分后重新映射解变量。

设置ADVECTION=FIRST ORDER以使用一阶算法在执行自适应网格划分后重新映射解变量。

CURVATURE REFINEMENT

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为解相关性权重，![](../graphics/key_eqn00003.gif)。默认值为![](../graphics/key_eqn00004.gif)。

GEOMETRIC ENHANCEMENT

设置GEOMETRIC ENHANCEMENT=YES（在Abaqus/Explicit分析中为默认值）以使用基于演化元素几何形状增强的平滑算法。

设置GEOMETRIC ENHANCEMENT=NO（在Abaqus/Standard分析中为默认值）以使用传统形式的平滑算法。

INITIAL FEATURE ANGLE

将此参数设置为初始几何特征角，![](../graphics/key_eqn00005.gif)，以度为单位（![](../graphics/key_eqn00006.gif)）。此角度用于检测几何边缘和角落。默认值为![](../graphics/key_eqn00007.gif)。设置![](../graphics/key_eqn00008.gif)将确保不检测或强制执行任何几何边缘或角落。

MESH CONSTRAINT ANGLE

此参数仅适用于Abaqus/Explicit分析。

将此参数设置为网格约束角，![](../graphics/key_eqn00009.gif)，以度为单位（![](../graphics/key_eqn00010.gif)）。默认值为![](../graphics/key_eqn00011.gif)。

当自适应网格约束应用于Lagrangian或滑动边界区域上的节点时，如果边界区域的法线方向与规定约束方向之间的角度变得小于![](../graphics/key_eqn00009.gif)，分析将终止。当自适应网格约束应用于属于Lagrangian或活动几何边缘一部分的节点时，如果规定约束与垂直于边缘的平面之间的角度变得小于![](../graphics/key_eqn00009.gif)，分析将终止。

MESHING PREDICTOR

此参数在Abaqus/Explicit和Abaqus/Standard分析中的解释不同。

在Abaqus/Explicit分析中，如果自适应网格域没有Eulerian边界区域，设置MESHING PREDICTOR=CURRENT（默认值）以基于当前节点位置执行自适应网格划分；此方法推荐用于所有类Lagrangian问题和具有非常大扭曲的问题。设置MESHING PREDICTOR=PREVIOUS（默认值，如果自适应网格域有一个或多个Eulerian边界区域）以基于前一个自适应网格增量结束时的节点位置执行自适应网格划分；此技术推荐用于材料流动相对于整体变形显著的Eulerian类问题。

在Abaqus/Standard分析中，设置MESHING PREDICTOR=CURRENT以基于当前自适应网格增量开始时的节点位置执行自适应网格划分。设置MESHING PREDICTOR=PREVIOUS（默认值）以基于原始网格中的节点位置执行自适应网格划分。

MOMENTUM ADVECTION

此参数仅适用于Abaqus/Explicit分析。

设置MOMENTUM ADVECTION=ELEMENT CENTER PROJECTION（默认值）以使用元素中心投影方法进行动量对流。此方法比半指数偏移方法计算成本更低。

设置MOMENTUM ADVECTION=HALF INDEX SHIFT以使用半指数偏移方法进行动量对流。此算法的计算成本更高，但可能表现出比元素中心投影方法更好的色散特性。

RESET

包含此参数以将所有自适应网格控制重置为其默认值。在同一[*ADAPTIVE MESH CONTROLS](ch01abk06.md)选项上使用其他参数指定的控制将被保留。如果省略此参数，则仅更改当前step中指定控制；其他控制将保持其在前一个step中的设置。

SMOOTHING OBJECTIVE

此参数仅适用于Abaqus/Explicit分析。

如果自适应网格域在显式动态分析中没有Eulerian边界区域，设置SMOOTHING OBJECTIVE=UNIFORM（默认值）以执行最小化元素扭曲并改善元素长宽比的自适应网格划分，代价是扩散初始网格梯度。此目标推荐用于具有中等到大整体变形的问题。

如果自适应网格域在显式动态分析中有一个或多个Eulerian边界区域，设置SMOOTHING OBJECTIVE=GRADED（默认值）以执行尝试在分析演化过程中保持初始网格梯度的同时减少扭曲的自适应网格划分。此目标仅推荐用于具有合理结构化梯度网格且经历低到中等整体变形的自适应网格域。

TRANSITION FEATURE ANGLE

将此参数设置为过渡几何特征角，![](../graphics/key_eqn00012.gif)，以度为单位（![](../graphics/key_eqn00013.gif)）。此角度用于确定何时应停用几何边缘和角落以允许跨它们重划分网格。默认值为![](../graphics/key_eqn00014.gif)。设置![](../graphics/key_eqn00015.gif)将确保不停用任何几何边缘或角落。

### **在Abaqus/Explicit分析中定义组合网格平滑方法的数据行：**

**第一行（也是唯一一行）：**

每个权重必须为零或正数，它们的和通常应为1.0。如果权重之和小于1.0，则网格平滑算法在每个自适应网格增量中将不那么积极。如果权重之和大于1.0，则对其值进行归一化，使其和为1.0。

### **在Abaqus/Standard分析中定义组合网格平滑方法的数据行：**

**第一行（也是唯一一行）：**

每个权重必须为零或正数，且它们的和必须非零。权重仅在相对意义上重要；对其值进行归一化，使其和为1.0。