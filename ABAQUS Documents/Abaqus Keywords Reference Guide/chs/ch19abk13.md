# *TRANSPORT EQUATION SOLVER





### *TRANSPORT EQUATION SOLVER为Abaqus/CFD分析中求解传输方程指定线性求解器和参数。

此选项只能作为[*CFD](ch03abk13.md)选项的子选项使用，以启用线性求解器参数来求解标量变量（如温度、物种浓度、湍流动能耗散率、湍流动能等）的传输方程。对于稳态分析，此选项还用于启用标量变量传输的欠松弛参数。

**产品：**Abaqus/CFD  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Step模块

##### **参考：**

- ["不可压缩流体动力学分析," Section 6.6.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aifluiddyn)
- [*CFD](ch03abk13.md)

### **可选参数：**

CONVERGENCE

设置CONVERGENCE=ON以将收敛信息写入日志文件。

设置CONVERGENCE=OFF（默认）以抑制收敛信息。

DIAGNOSTICS

设置DIAGNOSTICS=ON以将关于求解器的诊断信息写入日志文件。

设置DIAGNOSTICS=OFF（默认）以抑制诊断信息。

TYPE

设置TYPE=DSFGMRES（默认）以启用对角缩放灵活广义最小残差线性求解器。

设置TYPE=DSGMRES以启用对角缩放广义最小残差线性求解器。

设置TYPE=ILUFGMRES以启用不完全LU分解预条件灵活广义最小残差线性求解器。

### **TYPE=DSFGMRES、TYPE=DSGMRES和TYPE=ILUFGMRES的数据行：**

**第一行（也是唯一行）：**





