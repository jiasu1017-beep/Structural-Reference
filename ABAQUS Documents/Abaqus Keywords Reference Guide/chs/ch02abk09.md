# *BIAXIAL TEST DATA





### *BIAXIAL TEST DATA用于提供双轴测试数据（压缩和/或拉伸）。

此选项用于提供双轴测试数据。它只能与[*HYPERELASTIC](ch08abk06.md)选项、[*HYPERFOAM](ch08abk07.md)选项和[*MULLINS EFFECT](ch13abk31.md)选项配合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**属性模块

##### **参考：**

- ["橡胶类材料的超弹性行为，" Abaqus Analysis User's Guide第22.5.1节](../usb/usb-link.md#usb-mat-chyperelastic)
- ["elastomeric泡沫中的超弹性行为，" Abaqus Analysis User's Guide第22.5.2节](../usb/usb-link.md#usb-mat-chyperfoam)
- ["Mullins效应，" Abaqus Analysis User's Guide第22.6.1节](../usb/usb-link.md#usb-mat-cmullins)
- ["elastomeric泡沫中的能量耗散，" Abaqus Analysis User's Guide第22.6.2节](../usb/usb-link.md#usb-mat-cfoamdissipation)
- [*HYPERELASTIC](ch08abk06.md)
- [*HYPERFOAM](ch08abk07.md)
- [*MULLINS EFFECT](ch13abk31.md)

### 使用双轴测试数据定义超弹性材料

### **可选参数：**

SMOOTH

包含此参数以对应力-应变数据应用平滑滤波器。如果省略参数，则不进行平滑。

将此参数设置为数字*n*，使得![](../graphics/key_eqn00106.gif)等于通过其拟合三次多项式的移动窗口中的数据点总数（使用最小二乘法）。*n*应大于1。默认值为SMOOTH=3。

### **当[*BIAXIAL TEST DATA](ch02abk09.md)选项与[*HYPERELASTIC](ch08abk06.md)，MARLOW选项配合使用时的可选参数：**

DEPENDENCIES

将此参数设置为测试数据定义中包含的场变量依赖项数。如果省略此参数，则假定测试数据仅取决于温度。

### **为除Marlow模型之外的超弹性定义双轴测试数据的数据行（如果使用SMOOTH参数，名义应变必须按升序或降序排列）：**

**第一行：**

根据需要重复此数据行以给出应力-应变数据。

### **为Marlow模型定义双轴测试数据的数据行（如果使用SMOOTH参数，名义应变必须按升序排列）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时才需要）：**

根据需要重复此组数据行，以将测试数据定义为温度和其他预定义场变量的函数。名义应变和名义应力必须按升序给出。

### 使用双轴测试数据定义elastomeric泡沫

**此选项没有参数。**

### **为hyperfoam指定双轴测试数据的数据行：**

**第一行：**

根据需要重复此数据行以给出应力-应变数据。

### 使用双轴测试数据定义Mullins效应材料模型

**此选项没有参数。**

### **为定义Mullins效应材料模型的卸载-再加载响应指定双轴测试数据的数据行：**

**第一行：**

根据需要重复此数据行以给出应力-应变数据。


