# *DAMAGE INITIATION





### *DAMAGE INITIATION指定定义损伤起始的材料属性和接触属性。

此选项用于提供定义损伤起始的材料属性。它还可以与 [*SURFACE INTERACTION](ch18abk50.md) 选项结合使用，以定义允许定义内聚表面损伤起始的接触属性模型。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["延性金属的损伤起始，" Abaqus分析用户指南第24.2.2节](../usb/usb-link.md#usb-mat-cdamageinitductile)
- ["纤维增强复合材料的损伤起始，" Abaqus分析用户指南第24.3.2节](../usb/usb-link.md#usb-mat-cdamageinitfibercomposite)
- ["低循环疲劳中延性材料的损伤起始，" Abaqus分析用户指南第24.4.2节](../usb/usb-link.md#usb-mat-cdamageinitfatigue)
- ["使用牵引-分离描述定义内聚单元的本构响应，" Abaqus分析用户指南第32.5.6节](../usb/usb-link.md#usb-elm-ecohesivebehavior)
- ["使用扩展有限元方法将不连续性建模为富集特征，" Abaqus分析用户指南第10.7.1节](../usb/usb-link.md#usb-anl-aenrichment)
- ["基于表面的内聚行为，" Abaqus分析用户指南第37.1.10节](../usb/usb-link.md#usb-cni-acohesivebehavior)
- ["UDMGINI，" Abaqus用户子程序参考指南第1.1.26节](../sub/sub-link.md#sub-rtn-uudmgini)

### 将损伤起始定义为材料属性

### **必需参数：**

CRITERION

设置 CRITERION=DUCTILE 以指定基于延性失效应变的损伤起始准则。

设置 CRITERION=FLD 以指定基于成形极限图的损伤起始准则。

设置 CRITERION=FLSD 以指定基于成形极限应力图的损伤起始准则。

设置 CRITERION=HASHIN 以指定基于Hashin分析的损伤起始准则。

设置 CRITERION=HYSTERESIS ENERGY 以指定基于低循环疲劳分析中每个稳定循环消耗的非弹性滞回能的损伤起始准则。

设置 CRITERION=JOHNSON COOK 以指定基于Johnson-Cook失效应变的损伤起始准则。

设置 CRITERION=MAXE 以指定基于内聚单元或富集单元的最大名义应变的损伤起始准则。

设置 CRITERION=MAXS 以指定基于内聚单元或富集单元的最大名义应力准则的损伤起始准则。

设置 CRITERION=MAXPE 以指定基于富集单元的最大主应变的损伤起始准则。

设置 CRITERION=MAXPS 以指定基于富集单元的最大主应力准则的损伤起始准则。

设置 CRITERION=MK 以指定基于Marciniak-Kuczynski分析的损伤起始准则。

设置 CRITERION=MSFLD 以指定基于Mschenborn和Sonne成形极限图的损伤起始准则。

设置 CRITERION=QUADE 以指定基于内聚单元或富集单元的二次分离-相互作用准则的损伤起始。

设置 CRITERION=QUADS 以指定基于内聚单元或富集单元的二次牵引-相互作用准则的损伤起始。

设置 CRITERION=SHEAR 以指定基于剪切失效应变的损伤起始准则。

设置 CRITERION=USER 以指定富集单元的用户定义损伤起始准则。

### **可选参数：**

ALPHA

此参数只能与 CRITERION=HASHIN 结合使用。

将此参数设置为将与Hashin纤维起始准则中剪切贡献相乘的系数值。默认值为 ![](../graphics/key_eqn00549.gif)。

DEFINITION

此参数只能与 CRITERION=MSFLD 结合使用。

设置 DEFINITION=MSFLD（默认）以通过将极限等效塑性应变作为 ![](../graphics/key_eqn00080.gif) 的表格函数来指定MSFLD损伤起始准则。

设置 DEFINITION=FLD 以通过将极限主应变作为次应变的函数来指定MSFLD损伤起始准则。

DEPENDENCIES

将此参数设置为损伤起始属性定义中包含的场变量数量。如果省略此参数，则假定损伤起始属性是常数或仅取决于温度。此参数不能与 CRITERION=JOHNSON COOK 结合使用。

FAILURE MECHANISMS

此参数只能与 CRITERION=USER 结合使用。

将此参数设置为用户定义的损伤起始准则中要指定的失效机制总数。此参数值必须为非零值。

FEQ

此参数只能与 CRITERION=MK 结合使用。

将此参数设置为等效塑性应变变形严重指数的临界值 ![](../graphics/key_eqn00550.gif)。默认值为 ![](../graphics/key_eqn00551.gif)。

如果不应考虑等效塑性应变的变形严重因子来评估Marciniak-Kuczynski准则，则将此参数设置为零。

FNN

此参数只能与 CRITERION=MK 结合使用。

将此参数设置为沟槽方向法线应变变形严重指数的临界值 ![](../graphics/key_eqn00552.gif)。默认值为 ![](../graphics/key_eqn00553.gif)。

如果不应考虑沟槽法线应变变形严重因子来评估Marciniak-Kuczynski准则，则将此参数设置为零。

FNT

此参数只能与 CRITERION=MK 结合使用。

将此参数设置为剪切应变变形严重指数的临界值 ![](../graphics/key_eqn00554.gif)。默认值为 ![](../graphics/key_eqn00555.gif)。

如果不应考虑剪切应变变形严重因子来评估Marciniak-Kuczynski准则，则将此参数设置为零。

FREQUENCY

此参数只能与 CRITERION=MK 结合使用。

将此参数设置为执行Marciniak-Kuczynski分析的频率（以增量为单位）。默认情况下，M-K分析每增量执行一次；即 FREQUENCY=1。

KS

此参数只能与 CRITERION=SHEAR 结合使用。

将此参数设置为 ![](../graphics/key_eqn00556.gif) 的值。默认值为 ![](../graphics/key_eqn00557.gif)。

LODE DEPENDENT

包含此参数以定义依赖于Lode角的延性损伤起始准则。

NORMAL DIRECTION

此参数只能与 Abaqus/Standard 中富集单元的 CRITERION=MAXE、CRITERION=MAXS、CRITERION=QUADE 或 CRITERION=QUADS 结合使用。

设置 NORMAL DIRECTION=1（默认）以指定当损伤起始准则满足时，将引入与单元局部1方向正交的新裂纹。

设置 NORMAL DIRECTION=2 以指定当损伤起始准则满足时，将引入与单元局部2方向正交的新裂纹。

NUMBER IMPERFECTIONS

此参数只能与 CRITERION=MK 结合使用。

将此参数设置为评估Marciniak-Kuczynski分析时要考虑的缺陷数量。这些缺陷假定在角方向上等距分布。默认情况下，使用四个缺陷。

OMEGA

此参数只能与 Abaqus/Explicit 中的 CRITERION=MSFLD 结合使用。

将此参数设置为用于过滤用于评估MSFLD损伤起始准则的主应变率比率的因子 ![](../graphics/key_eqn00018.gif)。默认值为 ![](../graphics/key_eqn00558.gif)。

PEINC

此参数只能与 Abaqus/Explicit 中的 CRITERION=MSFLD 结合使用。

将此参数设置为用于触发MSFLD损伤起始准则评估的等效塑性应变累积增量。默认值为 ![](../graphics/key_eqn00559.gif)（![](../graphics/key_eqn00560.gif)%）。

POSITION

此参数只能与 Abaqus/Standard 中富集单元的 CRITERION=MAXPE、CRITERION=MAXPS、CRITERION=MAXE、CRITERION=MAXS、CRITERION=QUADE、CRITERION=QUADS 或 CRITERION=USER 结合使用。

设置 POSITION=CENTROID（默认）以使用裂纹尖端前方单元质心处的应力/应变来确定损伤起始准则是否满足，并确定裂纹扩展方向（如果需要）。

设置 POSITION=COMBINED 以使用外推到裂纹尖端的应力/应变来确定损伤起始准则是否满足，并使用单元质心处的应力/应变来确定裂纹扩展方向（如果需要）。

设置 POSITION=CRACKTIP 以使用外推到裂纹尖端的应力/应变来确定损伤起始准则是否满足，并确定裂纹扩展方向（如果需要）。

设置 POSITION=NONLOCAL 以使用外推到裂纹尖端的应力/应变来确定损伤起始准则是否满足，并使用富集区域中裂纹尖端周围一组单元平均的应力/应变来确定裂纹扩展方向（如果需要）。此选项只能与 CRITERION=MAXPE 或 CRITERION=MAXPS 结合使用。

PROPERTIES

此参数只能与 CRITERION=USER 结合使用。

将此参数设置为为用户定义的损伤起始准则指定的材料常数数量。参数值必须为非零值。

R CRACK DIRECTION

此参数只能与 POSITION=NONLOCAL 结合使用。

将此参数设置为裂纹尖端周围包含单元的半径，用于计算获取裂纹扩展方向所使用的平均应力/应变。默认值为富集区域中典型单元特征长度的三倍。

TOLERANCE

此参数只能与 Abaqus/Standard 中富集单元的 CRITERION=MAXPE、CRITERION=MAXPS、CRITERION=MAXE、CRITERION=MAXS、CRITERION=QUADE、CRITERION=QUADS 或 CRITERION=USER 结合使用。

将此参数设置为损伤起始准则必须满足的容差。默认值为0.05。

### **指定 CRITERION=DUCTILE 且没有 LODE DEPENDENT 参数的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将损伤起始时的等效塑性应变定义为三轴度、应变率、温度和其他预定义场变量的函数。

### **指定 CRITERION=DUCTILE、LODE DEPENDENT 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此组数据行，以将损伤起始时的等效塑性应变定义为三轴度、Lode角、应变率、温度和其他预定义场变量的函数。

### **指定 CRITERION=FLD 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将损伤起始时的主应变定义为次应变、温度和其他预定义场变量的函数。

### **指定 CRITERION=FLSD 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将损伤起始时的主应力定义为次应力、温度和其他预定义场变量的函数。

### **指定 CRITERION=HASHIN 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于一时需要）：**

根据需要重复此组数据行，以将强度对温度和其他预定义场变量的依赖性定义为函数。

### **指定 CRITERION=HYSTERESIS ENERGY 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将材料常数对温度和其他预定义场变量的依赖性定义为函数。

### **指定 CRITERION=JOHNSON COOK 的损伤起始的数据行：**

**第一行（也是唯一一行）：**

### **指定 CRITERION=MK 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于五时需要）：**

根据需要重复此组数据行，以将槽尺寸定义为角距离、温度和其他预定义场变量的函数。

### **指定 CRITERION=MSFLD、DEFINITION=MSFLD 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将损伤起始时的等效塑性应变定义为 ![](../graphics/key_eqn00080.gif)、等效塑性应变率、温度和其他预定义场变量的函数。

### **指定 CRITERION=MSFLD、DEFINITION=FLD 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将损伤起始时的主应变定义为次应变、等效塑性应变率、温度和其他预定义场变量的函数。

### **指定 CRITERION=QUADE 或 CRITERION=MAXE 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将损伤起始时的最大法向和剪切牵引力定义为温度和其他预定义场变量的函数。

### **指定 CRITERION=QUADS 或 CRITERION=MAXS 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将损伤起始时的最大法向和剪切牵引力定义为温度和其他预定义场变量的函数。

### **指定 CRITERION=MAXPE 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于六时需要）：**

根据需要重复此组数据行，以将损伤起始时的最大主应变定义为温度和其他预定义场变量的函数。

### **指定 CRITERION=MAXPS 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于六时需要）：**

根据需要重复此组数据行，以将损伤起始时的最大主应力定义为温度和其他预定义场变量的函数。

### **指定 CRITERION=SHEAR 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将损伤起始时的等效塑性应变定义为剪切应力比、应变率、温度和其他预定义场变量的函数。

### **指定 CRITERION=USER 的损伤起始的数据行：**

**第一行：**

根据需要重复此数据行，以定义所有材料常数。

### 将损伤起始定义为接触属性模型的一部分

### **必需参数：**

CRITERION

设置 CRITERION=MAXS 以指定基于内聚表面最大名义应力准则的损伤起始准则。

设置 CRITERION=MAXU 以指定基于内聚表面最大分离准则的损伤起始准则。

设置 CRITERION=QUADS 以指定基于内聚表面二次牵引-相互作用准则的损伤起始。

设置 CRITERION=QUADU 以指定基于内聚表面二次分离-相互作用准则的损伤起始。

### **可选参数：**

DEPENDENCIES

将此参数设置为损伤起始属性定义中包含的场变量数量。如果省略此参数，则假定损伤起始属性是常数或仅取决于温度。

### **指定 CRITERION=QUADU 或 CRITERION=MAXU 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将损伤起始时的最大法向和剪切分离定义为温度和其他预定义场变量的函数。

### **指定 CRITERION=QUADS 或 CRITERION=MAXS 的损伤起始的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将损伤起始时的最大法向和剪切牵引力定义为温度和其他预定义场变量的函数。




