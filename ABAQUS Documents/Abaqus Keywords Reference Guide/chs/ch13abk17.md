# *MODAL DAMPING









### *MODAL DAMPING指定模态动力学分析的阻尼。

此选项用于为基于模式的程序指定阻尼。它通常与[*SELECT EIGENMODES](ch18abk07.md)选项结合使用，以选择模态叠加的特征模式。如果未使用[*SELECT EIGENMODES](ch18abk07.md)选项，则所有在先前[*FREQUENCY](ch06abk35.md)步骤中提取的特征模式都将使用[*MODAL DAMPING](ch13abk17.md)选项下指定的阻尼值。如果未使用[*MODAL DAMPING](ch13abk17.md)选项，则假定阻尼值为零。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["材料阻尼，" Abaqus Analysis User's Guide第26.1.1节](../usb/usb-link.md#usb-mat-cdampingopt)
- ["动力学分析程序概述，" Abaqus Analysis User's Guide第6.3.1节](../usb/usb-link.md#usb-anl-adynamicproc)

### **可选的互斥参数（如果未指定参数，Abaqus假定模态阻尼系数在数据行上提供）：**

MODAL

此参数已被VISCOUS参数取代。建议使用VISCOUS参数。

设置MODAL=DIRECT以选择使用此选项中给出的阻尼系数的模态阻尼。关键字行后的数据行指定要用于分析的模态阻尼值。

设置MODAL=COMPOSITE以选择使用在[*FREQUENCY](ch06abk35.md)步骤中计算的阻尼系数的复合模态阻尼。这些系数根据用于传统架构程序的[*DAMPING](ch04abk06.md)材料定义选项中给出的材料阻尼因子计算，以及用于使用Lanczos特征求解器的基于SIM的分析的[*COMPOSITE MODAL DAMPING](ch03abk27.md)选项提供的复合模态阻尼因子计算。复合模态阻尼只能与DEFINITION=MODE NUMBERS一起使用。

RAYLEIGH

此参数已被VISCOUS参数取代。建议使用VISCOUS=RAYLEIGH选择Rayleigh阻尼。

包含此参数以选择Rayleigh阻尼。特定模式的阻尼项定义为，其中和是选项第一数据行上定义的因子，是模式的模态质量，是模式的模态刚度。

STRUCTURAL

包含此参数以选择结构阻尼，这意味着阻尼与内力成正比但方向与速度相反。此参数只能与[*STEADY STATE DYNAMICS](ch18abk34.md)、[*RANDOM RESPONSE](ch17abk07.md)或基于SIM的[*MODAL DYNAMIC](ch13abk18.md)或[*COMPLEX FREQUENCY](ch03abk26.md)程序一起使用。乘以内力的阻尼常数的值在数据行上输入。

VISCOUS

此参数取代了MODAL和RAYLEIGH参数。建议使用此参数。

设置VISCOUS=FRACTION OF CRITICAL DAMPING以选择使用此选项中给出的阻尼系数的模态阻尼。关键字行后的数据行指定要用于分析的模态阻尼值。

设置VISCOUS=COMPOSITE以选择使用在[*FREQUENCY](ch06abk35.md)步骤中计算的阻尼系数的复合模态阻尼。这些系数根据用于传统架构程序的[*DAMPING](ch04abk06.md)材料定义选项中给出的材料阻尼因子计算，以及用于使用Lanczos特征求解器的基于SIM的分析的[*COMPOSITE MODAL DAMPING](ch03abk27.md)选项提供的复合模态阻尼因子计算。复合模态阻尼只能与DEFINITION=MODE NUMBERS一起使用。

设置VISCOUS=RAYLEIGH以指示特定模式的阻尼定义为，其中和是选项第一数据行上定义的因子，是模式的模态质量，是模式的模态刚度。

### **可选参数：**

DEFINITION

设置DEFINITION=MODE NUMBERS（默认）以指示阻尼值针对指定模式号给出。

设置DEFINITION=FREQUENCY RANGE以指示阻尼值针对指定频率范围给出。频率范围可以是不连续的。

如果在同一步骤中同时使用了[*MODAL DAMPING](ch13abk17.md)和[*SELECT EIGENMODES](ch18abk07.md)选项，则DEFINITION参数必须在两个选项中设置为相同的值。

FIELD

设置FIELD=ALL（默认）以指示阻尼值将应用于结构和声学模式。

设置FIELD=MECHANICAL以指示阻尼值仅应用于结构模式。

设置FIELD=ACOUSTIC以指示阻尼值仅应用于声学模式。

此选项只能与VISCOUS=FRACTION OF CRITICAL DAMPING或MODAL=DIRECT和DEFINITION=FREQUENCY RANGE一起用于通过AMS特征提取获得的非耦合结构和声学模式。

### **通过指定模式号定义临界阻尼比例的数据行（如果未指定参数或如果VISCOUS=FRACTION OF CRITICAL DAMPING或MODAL=DIRECT和DEFINITION=MODE NUMBERS）：**

**第一行：**

根据需要重复此数据行以定义不同模式的模态阻尼。

### **通过指定模式号定义Rayleigh阻尼的数据行（VISCOUS=RAYLEIGH或RAYLEIGH和DEFINITION=MODE NUMBERS）：**

**第一行：**

根据需要重复此数据行以定义不同模式的模态阻尼。

### **定义复合模态阻尼的数据行（VISCOUS=COMPOSITE或MODAL=COMPOSITE）：**

**第一行：**

根据需要重复此数据行以定义不同模式的模态阻尼。

### **通过指定模式号定义结构阻尼的数据行（STRUCTURAL和DEFINITION=MODE NUMBERS）：**

**第一行：**

根据需要重复此数据行以定义不同模式的模态阻尼。

### **通过指定频率范围定义临界阻尼比例的数据行（VISCOUS=FRACTION OF CRITICAL DAMPING或MODAL=DIRECT和DEFINITION=FREQUENCY RANGE）：**

**第一行：**

根据需要重复此数据行以定义不同频率的模态阻尼。Abaqus将在频率之间进行线性插值，并在频率范围外保持阻尼值恒定等于最接近的指定值。

### **通过指定频率范围定义Rayleigh阻尼的数据行（VISCOUS=RAYLEIGH或RAYLEIGH和DEFINITION=FREQUENCY RANGE）：**

**第一行：**

根据需要重复此数据行以定义不同频率的模态阻尼。Abaqus将在频率之间进行线性插值，并在频率范围外保持阻尼值恒定等于最接近的指定值。

### **通过指定频率范围定义结构阻尼的数据行（STRUCTURAL和DEFINITION=FREQUENCY RANGE）：**

**第一行：**

根据需要重复此数据行以定义不同频率的模态阻尼。Abaqus将在频率之间进行线性插值，并在频率范围外保持阻尼值恒定等于最接近的指定值。