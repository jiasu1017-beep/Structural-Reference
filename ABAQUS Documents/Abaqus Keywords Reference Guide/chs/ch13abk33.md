# *M1









### *M1定义梁的第一弯曲矩行为。

此选项用于定义梁的第一弯曲矩行为。它只能与[*BEAM GENERAL SECTION](ch02abk05.md)、SECTION=NONLINEAR GENERAL选项结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  

**类型：**模型数据  

**级别：**部件、部件实例  

##### **参考：**

- ["使用通用梁截面定义截面行为，" Abaqus Analysis User's Guide第29.3.7节](../usb/usb-link.md#usb-elm-eusingbeamgensect)
- [*BEAM GENERAL SECTION](ch02abk05.md)

### **可选参数（如果既不包含ELASTIC也不包含LINEAR，则假定为弹塑性响应）：**

DEPENDENCIES

将此参数设置为除温度外矩-曲率关系中包含的场变量依赖数量。如果省略此参数，则假定矩-曲率关系是常数或仅取决于温度。

ELASTIC

如果弯曲矩-曲率关系是非线性但弹性的，则包含此参数。

LINEAR

如果弯曲矩随曲率线性变化，则包含此参数。

### **如果包含LINEAR参数的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于6时需要）：**

根据需要重复此组数据行，以将弯曲刚度定义为温度和其他预定义场变量的函数。

### **如果省略LINEAR参数的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将弯曲矩-曲率关系定义为温度和其他预定义场变量的函数。