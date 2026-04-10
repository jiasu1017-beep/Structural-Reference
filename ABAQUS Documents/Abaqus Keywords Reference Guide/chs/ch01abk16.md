# *AXIAL





### *AXIAL用于定义梁的轴向行为。

此选项只能与[*BEAM GENERAL SECTION](ch02abk05.md)，SECTION=NONLINEAR GENERAL选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  

**类型：**模型数据

**级别：**Part、Part instance

##### **参考：**

- [*BEAM GENERAL SECTION](ch02abk05.md)
- ["使用通用梁截面定义截面行为，" Abaqus Analysis User's Guide第29.3.7节](../usb/usb-link.md#usb-elm-eusingbeamgensect)

### **可选参数（如果既不包含ELASTIC也不包含LINEAR，则假定为弹塑性响应）：**

DEPENDENCIES

将此参数设置为除温度外还包括在轴力-轴应变关系中的场变量依赖项数。如果省略此参数，则假定轴力-轴应变关系是常数或仅取决于温度。参见["在材料数据定义中指定场变量依赖性，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，了解更多信息。

ELASTIC

如果轴力-轴应变关系是非线性但弹性的，请包含此参数。

LINEAR

如果轴力-轴应变关系是线性的，请包含此参数。

### **包含LINEAR参数时的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以将轴向刚度定义为温度和其他预定义场变量的函数。

### **省略LINEAR参数时的数据行：**

**第一行：**

**后续行（仅当DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以将轴力-轴应变关系定义为温度和其他预定义场变量的函数。