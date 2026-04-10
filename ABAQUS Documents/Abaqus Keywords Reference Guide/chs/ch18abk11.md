# *SHEAR FAILURE





### *SHEAR FAILURE指定剪切失效模型和准则。

此选项与Mises或Johnson-Cook塑性模型配合使用以指定材料的剪切失效。它必须与选项[*PLASTIC](ch16abk14.md)，HARDENING=ISOTROPIC或JOHNSON COOK配合使用。

**产品：**Abaqus/Explicit

**类型：**模型数据

**级别：**模型

##### **参考：**

- ["Classical metal plasticity," Section 23.2.1 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["Johnson-Cook plasticity," Section 23.2.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cjohnsoncook)
- ["Dynamic failure models," Section 23.2.8 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cfailuremodels)
- [*PLASTIC](ch16abk14.md)

### **可选参数：**

DEPENDENCIES

此参数仅与TYPE=TABULAR相关。

将此参数设置为除了温度之外还包括失效时等效塑性应变定义中的场变量依赖项数。如果省略此参数，则假定失效应变取决于塑性应变、塑性应变率、 dimensionless pressure-deviatoric stress ratio以及可能取决于温度。有关更多信息，请参见["Material data definition," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata)中的"使用DEPENDENCIES参数定义场变量依赖性"。

ELEMENT DELETION

设置ELEMENT DELETION=YES（默认）以允许在满足失效准则时删除单元。

设置ELEMENT DELETION=NO以允许单元仅在满足失效准则时承受静水压应力。

TYPE

设置TYPE=JOHNSON COOK以定义Johnson-Cook剪切失效准则。它需要使用[*PLASTIC](ch16abk14.md)，HARDENING=JOHNSON COOK选项。

设置TYPE=TABULAR（默认）以表格数据形式定义失效应变。它需要使用[*PLASTIC](ch16abk14.md)，HARDENING=ISOTROPIC选项。

### **以表格形式定义失效应变的数据行（TYPE=TABULAR）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于四时需要）：**

根据需要重复此组数据行以定义失效应变对塑性应变、塑性应变率、应力比的依赖性，以及在需要时对温度和其他预定义场变量的依赖性。

### **定义Johnson-Cook剪切失效准则的数据行（TYPE=JOHNSON COOK）：**

**第一行（也是唯一行）：**




