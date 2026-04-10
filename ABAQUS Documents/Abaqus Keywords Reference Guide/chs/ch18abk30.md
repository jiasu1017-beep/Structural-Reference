# *SRADIATE





### *SRADIATE在传热分析中指定表面辐射条件。

此选项用于在完全耦合热应力分析中在非凹表面和非反射环境之间施加表面辐射边界条件，或定义近似腔体辐射相互作用。在Abaqus/Standard中，它还用于传热、耦合热电和耦合热电结构分析。

它必须与[*PHYSICAL CONSTANTS](ch16abk09.md)选项配合使用，后者用于定义Stefan-Boltzmann常数。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CFD  Abaqus/CAE

**类型：**历史数据

**级别：**步

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["Thermal loads," Section 34.4.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-prc-pthermal)
- ["Cavity radiation," Section 41.1.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-acavityradiation)

### **可选参数：**

AMPLITUDE

将此参数设置为给出环境温度随时间变化的[*AMPLITUDE](ch01abk09.md)选项名称。

如果在Abaqus/Standard分析中省略此参数，则参考幅值将在步开始时立即应用或线性跨越步应用，具体取决于[*STEP](ch18abk36.md)选项上AMPLITUDE参数分配的值（参见["Defining an analysis," Section 6.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-anl-aover)）。如果在Abaqus/Explicit分析中省略此参数，则参考幅值将在步开始时立即应用。

OP

设置OP=MOD（默认）以保留现有[*SRADIATE](ch18abk30.md)定义，此选项修改现有辐射条件或定义附加辐射条件。

如果应删除应用于模型的所有现有[*SRADIATE](ch18abk30.md)定义，则设置OP=NEW。

### **定义表面辐射条件的数据行：**

**第一行：**

根据需要重复此数据行以定义不同表面的辐射条件。

### **定义近似腔体辐射的数据行（仅在Abaqus/Standard中可用）：**

**第一行：**

根据需要重复此数据行以定义不同表面的辐射条件。




