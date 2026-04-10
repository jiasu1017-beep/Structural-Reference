# *MOHR COULOMB









### *MOHR COULOMB指定莫尔-库仑塑性模型。

此选项用于为使用莫尔-库仑塑性模型的弹塑性材料定义屈服面和流动势参数。它必须与[*MOHR COULOMB HARDENING](ch13abk24.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["莫尔-库仑塑性，" Abaqus Analysis User's Guide第23.3.3节](../usb/usb-link.md#usb-mat-cmohrcoulomb)
- [*MOHR COULOMB HARDENING](ch13abk24.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为材料参数定义中除温度外的场变量依赖数量。如果省略此参数，则假定材料特性是常数或仅取决于温度。

DEVIATORIC ECCENTRICITY

将此参数设置为偏平面中的流动势偏心率。如果省略此参数，则默认情况下偏心率计算为，其中是数据行上定义的莫尔-库仑摩擦角。值的范围为。

ECCENTRICITY

将此参数设置为子午面中的流动势偏心率，。子午偏心率是一个小的正数，定义流动势接近其渐近线的速率。默认值为。

### **定义莫尔-库仑塑性模型的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以定义材料参数对温度和其他预定义场变量的依赖性。