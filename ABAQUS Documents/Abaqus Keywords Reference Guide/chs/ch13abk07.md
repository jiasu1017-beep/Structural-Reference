# *MASS FLOW RATE









### *MASS FLOW RATE在热传递分析中指定流体质量流量。

此选项用于在热传递分析中为强制对流/扩散单元指定单位面积的质量流量（或对于一维单元指定通过整个截面的流量）。此选项不能与静水流体单元一起使用。

**产品：**Abaqus/Standard  

**类型：**历史数据  

**级别：**步骤

##### **参考：**

- ["非耦合热传递分析，" Abaqus Analysis User's Guide第6.5.2节](../usb/usb-link.md#usb-anl-aheattransfer)
- ["UMASFL，" Abaqus User Subroutines Reference Guide第1.1.40节](../sub/sub-link.md#sub-rtn-uumasfl)

### **可选参数：**

AMPLITUDE

将此参数设置为幅值与时间曲线，该曲线定义步骤期间流量的大小。如果省略此参数，则根据[*STEP](ch18abk36.md)选项上AMPLITUDE参数分配的值，在步骤开始时立即应用参考幅度或在线性地跨越步骤。

INPUT

将此参数设置为包含此选项数据行的备用输入文件名称。如果省略此参数，则假定数据在关键字行之后。

OP

设置OP=MOD（默认）以保持现有的[*MASS FLOW RATE](ch13abk07.md)值，此选项修改现有流量或定义额外流量。

如果应删除应用于模型的所有现有[*MASS FLOW RATE](ch13abk07.md)值，则设置OP=NEW。

USER

包含此参数以指示将使用用户子程序[`UMASFL`](../sub/sub-link.md#sub-xsl-umasfl)来定义质量流量值。将在数据行上给出的每个节点调用[`UMASFL`](../sub/sub-link.md#sub-xsl-umasfl)。如果数据行上也给出了值，这些值将被忽略。

### **定义质量流量的数据行：**

**第一行：**

根据需要重复此数据行以定义不同节点处的质量流量。

### **使用用户子程序[`UMASFL`](../sub/sub-link.md#sub-xsl-umasfl)定义质量流量的数据行：**

**第一行：**

根据需要重复此数据行。将在每个列出的节点调用[`UMASFL`](../sub/sub-link.md#sub-xsl-umasfl)。