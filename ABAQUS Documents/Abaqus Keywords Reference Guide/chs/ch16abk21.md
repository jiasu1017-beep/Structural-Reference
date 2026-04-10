# *POROUS ELASTIC







### *POROUS ELASTIC指定多孔材料的弹性材料属性。

此选项用于定义多孔材料的弹性参数。

**产品：**Abaqus/Standard  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["多孔材料的弹性行为，" Abaqus Analysis User's Guide第22.3.1节](../usb/usb-link.md#usb-mat-celasticporous)

### **可选参数：**

DEPENDENCIES

将此参数设置为参数定义中包含的场变量依赖数量，不包括温度。如果省略此参数，则假定参数仅依赖于温度。有关更多信息，请参见["指定场变量依赖性"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中。

SHEAR

设置SHEAR=G以使用恒定剪切模量*G*定义偏行为。设置SHEAR=POISSON（默认）以根据体积模量和泊松比计算瞬时剪切模量。泊松比应在数据行上给出。

### **使用恒定剪切模量*G*定义偏行为的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于4时需要）：**

根据需要重复此组数据行，以将材料参数![](../graphics/key_eqn00073.gif)、*G*和![](../graphics/key_eqn01001.gif)定义为温度和场变量的函数。

### **根据体积模量和泊松比定义瞬时剪切模量的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于4时需要）：**

根据需要重复此组数据行，以将材料参数![](../graphics/key_eqn00073.gif)、![](../graphics/key_eqn00579.gif)和![](../graphics/key_eqn01001.gif)定义为温度和场变量的函数。
