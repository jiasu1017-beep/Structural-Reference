# *DAMAGE EVOLUTION





### *DAMAGE EVOLUTION指定定义损伤演化的材料属性。

此选项用于提供定义导致最终失效的损伤演化的材料属性。它必须与 [*DAMAGE INITIATION](ch04abk04.md) 选项结合使用。它可用于为内聚单元定义的材料、为富集单元、为使用纤维增强材料损伤模型的平面应力公式（平面应力、壳、连续壳和膜单元）定义的材料、与任何单元类型相关的低循环疲劳分析中的延性体材料，以及在Abaqus/Explicit中与任何单元类型相关的弹塑性材料。它还可以与 [*SURFACE INTERACTION](ch18abk50.md) 和 [*DAMAGE INITIATION](ch04abk04.md) 选项结合使用，以定义允许为内聚表面建模渐进失效的接触属性模型。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["延性金属的损伤演化与单元移除，" Abaqus分析用户指南第24.2.3节](../usb/usb-link.md#usb-mat-cdamageevolductile)
- ["纤维增强复合材料的损伤演化与单元移除，" Abaqus分析用户指南第24.3.3节](../usb/usb-link.md#usb-mat-cdamageevolfibercomposite)
- ["低循环疲劳中延性材料的损伤演化，" Abaqus分析用户指南第24.4.3节](../usb/usb-link.md#usb-mat-cdamageevolfatigue)
- ["使用牵引-分离描述定义内聚单元的本构响应，" Abaqus分析用户指南第32.5.6节](../usb/usb-link.md#usb-elm-ecohesivebehavior)
- ["基于表面的内聚行为，" Abaqus分析用户指南第37.1.10节](../usb/usb-link.md#usb-cni-acohesivebehavior)
- ["使用扩展有限元方法将不连续性建模为富集特征，" Abaqus分析用户指南第10.7.1节](../usb/usb-link.md#usb-anl-aenrichment)

### **必需参数：**

TYPE

设置 TYPE=DISPLACEMENT 以将损伤演化定义为损伤起始后总位移（对于内聚单元中的弹性材料）或塑性位移（对于体弹塑性材料）的函数。

设置 TYPE=ENERGY 以根据损伤起始后的失效所需能量（断裂能）定义损伤演化。

设置 TYPE=HYSTERESIS ENERGY 以根据低循环疲劳分析中损伤起始后每个稳定循环消耗的非弹性滞回能定义损伤演化。

### **可选参数：**

DEGRADATION

设置 DEGRADATION=MAXIMUM（默认）以指定当前损伤演化机制将以最大值方式与其他损伤演化机制相互作用，以确定来自多个机制的总损伤。

设置 DEGRADATION=MULTIPLICATIVE 以指定当前损伤演化机制将使用乘法方式与具有相同 DEGRADATION 参数值的其他损伤演化机制相互作用，以确定来自多个机制的总损伤。

DEPENDENCIES

将此参数设置为损伤演化定义中包含的场变量数量。如果省略此参数，则假定定义损伤演化的属性是常数或仅取决于温度。有关详细信息，请参见Abaus分析用户指南第21.1.2节中的["指定场变量依赖性"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

FAILURE INDEX

此参数只能与用户定义的损伤起始准则结合使用。

将此参数设置为富集单元的用户定义损伤起始准则中指定的相应失效机制。

MIXED MODE BEHAVIOR

此参数仅在 [*DAMAGE EVOLUTION](ch04abk03.md) 选项用于定义与内聚单元关联的材料或基于表面的内聚行为的损伤演化时才有意义。如果省略此参数，Abaqus假定损伤演化行为与模式无关。

设置 MIXED MODE BEHAVIOR=TABULAR 以直接作为内聚单元剪切-法向模式混合的函数指定断裂能或位移（总位移或塑性位移）。当 TYPE=DISPLACEMENT 时，此方法必须用于指定内聚单元的混合模式行为。

设置 MIXED MODE BEHAVIOR=POWER LAW 以通过幂律混合模式断裂准则将断裂能作为模式混合的函数指定。

设置 MIXED MODE BEHAVIOR=BK 以通过Benzeggagh-Kenane混合模式断裂准则将断裂能作为模式混合的函数指定。

MODE MIX RATIO

此参数只能与 MIXED MODE BEHAVIOR 参数结合使用。损伤演化属性（断裂能或有效位移）作为模式混合函数的规范取决于此参数的值。有关详细信息，请参见"使用牵引-分离描述定义内聚单元的本构响应"第32.5.6节中的["将损伤演化数据定义为模式混合的表格函数"]（../usb/usb-link.md#usb-elm-ecohesivebehavior-modemix），或"基于表面的内聚行为"第37.1.10节中的["将损伤演化数据定义为模式混合的表格函数"]（../usb/usb-link.md#usb-cni-acohesivebehavior-modemix）。

设置 MODE MIX RATIO=ENERGY（Abaqus/Standard中基于表面的内聚行为和与内聚单元关联的材料的默认设置）以根据不同模式中断裂能的比率定义模式混合。断裂能仅基于当前的变形状态计算，而不是变形历史。此选项可在 MIXED MODE BEHAVIOR=POWER LAW 或 BK 时使用。此选项不适用于Abaqus/Explicit中基于表面的内聚行为。

设置 MODE MIX RATIO=ACCUMULATED ENERGY（Abaqus/Explicit中基于表面的内聚行为的默认设置）以根据不同模式中断裂能的比率定义模式混合。断裂能基于积分点整个变形历史中累积的能量计算。此选项可在 MIXED MODE BEHAVIOR=POWER LAW 或 BK 时使用。

设置 MODE MIX RATIO=TRACTION 以根据牵引分量的比率定义模式混合。

POWER

此参数只能与 MIXED MODE BEHAVIOR=POWER LAW 或 MIXED MODE BEHAVIOR=BK 结合使用。

将此参数设置为幂律或Benzeggagh-Kenane准则中定义为内聚单元模式混合函数的断裂能变化的指数。

SOFTENING

设置 SOFTENING=LINEAR（默认）以为线性弹性材料指定线性软化应力-应变响应（损伤起始后），或为弹塑性材料指定损伤变量随变形的线性演化（损伤起始后）。

设置 SOFTENING=EXPONENTIAL 以为线性弹性材料指定指数软化应力-应变响应（损伤起始后），或为弹塑性材料指定损伤变量随变形的指数演化（损伤起始后）。

设置 SOFTENING=TABULAR 以表格形式指定损伤变量随变形的演化（损伤起始后）。SOFTENING=TABULAR 只能与 TYPE=DISPLACEMENT 结合使用。

### **指定 TYPE=DISPLACEMENT、SOFTENING=LINEAR 且没有 MIXED MODE BEHAVIOR 参数的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于六时需要）：**

根据需要重复此组数据行，以将失效时的总位移或塑性位移定义为温度和其他预定义场变量的函数。

### **指定 TYPE=ENERGY、SOFTENING=LINEAR 且没有 MIXED MODE BEHAVIOR 参数的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于六时需要）：**

根据需要重复此组数据行，以将断裂能定义为温度和其他预定义场变量的函数。

### **指定 TYPE=DISPLACEMENT、SOFTENING=LINEAR、MIXED MODE BEHAVIOR=TABULAR 的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将失效时的总位移定义为其与模式混合、温度和其他预定义场变量的函数。

### **指定 TYPE=ENERGY、SOFTENING=LINEAR、MIXED MODE BEHAVIOR=TABULAR 的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将断裂能定义为其与模式混合、温度和其他预定义场变量的函数。

### **指定 TYPE=DISPLACEMENT、SOFTENING=EXPONENTIAL 且没有 MIXED MODE BEHAVIOR 参数的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将失效时的总位移或塑性位移以及指数律参数定义为温度和其他预定义场变量的函数。

### **指定 TYPE=ENERGY、SOFTENING=EXPONENTIAL 且没有 MIXED MODE BEHAVIOR 参数的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于六时需要）：**

根据需要重复此组数据行，以将断裂能定义为温度和其他预定义场变量的函数。

### **指定 TYPE=DISPLACEMENT、SOFTENING=EXPONENTIAL、MIXED MODE BEHAVIOR=TABULAR 的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此组数据行，以将失效时的总位移和指数律参数定义为其与模式混合、温度和其他预定义场变量的函数。

### **指定 TYPE=ENERGY、SOFTENING=EXPONENTIAL、MIXED MODE BEHAVIOR=TABULAR 的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将断裂能定义为其与模式混合、温度和其他预定义场变量的函数。

### **指定 TYPE=DISPLACEMENT、SOFTENING=TABULAR 且没有 MIXED MODE BEHAVIOR 参数的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将损伤变量定义为其与总位移或塑性位移、温度和其他预定义场变量的函数。

### **指定 TYPE=DISPLACEMENT、SOFTENING=TABULAR、MIXED MODE BEHAVIOR=TABULAR 的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此组数据行，以将损伤变量定义为其与总位移、模式混合、温度和其他预定义场变量的函数。

### **指定 TYPE=ENERGY、SOFTENING=LINEAR 或 EXPONENTIAL、MIXED MODE BEHAVIOR=POWER LAW 或 BK 的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将断裂能定义为温度和其他预定义场变量的函数。

### **指定 TYPE=ENERGY、SOFTENING=LINEAR 用于纤维增强材料损伤模型的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此组数据行，以将断裂能量对温度和其他预定义场变量的依赖性定义为函数。

### **指定低循环疲劳分析中 TYPE=HYSTERESIS ENERGY 的损伤演化的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将材料常数对温度和其他预定义场变量的依赖性定义为函数。




