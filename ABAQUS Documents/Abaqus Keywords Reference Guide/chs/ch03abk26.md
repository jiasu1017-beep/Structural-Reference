# *COMPLEX FREQUENCY





### *COMPLEX FREQUENCY提取复特征值和模态向量。

此选项用于执行特征值提取，以计算系统的复特征值和相应的复振型。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**Step模块

##### **参考：**

- ["复特征值提取"，Abaqus Analysis User's Guide第6.3.6节](../usb/usb-link.md#usb-anl-acomplexfreqextract)

### **可选参数：**

FRICTION DAMPING

设置FRICTION DAMPING=NO（默认值）以忽略摩擦引起的阻尼效应。

设置FRICTION DAMPING=YES以包含摩擦引起的阻尼效应。

NORMALIZATION

设置NORMALIZATION=DISPLACEMENT（SIM基础分析的默认值），以归一化复特征向量，使每个向量中最大值的实部为1，虚部为0。

设置NORMALIZATION=MODAL（非SIM架构分析的唯一选项），仅归一化投影系统的复特征向量。

PROPERTY EVALUATION

将此参数设置为在复特征值提取过程中评估粘弹性、弹簧和阻尼器频率相关属性的频率。如果省略此参数，Abaqus/Standard将在零频率下评估与频率相关弹簧和阻尼器相关的材料属性，并且在[*COMPLEX FREQUENCY](ch03abk26.md)步骤中不考虑频域粘弹性的贡献。

UNSTABLE MODES ONLY

将此参数设置为复模态的截止值。只有特征值实部高于截止值的复模态才会写入输出数据库（.odb）文件。此参数的默认值为0.0。如果省略此参数，则输出所有复模态。

### **可选的互斥参数：**

LEFT EIGENVECTORS

包含此参数以请求左复特征向量。此参数仅与基于SIM架构的分析相关。

RIGHT EIGENVECTORS

包含此参数（默认值）以请求右复特征向量。

### **复特征值提取的数据行：**

**第一行（也是唯一一行）：**




