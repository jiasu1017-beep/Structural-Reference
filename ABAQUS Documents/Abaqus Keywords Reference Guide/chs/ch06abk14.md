# *FLOW





### *FLOW定义渗流系数和相关的渗流孔隙压力。

此选项用于提供渗流系数和渗流孔隙压力，以控制在固结分析中垂直于表面的孔隙流体流动。

**产品：**Abaqus/Standard   Abaqus/Explicit   Abaqus/CAE   

**类型：**历史数据  

**级别：**步骤  

##### **参考：**

- ["孔隙流体流动，" Abaqus Analysis User's Guide第34.4.7节](../usb/usb-link.md#usb-prc-pporousflow)
- ["FLOW，" Abaqus User Subroutines Reference Guide第1.1.7节](../sub/sub-link.md#sub-rtn-uflow)

### **可选参数：**

AMPLITUDE

将此参数设置为幅值曲线的名称，该曲线给出参考孔隙压力随时间的变化。如果省略此参数，则根据[*STEP](ch18abk36.md)选项上AMPLITUDE参数的值（参见["定义分析，" Abaqus Analysis User's Guide第6.1.2节](../usb/usb-link.md#usb-anl-aover)），参考幅值在步骤开始时立即应用或在步骤中线性应用。对于在用户子程序[`FLOW`](../sub/sub-link.md#sub-xsl-flow)中定义的非均匀渗流边界条件和仅排水的渗流边界条件，AMPLITUDE参数将被忽略。

OP

对于现有[*FLOW](ch06abk14.md)s保持不变，将OP=MOD（默认）设置为此选项修改现有流动或定义额外流动。

如果应该删除应用于模型的所有现有[*FLOW](ch06abk14.md)s，则设置OP=NEW。可以定义新流动。

### **定义均匀渗流的数据行：**

**第一行：**

根据需要重复此数据行，以定义各种单元或单元集的均匀渗流。

### **定义仅排水渗流的数据行：**

**第一行：**

根据需要重复此数据行，以定义各种单元或单元集的仅排水渗流。

### **定义非均匀渗流的数据行：**

**第一行：**

参考孔隙压力值，![](../graphics/key_eqn00712.gif)，和参考渗流系数，![](../graphics/key_eqn00556.gif)，在用户子程序[`FLOW`](../sub/sub-link.md#sub-xsl-flow)中为非均匀流动定义。

根据需要重复此数据行，以定义各种单元或单元派的非均匀渗流。

