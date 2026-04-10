# *VOLUMETRIC TEST DATA





### *VOLUMETRIC TEST DATA提供体积试验数据。

此选项只能与[*HYPERELASTIC](ch08abk06.md)选项、[*HYPERFOAM](ch08abk07.md)选项或[*VISCOELASTIC](ch21abk04.md)选项一起使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["橡胶类材料的超弹性行为," Section 22.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chhyperelastic)
- ["弹性体泡沫中的超弹性行为," Section 22.5.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chyperfoam)
- ["时域粘弹性," Section 22.7.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-ctimevisco)
- [*HYPERELASTIC](ch08abk06.md)
- [*HYPERFOAM](ch08abk07.md)
- [*VISCOELASTIC](ch21abk04.md)

### 超弹性材料模型

可以通过此选项提供体积加载试验数据以包括用户定义的材料可压缩性。可压缩性也可以通过在[*HYPERELASTIC](ch08abk06.md)选项上使用POISSON参数来包括，或者对于Marlow模型，通过在[*UNIAXIAL TEST DATA](ch20abk04.md)选项上指定标称横向应变来包括。如果这些选项都未用于指定体积行为，Abaqus/Standard假定材料是不可压缩的，而Abaqus/Explicit将为可压缩性选择默认值。在Abaqus/Explicit中使用此选项之前，请参阅["橡胶类材料的超弹性行为," Section 22.5.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-chhyperelastic)中"可压缩性"下的讨论。

### **可选参数：**

SMOOTH

包含此参数以对应力-应变数据应用平滑过滤器。如果省略此参数，则不执行平滑。

将此参数设置为数字*n*，使得![](../graphics/key_eqn00106.gif)等于移动窗口中数据点的总数，使用最小二乘法拟合三次多项式。*n*应该大于1。默认值为SMOOTH=3。

### **当[*VOLUMETRIC TEST DATA](ch21abk08.md)选项与[*HYPERELASTIC](ch08abk06.md)、MARLOW选项结合使用时的可选参数：**

DEPENDENCIES

将此参数设置为测试数据定义中包含的场变量依赖项数。如果省略此参数，则假定测试数据仅取决于温度。请参见["材料数据定义," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)中的"使用DEPENDENCIES参数定义场变量依赖性"。

### **为除Marlow模型之外的超弹性指定体积试验数据的数据行（如果使用SMOOTH参数，则体积比必须按升序或降序排列）：**

**第一行：**

根据需要重复此数据行。

### **为Marlow模型指定体积试验数据的数据行（如果使用SMOOTH参数，则体积比必须按降序排列）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以将测试数据定义为温度和其他预定义场变量的函数。体积比必须按降序给出。

### Hyperfoam材料模型

**此选项没有关联的参数。**

### **为hyperfoam指定体积试验数据的数据行：**

**第一行：**

根据需要重复此数据行。

### 粘弹性材料模型

### **可选参数：**

VOLINF

要指定蠕变试验数据，请将此参数设置为长期归一化体积柔量值，![](../graphics/key_eqn00200.gif)。

要指定松弛试验数据，请将此参数设置为长期归一化体积模量值，![](../graphics/key_eqn00201.gif)。

体积柔量与体积模量的关系为：![](../graphics/key_eqn00202.gif)。拟合过程将在约束条件![](../graphics/key_eqn00203.gif)中使用此值。

### **为粘弹性材料指定体积蠕变试验数据的数据行：**

**第一行：**

根据需要重复此数据行，以给出柔量-时间数据。

### **为粘弹性材料指定体积松弛试验数据的数据行：**

**第一行：**

根据需要重复此数据行，以给出模量-时间数据。





