# *EULERIAN BOUNDARY









### *EULERIAN BOUNDARY定义欧拉网格边界处的流入和流出条件。

此选项用于指定欧拉网格边界处的流入和流出条件。

**产品：**Abaqus/Explicit  Abaqus/CAE

**类型：**历史数据

**级别：**步骤

**Abaqus/CAE：**载荷模块

##### **参考：**

- ["定义欧拉边界，" Abaqus分析用户指南第14.1.2节](../usb/usb-link.md#usb-anl-aeulerianboundary)

### **可选参数：**

INFLOW

如果欧拉材料可以自由流入欧拉域，则设置 INFLOW=FREE（默认）。

如果欧拉材料和空隙都不能流入欧拉域，则设置 INFLOW=NONE。

如果只有空隙可以流入欧拉域，则设置 INFLOW=VOID。

OP

设置 OP=MOD（默认）以修改现有流入/流出条件或定义额外的流入/流出条件。

设置 OP=NEW 以删除所有现有的流入/流出条件。

OUTFLOW

此参数用于定义无界域问题中的边界条件。

如果欧拉材料可以自由流出欧拉域，则设置 OUTFLOW=FREE（如果 INFLOW=VOID，则为默认）。

设置 OUTFLOW=NONREFLECTING 以指定非反射辐射边界条件。

设置 OUTFLOW=NONUNIFORM PRESSURE 以指定边界处的平衡条件。

设置 OUTFLOW=ZERO PRESSURE（默认）以指定边界处的零压力。

### **定义应用欧拉边界条件的表面的数据行：**

**第一行：**

根据需要重复此数据行，以定义不同表面的流入/流出条件。




