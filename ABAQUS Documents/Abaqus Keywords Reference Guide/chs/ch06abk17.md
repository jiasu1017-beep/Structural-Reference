# *FLUID BOUNDARY





### *FLUID BOUNDARY指定流体流动分析的边界条件。

此选项用于指定流体流动分析的边界条件。边界条件可以指定为空间变化的或恒定的，并带有相关的时间变化。

**产品：**Abaqus/CFD   Abaqus/CAE   

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**载荷模块

##### **参考：**

- ["不可压缩流体动力学分析，" Abaqus Analysis User's Guide第6.6.2节](../usb/usb-link.md#usb-anl-aifluiddyn)
- ["Abaqus/CFD中的边界条件，" Abaqus Analysis User's Guide第34.3.2节](../usb/usb-link.md#usb-prc-pboundarycfd)
- [*CFD](ch03abk13.md)

### **必需参数：**

TYPE

设置TYPE=ELEMENT以在单元面上指定分布式边界值。

设置TYPE=NODE以在节点上指定分布式边界值。

设置TYPE=PHYSICAL以基于物理类型指定边界值。

设置TYPE=SURFACE以在表面上指定边界值。

### **与TYPE=PHYSICAL一起使用的必需互斥参数：**

PRESSUREOUTLET

包含此参数以指定压力出口边界条件。

SYMMETRY

包含此参数以指定对称边界条件。

VELOCITYINLET

包含此参数以指定速度入口边界条件。

WALL

包含此参数以指定壁面边界条件。

### **如果TYPE=PHYSICAL，则为必需参数：**

SURFACE

将此参数设置为要在其上施加边界条件的表面名称。

### **可选参数：**

AMPLITUDE

将此参数设置为幅值曲线的名称，该曲线定义步骤中边界条件幅值的变化（["幅值曲线，" Abaqus Analysis User's Guide第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)）。

如果省略此参数，则在步骤开始时立即应用参考幅值。当TYPE=PHYSICAL时，此参数不能使用。

DISTRIBUTION

将此参数设置为与PVDEP边界类型一起使用的分布标签（["分布定义，" Abaqus Analysis User's Guide第2.8.1节](../usb/usb-link.md#usb-int-adefiningdistributions)）。如果边界类型不是PVDEP，则忽略此参数。当TYPE=PHYSICAL时，此参数不能使用。

OP

对于现有[*FLUID BOUNDARY](ch06abk17.md)s保持不变，将OP=MOD（默认）设置为此选项修改现有边界条件或定义额外边界条件。

如果应该删除应用于模型的所有现有[*FLUID BOUNDARY](ch06abk17.md)s，则设置OP=NEW。可以定义新边界条件。

SLIP

仅当包含WALL参数时才能使用此参数。设置SLIP=NO（默认）以指示无滑移壁面边界条件。设置SLIP=YES以指示滑移壁面边界条件。

### **TYPE=ELEMENT的数据行：**

**第一行：**

根据需要重复此数据行，以在不同单元和自由度上指定固定边界条件。

### **TYPE=NODE的数据行：**

**第一行：**

根据需要重复此数据行，以在不同节点和自由度上指定固定边界条件。

### **如果包含WALL和SLIP=NO参数，则TYPE=PHYSICAL的数据行：**

**第一行（唯一行）：**

### **如果包含WALL和SLIP=YES参数，则TYPE=PHYSICAL的数据行：**

**第一行：**

根据需要重复此数据行，以在滑移壁面上指定边界条件。

### **如果包含PRESSUREOUTLET参数，则TYPE=PHYSICAL的数据行：**

**第一行：**

根据需要重复此数据行，以在压力出口处指定边界条件。

### **如果包含VELOCITYINLET参数，则TYPE=PHYSICAL的数据行：**

**第一行：**

根据需要重复此数据行，以在速度入口处指定边界条件。

### **TYPE=SURFACE的数据行：**

**第一行：**

根据需要重复此数据行，以在不同表面和自由度上指定边界条件。

### **如果指定了SYMMETRY参数，则没有数据行。**
