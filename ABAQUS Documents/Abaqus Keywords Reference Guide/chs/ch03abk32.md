# *CONCRETE TENSION DAMAGE





### *CONCRETE TENSION DAMAGE为混凝土损伤塑性模型定义裂后损伤属性。

此选项用于为混凝土损伤塑性材料模型定义裂后损伤（或刚度退化）属性。[*CONCRETE TENSION DAMAGE](ch03abk32.md)选项必须与[*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)、[*CONCRETE TENSION STIFFENING](ch03abk33.md)和[*CONCRETE COMPRESSION HARDENING](ch03abk30.md)选项结合使用。此外，[*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)选项可用于指定压缩刚度退化损伤。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["混凝土损伤塑性"，Abaqus Analysis User's Guide第23.6.3节](../usb/usb-link.md#usb-mat-cconcretedamaged)
- [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)
- [*CONCRETE TENSION STIFFENING](ch03abk33.md)
- [*CONCRETE COMPRESSION HARDENING](ch03abk30.md)
- [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)

### **可选参数：**

COMPRESSION RECOVERY

此参数用于定义刚度恢复因子![](../graphics/key_eqn00233.gif)，该因子确定在载荷从拉伸变为压缩时恢复的压缩刚度量。如果![](../graphics/key_eqn00234.gif)，材料完全恢复压缩刚度；如果![](../graphics/key_eqn00235.gif)，则没有刚度恢复。![](../graphics/key_eqn00233.gif)的中间值![](../graphics/key_eqn00236.gif)会导致压缩刚度的部分恢复。默认值为![](../graphics/key_eqn00237.gif)，对应于假设当裂纹闭合时，压缩刚度不受拉伸损伤的影响。

DEPENDENCIES

将此参数设置为除了温度之外还包括在拉伸损伤定义中的场变量依赖项数。如果省略此参数，则假定拉伸损伤行为仅取决于温度。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

TYPE

设置TYPE=STRAIN（默认值）以将拉伸损伤变量指定为开裂应变的函数。

设置TYPE=DISPLACEMENT以将拉伸损伤变量指定为开裂位移的函数。

### **如果将拉伸损伤指定为开应变函数的数据行（TYPE=STRAIN）：**

**第一行：**

每个温度值的第一点必须具有0.0的开裂应变和0.0的拉伸损伤值。

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以定义拉伸损伤行为对开裂应变、温度和其他预定义场变量的依赖关系。

### **如果将拉伸损伤指定为开裂位移函数的数据行（TYPE=DISPLACEMENT）：**

**第一行：**

每个温度值的第一点必须具有0.0的开裂位移和0.0的拉伸损伤值。

**后续行（仅在DEPENDENCIES参数的值大于五时需要）：**

根据需要重复此组数据行，以定义拉伸损伤行为对开裂位移、温度和其他预定义场变量的依赖关系。




