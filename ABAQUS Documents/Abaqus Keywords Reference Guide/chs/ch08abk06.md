# *HYPERELASTIC






### *HYPERELASTIC为近似不可压缩弹性体指定弹性特性。

此选项用于为通用超弹性材料定义材料常数。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Property 模块

##### **参考文献：**

- ["类橡胶材料的超弹性行为，" Abaqus Analysis User's Guide 第 22.5.1 节](../usb/usb-link.md#usb-mat-chyperelastic)
- ["UHYPER，" Abaqus User Subroutines Reference Guide 第 1.1.38 节](../sub/sub-link.md#sub-rtn-uuhyper)
- [*BIAXIAL TEST DATA](ch02abk09.md)
- [*PLANAR TEST DATA](ch16abk13.md)
- [*UNIAXIAL TEST DATA](ch20abk04.md)
- [*VOLUMETRIC TEST DATA](ch21abk08.md)

### **可选的、互斥的参数：**

ARRUDA-BOYCE

包含此参数以使用 Arruda-Boyce 模型，也称为八链模型。

MARLOW

包含此参数以使用 Marlow 模型。

MOONEY-RIVLIN

包含此参数以使用 Mooney-Rivlin 模型。此方法等同于使用 POLYNOMIAL 参数并将 N=1。

NEO HOOKE

包含此参数以使用 neo-Hookean 模型。此方法等同于使用 REDUCED POLYNOMIAL 参数并将 N=1。

OGDEN

包含此参数以使用 Ogden 应变能势。

POLYNOMIAL

包含此参数以使用多项式应变能势。此方法是定义应变能势的默认方法。

REDUCED POLYNOMIAL

包含此参数以使用减缩多项式应变能势。此方法等同于使用 POLYNOMIAL 参数并将 ![](../graphics/key_eqn00781.gif) 用于 ![](../graphics/key_eqn00782.gif)。

USER

此参数仅适用于 Abaqus/Standard 分析。

如果应变能势对应变不变量的导数在用户子程序 [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper) 中定义，则包含此参数。

VAN DER WAALS

包含此参数以使用 Van der Waals 模型，也称为 Kilian 模型。

YEOH

包含此参数以使用 Yeoh 模型。此方法等同于使用 REDUCED POLYNOMIAL 参数并将 N=3。

### **如果使用了 USER 参数，则为必需参数：**

TYPE

此参数仅适用于 Abaqus/Standard 分析。

设置 TYPE=INCOMPRESSIBLE 以指示由 [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper) 定义的超弹性材料是不可压缩的。

设置 TYPE=COMPRESSIBLE 以指示由 [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper) 定义的超弹性材料是可压缩的。

### **可选参数：**

BETA

此参数只能在 VAN DER WAALS 和 TEST DATA INPUT 参数同时使用时使用；它定义了 ![](../graphics/key_eqn00135.gif) 的值，而 Van der Waals 模型的其他系数则由用户给出的测试数据拟合。如果省略此参数，则 ![](../graphics/key_eqn00135.gif) 将从测试数据的非线性最小二乘拟合中确定。BETA 的允许值为 ![](../graphics/key_eqn00783.gif)。如果只有一种类型的测试数据可用，建议将 ![](../graphics/key_eqn00135.gif) = 0。

MODULI

此参数仅在 [*HYPERELASTIC](ch08abk06.md) 选项与 [*VISCOELASTIC](ch21abk04.md) 或 [*HYSTERESIS](ch08abk09.md) 选项一起使用时才适用。

设置 MODULI=INSTANTANEOUS 以指示超弹性材料常数定义瞬时行为。此参数值不适用于 Abaqus/Standard 分析中的频域粘弹性。如果超弹性材料在用户子程序 [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper) 中定义，则这是唯一可用的选项。

设置 MODULI=LONG TERM 以指示超弹性材料常数定义长期行为。当使用用户子程序 [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper) 定义超弹性材料时，此选项不可用。对于所有其他超弹性模型，它是默认值。

N

此参数只能与 OGDEN、POLYNOMIAL 和 REDUCED POLYNOMIAL 参数一起使用。包含此参数以定义应变能势的阶数。默认值为 N=1。

如果使用了 TEST DATA INPUT 参数，则对于 POLYNOMIAL 形式，参数 N 只能取 1 或 2；对于 OGDEN 和 REDUCED POLYNOMIAL 形式，N 最多可为 6。

如果省略 TEST DATA INPUT 参数，则对于任何形式，N 的最大值为 6。

POISSON

将此参数设置为泊松比 ![](../graphics/key_eqn00579.gif)，以考虑可压缩性。如果直接指定材料系数，或者如果在数据行上通过为 ![](../graphics/key_eqn00784.gif) 输入非零值或通过指定 [*VOLUMETRIC TEST DATA](ch21abk08.md) 选项来定义体积行为，则不能使用此参数。此外，如果标称横向应变在 [*UNIAXIAL TEST DATA](ch20abk04.md)、[*BIAXIAL TEST DATA](ch02abk09.md) 或 [*PLANAR TEST DATA](ch16abk13.md) 选项上指定，则对于 Marlow 模型也不能使用此参数。

PROPERTIES

此参数仅适用于 Abaqus/Standard 分析。

此参数只能在指定了 USER 参数时使用。将其设置为在用户子程序 [`UHYPER`](../sub/sub-link.md#sub-xsl-uhyper) 中作为数据所需的属性值数量。默认值为 0。

TEST DATA INPUT

如果材料常数要由 Abaqus 从从材料试样上进行的简单测试获取的数据中计算得出，则包含此参数。

如果省略此参数，则必须直接在数据行上给出材料常数。此参数与 Marlow 模型不相关，在这种情况下，必须指定测试数据。

### **通过给出测试数据来定义材料行为：**

除了用户定义的模型之外，对于所有超弹性材料模型，都有替代选项来指定测试数据，而不是在 [*HYPERELASTIC](ch08abk06.md) 选项的数据行上指定相关材料常数。当指定了 MARLOW 或 TEST DATA INPUT 参数时，[*HYPERELASTIC](ch08abk06.md) 选项不使用数据行。在这种情况下，测试数据通过 [*BIAXIAL TEST DATA](ch02abk09.md)、[*PLANAR TEST DATA](ch16abk13.md)、[*UNIAXIAL TEST DATA](ch20abk04.md) 和 [*VOLUMETRIC TEST DATA](ch21abk08.md) 选项指定。

### **定义 ARRUDA-BOYCE 模型的材料常数的数据行：**

**第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

### **定义 MOONEY-RIVLIN 模型的材料常数的数据行：**

**第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

### **定义 NEO HOOKE 模型的材料常数的数据行：**

**第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

### **定义 OGDEN 应变能势的材料常数的数据行：**

**如果 N=1 的第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

**如果 N=2 的第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

**如果 N=3 的第一行：**

**如果 N=3 的第二行：**

根据需要重复此数据行对，以将材料常数定义为温度的函数。

**对于 N 的更高值（最多 6）的数据行：**

### **定义 POLYNOMIAL 应变能势的材料常数的数据行：**

**如果 N=1 的第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

**如果 N=2 的第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

**如果 N=3 的第一行：**

**如果 N=3 的第二行：**

根据需要重复此数据行对，以将材料常数定义为温度的函数。

**对于 N 的更高值（最多 6）的数据行：**

### **定义 REDUCED POLYNOMIAL 应变能势的材料常数的数据行：**

**如果 N=1 的第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

**如果 N=2 的第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

**如果 N=3 的第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

**对于 N 的更高值（最多 6）的数据行：**

### **定义 USER 超弹性模型材料特性的数据行：**

**如果 PROPERTIES 参数被省略或设置为 0，则不需要数据行。否则，第一行：**

根据需要重复此数据行以定义材料特性。

### **定义 VAN DER WAALS 模型的材料常数的数据行：**

**第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

### **定义 YEOH 模型的材料常数的数据行：**

**第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。




