# *CONCRETE TENSION STIFFENING





### *CONCRETE TENSION STIFFENING为混凝土损伤塑性模型定义裂后属性。

此选项用于为混凝土损伤塑性材料模型定义开裂和裂后属性。[*CONCRETE TENSION STIFFENING](ch03abk33.md)选项必须与[*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)和[*CONCRETE COMPRESSION HARDENING](ch03abk30.md)选项结合使用。此外，[*CONCRETE TENSION DAMAGE](ch03abk32.md)和/或[*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)选项可用于指定拉伸和/或压缩刚度退化损伤。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["混凝土损伤塑性"，Abaqus Analysis User's Guide第23.6.3节](../usb/usb-link.md#usb-mat-cconcretedamaged)
- [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)
- [*CONCRETE COMPRESSION HARDENING](ch03abk30.md)
- [*CONCRETE TENSION DAMAGE](ch03abk32.md)
- [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在裂后行为定义中的场变量依赖项数。如果省略此参数，则裂后应力仅取决于开裂应变、应变率，也可能取决于温度。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

TYPE

设置TYPE=STRAIN（默认值）以通过输入失效后应力/开裂-应变关系来指定裂后行为。

设置TYPE=DISPLACEMENT以通过输入失效后应力/开裂-位移关系来定义裂后行为。

设置TYPE=GFI以通过输入失效应力![](../graphics/key_eqn00241.gif)和断裂能![](../graphics/key_eqn00242.gif)来定义裂后行为。

### **如果包含TYPE=STRAIN参数时的数据行（默认值）：**

**第一行：**

每个温度值的第一点必须具有0.0的开裂应变，并给出失效应力值![](../graphics/key_eqn00241.gif)。

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以定义裂后行为对温度和其他预定义场变量的依赖关系。

### **如果包含TYPE=DISPLACEMENT参数时的数据行：**

**第一行：**

每个温度值的第一点必须具有0.0的开裂位移，并给出失效应力值。

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以定义裂后行为对温度和其他预定义场变量的依赖关系。

### **如果包含TYPE=GFI参数时的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以定义裂后行为对温度和其他预定义场变量的依赖关系。




