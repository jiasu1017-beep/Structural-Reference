# *DSFLUX





### *DSFLUX指定热传递分析的分布表面热通量。

此选项用于为Abaqus/Standard和Abaqus/Explicit中的全耦合热应力分析施加分布表面热通量。在Abaqus/Standard中，它还用于热传递、耦合热电和耦合热电结构分析。在Abaqus/CFD中，它用于热能（热量）传递和共轭热传递分析。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE  

**类型：**历史数据 

**级别：**步骤

**Abaqus/CAE：**载荷模块

##### **参考：**

- ["热载荷，" Abaqus分析用户指南第34.4.4节](../usb/usb-link.md#usb-prc-pthermal)
- ["DFLUX，" Abaqus用户子程序参考指南第1.1.3节](../sub/sub-link.md#sub-rtn-udflux)

### **可选参数：**

AMPLITUDE

将此参数设置为振幅曲线的名称，该曲线定义步骤期间分布热通量的大小（["振幅曲线，" Abaqus分析用户指南第34.1.2节](../usb/usb-link.md#usb-prc-pamplitude)）。

对于Abaqus/Standard中的均匀热通量类型，如果省略此参数，则参考值将在步骤开始时立即应用或线性地跨越步骤应用，具体取决于分配给 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数的值（["定义分析，" Abaqus分析用户指南第6.1.2节](../usb/usb-link.md#usb-anl-aover)）。如果在Abaqus/Explicit或Abaqus/CFD分析中省略此参数，则参考值将在步骤开始时立即应用。

对于非均匀热通量类型 SNU（仅在Abaqus/Standard中可用），热通量大小在用户子程序 [`DFLUX`](../sub/sub-link.md#sub-xsl-dflux) 中定义，AMPLITUDE引用将被忽略。

OP

设置 OP=MOD（默认）以保留现有的 [*DSFLUX](ch04abk41.md)s，此选项修改现有热通量或定义额外热通量。

如果应该移除模型上所有现有的 [*DSFLUX](ch04abk41.md)s，设置 OP=NEW。

### **定义分布表面热通量的数据行：**

**第一行：**

根据需要重复此数据行，以定义不同表面的分布热通量。




