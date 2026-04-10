# *RADIATION VIEW FACTOR







### *RADIATION VIEW FACTOR控制腔体辐射和视角因子计算。

此选项用于控制在腔体辐射分析期间视角因子的计算。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["腔体辐射，" Abaqus Analysis User's Guide第41.1.1节](../usb/usb-link.md#usb-cni-acavityradiation)

### **可选参数：**

BLOCKING

设置BLOCKING=ALL（默认）以指定在视角因子计算中执行完整的遮挡检查。

设置BLOCKING=NO以指定在视角因子计算中不执行遮挡检查。

设置BLOCKING=PARTIAL以指定在视角因子计算中执行部分遮挡检查。然后使用数据行指定潜在的遮挡表面。

CAVITY

将此参数设置为正在为其指定辐射视角因子控制的腔体名称。如果省略此参数，则规范适用于模型中定义的所有腔体。

INFINITESIMAL

将此参数设置为小平面面积比，高于此值时将在视角因子计算中使用无穷小到有限面积的近似。默认值为64.0。

INTEGRATION

将此参数设置为在使用轮廓积分数值积分进行视角因子计算时沿每条边使用的Gauss积分点数量。允许一到五个积分点。默认值为三个积分点。

LUMPED AREA

将此参数设置为无量纲距离平方值，高于此值时将在视角因子计算中使用集总面积近似。默认值为5.0。

OFF

包含此参数以关闭腔体辐射效应。可以通过随后使用此选项（不带OFF参数）再次打开腔体辐射效应。如果省略此参数，腔体辐射处于活动状态。

RANGE

将此参数设置为一个距离，超过该距离时不需要计算视角因子，因为表面被认为相距太远而无法"看到"彼此（由于被其他表面遮挡）。

REFLECTION

设置REFLECTION=YES（默认）以指示必须在腔体辐射计算中包含反射。

设置REFLECTION=NO以指示在腔体辐射计算中忽略反射。无反射对应于*黑体*辐射的特殊情况（参见["腔体辐射，" Abaqus Theory Guide第2.11.4节](../stm/stm-link.md#stm-anl-cavradiation)）。

SYMMETRY

包含此参数以指示模型中辐射对称性的存在。此参数必须设置为出现在[*RADIATION SYMMETRY](ch17abk05.md)选项中定义对称性的名称。如果省略此参数，则假定腔体中没有辐射对称性。

VTOL

将此参数设置为视角因子计算的可接受容差。如果省略此参数，则默认视角因子容差为0.05。

### **（与[*MOTION](ch13abk29.md)选项结合使用的可选参数）：**

MDISP

将此参数设置为在重新计算辐射视角因子之前，监控节点集中任何节点的最大允许位移。此参数仅在[*MOTION](ch13abk29.md)选项与[*RADIATION VIEW FACTOR](ch17abk06.md)选项一起出现时相关。此参数必须与NSET参数一起使用。

NSET

将此参数设置为节点集名称，该节点集的位移将被监控，以决定几何变化在步骤期间是否足够显著以触发辐射视角因子的重新计算。此参数仅在[*MOTION](ch13abk29.md)选项与[*RADIATION VIEW FACTOR](ch17abk06.md)选项一起出现时相关。此参数必须与MDISP参数一起使用。

### **定义遮挡表面的数据行（BLOCKING=PARTIAL）：**

**第一行：**

根据需要重复此数据行以定义部分遮挡。

### **如果未指定BLOCKING=PARTIAL，则此选项没有关联的数据行。**
