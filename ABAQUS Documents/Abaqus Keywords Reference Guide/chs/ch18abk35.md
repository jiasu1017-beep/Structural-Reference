# *STEADY STATE DYNAMICS





### *STEADY STATE DYNAMICS基于谐波激励的稳态动力学响应。

此选项用于计算系统对谐波激励的线性化稳态响应。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Step模块

##### **参考：**

- ["Direct-solution steady-state dynamic analysis," Section 6.3.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdyndirect)
- ["Mode-based steady-state dynamic analysis," Section 6.3.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdyn)
- ["Subspace-based steady-state dynamic analysis," Section 6.3.9 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystdynsubspace)

### **可选和互斥参数（仅在动态响应不是基于模态叠加时使用）：**

DIRECT

包含此参数以基于模型物理自由度直接计算稳态谐波响应。这通常会使过程显著更昂贵，但如果模型参数依赖于频率，或者系统刚度是非对称的且非对称项很重要，或者系统包含离散阻尼（如阻尼器单元），则可以使用此参数。

SUBSPACE PROJECTION

包含此参数以基于子空间投影方法计算稳态谐波响应。在这种情况下，对于投影到前一个[*FREQUENCY](ch06abk35.md)步获得的特征向量上的模型获得直接解。这是一种包含非对称刚度和频率相关模型参数考虑的经济有效的方法。它比模态叠加方法更昂贵，但比直接求解方法便宜。

如果要对数据行上请求的每个频率执行动态方程到模态子空间的投影，则设置SUBSPACE PROJECTION=ALL FREQUENCIES（默认）。

如果要对数据行上请求的所有频率使用动态方程到模态子空间的单一投影，则设置SUBSPACE PROJECTION=CONSTANT。投影使用在由FREQUENCY SCALE参数值决定的对数或线性尺度上确定的中心频率评估的模型属性执行。

如果要对动态方程的子空间投影在请求范围内每个特征频率以及这些范围之外的紧邻特征频率处执行，则设置SUBSPACE PROJECTION=EIGENFREQUENCY。然后在数据行上请求的每个频率处对投影进行插值。插值根据FREQUENCY SCALE参数的值以对数或线性尺度完成。

设置SUBSPACE PROJECTION=PROPERTY CHANGE以基于作为频率函数的材料属性变化选择子空间投影到模态子空间的执行频率。插值根据FREQUENCY SCALE参数的值以对数或线性尺度完成。

如果要对动态方程的子空间投影在每个频率范围的下限和最后一个频率范围的上限处执行，则设置SUBSPACE PROJECTION=RANGE。插值以线性尺度完成。此值只能与SIM架构一起使用。

### **可选参数：**

DAMPING CHANGE

此参数仅与SUBSPACE PROJECTION=PROPERTY CHANGE相关。

将此参数设置为在新投影执行之前阻尼材料属性的最大相对变化。默认值为0.1。

FREQUENCY SCALE

此参数仅在INTERVAL=EIGENFREQUENCY或INTERVAL=RANGE时相关。如果INTERVAL=SPREAD则使用线性尺度。

将此参数设置为LOGARITHMIC（默认）或LINEAR，以确定用于输出的尺度是对数还是线性。如果包含了SUBSPACE PROJECTION参数并设置为EIGENFREQUENCY或PROPERTY CHANGE，则相同的尺度将用于子空间投影的插值。

FRICTION DAMPING

此参数仅在包含DIRECT或SUBSPACE PROJECTION参数时相关。

设置FRICTION DAMPING=NO（默认）或YES，以忽略或包括在施加速度微分的滑动接触界面处的摩擦阻尼效应。

INTERVAL

如果使用系统的特征频率细分每个数据行上指定的频率范围，则设置INTERVAL=EIGENFREQUENCY。此选项需要前一个[*FREQUENCY](ch06abk35.md)步，如果省略DIRECT参数，则这是默认设置。

如果直接使用每个数据行上指定的频率范围，则设置INTERVAL=RANGE。如果包含DIRECT参数，则这是默认设置。

设置INTERVAL=SPREAD以在每个数据行上指定的频率范围内找到的特征频率周围定义频率点。此选项需要前一个[*FREQUENCY](ch06abk35.md)步。

REAL ONLY

此参数仅在包含DIRECT或SUBSPACE PROJECTION参数时相关。

如果忽略阻尼项以使实数（而非复数）系统矩阵被分解，则包含此参数。对于DIRECT过程，这可以显著减少计算时间，对于SUBSPACE PROJECTION过程则程度较轻。

STIFFNESS CHANGE

此参数仅与SUBSPACE PROJECTION=PROPERTY CHANGE相关。

将此参数设置为在新投影执行之前刚度材料属性的最大相对变化。默认值为0.1。

### **如果INTERVAL=EIGENFREQUENCY时的稳态动力学分析数据行：**

**第一行：**

根据需要重复此数据行以定义需要结果的所有频率范围。

### **如果INTERVAL=RANGE时的稳态动力学分析数据行：**

**第一行：**

根据需要重复此数据行以定义需要结果的所有频率范围。

### **如果INTERVAL=SPREAD时的稳态动力学分析数据行：**

**第一行：**

根据需要重复此数据行以定义需要结果的所有频率范围。




