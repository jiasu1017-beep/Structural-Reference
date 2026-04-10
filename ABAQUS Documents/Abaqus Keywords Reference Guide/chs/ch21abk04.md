# *VISCOELASTIC





### *VISCOELASTIC指定与弹性一起使用的耗散行为。

此选项用于将材料的弹性响应推广以包括粘弹性。粘弹性可以定义为稳态小振动分析中频率的函数、时间相关分析中缩减时间的函数，或通过为非线性粘弹性分析指定蠕变定律来定义。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["并行流变框架," Section 22.8.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cnonlinvisco)
- ["时域粘弹性," Section 22.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ctimevisco)
- ["频域粘弹性," Section 22.7.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfreqvisco)
- ["UCREEPNETWORK," Section 1.1.23 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uucreepnetwork)
- [*COMBINED TEST DATA](ch03abk25.md)
- [*SHEAR TEST DATA](ch18abk13.md)
- [*TRS](ch19abk16.md)
- [*VOLUMETRIC TEST DATA](ch21abk08.md)

### **必需的互斥参数：**

FREQUENCY

此参数仅适用于Abaqus/Standard分析。

使用此参数选择频域定义。在这种情况下，材料的长期弹性必须使用[*ELASTIC](ch05abk03.md)或[*HYPERELASTIC](ch08abk06.md)选项定义。

设置FREQUENCY=CREEP TEST DATA以使用Prony系列松弛模量表示定义频域响应（如果Prony系列参数要从剪切和体积蠕变试验数据计算）。

设置FREQUENCY=FORMULA以通过幂律公式定义耗散材料参数。

设置FREQUENCY=PRONY以通过指定Prony系列参数使用Prony系列松弛模量表示定义频域响应。

设置FREQUENCY=RELAXATION TEST DATA以使用Prony系列松弛模量表示定义频域响应（如果Prony系列参数要从剪切和体积松弛试验数据计算）。

设置FREQUENCY=TABULAR以提供频域响应的表格定义。

NONLINEAR

包含此参数以在并行流变框架内定义非线性粘弹性网络。

TIME

使用此参数选择时域定义。在这种情况下，材料的弹性必须使用[*ELASTIC](ch05abk03.md)、[*HYPERELASTIC](ch08abk06.md)或[*HYPERFOAM](ch08abk07.md)选项定义。

如果Prony系列参数将由Abaqus从剪切和体积蠕变试验数据计算，则设置TIME=CREEP TEST DATA。

如果Prony系列参数将由Abaqus从频率相关循环试验数据计算，则设置TIME=FREQUENCY DATA。

设置TIME=PRONY通过给出Prony系列松弛模量表示的参数来定义线性、各向同性粘弹性材料。

如果Prony系列参数将由Abaqus从剪切和体积松弛试验数据计算，则设置TIME=RELAXATION TEST DATA。

### **包含NONLINEAR参数时的必需参数：**

LAW

设置LAW=BERGSTROM-BOYCE以选择Bergstrom-Boyce定律。

设置LAW=HYPERB以选择双曲正弦定律。

设置LAW=POWER LAW以选择幂律模型。

设置LAW=STRAIN以选择应变硬化幂律。

设置LAW=USER以使用用户子程序[`UCREEPNETWORK`](../sub/sub-link.md#sub-xsl-ucreepnetwork)输入蠕变定律。此值仅适用于Abaqus/Standard分析。

NETWORKID

将此参数设置为主网络ID。此数字必须大于或等于1且小于或等于网络数。网络ID必须由连续整数组成。

SRATIO

将此参数设置为网络的刚度比。网络的刚度比之和必须小于或等于1。如果和小于1，则将定义具有刚度比值的额外弹性网络以满足条件。

### **可选参数：**

DEPENDENCIES

此参数仅适用于Abaqus/Standard分析，并且只能与NONLINEAR参数一起使用时才相关。

将此参数设置为除了温度之外蠕变常数定义中包含的场变量依赖项数。如果省略此参数，则假定蠕变常数没有依赖性或仅取决于温度。请参见["材料数据定义," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

PRELOAD

此参数仅适用于Abaqus/Standard分析。

此参数只能与FREQUENCY=TABULAR一起使用，以指定用于定义频域粘弹性材料属性或有效厚度方向垫圈属性的预加载性质。

设置PRELOAD=UNIAXIAL以指定频域粘弹性材料属性对应于单轴试验。

设置PRELOAD=VOLUMETRIC以指定频域粘弹性材料属性对应于体积试验。当与垫圈元素一起使用以定义有效厚度方向属性时，此设置没有意义。

PROPERTIES

此参数仅适用于Abaqus/Standard分析，并且只能与LAW=USER一起使用时才相关。

将此参数设置为在用户子程序[`UCREEPNETWORK`](../sub/sub-link.md#sub-xsl-ucreepnetwork)中所需的数据属性值数量。默认值为PROPERTIES=0。

TYPE

此参数不能与NONLINEAR参数一起使用。

使用此参数定义[*VISCOELASTIC](ch21abk04.md)选项是否用于定义连续体材料属性或有效厚度方向垫圈属性。

设置TYPE=ISOTROPIC（默认，且是Abaqus/Explicit的唯一选项）以定义连续体材料属性。当粘弹性材料模型用于任何其材料响应使用连续体材料属性建模的连续体、结构或专用单元时，此选择是合适的（此类专用单元的示例包括使用连续体响应建模内聚单元——参见["使用连续体方法定义有限厚度粘附层" in "定义使用连续体方法的内聚单元的构成响应," Section 32.5.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesivematbehavior-continuum)，或使用材料响应的垫圈单元——参见["使用材料模型定义垫圈行为," Section 32.6.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-egasketmatbehavior)）。在Abaqus/Explicit中，此参数也应与具有弹性牵引-分离行为的内聚单元的粘弹性属性定义一起使用（["在Abaqus/Explicit中定义率相关牵引-分离行为" in "定义使用牵引-分离描述的内聚单元的构成响应," Section 32.5.6 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-ecohesivebehavior-timevisco)）。

设置TYPE=TRACTION以定义有效厚度方向垫圈属性。此选项仅支持其行为直接使用垫圈行为模型建模的垫圈单元（["使用材料模型定义垫圈行为," Section 32.6.5 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-egasketmatbehavior)）。

### **当给出试验数据以使用TIME=CREEP TEST DATA、TIME=RELAXATION TEST DATA或TIME=FREQUENCY DATA定义时域粘弹性，或当给出试验数据以使用FREQUENCY=CREEP TEST DATA或FREQUENCY=RELAXATION TEST DATA定义频域粘弹性时的可选参数：**

ERRTOL

将此参数设置为最小二乘拟合中数据点的允许平均均方根误差。默认值为0.01（1%）。

NMAX

将此参数设置为Prony系列中的最大项数*N*。Abaqus将从![](../graphics/key_eqn01156.gif)到![](../graphics/key_eqn01157.gif)执行最小二乘拟合，直到就ERRTOL而言对于最低*N*实现收敛。默认值和最大值为13。

### **对于FREQUENCY=FORMULA定义连续体材料属性的数据行：**

**第一行（也是唯一行）：**

### **对于FREQUENCY=TABULAR（无PRELOAD参数）或TIME=FREQUENCY DATA定义连续体材料属性的数据行：**

**第一行：**

根据需要重复此数据行，以定义材料行为的耗散部分。

### **对于FREQUENCY=TABULAR、PRELOAD=UNIAXIAL定义连续体材料属性的数据行：**

**第一行：**

根据需要重复此数据行，以将单轴损耗和存储模量定义为频率和预加载的函数。

### **对于FREQUENCY=TABULAR、PRELOAD=VOLUMETRIC定义连续体材料属性的数据行：**

**第一行：**

根据需要重复此数据行，以将体积损耗和存储模量定义为频率和预加载的函数。

### **使用TIME=PRONY或FREQUENCY=PRONY直接使用Prony系列参数指定连续体材料属性的数据行：**

**第一行：**

根据需要重复此数据行，以定义Prony系列中的第二、第三等项。Prony系列中的项数没有限制。

### **使用TIME=PRONY为具有弹性牵引-分离行为的内聚单元定义粘弹性属性的数据行：**

**第一行：**

根据需要重复此数据行，以定义Prony系列中的第二、第三等项。Prony系列中的项数没有限制。

### **使用TIME=FREQUENCY DATA为具有弹性牵引-分离行为的内聚单元定义粘弹性属性的数据行：**

**第一行：**

根据需要重复此数据行，以定义材料行为的耗散部分。

### **通过试验数据指定粘弹性行为：**

当指定了TIME=CREEP TEST DATA或TIME=RELAXATION TEST DATA时，此选项不使用数据行。试验数据由[*SHEAR TEST DATA](ch18abk13.md)和[*VOLUMETRIC TEST DATA](ch21abk08.md)选项或[*COMBINED TEST DATA](ch03abk25.md)选项给出。

### **对于PRELOAD=UNIAXIAL定义有效厚度方向垫圈属性的数据行：**

**第一行：**

根据需要重复此数据行，以将有效厚度方向垫圈损耗和存储模量定义为频率和预加载的函数。

### **如果未包含PRELOAD=UNIAXIAL，则定义有效厚度方向垫圈属性的数据行：**

**第一行：**

根据需要重复此数据行，以将归一化有效厚度方向垫圈损耗和存储模量定义为频率的函数。

### **对于LAW=BERGSTROM-BOYCE的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将蠕变常数定义为温度和其他预定义场变量的函数。

### **对于LAW=HYPERB的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以将蠕变常数定义为预定义场变量的函数。

### **对于LAW=POWER LAW的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将蠕变常数定义为温度和其他预定义场变量的函数。

### **对于LAW=STRAIN的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将蠕变常数定义为温度和其他预定义场变量的函数。

### **对于LAW=USER的数据行：**

**如果PROPERTIES参数被省略或设置为0，则不需要数据行。否则，第一行：**

根据需要重复此数据行，以定义材料属性。





