# *ENERGY EQUATION SOLVER









### *ENERGY EQUATION SOLVER指定用于在Abaqus/CFD分析中求解传导方程的线性求解器和参数。

此选项用于启用Abaqus/CFD中求解传导方程的线性求解器参数。它必须与[*CFD](ch03abk13.md)或[*HEAT TRANSFER](ch08abk03.md)选项结合使用。

**产品：**Abaqus/CFD

**类型：**历史数据

**级别：**步骤

##### **参考：**

- ["不可压缩流体动力学分析，" Abaqus分析用户指南第6.6.2节](../usb/usb-link.md#usb-anl-aifluiddyn)
- ["非耦合传热分析，" Abaqus分析用户指南第6.5.2节](../usb/usb-link.md#usb-anl-aheattransfer)
- [*CFD](ch03abk13.md)
- [*HEAT TRANSFER](ch08abk03.md)

### **可选参数：**

CONVERGENCE

设置 CONVERGENCE=ON 以将收敛信息写入日志文件。

设置 CONVERGENCE=OFF（默认）以抑制收敛信息。

DIAGNOSTICS

设置 DIAGNOSTICS=ON 以将关于求解器的诊断信息写入日志文件。

设置 DIAGNOSTICS=OFF（默认）以抑制诊断信息。

TYPE

设置 TYPE=DSCG 以启用对角缩放共轭梯度线性求解器。

设置 TYPE=SSORCG 以启用对称逐次超松弛共轭梯度线性求解器。

设置 TYPE=DSGMRES 以启用对角缩放广义最小残差线性求解器。

设置 TYPE=DSFGMRES 以启用对角缩放灵活广义最小残差线性求解器。

设置 TYPE=AMG 以启用代数多重网格线性求解器。

如果选择以节点为中心的求解器，默认值为 TYPE=DSCG；如果选择以单元为中心的求解器，默认值为 TYPE=DSFGMRES。

### **TYPE=DSCG和TYPE=SSORCG的数据行：**

**第一行（也是唯一一行）：**

### **TYPE=DSGMRES和TYPE=DSFGMRES的数据行：**

**第一行（也是唯一一行）：**

### **TYPE=AMG的数据行：**

**第一行：**

**第二行：**

**第三行：**




