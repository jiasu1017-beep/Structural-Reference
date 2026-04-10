# *SURFACE PROPERTY ASSIGNMENT





### *SURFACE PROPERTY ASSIGNMENT为通用接触算法将表面属性分配给表面。

此选项用于修改参与通用接触相互作用的表面的表面属性。它必须与[*CONTACT](ch03abk54.md)选项一起使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**Abaqus/Standard中的模型数据；Abaqus/Explicit中的模型或历史数据

**级别：**Abaqus/Standard中的模型；Abaqus/Explicit中的模型或步

**Abaqus/CAE：**Interaction模块

##### **参考：**

- ["Abaqus/Standard中通用接触的表面属性," Section 36.2.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-asurfacepropassignstd)
- ["Abaqus/Explicit中通用接触的表面属性分配," Section 36.4.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-cni-asurfacepropassign)
- [*CONTACT](ch03abk54.md)

### **必需参数：**

PROPERTY

使用此参数指定正在分配的属性类型。要修改多种类型的表面属性，请多次包含[*SURFACE PROPERTY ASSIGNMENT](ch18abk53.md)选项，并为此参数设置不同的值。

设置PROPERTY=BEAM SMOOTHING以控制梁-梁接触中梁段的平滑。此参数值仅适用于Abaqus/Standard分析。

设置PROPERTY=FEATURE EDGE CRITERIA以控制应在通用接触域中激活哪些主特征边缘和次特征边缘。

设置PROPERTY=GEOMETRIC CORRECTION以分配几何修正。

设置PROPERTY=OFFSET FRACTION以将表面偏移分配为表面厚度的分数。

设置PROPERTY=THICKNESS以分配表面厚度。

### **PROPERTY=BEAM SMOOTHING的数据行：**

**第一行：**

根据需要重复此数据行。如果梁平滑分配重叠，最后的分配将应用于重叠区域。

### **Abaqus/Standard中PROPERTY=FEATURE EDGE CRITERIA的数据行：**

**第一行：**

根据需要重复此数据行。如果特征边缘标准分配重叠，最后的分配将应用于重叠区域。

### **Abaqus/Explicit中PROPERTY=FEATURE EDGE CRITERIA的数据行：**

**第一行：**

根据需要重复此数据行。如果特征边缘标准分配重叠，最后的分配将应用于重叠区域。

### **PROPERTY=GEOMETRIC CORRECTION的数据行，用于在对应（或近似对应）圆弧的二维表面区域上定义平滑：**

**第一行：**

根据需要重复此数据行。如果几何修正分配重叠，最后的分配将应用于重叠区域。

**图18.53-1** 二维圆周平滑。

![](../graphics/usb-kws-msmoothcir2d-nls.png)

### **PROPERTY=GEOMETRIC CORRECTION的数据行，用于在对应（或近似对应）旋转曲面的表面区域上定义平滑：**

**第一行：**

根据需要重复此数据行。如果几何修正分配重叠，最后的分配将应用于重叠区域。

**图18.53-2** 三维圆周平滑。

![](../graphics/usb-kws-msmoothcir3d-nls.png)

### **PROPERTY=GEOMETRIC CORRECTION的数据行，用于在对应（或近似对应）球面截面的表面区域上定义平滑：**

**第一行：**

根据需要重复此数据行。如果几何修正分配重叠，最后的分配将应用于重叠区域。

**图18.53-3** 球面平滑。

![](../graphics/usb-kws-msmoothsph3d-nls.png)

### **PROPERTY=GEOMETRIC CORRECTION的数据行，用于在对应（或近似对应）绕轴旋转的圆弧的表面区域上定义平滑：**

**第一行：**

根据需要重复此数据行。如果几何修正分配重叠，最后的分配将应用于重叠区域。从点*a*到圆弧中心的连线应垂直于旋转轴。

**图18.53-4** 三维环面平滑。

![](../graphics/usb-kws-msmoothtor3d-nls.png)

### **PROPERTY=GEOMETRIC CORRECTION的数据行，用于定义不应平滑的表面区域（对应默认值）：**

**第一行：**

根据需要重复此数据行。如果几何修正分配重叠，最后的分配将应用于重叠区域。

### **PROPERTY=OFFSET FRACTION的数据行：**

**第一行：**

根据需要重复此数据行。如果偏移分数分配重叠，最后的分配将应用于重叠区域。

### **PROPERTY=THICKNESS的数据行：**

**第一行：**

根据需要重复此数据行。如果厚度分配重叠，最后的分配将应用于重叠区域。





