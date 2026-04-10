# *BUCKLE





### *BUCKLE获取特征值屈曲估计。

此选项用于控制特征值屈曲估计。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["特征值屈曲预测，" Abaqus Analysis User's Guide第6.2.3节](../usb/usb-link.md#usb-anl-aeigenbuckling)

### **可选参数：**

EIGENSOLVER

使用此参数选择特征值求解器。

设置EIGENSOLVER=SUBSPACE（默认）以调用子空间迭代特征值求解器。

设置EIGENSOLVER=LANCZOS以调用Lanczos特征值求解器。

### **当EIGENSOLVER=SUBSPACE时的特征值屈曲分析数据行：**

**第一行（也是唯一一行）：**

### **当EIGENSOLVER=LANCZOS时的特征值屈曲分析数据行：**

**第一行（也是唯一一行）：**


