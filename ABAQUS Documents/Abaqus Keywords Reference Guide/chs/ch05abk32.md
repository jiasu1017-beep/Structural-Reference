# *EULERIAN MESH MOTION









### *EULERIAN MESH MOTION定义欧拉网格的运动。

此选项允许欧拉网格随指定表面的运动而平移，并扩展和收缩以覆盖表面的范围。

**产品：**Abaqus/Explicit  Abaqus/CAE

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**载荷模块

##### **参考：**

- ["欧拉分析，" Abaqus分析用户指南第14.1.1节](../usb/usb-link.md#usb-anl-aeuleriananalysis)
- ["欧拉网格运动，" Abaqus分析用户指南第14.1.3节](../usb/usb-link.md#usb-anl-aeulerianmeshmotion)

### **必需参数：**

ELSET

将此参数设置为在[*EULERIAN SECTION](ch05abk33.md)定义中给出的单元集名称，以激活网格运动。

### **首次激活网格运动或在使用OP=NEW后重新定义网格运动时的必需参数：**

SURFACE

将此参数设置为用于控制欧拉网格运动的基于节点、基于单元或欧拉材料表面的名称。

### **可选参数：**

ASPECT RATIO MAX

将此参数设置为三个边界框方向（1-2、2-3、3-1）中任何一个允许长宽比的最大变化值。默认值为10.0。

BUFFER

将此参数设置为一个值，以在边界框和表面之间保持缓冲区，等于该值乘以网格中最大欧拉单元尺寸。默认值为BUFFER=2.0。

设置 BUFFER=INITIAL 以保持网格相对于表面的初始缩放比例。

CENTER

设置 CENTER=BOUNDING BOX（默认）以将边界框的中心与表面边界框的中心对齐。

设置 CENTER=MASS 以将边界框的中心与表面的质心对齐。

CONTRACT

设置 CONTRACT=YES（默认）以允许边界框在分析过程中收缩。

设置 CONTRACT=NO 以禁止边界框收缩。

OP

设置 OP=MOD（默认）以修改现有网格运动选项或为给定单元集定义额外的网格运动选项。

设置 OP=NEW 以删除或覆盖给定单元集的现有网格运动定义。

ORIENTATION

将此参数设置为在[*ORIENTATION](ch15abk01.md)选项（["方向，" Abaqus分析用户指南第2.2.5节](../usb/usb-link.md#usb-int-corientation)）上给出的名称，用于定义边界框的局部方向。只能指定使用SYSTEM=RECTANGULAR或SYSTEM=Z RECTANGULAR定义的方向。

VMAX FACTOR

将此参数设置为表面节点最大速度的分数，以限制网格运动速度。默认值为VMAX FACTOR=1.01。

VOLFRAC MIN

将此参数设置为用于确定在欧拉材料表面的边界框计算中包含哪些节点的体积分数下限。默认值为VOLFRAC MIN=0.5。

### **定义边界框约束的可选数据行：**

**第一行：**

**第二行：**

**第三行：**




