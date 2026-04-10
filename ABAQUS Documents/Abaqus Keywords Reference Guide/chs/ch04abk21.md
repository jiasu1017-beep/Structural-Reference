# *DIAGNOSTICS





### *DIAGNOSTICS控制诊断消息。

此选项用于请求详细的诊断输出或取消特定的诊断检查。默认情况下，如果在分析期间检测到问题，将输出诊断检查的简短摘要。在Abaqus/Explicit中，诊断消息被写入状态（`.sta`）文件或消息（`.msg`）文件。在Abaqus/Standard中，诊断消息被写入数据（`.dat`）文件。

对于多步骤分析，所有参数值在分析期间保持不变，直到在下一次步骤开始时明确重新定义。

**产品：**Abaqus/Standard  Abaqus/Explicit  

**类型：**Abaqus/Standard中的模型数据；Abaqus/Explicit中的历史数据  

**级别：**Abaqus/Standard中的模型；Abaqus/Explicit中的步骤  

##### **参考：**

- ["显式动态分析，" Abaqus分析用户指南第6.3.3节](../usb/usb-link.md#usb-anl-aexpdynamic)
- ["Abaqus/Explicit中ALE自适应网格划分的输出和诊断，" Abaqus分析用户指南第12.2.5节](../usb/usb-link.md#usb-anl-aaleoutput)
- ["Abaqus/Explicit分析中的接触诊断，" Abaqus分析用户指南第39.2.1节](../usb/usb-link.md#usb-cni-aexpcontactdiagnostics)
- ["线性弹性行为，" Abaqus分析用户指南第22.2.1节](../usb/usb-link.md#usb-mat-clinearelastic)
- ["类橡胶材料的超弹性行为，" Abaqus分析用户指南第22.5.1节](../usb/usb-link.md#usb-mat-chyperelastic)
- [*CONTACT CONTROLS](ch03abk57.md)

### 在Abaqus/Explicit分析中定义诊断

### **可选参数：**

ADAPTIVE MESH

自适应网格信息被写入问题中每个自适应网格域的消息（`.msg`）文件。

设置 ADAPTIVE MESH=STEP SUMMARY（默认）以在步骤结束时获得摘要。摘要给出了每个自适应网格增量中的平均平流扫描次数以及步骤期间移动节点的平均、最大和最小百分比。

设置 ADAPTIVE MESH=SUMMARY 以获得每个自适应网格增量的摘要。摘要给出了网格扫描次数、这些网格扫描期间移动节点的平均百分比以及自适应网格增量期间执行的平流扫描次数。除此信息外，还将在每个步骤结束时写入 STEP SUMMARY 信息。

设置 ADAPTIVE MESH=DETAIL 以获取有关每个自适应网格增量的详细信息。详细报告给出了执行的网格扫描次数；这些网格扫描期间移动节点的最小、平均和最大百分比；执行的平流扫描次数；平流前后的质量和动量；以及自适应网格增量期间的体积变化百分比。除此信息外，还将在每个步骤结束时写入 STEP SUMMARY 信息。

设置 ADAPTIVE MESH=OFF 以抑制所有关于自适应网格划分的诊断消息。

CONTACT INITIAL OVERCLOSURE

设置 CONTACT INITIAL OVERCLOSURE=DETAIL（默认）以将解决初始过闭合所需的所有初始位移写入消息（`.msg`）文件，并将每个接触对的最大初始过闭合摘要写入状态（`.sta`）文件。

设置 CONTACT INITIAL OVERCLOSURE=SUMMARY 以仅在状态（`.sta`）文件中获取每个接触对的最大初始过闭合摘要。

CRITICAL ELEMENTS

将此参数设置为要写入输出数据库诊断信息的关键单元（具有最小稳定时间增量的单元）的数量。默认值为10。

CUTOFF RATIO

将此参数设置为变形速度与波速度的截止比率（默认值为1.0）。如果计算的最大比率大于此值，分析将以错误消息结束。截止检查不适用于具有状态方程材料或用户定义材料的模型。

DEEP PENETRATION FACTOR

将此参数设置为通用接触域中典型单元面尺寸的分数，用于检测过度深的穿透（默认值为0.5）。如果在节点-面接触中，节点穿透其跟踪面的深度超过通用接触域中典型单元面尺寸乘以深度穿透因子，将发出诊断消息。深度穿透检查不适用于接触对算法检测到的接触穿透。

DEFORMATION SPEED CHECK

设置 DEFORMATION SPEED CHECK=SUMMARY（默认）仅为模型中变形速度与波速度比率最大的单元打印消息。此信息输出到状态（`.sta`）文件。

设置 DEFORMATION SPEED CHECK=DETAIL 为所有具有相对较大变形速度的单元打印消息。此信息输出到消息（`.msg`）文件。

设置 DEFORMATION SPEED CHECK=OFF 以抑制变形速度检查。

DETECT CROSSED SURFACES

此参数仅适用于一般接触。

设置 DETECT CROSSED SURFACES=ON（默认）以为初始配置中相邻从属节点位于主表面相对两侧的情况发出警告消息。

设置 DETECT CROSSED SURFACES=OFF 以抑制此诊断。

PLASTICITY

设置 PLASTICITY=SUMMARY（默认）以获取塑性算法未收敛的材料点总数的摘要。此信息仅在状态（`.sta`）文件中首次出现时打印。

设置 PLASTICITY=DETAIL 以获取有关塑性算法未收敛的单元的详细信息。此信息将在消息（`.msg`）文件中打印。此请求可能导致分析运行时间更长。目前仅适用于Mises塑性。

设置 PLASTICITY=OFF 以抑制所有关于塑性算法的诊断消息。

WARNING RATIO

将此参数设置为变形速度与波速度的警告比率（默认比率为0.3）。如果在一个单元中计算的比率大于此值，将向状态（`.sta`）文件或消息（`.msg`）文件打印警告消息。

WARPED SURFACE

设置 WARPED SURFACE=SUMMARY（默认）以在表面首次被认为包含至少一个高度翘曲小平面时在状态（`.sta`）文件中获取警告消息。

设置 WARPED SURFACE=DETAIL 以将详细警告消息也输出到消息（`.msg`）文件。

设置 WARPED SURFACE=OFF 以抑制所有关于翘曲表面的警告。

**此选项没有关联的数据行。**

### 在Abaqus/Standard分析中定义诊断

### **可选参数：**

NONHYBRID INCOMPRESSIBLE

如果模型具有近乎不可压缩的弹性或超弹性材料，其有效初始泊松比大于0.495（即，初始体积模量与初始剪切模量的比率大于100），用于非混合连续单元（平面应力单元除外），则在预处理期间将错误消息写入数据（`.dat`）文件。

设置 NONHYBRID INCOMPRESSIBLE=WARNING 以将错误消息替换为相应的警告消息。

**此选项没有关联的数据行。**




