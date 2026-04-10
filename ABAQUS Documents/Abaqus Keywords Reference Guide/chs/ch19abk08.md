# *TORQUE





### *TORQUE定义梁的扭转行为。

此选项仅能与[*BEAM GENERAL SECTION](ch02abk05.md)、SECTION=NONLINEAR GENERAL选项一起使用。

**产品：**Abaqus/Standard  Abaqus/Explicit

**类型：**模型数据

**级别：**部件、部件实例

##### **参考：**

- ["使用通用梁截面定义截面行为," Section 29.3.7 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-elm-eusingbeamgensect)
- [*BEAM GENERAL SECTION](ch02abk05.md)

### **可选参数（如果既不包含ELASTIC也不包含LINEAR，则假定为弹塑性响应）：**

DEPENDENCIES

将此参数设置为除了温度之外扭矩-扭转关系中的场变量依赖项数。如果省略此参数，则假定扭矩-扭转关系是恒定的或仅取决于温度。请参见["材料数据定义," Section 21.1.2 of the Abaqus Analysis User's Guide](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中的"指定场变量依赖性"。

ELASTIC

如果扭矩-扭转关系是非线性但弹性的，则包含此参数。

LINEAR

如果扭矩随扭转线性变化，则包含此参数。

### **如果包含LINEAR参数的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于六时需要）：**

根据需要重复此组数据行，以定义扭转刚度对温度和其他预定义场变量的函数关系。

### **如果省略LINEAR参数的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以定义扭转行为对温度和其他预定义场变量的函数关系。





