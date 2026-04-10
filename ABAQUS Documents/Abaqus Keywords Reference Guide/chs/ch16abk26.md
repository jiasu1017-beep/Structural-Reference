# *PRESSURE EQUATION SOLVER







### *PRESSURE EQUATION SOLVER指定用于求解不可压缩流动压力方程的线性求解器和参数。

此选项只能作为[*CFD](ch03abk13.md)选项的子选项使用，以启用不可压缩流动压力方程的线性求解器参数。对于稳态分析，此选项还用于启用压力校正方程的欠松弛参数。

**产品：**Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["不可压缩流体动力学分析，" Abaqus Analysis User's Guide第6.6.2节](../usb/usb-link.md#usb-anl-aifluiddyn)
- [*CFD](ch03abk13.md)

### **可选参数：**

CONVERGENCE

设置CONVERGENCE=ON以将收敛信息写入日志文件。

设置CONVERGENCE=OFF（默认）以抑制收敛信息。

DIAGNOSTICS

设置DIAGNOSTICS=ON以将关于求解器的诊断信息写入日志文件。

设置DIAGNOSTICS=OFF（默认）以抑制诊断信息。

TYPE

设置TYPE=AMG（默认）以启用代数多重网格线性求解器。

设置TYPE=DSCG以启用对角缩放共轭梯度线性求解器。

设置TYPE=SSORCG以启用对称逐次超松弛共轭梯度线性求解器。

### **TYPE=AMG的数据行：**

**第一行：**

**第二行：**

**第三行：**

### **TYPE=DSCG和TYPE=SSORCG的数据行：**

**第一行（也是唯一一行）：**
