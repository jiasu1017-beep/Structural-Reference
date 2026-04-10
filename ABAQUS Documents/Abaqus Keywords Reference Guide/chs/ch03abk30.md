# *CONCRETE COMPRESSION HARDENING





### *CONCRETE COMPRESSION HARDENING为混凝土损伤塑性模型定义压缩强化。

此选项用于为混凝土损伤塑性材料模型定义压缩强化数据。它必须与[*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)和[*CONCRETE TENSION STIFFENING](ch03abk33.md)选项结合使用。此外，[*CONCRETE TENSION DAMAGE](ch03abk32.md)和/或[*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)选项可用于指定拉伸和/或压缩刚度退化损伤。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["混凝土损伤塑性"，Abaqus Analysis User's Guide第23.6.3节](../usb/usb-link.md#usb-mat-cconcretedamaged)
- [*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)
- [*CONCRETE TENSION STIFFENING](ch03abk33.md)
- [*CONCRETE TENSION DAMAGE](ch03abk32.md)
- [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在压缩屈服应力定义中的场变量依赖项数。如果省略此参数，则压缩屈服应力仅取决于非弹性应变、应变率，也可能取决于温度。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

### **定义压缩强化的数据行：**

**第一行：**

每个温度值的第一点必须具有0.0的压碎应变，并给出初始屈服应力值![](../graphics/key_eqn00220.gif)。

**后续行（仅在DEPENDENCIES参数的值大于四时需要）：**

根据需要重复此组数据行，以定义压缩屈服应力对压碎应变、压碎应变率和其他预定义场变量的依赖关系。




