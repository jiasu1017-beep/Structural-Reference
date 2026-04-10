# *COMPOSITE MODAL DAMPING





### *COMPOSITE MODAL DAMPING为基于SIM架构的模态分析指定复合模态阻尼。

此选项只能与SIM架构结合使用，且只能与[*FREQUENCY](ch06abk35.md)选项结合使用。它指定复合模态阻尼数据，使能够在特征值提取分析期间计算每个提取特征模态的加权质量和刚度复合阻尼。为质量比例临界阻尼分数和指定单元集的刚度比例临界阻尼分数请求阻尼数据。此选项也可用于为质量和刚度矩阵输入分配临界阻尼分数。

**产品：**Abaqus/Standard  

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["材料阻尼"，Abaqus Analysis User's Guide第26.1.1节](../usb/usb-link.md#usb-mat-cdampingopt)
- ["动力学分析过程：概述"，Abaqus Analysis User's Guide第6.3.1节](../usb/usb-link.md#usb-anl-adynamicproc)

### **可选参数：**

MASS MATRIX INPUT

将此参数设置为使用[*MATRIX INPUT](ch13abk13.md)，MATRIX=MASS选项包含在模型中的所有质量矩阵的临界阻尼分数值。如果省略此参数，默认值为零。

STIFFNESS MATRIX INPUT

将此参数设置为使用[*MATRIX INPUT](ch13abk13.md)，MATRIX=STIFFNESS选项包含在模型中的所有刚度矩阵的临界阻尼分数值。如果省略此参数，默认值为零。

### **定义临界阻尼分数的数据行：**

**第一行：**

根据需要重复此数据行，以定义不同单元和/或单元集的模态阻尼。




