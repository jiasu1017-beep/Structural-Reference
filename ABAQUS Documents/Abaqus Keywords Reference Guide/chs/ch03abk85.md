# *CREEP






### *CREEP定义蠕变定律。

当要在材料定义中包含金属蠕变行为时使用此选项。定义的金属蠕变行为仅在 [*DIRECT CYCLIC](ch04abk24.md)；[*SOILS](ch18abk21.md)、CONSOLIDATION；[*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md)；[*STEADY STATE TRANSPORT](ch18abk35.md)；和 [*VISCO](ch21abk03.md) 过程中激活。此选项也可用于在垫片中定义厚度方向的蠕变行为；在这种情况下，此选项仅在 [*VISCO](ch21abk03.md) 过程中激活。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型

**Abaqus/CAE: **属性模块

##### **参考：**

- ["率相关塑性：蠕变和膨胀，" Abaqus 分析用户指南第 23.2.4 节](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["各向异性屈服/蠕变，" Abaqus 分析用户指南第 23.2.6 节](../usb/usb-link.md#usb-mat-canisoyield)
- ["CREEP，" Abaqus 用户子程序参考指南第 1.1.1 节](../sub/sub-link.md#sub-rtn-ucreep)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在蠕变常数定义中的场变量依赖项数。如果省略此参数，则假定蠕变常数没有依赖或仅依赖于温度。请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

LAW

设置 LAW=STRAIN（默认）以选择应变强化幂律。

设置 LAW=TIME 以选择时间强化幂律。

设置 LAW=HYPERB 以选择双曲正弦定律。

设置 LAW=USER 以使用用户子程序 [`CREEP`](../sub/sub-link.md#sub-xsl-creep) 输入蠕变定律。

设置 LAW=ANAND 以选择 Anand 定律。

设置 LAW=DARVEAUX 以选择 Darveaux 定律。

设置 LAW=DOUBLE POWER 以选择双幂律。

TIME

此参数仅在 LAW=TIME 时相关。

设置 TIME=CREEP 以在时间强化关系中使用蠕变时间。

设置 TIME=TOTAL（默认）以在时间强化关系中使用总时间。

### **LAW=TIME 或 LAW=STRAIN 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此数据行集，以定义蠕变常数对温度和其他预定义场变量的依赖性。

### **LAW=HYPERB 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此数据行集，以定义蠕变常数对预定义场变量的依赖性。

### **LAW=ANAND 的数据行：**

**第一行：**

**第二行：**

### **LAW=DARVEAUX 的数据行：**

**第一行：**

### **LAW=DOUBLE POWER 的数据行：**

**第一行：**




