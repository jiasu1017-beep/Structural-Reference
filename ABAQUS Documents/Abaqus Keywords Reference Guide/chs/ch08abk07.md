# *HYPERFOAM






### *HYPERFOAM为超弹性泡沫指定弹性特性。

此选项用于为通用弹性体泡沫定义材料常数。此材料与常规超弹性材料的区别在于它是高度可压缩的。

**产品：** Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：** 模型数据  

**级别：** 模型  

**Abaqus/CAE：** Property 模块

##### **参考文献：**

- ["弹性体泡沫中的超弹性行为，" Abaqus Analysis User's Guide 第 22.5.2 节](../usb/usb-link.md#usb-mat-chyperfoam)
- [*BIAXIAL TEST DATA](ch02abk09.md)
- [*PLANAR TEST DATA](ch16abk13.md)
- [*SIMPLE SHEAR TEST DATA](ch18abk18.md)
- [*UNIAXIAL TEST DATA](ch20abk04.md)
- [*VOLUMETRIC TEST DATA](ch21abk08.md)

### **可选参数：**

MODULI

此参数仅在 [*HYPERFOAM](ch08abk07.md) 选项与 [*VISCOELASTIC](ch21abk04.md) 选项一起使用时才适用。

设置 MODULI=INSTANTANEOUS 以指示超泡沫材料常数定义瞬时行为。此参数值不适用于 Abaqus/Standard 分析中的频域粘弹性。

设置 MODULI=LONG TERM（默认）以指示超泡沫材料常数定义长期行为。

N

将此参数设置为应变能势的阶数。最大值为 N=6。默认值为 N=1。

POISSON

将此参数设置为材料的有效泊松比 ![](../graphics/key_eqn00579.gif)。此参数仅在指定了 TEST DATA INPUT 参数时有效。

如果包含此参数，则假定对于所有 *i* 有 ![](../graphics/key_eqn00805.gif)，并且不需要横向应变测试数据和体积测试数据。如果省略此参数，则 ![](../graphics/key_eqn00806.gif) 将从横向应变数据和/或体积测试数据中计算。

TEST DATA INPUT

如果 ![](../graphics/key_eqn00792.gif)、![](../graphics/key_eqn00793.gif) 和 ![](../graphics/key_eqn00806.gif) 材料常数要由 Abaqus 从从材料试样上进行的简单测试获取的数据中计算得出，则包含此参数。如果省略此参数，则 ![](../graphics/key_eqn00792.gif)、![](../graphics/key_eqn00793.gif) 和 ![](../graphics/key_eqn00806.gif) 必须直接在数据行上给出。

### **通过给出测试数据来定义弹性体泡沫行为：**

当指定了 TEST DATA INPUT 参数时，此选项不使用数据行。相反，数据在 [*BIAXIAL TEST DATA](ch02abk09.md)、[*PLANAR TEST DATA](ch16abk13.md)、[*SIMPLE SHEAR TEST DATA](ch18abk18.md)、[*UNIAXIAL TEST DATA](ch20abk04.md) 和 [*VOLUMETRIC TEST DATA](ch21abk08.md) 选项下给出。

### **直接定义弹性特性的数据行：**

**如果 N=1 的第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

**如果 N=2 的第一行：**

根据需要重复此数据行，以将材料常数定义为温度的函数。

**如果 N=3 的第一行：**

**如果 N=3 的第二行：**

根据需要重复此数据行对，以将材料常数定义为温度的函数。

**对于 N 的更高值（最多 6）的数据行：**




