# *CONTACT PERMEABILITY






### *CONTACT PERMEABILITY指定流体渗透性接触属性。

此选项用于修改表面相互作用模型中的孔隙流体渗透性。必须与 [*SURFACE INTERACTION](ch18abk50.md) 选项结合使用。如果省略此选项，则表面相互作用模型将在接触活跃时以及对于高达默认容差距离的间隙具有对流体流过接触界面的无阻力（对应于无限渗透性）。

**产品：**Abaqus/Standard  

**类型：**模型数据  

**级别：**模型

##### **参考：**

- ["孔隙流体接触属性，" Abaqus 分析用户指南第 37.4.1 节](../usb/usb-link.md#usb-cni-aporefluidinteraction)
- ["耦合孔隙流体扩散和应力分析，" Abaqus 分析用户指南第 6.8.1 节](../usb/usb-link.md#usb-anl-acoupdiffstress)
- [*SURFACE INTERACTION](ch18abk50.md)
- [*SOILS](ch18abk21.md)

### **可选参数：**

CUTOFF FLOW ACROSS

将此参数设置为一个截止间隙距离，超过该距离时不会有流体流过接触界面。

CUTOFF GAP FILL

将此参数设置为一个截止间隙距离，超过该距离时由于间隙距离的变化，不会有流体流入或流出接触界面。

DEPENDENCIES

将此参数设置为接触渗透性 ![](../graphics/key_eqn00372.gif) 所依赖的场变量数。

### **用于直接定义接触渗透性 ![](../graphics/key_eqn00372.gif) 的数据行：**

**第一行：**

根据需要重复此数据行，以定义接触渗透性对接触压力、平均表面孔隙压力、平均表面温度以及表面上任何预定义场变量的平均值的依赖性。




