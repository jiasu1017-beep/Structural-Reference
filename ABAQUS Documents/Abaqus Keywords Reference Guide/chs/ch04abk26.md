# *DISCRETE SECTION





### *DISCRETE SECTION为离散单元指定单元属性。

此选项用于定义离散单元的属性。

**产品：**Abaqus/Explicit  

**类型：**模型数据  

**级别：**部件、部件实例  

##### **参考：**

- ["离散单元方法，" Abaqus分析用户指南第15.1.1节](../usb/usb-link.md#usb-anl-ademanalysis)

### **必需参数：**

ELSET

将此参数设置为包含正在定义截面的单元的单元集合名称。

DENSITY

将此参数设置为一个数值或分布名称（请参见["分布定义，" Abaqus分析用户指南第2.8.1节](../usb/usb-link.md#usb-int-adefiningdistributions)），以用于这些单元。

SHAPE

此参数用于指定离散单元的形状。

将此参数设置为 SPHERE（默认）。

### **可选参数：**

ALPHA

将此参数设置为离散单元的质量比例阻尼因子值。默认值为0.0。

### **离散单元的数据行：**

**第一行（也是唯一一行）：**




