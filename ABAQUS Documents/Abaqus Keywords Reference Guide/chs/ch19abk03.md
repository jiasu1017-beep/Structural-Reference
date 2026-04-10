# *TENSION CUTOFF





### *TENSION CUTOFF为Mohr-Coulomb塑性模型指定抗拉截止数据。

此选项用于指定抗拉截止数据，以限制Mohr-Coulomb塑性模型在拉伸区域附近的承载能力。此选项必须与[*MOHR COULOMB](ch13abk23.md)和[*MOHR COULOMB HARDENING](ch13abk24.md)选项一起使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["Mohr-Coulomb塑性," Section 23.3.3 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmohrcoulomb)
- [*MOHR COULOMB](ch13abk23.md)
- [*MOHR COULOMB HARDENING](ch13abk24.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括抗拉截止应力定义中的场变量依赖项数。如果省略此参数，则假定抗拉屈服应力仅取决于塑性应变，可能还取决于温度。

### **定义抗拉截止的数据行：**

**第一数据行：**

**后续数据行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以定义抗拉截止对预定义场变量的依赖性。





