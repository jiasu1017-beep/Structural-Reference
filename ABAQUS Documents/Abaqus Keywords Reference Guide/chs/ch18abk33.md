# *STEADY STATE TRANSPORT





### *STEADY STATE TRANSPORT稳态传输分析。

此选项用于指示该步应作为稳态传输分析进行分析。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步

##### **参考：**

- ["Steady-state transport analysis," Section 6.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-asteadystatetransport)
- ["Symmetric model generation," Section 10.4.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aaximodelgen)

### **可选参数：**

ALLSDTOL

包含此参数以指示将在此步中激活自适应自动阻尼算法。将此参数设置为稳定能量与总应变能量的最大允许比值。初始阻尼因子通过STABILIZE参数或FACTOR参数指定。然后，该阻尼因子将基于收敛历史和ALLSDTOL值在步中调整。如果此参数设置为零，则不会激活自适应自动阻尼算法；将在整个步中使用恒定阻尼因子。如果此参数包含但未指定值，则默认值为0.05。如果省略此参数但包含具有耗散能量分数默认值的STABILIZE参数，则自适应自动阻尼算法将自动激活，ALLSDTOL=0.05。

此参数必须与STABILIZE参数配合使用（参见["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)）。

CONTINUE

设置CONTINUE=NO（默认）以指定此步不会从前一个通用步的结果中继承阻尼因子。在这种情况下，初始阻尼因子将基于声明的阻尼强度和步第一增量解重新计算，或可以直接指定。

设置CONTINUE=YES以指定此步将继承紧邻前一个通用步结束时的阻尼因子。

此参数必须与ALLSDTOL和STABILIZE参数配合使用。

DIRECT

此参数选择用户对步中间接增量的直接控制。如果使用此参数，则使用数据行第一项定义大小的恒定增量。如果省略此参数，则Abaqus/Standard将选择增量（在第一增量第一次尝试时尝试用户的初始时间增量后）。

参数可以具有值NO STOP。如果包含此值，则在完成允许的最大迭代次数（如[*CONTROLS](ch03abk75.md)选项所定义）后，即使未满足平衡容差，也将接受增量的解。如果使用此值，通常需要非常小的增量且至少两次迭代。*不推荐此方法；仅在分析师对如何解释以这种方式获得的结果有透彻理解的特殊情况下才应使用。*

ELSET

将此参数设置为将以空间或欧拉方式描述刚体运动的单元集名称。模型中其余单元将以经典拉格朗日方式处理。整个模型中只能指定一个欧拉单元集。

如果省略此参数，则整个模型中的刚体运动将以空间或欧拉方式描述。

FACTOR

如果由于局部不稳定预期问题可能不稳定，且Abaqus计算的阻尼因子不合适，则将此参数设置为自动阻尼算法（参见["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)）中使用的阻尼因子。此参数必须与STABILIZE参数配合使用，并覆盖基于耗散能量分数值对阻尼因子的自动计算。

INERTIA

包含此参数以指示必须考虑惯性效应。

设置INERTIA=NO（默认）以忽略惯性效应。

设置INERTIA=YES以包括惯性效应。

LONG TERM

包含此参数以指示在此步期间没有粘弹性或粘塑性材料响应。如果材料描述包括粘弹性材料属性，则解必须基于长期弹性模量；如果使用双层粘塑性材料模型，则解必须仅基于弹塑性网络的长期响应。

MULLINS

当使用Mullins效应材料模型时，包含此参数以指示Mullins效应应如何在此步中应用。

设置MULLINS=RAMP以指示Mullins效应应在当前步的时间段内斜升。

设置MULLINS=STEP（默认）以指示Mullins效应应在当前步开始时立即应用。

PASS BY PASS

包含此参数以指示将使用准稳态（逐通道）过程来获得稳态解。

如果省略此参数，则将直接获得稳态解。

STABILIZE

如果由于局部不稳定预期问题可能不稳定，则包含此参数以使用自动稳定。将此参数设置为自动阻尼算法（参见["Solving nonlinear problems," Section 7.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-anonlineareqns)）的耗散能量分数。如果省略此参数，则不会激活稳定算法。如果此参数包含但未指定值，则耗散能量分数的默认值为 ![](../graphics/key_eqn01084.gif)，并且自适应自动阻尼算法将默认在此步中激活，ALLSDTOL=0.05；设置ALLSDTOL=0以停用自适应自动阻尼算法。如果使用FACTOR参数，则任何耗散能量分数值都将被阻尼因子覆盖。

### **定义稳态传输分析的数据行：**

**第一行（也是唯一行）：**




