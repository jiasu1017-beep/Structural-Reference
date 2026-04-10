# *DFLUX





### *DFLUX 在热传递、计算流体动力学或质量扩散分析中指定分布热通量。

此选项用于在全耦合热应力分析中施加分布热通量。在Abaqus/Standard中，它还用于热传递、耦合热电和质量扩散分析。在Abaqus/CFD中，此选项用于指定分布体积热源。

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

对于Abaqus/Standard分析中的均匀热通流类型，如果省略此参数，则参考值将在步骤开始时立即应用或线性地跨越步骤应用，具体取决于分配给 [*STEP](ch18abk36.md) 选项上 AMPLITUDE 参数的值（["定义分析，" Abaqus分析用户指南第6.1.2节](../usb/usb-link.md#usb-anl-aover)）。如果省略此参数，在Abaqus/Explicit或Abaqus/CFD分析中，参考值将在步骤开始时立即应用。

对于类型 BFNU 和 S*n*NU 的非均匀热通流（仅在Abaqus/Standard中可用），热通流大小在用户子程序 [`DFLUX`](../sub/sub-link.md#sub-xsl-dflux) 中定义，AMPLITUDE引用将被忽略。

OP

设置 OP=MOD（默认）以保留现有的 [*DFLUX](ch04abk20.md)s，此选项修改现有热通流或定义额外热通流。

如果应该移除模型上所有现有的 [*DFLUX](ch04abk20.md)s，设置 OP=NEW。

### **定义分布热通流的数据行：**

**第一行：**

根据需要重复此数据行，以定义不同单元表面的分布热通流。




