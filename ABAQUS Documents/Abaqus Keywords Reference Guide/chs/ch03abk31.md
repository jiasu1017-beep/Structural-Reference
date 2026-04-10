# *CONCRETE DAMAGED PLASTICITY





### *CONCRETE DAMAGED PLASTICITY为混凝土损伤塑性模型定义流动势、屈服面和粘度参数。

此选项用于为混凝土损伤塑性材料模型定义流动势、屈服面和粘度参数。[*CONCRETE DAMAGED PLASTICITY](ch03abk31.md)选项必须与[*CONCRETE TENSION STIFFENING](ch03abk33.md)和[*CONCRETE COMPRESSION HARDENING](ch03abk30.md)选项结合使用。此外，[*CONCRETE TENSION DAMAGE](ch03abk32.md)和/或[*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)选项可用于指定拉伸和/或压缩刚度退化损伤。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据

**级别：**模型

**Abaqus/CAE：**Property模块

##### **参考：**

- ["混凝土损伤塑性"，Abaqus Analysis User's Guide第23.6.3节](../usb/usb-link.md#usb-mat-cconcretedamaged)
- [*CONCRETE TENSION STIFFENING](ch03abk33.md)
- [*CONCRETE COMPRESSION HARDENING](ch03abk30.md)
- [*CONCRETE TENSION DAMAGE](ch03abk32.md)
- [*CONCRETE COMPRESSION DAMAGE](ch03abk29.md)

### **可选参数：**

DEPENDENCIES

将此参数设置为除了温度之外还包括在材料参数定义中的场变量依赖项数。如果省略此参数，则假定材料参数仅取决于温度。请参见["指定场变量依赖性"，Abaqus Analysis User's Guide第21.1.2节"材料数据定义"](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)，以获取更多信息。

### **定义混凝土损伤塑性流动势、屈服面和粘度参数的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数的值大于二时需要）：**

根据需要重复此组数据行，以定义材料参数对温度和其他预定义场变量的依赖关系。




