# *PLASTIC







### *PLASTIC指定金属塑性模型。

此选项用于为使用Mises或Hill屈服面的弹塑性材料指定材料模型的塑性部分。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["经典金属塑性，" Abaqus Analysis User's Guide第23.2.1节](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["承受循环加载的金属模型，" Abaqus Analysis User's Guide第23.2.2节](../usb/usb-link.md#usb-mat-chardening)
- ["Johnson-Cook塑性，" Abaqus Analysis User's Guide第23.2.7节](../usb/usb-link.md#usb-mat-cjohnsoncook)
- ["橡胶类材料中的永久变形，" Abaqus Analysis User's Guide第23.7.1节](../usb/usb-link.md#usb-mat-cpermanentset)
- ["UHARD，" Abaqus User Subroutines Reference Guide第1.1.36节](../sub/sub-link.md#sub-rtn-uuhard)
- ["VUHARD，" Abaqus User Subroutines Reference Guide第1.2.17节](../sub/sub-link.md#sub-rtn-uexphard)

### **可选参数：**

HARDENING

设置HARDENING=ISOTROPIC（默认）以指定各向同性硬化。

设置HARDENING=KINEMATIC以指定线性运动硬化。

设置HARDENING=COMBINED以指定非线性各向同性/运动硬化。

设置HARDENING=JOHNSON COOK以指定Johnson-Cook硬化。

设置HARDENING=USER以在Abaqus/Standard分析中的用户子程序[`UHARD`](../sub/sub-link.md#sub-xsl-uhard)或Abaqus/Explicit分析中的用户子程序[`VUHARD`](../sub/sub-link.md#sub-xsl-vuhard)中定义各向同性硬化。

SCALESTRESS

此参数不能与HARDENING参数一起使用。

将此参数设置为要缩放屈服应力的因子。

### **与HARDENING=ISOTROPIC或HARDENING=COMBINED结合使用的可选参数：**

DEPENDENCIES

将此参数设置为硬化行为定义中包含的场变量依赖数量，不包括温度和可能的应变范围。如果省略此参数，则硬化行为不依赖于场变量。有关更多信息，请参见["指定场变量依赖性"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中。

### **与HARDENING=ISOTROPIC结合使用的可选参数：**

RATE

将此参数设置为等效塑性应变率![](../graphics/key_eqn00543.gif)，用于指定此应力-应变曲线。

### **与HARDENING=COMBINED结合使用的可选参数：**

DATA TYPE

设置DATA TYPE=HALF CYCLE（默认）以指定用于校准运动硬化参数的第一半循环的应力与塑性应变值。

设置DATA TYPE=PARAMETERS以直接指定校准的运动硬化材料参数。

设置DATA TYPE=STABILIZED以指定用于校准运动硬化参数的稳定循环的应力与塑性应变值。

NUMBER BACKSTRESSES

将此参数设置为背应力数量。默认背应力数量为1，最大允许值为10。

### **与HARDENING=USER结合使用的可选参数：**

PROPERTIES

将此参数设置为在Abaqus/Standard分析的用户子程序[`UHARD`](../sub/sub-link.md#sub-xsl-uhard)和Abaqus/Explicit分析的用户子程序[`VUHARD`](../sub/sub-link.md#sub-xsl-vuhard)中所需的数据属性值数量。默认为PROPERTIES=0。

### **HARDENING=ISOTROPIC或HARDENING=COMBINED且DATA TYPE=HALF CYCLE的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将屈服应力定义为塑性应变以及温度和其他预定义场变量（如需要）的函数。

### **HARDENING=COMBINED且DATA TYPE=STABILIZED的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于4时需要）：**

根据需要重复此组数据行，以将屈服应力定义为塑性应变以及应变范围、温度和其他预定义场变量（如需要）的函数。

### **HARDENING=COMBINED且DATA TYPE=PARAMETERS的数据行：**

**第一行：**

**后续行（仅在条目数量大于8时需要）：**

根据需要重复此组数据行，以将屈服应力和运动硬化参数![](../graphics/key_eqn00996.gif)和![](../graphics/key_eqn00997.gif)定义为温度和其他预定义场变量的函数。

### **HARDENING=KINEMATIC的数据行：**

**第一行：**

最多重复此数据行两次，以定义与温度无关的线性运动硬化。根据需要重复此组数据行，以定义线性运动硬化模量随温度的变化。

### **HARDENING=JOHNSON COOK的数据行：**

**第一行（也是唯一一行）：**

### **HARDENING=USER且有PROPERTIES的数据行：**

**第一行：**

根据需要重复此数据行以定义所有硬化属性。
