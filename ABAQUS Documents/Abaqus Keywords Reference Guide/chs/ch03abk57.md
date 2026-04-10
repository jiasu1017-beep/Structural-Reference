# *CONTACT CONTROLS






### *CONTACT CONTROLS为接触指定附加控制。

此选项用于为涉及物体之间接触的模型提供额外的可选求解控制。标准求解控制通常足够，但附加控制有助于为涉及复杂几何形状和众多接触界面的模型获得具有成本效益的求解，也适用于最初未约束刚体运动的模型。

[*CONTACT CONTROLS](ch03abk57.md) 选项可以重复以为不同的接触对设置不同的控制值。必须在 Abaqus/Explicit 分析中与 [*CONTACT PAIR](ch03abk68.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE: **相互作用模块

##### **参考：**

- ["在 Abaqus/Standard 中调整接触控制，" Abaqus 分析用户指南第 36.3.6 节](../usb/usb-link.md#usb-cni-acontactcontrolsstd)
- ["在 Abaqus/Explicit 中定义接触对，" Abaqus 分析用户指南第 36.5.1 节](../usb/usb-link.md#usb-cni-aexpcontactpair)
- ["Abaqus/Explicit 中接触对的接触控制，" Abaqus 分析用户指南第 36.5.5 节](../usb/usb-link.md#usb-cni-acontactcontrolsexp)
- [*CONTACT PAIR](ch03abk68.md)

### 在 Abaqus/Standard 分析中为接触指定附加控制

### **适用于增广拉格朗日约束强制的可选互斥参数：**

ABSOLUTE PENETRATION TOLERANCE

将此参数设置为允许的渗透量。只有使用增广拉格朗日表面行为定义的接触约束将受此参数影响。

RELATIVE PENETRATION TOLERANCE

将此参数设置为允许渗透量与特征接触表面面孔尺寸的比值。只有使用增广拉格朗日表面行为定义的接触约束将受此参数影响。默认情况下，RELATIVE PENETRATION TOLERANCE 参数设置为 0.1%，对于有限滑动、表面到表面接触，默认设置为 5%。

### **可选参数：**

MASTER

将此参数设置为主表面名称，以将控制应用于特定的接触对。此参数必须与 SLAVE 参数结合使用以指定接触对。

PERTURBATION TANGENT SCALE FACTOR

将此参数设置为 Abaqus/Standard 在特定线性扰动步骤中用于接触对的默认切向刚度缩放的因子。只有使用惩罚方法强制的接触约束将受此参数影响。当在 [*FRICTION](ch06abk36.md) 选项的数据行上指定了非零摩擦时，此切向缩放因子被激活。

PRESSURE DEPENDENT PERTURBATION

将此参数设置为控制基态接触压力依赖的接触约束强制的 ![](../graphics/key_eqn00360.gif) 系数值。此参数允许你放松或移除低压下的法和切向接触约束。

RESET

包含此参数以将所有接触控制重置为其默认值。此参数不能与任何其他参数一起使用，SLAVE 和 MASTER 参数除外。当此参数与 SLAVE 和 MASTER 参数结合使用时，应用于特定接触对的控制将被移除。

SLAVE

将此参数设置为从表面名称，以将控制应用于特定的接触对。此参数必须与 MASTER 参数结合使用以指定接触对。

STABILIZE

包含此参数以解决只要接触未完全建立就存在刚体模式的情况。此参数基于底层网格的刚度和时间步长尺寸在法和切向方向激活阻尼。如果没有为些参数分配值，Abaqus 会自动计算阻尼系数。如果为些参数分配了数值，Abaqus 会将此数值乘以自动计算的阻尼系数。如果阻尼系数直接在数据行上定义，则此参数分配的任何数值将被忽略。

设置 STABILIZE=USER ADAPTIVE 以根据第二个数据行上指定的模式，在增量内的迭代过程中按因子减小自动计算的阻尼系数或在数据行上指定的阻尼系数。

STABILIZE 参数可用于为整个模型或单个接触对指定阻尼，方法是使用 SLAVE 和 MASTER 参数。为特定接触对指定的值将覆盖为整个模型指定的值（如果有）。

STIFFNESS SCALE FACTOR

将此参数设置为 Abaqus/Standard 将用于缩放默认惩罚刚度以获得接触对使用的刚度的因子。

设置 STIFFNESS SCALE FACTOR=USER ADAPTIVE 以在第一个增量的迭代过程中按因子增加默认惩罚刚度，并在后续增量中保持不变（等于最后指定的值）。

此缩放因子作为在 [*SURFACE BEHAVIOR](ch18abk48.md) 选项的数据行上指定的任何缩放因子的附加乘数。

TANGENT FRACTION

将此参数设置为如 STABILIZE 参数所指定的法向阻尼的一部分。默认情况下，切向和法向稳定化是相同的。

### **如果包含了 PRESSURE DEPENDENT PERTURBATION 参数时的可选数据行：**

**第一行（也是唯一一行）：**

### **如果包含了 STABILIZE 参数时的可选数据行：**

**第一行：**

**如果 STABILIZE=USER ADAPTIVE，则需要第二行：**

### **如果 STIFFNESS SCALE FACTOR=USER ADAPTIVE 时的可选数据行：**

**如果 STABILIZE=USER ADAPTIVE，则为第三行；否则为第一行：**

### 在 Abaqus/Explicit 分析中为接触指定附加控制

**警告：**这些控制适用于有经验的分析师，应谨慎使用。使用这些控制的非默认值可能会大大增加分析的计算时间或产生不准确的结果。

### **必需参数：**

CPSET

将此参数设置为与此接触控制定义关联的接触对集合名称。使用此选项定义的接触控制将应用于所有具有此接触对集合名称的接触对。

### **可选参数：**

FASTLOCALTRK

如果接触未正确强制执行，则设置 FASTLOCALTRK=NO。将使用更保守的局部跟踪方法来解决错误。默认为 FASTLOCALTRK=YES，使用计算效率更高的局部跟踪方法。

GLOBTRKINC

将此参数设置为全局接触搜索之间的最大增量数。默认值为双面接触 100 个增量，自接触 4 个增量。

RESET

包含此参数以将所有可选控制重置为其默认值。那些在同一 [*CONTACT CONTROLS](ch03abk57.md) 选项上通过其他参数明确指定控制不会被重置。如果省略此参数，则只有明确指定的控制将在当前步骤中更改；其他将保持其先前的设置。

SCALE PENALTY

将此参数设置为 Abaqus/Explicit 将用于缩放默认惩罚刚度以获得在 CPSET 参数指定的接触对集合内惩罚接触对使用的刚度的因子。使用软化表面行为和运动接触约束定义的惩罚接触约束将不受此参数影响。默认情况下，SCALE PENALTY 参数设置为 1。

WARP CHECK PERIOD

将此参数设置为检查主表面高度翘曲小平面之间的增量数。默认情况下，每 20 个增量执行一次检查。更频繁的检查会导致计算时间略有增加。

WARP CUT OFF

将此参数设置为一个平面外翘曲角度（以度为单位），超过该角度的小平面将被视为高度翘曲。平面外翘曲角定义为表面法线在小平面上的变化量。默认值为 WARP CUT OFF=20。

### **此选项没有关联的数据行。**




