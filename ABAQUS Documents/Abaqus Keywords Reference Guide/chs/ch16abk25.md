# *POTENTIAL







### *POTENTIAL定义各向异性屈服/蠕变模型。

此选项用于定义各向异性屈服和蠕变行为的应力比。它只能与[*CREEP](ch03abk85.md)选项、[*PLASTIC](ch16abk14.md)选项（HARDENING=ISOTROPIC、KINEMATIC或COMBINED；[*POTENTIAL](ch16abk24.md)选项只能在Abaqus/Explicit中与COMBINED硬化结合使用）和/或[*VISCOUS](ch21abk06.md)选项定义的材料模型结合使用。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["经典金属塑性，" Abaqus Analysis User's Guide第23.2.1节](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["承受循环加载的金属模型，" Abaqus Analysis User's Guide第23.2.2节](../usb/usb-link.md#usb-mat-chardening)
- ["率相关塑性：蠕变和膨胀，" Abaqus Analysis User's Guide第23.2.4节](../usb/usb-link.md#usb-mat-cratedepcreep)
- ["各向异性屈服/蠕变，" Abaqus Analysis User's Guide第23.2.6节](../usb/usb-link.md#usb-mat-canisoyield)
- ["双层粘塑性，" Abaqus Analysis User's Guide第23.2.11节](../usb/usb-link.md#usb-mat-cviscous)

### **可选参数：**

DEPENDENCIES

将此参数设置为![](../graphics/key_eqn01009.gif)定义中包含的场变量依赖数量，不包括温度。如果省略此参数，则假定各向异性比率是常数或仅依赖于温度。有关更多信息，请参见["指定场变量依赖性"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中。

### **用于定义应力比的数据行：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于1时需要）：**

根据需要重复此组数据行，以将![](../graphics/key_eqn01009.gif)定义为温度和其他场变量的函数。
