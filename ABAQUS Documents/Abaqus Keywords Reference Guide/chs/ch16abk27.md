# *PRESSURE PENETRATION







### *PRESSURE PENETRATION使用基于表面的接触指定压力渗透载荷。

此选项用于指定使用基于表面的接触模拟的压力渗透加载。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**历史数据  

**级别：**步骤  

**Abaqus/CAE：**相互作用模块

##### **参考：**

- ["压力渗透加载，" Abaqus Analysis User's Guide第37.1.7节](../usb/usb-link.md#usb-cni-apressurepenetration)

### **必需参数：**

MASTER

将此参数设置为压力渗透分析中使用的接触对的主表面名称。

SLAVE

将此参数设置为压力渗透分析中使用的接触对的从表面名称。

### **可选参数：**

AMPLITUDE

将此参数设置为在步骤期间定义流体压力变化的幅值曲线名称。如果省略此参数，则根据[*STEP](ch18abk36.md)选项上AMPLITUDE参数的值（参见["定义分析，" Abaqus Analysis User's Guide第6.1.2节](../usb/usb-link.md#usb-anl-aover)），参考幅值将在步骤开始时立即应用或在线性 ramping up。

OP

设置OP=MOD（默认）以保留现有的压力渗透载荷，此选项可修改现有压力渗透载荷或定义额外的压力渗透载荷。

如果应移除应用于模型的所有现有压力渗透载荷，则设置OP=NEW。可以定义新的压力渗透载荷。

PENETRATION TIME

将此参数设置为流体压力在新渗透的接触面段上 ramping up到当前幅值的时间周期。默认渗透时间周期选择为当前步骤时间的0.001。在线性扰动分析中，此参数将被忽略，在这种情况下，一旦满足压力渗透准则，将立即应用当前流体压力。

### **矩阵生成和稳态动力学分析（直接或模态）的可选、互斥参数：**

IMAGINARY

包含此参数以定义载荷的虚部（异相）部分。

REAL

包含此参数（默认）以定义载荷的实部（同相）部分。

### **定义压力渗透载荷的数据行：**

**第一行：**

根据需要重复此数据行，以定义来自表面上不同位置的流体渗透，可能具有不同的流体压力幅值。或者，可以重复[*PRESSURE PENETRATION](ch16abk27.md)选项（例如，如果需要不同的幅值参考）。
