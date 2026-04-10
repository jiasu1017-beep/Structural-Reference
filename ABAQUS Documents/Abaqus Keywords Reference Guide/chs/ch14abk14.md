# *NONSTRUCTURAL MASS









### *NONSTRUCTURAL MASS指定来自非结构特征的模型质量贡献。

此选项用于在模型中包含来自非结构特征的质量贡献。非结构质量可以应用于包含实体、壳、膜、表面、梁或桁架单元的单元集。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**部件、部件实例、装配  

**Abaqus/CAE：**属性模块和相互作用模块

##### **参考：**

- ["非结构质量定义，" Abaqus Analysis User's Guide第2.7.1节](../usb/usb-link.md#usb-int-anonstructuralmass)

### **必需参数：**

ELSET

将此参数设置为包含要分布给定非结构质量的单元的单元集名称。

UNITS

设置UNITS=TOTAL MASS以"质量"单位指定非结构质量。

设置UNITS=MASS PER VOLUME以"单位体积质量"单位指定非结构质量。

设置UNITS=MASS PER AREA以"单位面积质量"单位指定非结构质量。此值仅对包含常规壳、膜和/或表面单元的单元集有效。

设置UNITS=MASS PER LENGTH以"单位长度质量"单位指定非结构质量。此值仅对包含梁和/或桁架单元的单元集有效。

### **可选参数：**

DISTRIBUTION

此参数仅在UNITS=TOTAL MASS时相关。

设置DISTRIBUTION=MASS PROPORTIONAL（默认）以按照单元结构质量的比例在单元集区域的成员之间分配总非结构质量。单元集区域的基本结构密度被均匀缩放；因此，单元集区域的质心不会改变。

设置DISTRIBUTION=VOLUME PROPORTIONAL以按照初始配置中单元体积的比例在单元集区域的成员之间分配总非结构质量。在单元集区域的基本结构密度上添加均匀值；因此，如果区域具有不均匀的结构密度，单元集区域的质心可能会改变。

### **UNITS=TOTAL MASS的数据行：**

**第一行（也是唯一一行）：**

Abaqus不使用任何特定的物理单位，因此用户的选择必须一致。

### **UNITS=MASS PER VOLUME的数据行：**

**第一行（也是唯一一行）：**

Abaqus不使用任何特定的物理单位，因此用户的选择必须一致。

### **UNITS=MASS PER AREA的数据行：**

**第一行（也是唯一一行）：**

Abaqus不使用任何特定的物理单位，因此用户的选择必须一致。

### **UNITS=MASS PER LENGTH的数据行：**

**第一行（也是唯一一行）：**

Abaqus不使用任何特定的物理单位，因此用户的选择必须一致。