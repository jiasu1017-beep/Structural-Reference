# *DRUCKER PRAGER CREEP





### *DRUCKER PRAGER CREEP指定Drucker-Prager蠕变定律和材料属性。

此选项用于定义Drucker-Prager蠕变模型和材料属性。此选项定义的蠕变行为仅在 [*SOILS](ch18abk21.md)、CONSOLIDATION；[*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md)；和 [*VISCO](ch21abk03.md) 过程中生效。它必须与 [*DRUCKER PRAGER](ch04abk34.md) 和 [*DRUCKER PRAGER HARDENING](ch04abk36.md) 选项结合使用。输入的数据必须与 [*DRUCKER PRAGER HARDENING](ch04abk36.md) 选项上使用的 TYPE 参数一致。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["扩展Drucker-Prager模型，" Abaqus分析用户指南第23.3.1节](../usb/usb-link.md#usb-mat-cdruckerprager)
- [*DRUCKER PRAGER](ch04abk34.md)
- [*DRUCKER PRAGER HARDENING](ch04abk36.md)
- ["CREEP，" Abaqus用户子程序参考指南第1.1.1节](../sub/sub-link.md#sub-rtn-ucreep)

### **可选参数：**

DEPENDENCIES

除了温度之外，将此参数设置为蠕变常数定义中包含的场变量依赖项数量。如果省略此参数，则假定蠕变常数仅取决于温度。请参见Abaqus分析用户指南第21.1.2节中的["指定场变量依赖性"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多详细信息。

LAW

设置 LAW=STRAIN（默认）以选择应变硬化幂律。

设置 LAW=TIME 以选择时间硬化幂律。

设置 LAW=SINGHM 以选择Singh-Mitchell型定律。

设置 LAW=USER 以使用用户子程序 [`CREEP`](../sub/sub-link.md#sub-xsl-creep) 输入蠕变定律。

TIME

此参数仅在 LAW=TIME 或 LAW=SINGHM 时相关。

设置 TIME=CREEP 以使用蠕变时间。

设置 TIME=TOTAL（默认）以使用总时间。

### **LAW=TIME 或 LAW=STRAIN 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于四时需要）：**

根据需要重复此组数据行，以将蠕变常数对温度和其他预定义场变量的依赖性定义为函数。

### **LAW=SINGHM 的数据行：**

**第一行：**

**后续行（仅在 DEPENDENCIES 参数值大于三时需要）：**

根据需要重复此组数据行，以将蠕变常数对温度和其他预定义场变量的依赖性定义为函数。




