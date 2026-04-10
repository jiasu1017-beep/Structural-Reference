# *MULLINS EFFECT









### *MULLINS EFFECT为弹性体指定Mullins效应材料参数。

此选项用于为填充橡胶弹性体中的Mullins效应或为弹性体泡沫中的能量耗散建模定义材料常数。它只能与[*HYPERELASTIC](ch08abk06.md)或[*HYPERFOAM](ch08abk07.md)选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["橡胶类材料的超弹性行为，" Abaqus Analysis User's Guide第22.5.1节](../usb/usb-link.md#usb-mat-chhyperelastic)
- ["弹性体泡沫中的超弹性行为，" Abaqus Analysis User's Guide第22.5.2节](../usb/usb-link.md#usb-mat-chhyperfoam)
- ["Mullins效应，" Abaqus Analysis User's Guide第22.6.1节](../usb/usb-link.md#usb-mat-cmullins)
- ["弹性体泡沫中的能量耗散，" Abaqus Analysis User's Guide第22.6.2节](../usb/usb-link.md#usb-mat-cfoamdissipation)
- ["UMULLINS，" Abaqus User Subroutines Reference Guide第1.1.45节](../sub/sub-link.md#sub-rtn-uumullins)
- ["VUMULLINS，" Abaqus User Subroutines Reference Guide第1.2.21节](../sub/sub-link.md#sub-rtn-uexpumullins)
- [*BIAXIAL TEST DATA](ch02abk09.md)
- [*PLANAR TEST DATA](ch16abk13.md)
- [*UNIAXIAL TEST DATA](ch20abk04.md)

### **可选的互斥参数：**

TEST DATA INPUT

如果材料常数要由Abaqus根据从材料试样简单测试中获得的数据计算，则包含此参数。如果省略此参数，则可以直接在数据行上给出材料常数，或者可以通过Abaqus/Standard中的用户子程序[`UMULLINS`](../sub/sub-link.md#sub-xsl-umullins)或Abaqus/Explicit中的[`VUMULLINS`](../sub/sub-link.md#sub-xsl-vumullins)定义损伤变量。

USER

如果定义Mullins效应的损伤变量在Abaqus/Standard中的用户子程序[`UMULLINS`](../sub/sub-link.md#sub-xsl-umullins)或Abaqus/Explicit中的[`VUMULLINS`](../sub/sub-link.md#sub-xsl-vumullins)中定义，则包含此参数。

### **可选参数：**

BETA

此参数只能在使用TEST DATA INPUT参数时使用；它定义的值，而Mullins效应模型的其他系数从测试数据中拟合。如果同时指定了R和M参数，则不能指定此参数（使用数据行代替指定所有三个参数）。如果省略此参数，将从测试数据的非线性最小二乘拟合确定。允许的BETA值为。M和BETA参数不能同时为零。

DEPENDENCIES

将此参数设置为除温度外材料参数依赖的场变量数量。如果省略此参数，则假定材料参数是常数或仅取决于温度。

如果包含了USER或TEST DATA INPUT参数，则此参数不相关。

M

此参数只能在使用TEST DATA INPUT参数时使用；它定义的值，而Mullins效应模型的其他系数从测试数据中拟合。如果同时指定了R和BETA参数，则不能指定此参数（使用数据行代替指定所有三个参数）。如果省略此参数，将从测试数据的非线性最小二乘拟合确定m。允许的M值为。M和BETA参数不能同时为零。

PROPERTIES

此参数只能在指定了USER参数时使用。将此参数设置为在Abaqus/Standard中的用户子程序[`UMULLINS`](../sub/sub-link.md#sub-xsl-umullins)或Abaqus/Explicit中的[`VUMULLINS`](../sub/sub-link.md#sub-xsl-vumullins)中所需的数据属性值数量。默认值为0。

R

此参数只能在使用TEST DATA INPUT参数时使用；它定义的值，而Mullins效应模型的其他系数从测试数据中拟合。如果同时指定了M和BETA参数，则不能指定此参数（使用数据行代替指定所有三个参数）。如果省略此参数，将从测试数据的非线性最小二乘拟合确定r。允许的R值为。

### **通过给出测试数据来定义材料行为：**

当指定了TEST DATA INPUT参数时，此选项不使用数据行。数据改为在[*BIAXIAL TEST DATA](ch02abk09.md)、[*PLANAR TEST DATA](ch16abk13.md)和[*UNIAXIAL TEST DATA](ch20abk04.md)选项下给出。这些选项适用，除非是用户定义损伤变量的情况。

### **如果省略了TEST DATA INPUT和USER参数，则定义材料常数的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于4时需要）：**

根据需要重复此组数据行，以将材料常数定义为温度和其他预定义场变量的函数。

### **如果指定了USER参数，则定义材料特性的数据行：**

**如果省略PROPERTIES参数或设置为0，则不需要数据行。否则，第一行：**

根据需要重复此数据行以定义材料特性。