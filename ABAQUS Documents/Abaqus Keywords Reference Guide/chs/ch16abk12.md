# *PLANAR TEST DATA







### *PLANAR TEST DATA用于提供平面测试（或纯剪切）数据（压缩和/或拉伸）。

此选项用于提供平面测试（或纯剪切）数据。它只能与[*HYPERELASTIC](ch08abk06.md)选项、[*HYPERFOAM](ch08abk07.md)选项和[*MULLINS EFFECT](ch13abk31.md)选项结合使用。这种测试不能完全定义超弹性材料常数；至少还应提供单轴或双轴测试数据。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["橡胶类材料的超弹性行为，" Abaqus Analysis User's Guide第22.5.1节](../usb/usb-link.md#usb-mat-chyperelastic)
- ["弹性体泡沫中的超弹性行为，" Abaqus Analysis User's Guide第22.5.2节](../usb/usb-link.md#usb-mat-chyperfoam)
- ["Mullins效应，" Abaqus Analysis User's Guide第22.6.1节](../usb/usb-link.md#usb-mat-cmullins)
- ["弹性体泡沫中的能量耗散，" Abaqus Analysis User's Guide第22.6.2节](../usb/usb-link.md#usb-mat-cfoamdissipation)
- [*HYPERELASTIC](ch08abk06.md)
- [*HYPERFOAM](ch08abk07.md)
- [*MULLINS EFFECT](ch13abk31.md)

### 使用平面测试数据定义超弹性材料

### **可选参数：**

SMOOTH

包含此参数以对应力-应变数据应用平滑滤波器。如果省略此参数，则不进行平滑。

将此参数设置为数字*n*，使得![](../graphics/key_eqn00106.gif)等于移动窗口中的数据点总数，通过该窗口使用最小二乘法拟合三次多项式。*n*应大于1。默认值为SMOOTH=3。

### **当[*PLANAR TEST DATA](ch16abk13.md)选项与[*HYPERELASTIC](ch08abk06.md)，MARLOW选项结合使用时的可选参数：**

DEPENDENCIES

将此参数设置为测试数据定义中包含的场变量依赖数量。如果省略此参数，则假定测试数据仅依赖于温度。有关更多信息，请参见["指定场变量依赖性"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中。

### **指定超弹性（Marlow模型除外）平面测试数据的数据行（如果使用SMOOTH参数，名义应变必须按升序或降序排列）：**

**第一行：**

根据需要重复此数据行以提供应力-应变数据。

### **为Marlow模型指定平面测试数据的数据行（如果使用SMOOTH参数，名义应变必须按升序排列）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于4时需要）：**

根据需要重复此组数据行，以将测试数据定义为温度和其他预定义场变量的函数。名义应变和名义应力必须按升序给出。

### 使用平面测试数据定义弹性体泡沫

**此选项没有关联的参数。**

### **指定超泡沫平面测试数据的数据行：**

**第一行：**

根据需要重复此数据行以提供应力-应变数据。

### 使用平面测试数据定义Mullins效应材料模型

**此选项没有关联的参数。**

### **指定用于定义Mullins效应材料模型卸载-再加载响应的平面测试数据的数据行：**

**第一行：**

根据需要重复此数据行以提供应力-应变数据。
