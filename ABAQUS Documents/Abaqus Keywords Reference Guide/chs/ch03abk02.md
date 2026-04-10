# *CAP CREEP






### *CAP CREEP指定帽盖蠕变定律和材料属性。

此选项用于定义帽盖蠕变模型和材料属性。此选项定义的蠕变行为仅在 [*SOILS](ch18abk21.md)、CONSOLIDATION；[*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md)；和 [*VISCO](ch21abk03.md) 程序中激活。必须与 [*CAP PLASTICITY](ch03abk04.md) 和 [*CAP HARDENING](ch03abk03.md) 选项结合使用。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE: **属性模块

##### **参考：**

- ["改进的 Drucker-Prager/帽盖模型，" Abaqus 分析用户指南第 23.3.2 节](../usb/usb-link.md#usb-mat-ccapplastic)
- [*CAP PLASTICITY](ch03abk04.md)
- [*CAP HARDENING](ch03abk03.md)
- ["CREEP，" Abaqus 用户子程序参考指南第 1.1.1 节](../sub/sub-link.md#sub-rtn-ucreep)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在蠕变常数定义中的场变量依赖项数。如果省略此参数，则假定蠕变常数仅依赖于温度。有关更多信息，请参阅 ["材料数据定义"中的"指定场变量依赖性"，Abaqus 分析用户指南第 21.1.2 节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

LAW

设置 LAW=STRAIN（默认）选择应变强化幂律。

设置 LAW=TIME 选择时间强化幂律。

设置 LAW=SINGHM 选择 Singh-Mitchell 类型定律。

设置 LAW=USER 使用用户子程序 [`CREEP`](../sub/sub-link.md#sub-xsl-creep) 输入蠕变定律。

MECHANISM

设置 MECHANISM=COHESION（默认）选择内聚蠕变机制，其行为类似于 Drucker-Prager 蠕变。

设置 MECHANISM=CONSOLIDATION 选择固结蠕变机制，其行为类似于塑性帽盖区域。

TIME

仅当使用 LAW=TIME 或 LAW=SINGHM 时此参数才相关。

设置 TIME=CREEP 使用蠕变时间。

设置 TIME=TOTAL（默认）使用总时间。

### **LAW=TIME 或 LAW=STRAIN 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此数据行集，以定义蠕变常数对温度和其他预定义场变量的依赖性。

### **LAW=SINGHM 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此数据行集，以定义蠕变常数对温度和其他预定义场变量的依赖性。




