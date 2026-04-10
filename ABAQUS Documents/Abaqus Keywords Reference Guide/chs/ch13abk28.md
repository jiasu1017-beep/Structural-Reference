# *MPC









### *MPC定义多点约束。

此选项用于在模型的不同自由度之间施加约束。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例、装配  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["广义多点约束，" Abaqus Analysis User's Guide第35.2.2节](../usb/usb-link.md#usb-cni-pmpc)
- ["MPC，" Abaqus User Subroutines Reference Guide第1.1.14节](../sub/sub-link.md#sub-rtn-umpc)

### **可选参数：**

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。如果省略此参数，则假定数据在关键字行之后。

MODE

此参数仅适用于Abaqus/Standard分析。

此参数仅在包含USER参数时使用。

设置MODE=DOF（默认）以使用户子程序[`MPC`](../sub/sub-link.md#sub-xsl-mpc)在自由度模式下运行。

设置MODE=NODE以使用户子程序[`MPC`](../sub/sub-link.md#sub-xsl-mpc)在节点模式下运行。

USER

此参数仅适用于Abaqus/Standard分析。

包含此参数以指示约束在用户子程序[`MPC`](../sub/sub-link.md#sub-xsl-mpc)中定义。

### **定义多点约束的数据行：**

**第一行：**

MPC的前15个节点或节点集必须输入在第一行。如果MPC包含超过15个节点，则在下一行输入0以指示这是继续行，然后在此行继续输入以下节点。允许任意数量的继续行。除最后一行外，每行必须恰好给出15个节点或节点集。