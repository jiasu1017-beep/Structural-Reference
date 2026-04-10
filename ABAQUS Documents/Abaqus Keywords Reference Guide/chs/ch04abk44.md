# *DYNAMIC





### *DYNAMIC动态应力/位移分析。

此选项用于在Abaqus/Standard分析中提供动态应力/位移响应的直接积分，通常用于非线性情况。它用于在Abaqus/Explicit中使用显式积分执行动态应力/位移分析。Abaqus/Standard和Abaqus/Explicit中的分析也可以是绝热的。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["使用直接积分的隐式动态分析，" Abaqus分析用户指南第6.3.2节](../usb/usb-link.md#usb-anl-adynamic)
- ["显式动态分析，" Abaqus分析用户指南第6.3.3节](../usb/usb-link.md#usb-anl-aexpdynamic)
- ["绝热分析，" Abaqus分析用户指南第6.5.4节](../usb/usb-link.md#usb-anl-aadiabaticanal)

### 在Abaqus/Standard中定义动态分析

### **子空间投影方法的可选参数：**

SUBSPACE

包含此参数以选择子空间投影方法（在前一步骤之前获得的特征向量上投影的模型的显式积分）。

如果省略此参数，则使用所有全局自由度级别动态方程的隐式时间积分。

### **一般隐式积分方法的可选参数：**

ADIABATIC

如果将执行绝热应力分析，则包含此参数。此参数仅与具有Mises屈服面的各向同性金属塑性材料相关，且当已指定 [*INELASTIC HEAT FRACTION](ch09abk16.md) 选项时。

ALPHA

将此参数设置为隐式算子中数值（人工）阻尼控制参数 ![](../graphics/key_eqn00080.gif) 的非默认值，用于 TIME INTEGRATOR=HHT-TF 或 HHT-MD。允许值为0（无阻尼）到–0.5。值为0.333提供最大阻尼。TIME INTEGRATOR=HHT-TF 的默认值为 ALPHA=0.05，它提供轻微的数值阻尼。

APPLICATION

使用此参数选择时间积分方法。其他参数值由所选的时间积分方法确定。您可以通过直接指定这些参数值来覆盖默认值。

设置 APPLICATION=TRANSIENT FIDELITY（模型中无接触问题的默认设置）以选择具有轻微数值阻尼的精确求解方法。将设置 TIME INTEGRATOR=HHT-TF、IMPACT=AVERAGE TIME 和 INCREMENTATION=CONSERVATIVE。

设置 APPLICATION=MODERATE DISSIPATION（模型中有接触问题的默认设置）以选择具有大于默认数值阻尼和更积极的时间增量方案的方法，以牺牲一定的求解精度为代价。将设置 TIME INTEGRATOR=HHT-MD、IMPACT=NO 和 INCREMENTATION=AGGRESSIVE。

设置 APPLICATION=QUASI-STATIC 以选择具有非常显著的数值阻尼的方法，主要用于获得准静态解。将设置 TIME INTEGRATOR=BWE、IMPACT=NO 和 INCREMENTATION=AGGRESSIVE。此外，默认步骤幅值设置为 RAMP 而不是 STEP。

BETA

将此参数设置为隐式算子中数值 ![](../graphics/key_eqn00135.gif) 的非默认值，用于 TIME INTEGRATOR=HHT-TF 或 HHT-MD。允许值为正数。

DIRECT

包含此参数以选择通过步骤的直接用户控制增量。如果包含此参数且没有发生接触冲击或释放，则使用数据行上定义大小的恒定增量。如果省略此参数，Abaqus/Standard将在第一次增量尝试的第一次尝试用户的初始时间增量后使用自动时间增量方案。DIRECT 参数和 HAFTOL 和 HALFINC SCALE FACTOR 参数互斥。

DIRECT 参数可以具有值 NO STOP。如果包含此值，则在完成允许的最大迭代次数（如 [*CONTROLS](ch03abk75.md) 选项中所定义）后，即使未满足平衡容差，也将接受增量的解。如果使用此值，通常需要小增量和至少两次迭代。*这种方法通常不推荐；仅应在分析师对如何解释以这种方式获得的结果有透彻理解的特殊情况下使用。*

GAMMA

将此参数设置为隐式算子中数值 ![](../graphics/key_eqn00029.gif) 的非默认值，用于 TIME INTEGRATOR=HHT-TF 或 HHT-MD。允许值大于或等于0.5。

HAFTOL

将此参数设置为要与自动时间增量方案一起使用的半增量残差容差。对于自动时间增量，如果未指定 HALFINC SCALE FACTOR，则此值控制解的精度。建议使用 HALFINC SCALE FACTOR 参数而不是 HAFTOL 参数。如果同时包含两者，则忽略 HAFTOL 参数。DIRECT 和 HAFTOL 参数互斥。

HAFTOL 参数具有力维度，通常通过与典型实际力值（如施加的力或预期反作用力）的比较来选择。以下指南可能会有所帮助。对于预期有相当大的塑性或其他耗散来抑制高频响应的问题，选择 HAFTOL 为典型实际力值的10到100倍以获得中等精度和低成本；选择 HAFTOL 为典型实际力值的1到10倍以获得更高精度。在这种情况下，通常不需要更小的 HAFTOL 值。

对于具有小阻尼的弹性情况，高频模式通常在整个问题中保持重要；因此，HAFTOL 值应小于上面建议的值。选择 HAFTOL 为典型实际力值的1到10倍以获得中等精度；选择 HAFTOL 为实际力值的0.1到1倍以获得更高精度。

HALFINC SCALE FACTOR

将此参数设置为应用于Abaqus/Standard计算的时间平均力和力矩值的缩放因子，用作自动时间增量解精度检查方案的半增量残差容差。DIRECT 和 HALFINC SCALE FACTOR 参数互斥。当设置 NOHAF 参数时，HALFINC SCALE FACTOR 被忽略。

HALFINC SCALE FACTOR 参数是无量纲的。作为指导，较小的 HALFINC SCALE FACTOR 值应以使用更精细的时间增量为代价获得更精确的解。默认情况下，对于 APPLICATION=TRANSIENT FIDELITY，如果在模型中存在接触则设置为10000，否则设置为1000。这些默认值与建议的 HAFTOL 比率不同，主要是因为 HALFINC SCALE FACTOR 应用于已知的力平均值；因此，它们不必那么保守。

IMPACT

使用此参数在分析期间发生接触冲击或释放时选择时间增量类型。

设置 IMPACT=AVERAGE TIME 以选择采用冲击/释放回退的平均时间来强制能量平衡并保持主动接触界面上兼容的速度和加速度的时间增量方案。IMPACT=AVERAGE TIME 和 TIME INTEGRATOR=BWE 设置互斥。

设置 IMPACT=CURRENT TIME 以选择"穿越"方案，没有冲击/释放回退。速度和加速度在主动接触界面上兼容。

设置 IMPACT=NO 以选择没有冲击/释放回退且没有速度/加速度兼容性计算的"穿越"方案。

INCREMENTATION

使用此参数选择一般时间增量类型。

设置 INCREMENTATION=CONSERVATIVE 以选择最大化解精度的时间增量方案。

设置 INCREMENTATION=AGGRESSIVE 以选择仅基于收敛历史的时间增量方案，类似于静态问题中通常使用的方案（无速率或历史依赖）。设置 INCREMENTATION=AGGRESSIVE 也会设置 NOHAF 参数的值。

INITIAL

默认情况下，如果使用 IMPACT 值而不是 NO，Abaqus/Standard将在步骤开始时计算或重新计算加速度。设置 INITIAL=NO 以绕过步骤开始时初始加速度的计算。

如果 INITIAL=NO，如果当前步骤是第一个 [*DYNAMIC](ch04abk43.md) 步骤，则 Abaqus/Standard假定当前步骤的初始加速度为零。如果紧接前面的步骤也是 [*DYNAMIC](ch04abk43.md) 步骤，则使用 INITIAL=NO 会导致 Abaqus/Standard使用前一步骤结束时的加速度来继续新步骤。只有在步骤开始时载荷不会突然变化的情况下，这才是合适的。

NOHAF

包含此参数以抑制半增量残差的计算，从而跳过自动时间增量方案的一些精度检查。对于包含 DIRECT 参数的固定时间增量，Abaqus/Standard默认计算半增量残差；NOHAF 参数关闭此计算，节省一些求解成本。

SINGULAR MASS

使用此参数在初始化期间或接触冲击/释放计算期间检测到奇异全局质量矩阵时控制速度和加速度调整。

设置 SINGULAR MASS=ERROR（默认）以在检测到奇异全局质量矩阵时发出错误消息并停止执行。

设置 SINGULAR MASS=WARNING 以在检测到奇异全局质量矩阵时发出警告消息并避免这些速度和加速度调整（即，继续使用当前速度和加速度进行时间积分）。

设置 SINGULAR MASS=MAKE ADJUSTMENTS 以即使检测到奇异质量矩阵也调整速度和加速度。此设置可能导致大的、非物理的速度和/或加速度调整，这又可能导致差的时间积分解和人造收敛困难。*这种方法通常不推荐；仅应在分析师对如何解释以这种方式获得的结果有透彻理解的特殊情况下使用。*

TIME INTEGRATOR

使用此参数选择时间积分方法。

设置 TIME INTEGRATOR=BWE 以选择后向Euler时间积分器。

设置 TIME INTEGRATOR=HHT-TF 以选择Hilber-Hughes-Taylor时间积分器，其默认参数设置提供轻微的数值阻尼。这是 APPLICATION=TRANSIENT FIDELITY 的默认值。

设置 TIME INTEGRATOR=HHT-MD 以选择Hilber-Hughes-Taylor时间积分器，其默认参数设置提供中等数值阻尼。这是 APPLICATION=MODERATE DISSIPATION 的默认值。

### **瞬态动态分析的数据行：**

**第一行（也是唯一一行）：**

### 在Abaqus/Explicit中定义动态分析

### **必需参数：**

EXPLICIT

包含此参数以指定显式时间积分。

### **可选、互斥参数：**

DIRECT USER CONTROL

包含此参数以指定此步骤应使用由用户指定的固定时间增量。

ELEMENT BY ELEMENT

包含此参数以指示应使用逐单元稳定时间增量估计的可变自动时间增量。此方法通常需要比全局时间估计器更多的增量 和更多的计算时间。

FIXED TIME INCREMENTATION

包含此参数以指定此步骤应使用固定时间增量，该增量将在步骤开始时由Abaqus/Explicit使用逐单元时间估计器确定。

### **可选参数：**

ADIABATIC

包含此参数以指定将执行绝热应力分析。此参数仅与金属塑性（["非弹性行为，" Abaqus分析用户指南第23.1.1节](../usb/usb-link.md#usb-mat-cplastic)）相关。必须在适当的材料定义中指定 [*INELASTIC HEAT FRACTION](ch09abk16.md) 和 [*SPECIFIC HEAT](ch18abk27.md) 选项。

IMPROVED DT METHOD

设置 IMPROVED DT METHOD=YES（默认）以使用"改进"方法估计三维连续体单元和平面应力公式（壳、膜和二维平面应力单元）的单元稳定时间增量。

设置 IMPROVED DT METHOD=NO 以使用保守方法估计三维连续体单元和平面应力公式的单元稳定时间增量。

SCALE FACTOR

将此参数设置为用于缩放由Abaqus/Explicit计算的时间增量的因子。默认缩放因子为1.0。此参数可用于缩放默认的全局时间估计，并且可以与 ELEMENT BY ELEMENT 和 FIXED TIME INCREMENTATION 参数结合使用。它不能与 DIRECT USER CONTROL 参数结合使用。

### **自动时间增量（全局或逐单元估计）的数据行：**

**第一行（也是唯一一行）：**

### **使用 DIRECT USER CONTROL 的固定时间增量的数据行：**

**第一行（也是唯一一行）：**

### **使用 FIXED TIME INCREMENTATION 的固定时间增量的数据行：**

**第一行（也是唯一一行）：**




