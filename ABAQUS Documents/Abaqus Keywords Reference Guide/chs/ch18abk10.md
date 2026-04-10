# *SFLOW





### *SFLOW定义垂直于表面的渗流系数和相关环境孔隙压力。

此选项用于提供渗流系数和环境孔隙压力，以控制在固结分析中垂直于表面的孔隙流体流动。

**产品：**Abaqus/Standard

**类型：**历史数据

**级别：**步

##### **参考：**

- ["Pore fluid flow," Section 34.4.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pporousflow)
- ["FLOW," Section 1.1.7 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-uflow)

### **可选参数：**

AMPLITUDE

将此参数设置为给出参考孔隙压力随时间变化的幅值曲线名称。如果省略此参数，则参考幅值将在步开始时立即应用或线性跨越步应用，具体取决于[*STEP](ch18abk36.md)选项上AMPLITUDE参数分配的值（参见["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)）。对于在用户子程序[`FLOW`](../sub/sub-link.md#sub-xsl-flow)中定义的非均匀渗流边界条件和仅排水的渗流边界条件，AMPLITUDE参数被忽略。

OP

设置OP=MOD（默认）以修改现有流动或定义附加流动。

如果应删除应用于模型的所有现有[*SFLOW](ch18abk09.md)s，则设置OP=NEW。可以定义新的流动。

### **定义均匀渗流的数据行：**

**第一行：**

根据需要重复此数据行以定义各种表面的均匀渗流。

### **定义仅排水渗流的数据行：**

**第一行：**

根据需要重复此数据行以定义各种表面的仅排水渗流。

### **定义非均匀渗流的数据行：**

**第一行：**

对于非均匀流动，参考孔隙压力值 ![](../graphics/key_eqn00712.gif) 和参考渗流系数 ![](../graphics/key_eqn00556.gif) 在用户子程序[`FLOW`](../sub/sub-link.md#sub-xsl-flow)中定义。

根据需要重复此数据行以定义各种表面的非均匀渗流。




