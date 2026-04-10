# *FLUID CAVITY





### *FLUID CAVITY定义流体腔。

此选项用于定义基于表面的流体腔。

**产品：**Abaqus/Standard   Abaqus/Explicit   Abaqus/CAE   

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["流体腔定义，" Abaqus Analysis User's Guide第11.5.2节](../usb/usb-link.md#usb-anl-afluidcavities)

### **必需参数：**

NAME

将此参数设置为用于引用流体腔的标签。

REF NODE

将此参数设置为流体腔参考节点的节点编号或包含流体腔参考节点的节点集名称。如果选择节点集名称，则该节点集必须恰好包含一个节点。

### **必需的互斥参数：**

BEHAVIOR

将此参数设置为定义流体行为的[*FLUID BEHAVIOR](ch06abk16.md)选项的名称。

MIXTURE

此参数仅适用于Abaqus/Explicit分析。

如果流体腔中的流体是理想气体的混合物，则设置MIXTURE=MASS FRACTION（默认）以使用质量分数。

如果流体腔中的流体是理想气体的混合物，则设置MIXTURE=MOLAR FRACTION以使用摩尔分数。

### **可选参数：**

ADDED VOLUME

将此参数设置为流体额外体积的大小。额外体积将被添加到计算出的腔的实际体积中。

ADIABATIC

此参数仅适用于Abaqus/Explicit分析。

此参数仅在使用理想气体模型时相关。如果假定理想气体具有绝热行为，则包含此参数。

AMBIENT PRESSURE

将此参数设置为环境压力的大小。对于气动流体，环境压力通常为大气压力。

AMBIENT TEMPERATURE

此参数仅适用于Abaqus/Explicit分析，并且仅在为具有绝热行为的气动流体定义热能流动时相关。

将此参数设置为环境温度的大小。环境温度通常为大气温度。

CHECK NORMALS

此参数仅在表面被定义为形成流体腔边界时相关。

设置CHECK NORMALS=YES（默认）以检查表面法线的一致性。

设置CHECK NORMALS=NO以跳过表面法线的一致性检查。

MINIMUM VOLUME

此参数仅适用于Abaqus/Explicit分析。

使用此参数定义流体腔的最小体积。如果腔的体积（等于实际体积加上额外体积）降至最小值以下，则将使用最小值来评估状态方程模型。

将此参数设置为正值以直接定义最小体积。

设置MINIMUM VOLUME=INITIAL VOLUME以将最小体积设置为腔的初始体积。如果流体腔的初始体积为负值，则最小体积将被设置为零。

SURFACE

将此参数设置为形成流体腔边界的表面名称。如果省略ADDED VOLUME参数，则需要此参数。

### **如果包含BEHAVIOR参数，则数据行：**

**第一行（唯一行）：**

### **如果包含MIXTURE参数，则数据行：**

**第一行：**

**第二行：**

根据需要重复此数据行，以定义初始气体混合物。
