# *FRACTURE CRITERION





### *FRACTURE CRITERION指定裂纹扩展准则。

此选项用于指定沿初始部分粘结表面的裂纹扩展准则。在Abaqus/Standard中，它必须紧跟在[*DEBOND](ch04abk09.md)选项之后；在Abaqus/Explicit中，它必须紧跟在[*COHESIVE BEHAVIOR](ch03abk23.md)选项之后。此选项也可在Abaqus/Standard中用于为内嵌单元中的裂纹扩展指定基于线性弹性断裂力学的准则。在这种情况下，它必须紧跟在[*SURFACE BEHAVIOR](ch18abk48.md)选项之后。

**产品：**Abaqus/Standard   Abaqus/Explicit   Abaqus/CAE   

**类型：**Abaqus/Standard中的模型或历史数据；Abaqus/Explicit中的模型数据  

**级别：**Abaqus/Standard中的模型或步骤；Abaqus/Explicit中的模型  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["裂纹扩展分析，" Abaqus Analysis User's Guide第11.4.3节](../usb/usb-link.md#usb-anl-acrackpropagation)
- ["使用扩展有限元方法将不连续性建模为内嵌特征，" Abaqus Analysis User's Guide第10.7.1节](../usb/usb-link.md#usb-anl-aenrichment)
- [*DEBOND](ch04abk09.md)
- [*COHESIVE BEHAVIOR](ch03abk23.md)
- [*SURFACE BEHAVIOR](ch18abk48.md)

### **必需参数：**

DISTANCE

仅当使用TYPE=COD或TYPE=CRITICAL STRESS时，才需要此参数。

如果TYPE=CRITICAL STRESS，则将此参数设置为裂纹尖端前方潜在裂纹表面上评估临界应力准则的距离。

如果TYPE=COD，则将此参数设置为从裂纹尖端沿从表面测量的裂纹张开位移的距离。

NSET

仅当TYPE=CRACK LENGTH时，才需要此参数。将此参数设置为包含用于定义参考点的节点的节点集名称。

TYPE

设置TYPE=CRITICAL STRESS以使用裂纹尖端前方距离处的临界应力准则作为裂纹扩展准则。此设置仅在Abaqus/Standard中可用。

设置TYPE=COD以使用裂纹尖端后方距离处的裂纹张开位移临界值作为裂纹扩展准则。此设置仅在Abaqus/Standard中可用。

设置TYPE=CRACK LENGTH以将裂纹长度指定为时间的函数。此设置仅在Abaqus/Standard中可用。

设置TYPE=ENHANCED VCCT以使用增强型VCCT（虚拟裂纹闭合技术）准则，其中可以通过两个不同的临界断裂能量释放率来控制裂纹的萌生和扩展。此设置仅在Abaqus/Standard中可用。

设置TYPE=FATIGUE以指示裂纹萌生和疲劳裂纹扩展由基于Paris定律的裂纹尖端相对断裂能量释放率表征。此设置仅在Abaqus/Standard中可用。

设置TYPE=VCCT以使用VCCT（虚拟裂纹闭合技术）准则作为裂纹扩展准则。VCCT准则使用线性弹性断裂力学原理。

### **可选参数：**

DEPENDENCIES

此参数与TYPE=CRACK LENGTH无关。

将此参数设置为数据行中包含的场变量依赖项数。如果省略此参数，则假定数据为常数或仅取决于温度。有关详细信息，请参见["指定场变量依赖"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

MIXED MODE BEHAVIOR

此参数仅与TYPE=ENHANCED VCCT、TYPE=FATIGUE或TYPE=VCCT相关。

设置MIXED MODE BEHAVIOR=BK以通过Benzeggagh-Kenane混合模式断裂准则将断裂能量指定为模式混合的函数。

设置MIXED MODE BEHAVIOR=POWER以通过幂律混合模式断裂准则将断裂能量指定为模式混合的函数。

设置MIXED MODE BEHAVIOR=REEDER以通过REEDER混合模式断裂准则将断裂能量指定为模式混合的函数。

默认为MIXED MODE BEHAVIOR=BK。

NODAL ENERGY RATE

此参数仅与TYPE=FATIGUE或TYPE=VCCT相关。

包含此参数以指示不应从数据行读取临界能量释放率，而应从使用[*NODAL ENERGY RATE](ch14abk07.md)选项在节点处指定的临界能量释放率进行插值。指数仍从数据行读取。

NORMAL DIRECTION

此参数只能与Abaqus/Standard中内嵌单元的TYPE=ENHANCED VCCT、TYPE=FATIGUE或TYPE=VCCT结合使用。

设置NORMAL DIRECTION=MTS（默认）以指定当断裂准则满足时，裂纹将沿最大切应力方向正交扩展。

设置NORMAL DIRECTION=1以指定当断裂准则满足时，裂纹将沿单元局部1方向正交扩展。

设置NORMAL DIRECTION=2以指定当断裂准则满足时，裂纹将沿单元局部2方向正交扩展。

SYMMETRY

包含此参数以将从表面与对称平面之间的张开与指定COD值的一半进行比较。当用户使用对称条件对问题进行建模时，SYMMETRY参数仅与TYPE=COD相关。在这种情况下，必须在[*INITIAL CONDITIONS](ch09abk18.md)选项上指定NORMAL参数。

UNSTABLE GROWTH TOLERANCE

将此参数设置为在VCCT准则满足的不稳定裂纹问题中，允许裂纹尖端处和前方多个节点在一步中无需减小增量大小即可脱粘时，不稳定裂纹扩展准则必须满足的容差。

如果包含此参数但未指定值，则默认值为无穷大。

此参数仅在与Abaqus/Standard中的[*DEBOND](ch04abk09.md)选项一起使用时才有意义。

TOLERANCE

将此参数设置为裂纹扩展准则必须满足的容差。默认为TOLERANCE=0.1，适用于TYPE=CRITICAL STRESS、TYPE=COD和TYPE=CRACK LENGTH；对于TYPE=ENHANCED VCCT和TYPE=VCCT，默认为TOLERANCE=0.2。

VISCOSITY

此参数仅适用于Abaqus/Standard分析，且只能与TYPE=ENHANCED VCCT或TYPE=VCCT结合使用。

将此参数设置为粘性正则化中使用的粘性系数值。默认值为0.0。

### **定义临界应力准则的数据行（TYPE=CRITICAL STRESS）：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将临界应力准则定义为温度和/或场变量的函数。

### **定义裂纹张开位移准则的数据行（TYPE=COD）：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于五时才需要）：**

根据需要重复此组数据行，以将裂纹张开位移准则定义为温度和/或场变量的函数。

### **定义裂纹长度与时间准则的数据行（TYPE=CRACK LENGTH）：**

**第一行：**

根据需要重复此数据行，以将裂纹长度定义为时间的函数。

### **对于MIXED MODE BEHAVIOR=BK或REEDER，定义增强型VCCT准则的裂纹萌生和扩展的数据行（TYPE=ENHANCED VCCT）：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值非零时才需要）：**

根据需要重复此组数据行，以将临界能量率和指数定义为温度和场变量的函数。

### **对于MIXED MODE BEHAVIOR=POWER，定义增强型VCCT准则的裂纹萌生和扩展的数据行（TYPE=ENHANCED VCCT）：**

**第一行：**

**第二行：**

**后续行（仅当DEPENDENCIES参数的值大于六时才需要）：**

根据需要重复此组数据行，以将临界能量率和指数定义为温度和场变量的函数。

### **对于MIXED MODE BEHAVIOR=BK或REEDER，定义低周疲劳萌生和裂纹扩展准则的数据行（TYPE=FATIGUE）：**

**第一行：**

**第二行：**

**后续行（仅当DEPENDENCIES参数的值大于五时才需要）：**

根据需要重复此组数据行，以将Paris定律中使用的常数、临界能量率和指数定义为温度和场变量的函数。

### **对于MIXED MODE BEHAVIOR=POWER，定义低周疲劳萌生和裂纹扩展准则的数据行（TYPE=FATIGUE）：**

**第一行：**

**第二行：**

**后续行（仅当DEPENDENCIES参数的值大于三时才需要）：**

根据需要重复此组数据行，以将Paris定律中使用的常数、临界能量率和指数定义为温度和场变量的函数。

### **对于MIXED MODE BEHAVIOR=BK或REEDER，定义VCCT准则的数据行（TYPE=VCCT）：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于三时才需要）：**

根据需要重复此组数据行，以将临界能量率和指数定义为温度和场变量的函数。

### **对于MIXED MODE BEHAVIOR=POWER，定义VCCT准则的数据行（TYPE=VCCT）：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于一时才需要）：**

根据需要重复此组数据行，以将临界能量率和指数定义为温度和场变量的函数。
