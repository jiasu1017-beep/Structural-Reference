# *FREQUENCY





### *FREQUENCY提取固有频率和模态向量。

此选项用于执行特征值提取以计算系统的固有频率和相应的振型。

**产品：**Abaqus/Standard   Abaqus/CAE   Abaqus/AMS   

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["固有频率提取，" Abaqus Analysis User's Guide第6.3.5节](../usb/usb-link.md#usb-anl-afreqextraction)

### **可选参数：**

ACOUSTIC COUPLING

对于AMS特征值求解器和Lanczos特征值求解器，设置ACOUSTIC COUPLING=ON以在固有频率提取过程中考虑声-结构耦合效应，模型中使用[*TIE](ch19abk06.md)选项耦合的声学和结构单元，或使用ASI型单元的模型。这是Lanczos特征值求解器的默认选项。

对于基于SIM架构的AMS特征值求解器和Lanczos特征值求解器，设置ACOUSTIC COUPLING=PROJECTION以在固有频率提取过程中提取非耦合的声学和结构模式，并投影声-结构耦合算子，模型中使用[*TIE](ch19abk06.md)选项耦合的声学和结构单元。这是AMS特征值求解器的默认选项。

设置ACOUSTIC COUPLING=OFF以省略声-结构耦合算子的投影，并在固有频率提取过程中忽略声-结构耦合效应，模型中使用[*TIE](ch19abk06.md)选项耦合的声学和结构单元，或使用ASI型单元的模型。

此参数与子空间迭代特征值求解器无关。

DAMPING PROJECTION

此参数仅与AMS特征值求解器或与SIM参数结合使用的Lanczos特征值求解器相关。

设置DAMPING PROJECTION=ON（默认）以在固有频率提取过程中投影粘性和结构阻尼算子。如果模型中没有定义阻尼，则不执行投影。

设置DAMPING PROJECTION=OFF以省略阻尼算子的投影。

EIGENSOLVER

设置EIGENSOLVER=LANCZOS（默认）以调用Lanczos特征值求解器。

设置EIGENSOLVER=AMS以调用自动多级子结构（AMS）特征值求解器。

设置EIGENSOLVER=SUBSPACE以调用子空间迭代特征值求解器。

NORMALIZATION

设置NORMALIZATION=DISPLACEMENT以归一化特征向量，使每个向量中最大的位移、旋转或声压（在耦合声-结构提取中）条目为1。当子空间迭代特征值求解器和Lanczos特征值求解器不使用SIM参数时，位移归一化是默认值。

设置NORMALIZATION=MASS以相对于结构质量矩阵归一化特征向量（特征向量被缩放，使得每个向量的广义质量为1）。质量归一化是AMS特征值求解器的默认且唯一可用的选项。当Lanczos特征值求解器和子空间迭代特征值求解器与SIM参数结合使用时，质量归一化被开启。

PROPERTY EVALUATION

将此参数设置为在特征值提取过程中评估粘弹性、弹簧和阻尼器频率相关属性的频率。如果省略此参数，Abaqus/Standard将在零频率评估与频率相关弹簧和阻尼器相关的刚度，并且不会考虑[*FREQUENCY](ch06abk35.md)步骤中频域粘弹性的刚度贡献。

RESIDUAL MODES

此参数仅与Lanczos和AMS特征值求解器相关。

包含此参数以指示要计算残余模式。

SIM

此参数仅与Lanczos和子空间迭代特征值求解器相关。

包含此参数以指示后续的基于模式的线性动态分析步骤应使用基于SIM软件架构的高性能版本。如果激活了AMS特征值求解器，则默认开启SIM参数。

### **当EIGENSOLVER=AMS时的可选参数：**

NSET

将此参数设置为节点集名称，或包含没有值的参数以允许Abaqus/Standard自动选择要计算特征向量的节点。如果省略此参数，则将在所有节点计算特征向量。

### **当EIGENSOLVER=LANCZOS时，固有频率提取的数据行：**

**第一行（唯一行）：**

### **当EIGENSOLVER=AMS时，固有频率提取的数据行：**

**第一行：**

**如果默认残余模式足够或未请求残余模式，则不需要其他数据行。否则，后续行：**

根据需要重复此行以请求残余模式。

### **当EIGENSOLVER=SUBSPACE时，固有频率提取的数据行：**

**第一行（唯一行）：**
