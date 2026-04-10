# *ANISOTROPIC HYPERELASTIC





### *ANISOTROPIC HYPERELASTIC为近似不可压缩材料指定各向异性超弹性属性。

此选项用于定义通用各向异性超弹性材料的材料常数。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["各向异性超弹性行为，" Abaqus Analysis User's Guide第22.5.3节](../usb/usb-link.md#usb-mat-canisohyperelastic)
- ["UANISOHYPER_STRAIN，" Abaqus User Subroutines Reference Guide第1.1.21节](../sub/sub-link.md#sub-rtn-uuanisohyperstrn)
- ["UANISOHYPER_INV，" Abaqus User Subroutines Reference Guide第1.1.20节](../sub/sub-link.md#sub-rtn-uuanisohyperinv)
- ["VUANISOHYPER_STRAIN，" Abaqus User Subroutines Reference Guide第1.2.10节](../sub/sub-link.md#sub-rtn-uexpuanisohyperstrn)
- ["VUANISOHYPER_INV，" Abaqus User Subroutines Reference Guide第1.2.9节](../sub/sub-link.md#sub-rtn-uexpuanisohyperinv)

### **可选的、互斥的参数：**

FUNG-ANISOTROPIC

包含此参数以使用广义Fung各向异性应变能势。

FUNG-ORTHOTROPIC

包含此参数以使用广义Fung正交各向异性应变能势。

HOLZAPFEL

包含此参数以使用Holzapfel-Gasser-Ogden应变能势。

USER

如果应变能势及其导数在用户子程序中定义（[`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv)和[`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain)在Abaqus/Standard中，或[`VUANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-vuanisohyper_inv)和[`VUANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-vuanisohyper_strain)在Abaqus/Explicit中），请包含此参数。

### **如果包含USER参数，则需要以下参数：**

FORMULATION

设置FORMULATION=STRAIN以指示各向异性超弹性能量势以Green应变张量的分量形式表述，并由[`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain)（在Abaqus/Standard中）或[`VUANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-vuanisohyper_strain)（在Abaqus/Explicit中）定义。

设置FORMULATION=INVARIANT以指示各向异性超弹性能量势以伪不变量形式表述，并由[`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv)（在Abaqus/Standard中）或[`VUANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-vuanisohyper_inv)（在Abaqus/Explicit中）定义。

TYPE

此参数仅适用于Abaqus/Standard分析。

设置TYPE=INCOMPRESSIBLE以指示由[`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv)或[`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain)定义的各向异性超弹性材料是不可压缩的。

设置TYPE=COMPRESSIBLE以指示由[`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv)或[`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain)定义的超弹性材料是可压缩的。

### **可选参数：**

DEPENDENCIES

将此参数设置为包含在各向异性超弹性材料属性定义中的场变量依赖项数。如果省略此参数，则假定材料属性是常数或仅取决于温度。有关更多信息，请参见["在材料数据定义中指定场变量依赖性，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)。

LOCAL DIRECTIONS

此参数只能与基于不变量的应变能势（如HOLZAPFEL或USER，FORMULATION=INVARIANT）结合使用。将此参数设置为材料中首选局部方向（或纤维方向）的数量。默认值为LOCAL DIRECTIONS=0。

当LOCAL DIRECTIONS=*N*时，参考配置中*N*个局部方向向量的定义使用[*ORIENTATION](ch15abk01.md)，LOCAL DIRECTIONS=*M*选项指定，其中*M* ≥ *N*。如果*M* > *N*，则使用前*N*个方向。

如果使用HOLZAPFEL应变能势，则必须指定至少一个局部方向。

MODULI

此参数仅在[*ANISOTROPIC HYPERELASTIC](ch01abk10.md)选项与[*VISCOELASTIC](ch21abk04.md)选项结合使用时适用。

设置MODULI=INSTANTANEOUS以指示各向异性超弹性材料常数定义瞬时行为。此参数值不适用于Abaqus/Standard分析中的频域粘弹性。如果在用户子程序中定义各向异性超弹性能量势，则这是唯一可用的选项。

设置MODULI=LONG TERM以指示超弹性材料常数定义长期行为。当使用用户子程序定义各向异性超弹性能量势时，此选项不可用。对于所有其他各向异性超弹性模型，它是默认值。

PROPERTIES

此参数只能在指定USER参数时使用。设置此参数等于在用户子程序[`UANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-uanisohyper_inv)和[`UANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-uanisohyper_strain)（在Abaqus/Standard中）或[`VUANISOHYPER_INV`](../sub/sub-link.md#sub-xsl-vuanisohyper_inv)和[`VUANISOHYPER_STRAIN`](../sub/sub-link.md#sub-xsl-vuanisohyper_strain)（在Abaqus/Explicit中）中所需的数据属性值数量。默认值为0。

### **定义FUNG-ANISOTROPIC模型的材料常数的数据行：**

**第一行：**

**第二行：**

**第三行：**

**后续行（仅当DEPENDENCIES参数的值大于零时需要）：**

根据需要重复此组数据行，以将材料常数定义为温度和其他预定义场变量的函数。

### **定义FUNG-ORTHOTROPIC模型的材料常数的数据行：**

**第一行：**

**第二行：**

**后续行（仅当DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以将材料常数定义为温度和其他预定义场变量的函数。

### **定义HOLZAPFEL模型的材料常数的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于二时需要）：**

根据需要重复此组数据行，以将材料常数定义为温度和其他预定义场变量的函数。

### **定义USER各向异性超弹性模型材料属性的数据行：**

**如果PROPERTIES参数省略或设置为0，则不需要数据行。否则，第一行：**

根据需要重复此数据行以定义材料属性。