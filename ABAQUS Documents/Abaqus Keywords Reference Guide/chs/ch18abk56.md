# *SWELLING





### *SWELLING指定随时间变化的体积膨胀。

此选项用于指定随时间变化的金属膨胀。对于材料。仅有在[*SOILS](ch18abk21.md)、CONSOLIDATION；[*COUPLED TEMPERATURE-DISPLACEMENT](ch03abk81.md)；和[*VISCO](ch21abk03.md)过程期间，由些选项定义的膨胀行为才有效。

**产品：**Abaqus/Standard  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["率相关塑性：蠕变和膨胀," Section 23.2.4 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["CREEP," Section 1.1.1 of the Abaqus User Subroutines Reference Guide](../sub/sub-link.md#sub-rtn-ucreep)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括体积膨胀应变率定义中的场变量依赖项数。如果省略此参数，则假定体积膨胀应变率是恒定的或仅取决于温度。有关详细信息，请参见["指定场变量依赖性" in "材料数据定义," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

LAW

设置LAW=INPUT（默认）以在数据行上定义膨胀行为。

设置LAW=USER以在用户子程序[`CREEP`](../sub/sub-link.md#sub-xsl-creep)中定义膨胀行为。

### **LAW=INPUT的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以定义体积膨胀应变率对温度和其他预定义场变量的依赖性。





