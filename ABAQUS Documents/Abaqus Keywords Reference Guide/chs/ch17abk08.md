# *RATE DEPENDENT







### *RATE DEPENDENT定义率相关粘塑性模型。

此选项只能作为[*PLASTIC](ch16abk14.md)，HARDENING=ISOTROPIC选项的子选项使用；或者作为[*PLASTIC](ch16abk14.md)，HARDENING=JOHNSON COOK选项；或者作为[*DRUCKER PRAGER HARDENING](ch04abk36.md)选项；或者作为[*CRUSHABLE FOAM HARDENING](ch03abk88.md)选项的子选项使用，以在材料模型中引入应变率依赖性。

**产品：**Abaqus/Standard  Abaqus/Explicit  Abaqus/CAE  

**类型：**模型数据  

**级别：**模型  

**Abaqus/CAE：**属性模块

##### **参考：**

- ["率相关屈服，" Abaqus Analysis User's Guide第23.2.3节](../usb/usb-link.md#usb-mat-cratedependent)
- ["经典金属塑性，" Abaqus Analysis User's Guide第23.2.1节](../usb/usb-link.md#usb-mat-cmetalplastic)
- ["Johnson-Cook塑性，" Abaqus Analysis User's Guide第23.2.7节](../usb/usb-link.md#usb-mat-cjohnsoncook)
- ["扩展Drucker-Prager模型，" Abaqus Analysis User's Guide第23.3.1节](../usb/usb-link.md#usb-mat-cdruckerprager)
- ["可压碎泡沫塑性模型，" Abaqus Analysis User's Guide第23.3.5节](../usb/usat-cmat-ccrushfoam)

### **可选参数：**

DEPENDENCIES

在Abaqus/Explicit分析中，此参数仅与TYPE=POWER LAW或TYPE=YIELD RATIO相关。

将此参数设置为材料参数定义中的场变量依赖数量，不包括温度。如果省略此参数，则假定率相关材料行为仅依赖于温度。有关更多信息，请参见["指定场变量依赖性"在"材料数据定义，" Abaqus Analysis User's Guide第21.1.2节](../usb/usb-link.md#usb-mat-cmaterialdata-fvdepen)中。

TYPE

设置TYPE=POWER LAW（默认）以指定Cowper-Symonds过应力幂律。

设置TYPE=JOHNSON COOK以指定Johnson-Cook率依赖性（此选项不能与可压碎泡沫塑性模型一起使用）。

设置TYPE=YIELD RATIO以输入屈服应力比。

如果此选项与[*CRUSHABLE FOAM](ch03abk87.md)选项结合使用，则静态硬化关系必须在[*CRUSHABLE FOAM HARDENING](ch03abk88.md)选项上定义。

### **定义过应力幂律参数的数据行（TYPE=POWER LAW）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将材料参数定义为温度和其他场变量的函数。

### **定义Johnson-Cook率参数的数据行（TYPE=JOHNSON COOK）：**

**第一行（也是唯一一行）：**

### **定义屈服应力比的数据行（TYPE=YIELD RATIO）：**

**第一行：**

**后续行（仅在DEPENDENCIES参数值大于5时需要）：**

根据需要重复此组数据行，以将屈服应力比定义为等效塑性应变以及温度和其他预定义场变量（如需要）的函数。
