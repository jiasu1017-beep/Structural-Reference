# *PRINT







### *PRINT在Abaqus/Standard分析中请求或抑制对消息文件的输出，或在Abaqus/Explicit分析中请求或抑制对状态文件的输出。

此选项用于在Abaqus/Standard分析的消息（`.msg`）文件或Abaqus/Explicit分析的状态（`.sta`）文件中获取或抑制详细打印输出。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**步骤模块

##### **参考：**

- ["输出，" Abaqus Analysis User's Guide第4.1.1节](../usb/usb-link.md#usb-out-ooutput)
- ["输出到输出数据库，" Abaqus Analysis User's Guide第4.1.3节](../usb/usb-link.md#usb-out-odboutput)

### **Abaqus/Standard分析中的可选参数：**

ADAPTIVE MESH

设置ADAPTIVE MESH=YES以在自适应网格平滑期间请求详细输出。默认为ADAPTIVE MESH=NO。

CONTACT

设置CONTACT=YES以请求界面和间隙问题中接触或分离点的详细输出。此输出在困难的接触问题中很有用，可以跟踪增量内迭代期间解的发展。除非FREQUENCY=0，否则将为每个增量打印输出。默认为CONTACT=NO。

FREQUENCY

将此参数设置为输出频率，以增量为单位。除非FREQUENCY=0，否则输出始终在每个步骤的最后一个增量打印。默认为FREQUENCY=1。设置FREQUENCY=0以抑制输出。

MODEL CHANGE

设置MODEL CHANGE=YES以请求在步骤中被移除或重新激活的元素的详细输出。此输出包括在大位移分析中应变自由重新激活的元素的新原始坐标和法线。默认为MODEL CHANGE=NO。

PLASTICITY

设置PLASTICITY=YES以请求材料例程中塑性算法未能收敛的元素和积分点编号的详细输出。此输出有助于确定Abaqus/Standard遇到材料模型困难的网格位置和塑性模型。此信息可能有助于识别建模问题以及材料参数规格问题。默认为PLASTICITY=NO。

RESIDUAL

如果要在平衡迭代期间给出平衡残差的输出，则设置RESIDUAL=YES（默认）。设置RESIDUAL=NO以抑制输出。

SOLVE

设置SOLVE=YES（默认）以请求每次迭代中实际方程数量和内存需求的信息。设置SOLVE=NO以抑制输出。

### **Abaqus/Explicit分析中的可选参数：**

ALLKE

设置ALLKE=YES以请求在状态文件中打印包含总动能的一列。设置ALLKE=NO以抑制此打印输出。默认为ALLKE=YES。

CRITICAL ELEMENT

设置CRITICAL ELEMENT=YES以请求在状态文件中打印包含具有最小稳定时间增量的元素的一列以及打印该值的一列。设置CRITICAL ELEMENT=NO以抑制此打印输出。默认为CRITICAL ELEMENT=YES。

DMASS

设置DMASS=YES以请求在状态文件中打印由于质量缩放导致的模型总质量变化百分比的一列。设置DMASS=NO以抑制此打印输出。默认为DMASS=NO，除非步骤中存在主动质量缩放。从先前步骤传播的[*FIXED MASS SCALING](ch06abk13.md)不被视为主动质量缩放。

ETOTAL

设置ETOTAL=YES以请求在状态文件中打印模型能量平衡的一列。设置ETOTAL=NO以抑制此打印输出。默认为ETOTAL=YES。

其他能量变量也可以被打印。请参阅["输出到输出数据库，" Abaqus Analysis User's Guide第4.1.3节](../usb/usb-link.md#usb-out-odboutput-energy)中的"总能量输出"，了解Abaqus/Explicit中可用的能量变量。

MASS

设置MASS=YES以请求在状态文件中打印包含模型总质量的一列。设置MASS=NO以抑制此打印输出。默认为MASS=NO。

**此选项没有关联的数据行。**
