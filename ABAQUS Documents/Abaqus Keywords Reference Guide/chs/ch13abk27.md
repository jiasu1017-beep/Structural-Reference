# *MOMENTUM EQUATION SOLVER









### *MOMENTUM EQUATION SOLVER指定Abaqus/CFD分析中求解动量方程的线性求解器和参数。

此选项只能作为[*CFD](ch03abk13.md)选项的子选项使用，以启用求解动量方程的线性求解器参数。对于稳态分析，此选项还用于启用非线性动量求解器的欠松弛参数。

**产品：**Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["不可压缩流体动力学分析，" Abaqus Analysis User's Guide第6.6.2节](../usb/usb-link.md#usb-anl-aifluiddyn)
- [*CFD](ch03abk13.md)

### **可选参数：**

CONVERGENCE

设置CONVERGENCE=ON以在日志文件中写入收敛信息。

设置CONVERGENCE=OFF（默认）以抑制收敛信息。

DIAGNOSTICS

设置DIAGNOSTICS=ON以在日志文件中写入关于求解器的诊断信息。

设置DIAGNOSTICS=OFF（默认）以抑制诊断信息。

TYPE

设置TYPE=DSFGMRES（默认）以启用对角缩放灵活广义最小残差线性求解器。

设置TYPE=DSGMRES以启用对角缩放广义最小残差线性求解器。

设置TYPE=ILUFGMRES以启用不完全LU分解预处理的灵活广义最小残差线性求解器。

### **TYPE=DSFGMRES、TYPE=DSGMRES和TYPE=ILUFGMRES的数据行：**

**第一行（也是唯一一行）：**